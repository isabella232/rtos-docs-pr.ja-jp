---
title: 第 2 章 - Azure RTOS NetX Duo SNMP エージェントのインストールと使用
description: この章では、NetX Duo SNMP エージェント コンポーネントのインストール、セットアップ、および使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f011b73217c7f413dd19c555e9c2d40dace305ee
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810580"
---
# <a name="chapter-2---installation-and-use-of-the-azure-rtos-netx-duo-snmp-agent"></a>第 2 章 - Azure RTOS NetX Duo SNMP エージェントのインストールと使用

この章では、Azure RTOS NetX Duo SNMP エージェント コンポーネントのインストール、セットアップ、および使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品ディストリビューション

NetX Duo 用 SNMP エージェントは [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。 パッケージに含まれている 4 つのソース ファイル、1 つのインクルード ファイル、このドキュメントを含む PDF ファイルを以下に示します。

- **nxd_snmp.h** NetX Duo 用 SNMP のヘッダー ファイル
- **demo_snmp_helper.h** SNMP MIB データのヘッダー ファイル
- **nxd_snmp.c** NetX Duo 用 SNMP エージェントの C ソース ファイル
- **nx_md5.c** MD5 ダイジェスト アルゴリズム
- **nx_sha.c** SHA ダイジェストアルゴリズム
- **nx_des.c** DES 暗号化アルゴリズム
- **nxd_snmp.pdf** NetX Duo 用 SNMP エージェントのユーザー ガイド
- **demo_netxduo_snmp.c** 簡単な SNMP デモ
- **demo_netxduo_mib2.c** 簡単な MIB2 デモ (MIB に IPv6 アドレス要素がある)
- **demo_snmp_helper.h** MIB 要素を定義するヘッダーファイル

## <a name="netx-duo-snmp-agent-installation"></a>NetX Duo SNMP エージェントのインストール

NetX Duo SNMP を使用するためには、前述のディストリビューション全体を、NetX Duo がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX Duo が “ *\threadx\arm7\green*” ディレクトリにインストールされている場合は、*nxd_snmp.h*、*nxd_snmp.c*、*nx_md5.c、nx_sha.c* および nx_ *des.c* の各ファイルをこのディレクトリにコピーする必要があります。

## <a name="using-the-netx-duo-snmp-agent"></a>NetX Duo SNMP エージェントを使用する

アプリケーションには、*nxd_snmp.c*、*nx_md5.c、nx_sha.c*、および *nx_des.c* がビルド プロジェクトで必要です。 アプリケーション コードには、*nx_api.h* をインクルードした後に *nxd_snmp.h* もインクルードして SNMP サービスを呼び出せるようにする必要があります。 これらのファイルを他のアプリケーション ファイルと同じ方法でコンパイルし、そのオブジェクト フォームを NetX Duo ライブラリとリンクする必要があります。 これが NetX Duo SNMP を使用するために必要なすべてです。

> [!NOTE]
> ***NX_SNMP_NO_SECURITY** がビルド プロセスで指定されている場合、nx_md5.c、nx_sha.c、および nx_des.c の各ファイルは必要ありません。*

> [!NOTE]
> NetX Duo SNMP が UDP サービスを利用するため、SNMP を使用する前に *nx_udp_enable* の呼び出しで UDP を有効にする必要があります。

## <a name="small-example-system"></a>小規模システムの例

NetX Duo SNMP エージェントを使用する方法の例を、下の図 1.0 で説明します。 この例で、SNMP インクルード ファイル *nxd_snmp.h* は 6 行目で組み込まれています。 MIB データベース要素を定義するヘッダー ファイル (*demo_snmp_helper.h)* は、8 行目で組み込まれています。 MIB の定義は 32 行目からです。 次に、SNMP エージェントが 129 行目の "*tx_application_define*" で作成されています。 SNMP エージェント制御ブロック "*my_agent*" は、先に 18 行目でグローバル変数として定義されていることに注意してください。 IPv6 が有効な場合、IPv6 アドレスは IP インスタンスに 166 から 223 行で登録されています。 SNMP エージェントが 229 行目で開始しています。 SNMP マネージャーの GET、GETNEXT、および SET の各要求の SNMP オブジェクト コールバック定義、ユーザー名および MIB の更新要求が、250 行目から処理されます。 この例では、認証が行なわれません。

> [!NOTE]
> *下の MIB2 テーブルは単なる例です。アプリケーションは異なる MIB を使用して、それを別のファイルに含めたり、さらには、GET、GETNEXT、または SET の処理を、アプリケーションの要件に従って定義したりすることができます。*

```c
/* This is a small demo of the NetX SNMP Agent on the high-performance NetX TCP/IP  
   stack. This demo relies on ThreadX and NetX to show simple SNMP the SNMP
   GET/GETNEXT/SET requests on MIB-2 objects.  */

#include  "tx_api.h"
#include  "nx_api.h"
#include  "nxd_snmp.h"
#include  "demo_snmp_helper.h"

#define     DEMO_STACK_SIZE         4096
#define     AGENT_PRIMARY_ADDRESS   IP_ADDRESS(192, 2, 2, 66)

/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_SNMP_AGENT           my_agent;


/* Indicate if using IPv6 to communicate with SNMP servers. Note that
   IPv6 must be enabled in the NetX Duo library first. Further, IPv6
   and ICMPv6 services are enabled before starting the SNMP agent. */
#define USE_IPV6


/* Define authentication and privacy keys.  */

#ifdef AUTHENTICATION_REQUIRED
NX_SNMP_SECURITY_KEY    my_authentication_key;
#endif

#ifdef PRIVACY_REQUIRED
NX_SNMP_SECURITY_KEY    my_privacy_key;
#endif

/* Define an error counter variable. */
UINT error_counter = 0;

/* This binds a secondary interfaces to the primary IP network interface 
   if SNMP is required for required for that interface. */
/* #define  MULTI_HOMED_DEVICE */

/* Define function prototypes.  A generic ram driver is used in this demo.  However
   to properly run an SNMP agent demo, a real driver should be substituted. */

VOID    thread_agent_entry(ULONG thread_input);
VOID    _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);
UINT    mib2_get_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_getnext_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_set_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data);
UINT    mib2_username_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *username);
VOID    mib2_variable_update(NX_IP *ip_ptr, NX_SNMP_AGENT *agent_ptr);


UCHAR context_engine_id[] = {0x80, 0x00, 0x0d, 0xfe, 0x03, 0x00, 0x11, 0x23, 0x23, 
                             0x44, 0x55};
UINT  context_engine_size = 11;
UCHAR context_name[] = {0x69, 0x6e, 0x69, 0x74, 0x69, 0x61, 0x6c};
UINT  context_name_size = 7;

/* Define main entry point.  */

int main()
{

   /* Enter the ThreadX kernel.  */
   tx_kernel_enter();
}


/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

UCHAR   *pointer;
UINT    status;


   /* Setup the working pointer.  */
   pointer =  (UCHAR *) first_unused_memory;

   status = tx_thread_create(&thread_0, "agent thread", thread_agent_entry, 0,  
            pointer, DEMO_STACK_SIZE, 
            4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);
   if (status != NX_SUCCESS)
   {
      return;
   }

   pointer =  pointer + DEMO_STACK_SIZE;


   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create packet pool.  */
   status = nx_packet_pool_create(&pool_0, "NetX Packet Pool 0", 2048, 
                                   pointer, 20000);

   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer = pointer + 20000;
  
   /* Create an IP instance.  */
   status = nx_ip_create(&ip_0, "SNMP Agent IP Instance", AGENT_PRIMARY_ADDRESS, 
                        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
                        pointer, 4096, 1);

   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer =  pointer + 4096;
  
   /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
   nx_arp_enable(&ip_0, (void *) pointer, 1024);
   pointer = pointer + 1024;

   /* Enable UPD processing for IP instance.  */
   nx_udp_enable(&ip_0);
  
   /* Enable ICMP for ping.  */
   nx_icmp_enable(&ip_0);
  
   /* Create an SNMP agent instance.  */
   status = nx_snmp_agent_create(&my_agent, "SNMP Agent", &ip_0, pointer, 4096, 
                                 &pool_0, 
                                 mib2_username_processing, mib2_get_processing, 
                                 mib2_getnext_processing, 
                                 mib2_set_processing);


  
   if (status != NX_SUCCESS)
   {
      return;
   }
  
   pointer =  pointer + 4096;
  
   status = nx_snmp_agent_context_engine_set(&my_agent, context_engine_id, 
                                             context_engine_size);
  
   if (status != NX_SUCCESS)
   {
      error_counter++;
   }
  
   return;
}
  
VOID thread_agent_entry(ULONG thread_input)
{
  
#ifdef USE_IPV6
UINT        iface_index, address_index;
UINT        status;
NXD_ADDRESS agent_ipv6_address;
#endif
  
  
      /* Allow NetX time to get initialized. */
      tx_thread_sleep(100);
  
      /* If using IPv6, enable IPv6 and ICMPv6 services and get IPv6 addresses 
         registered with NetX Dou. */
  
#ifdef USE_IPV6
  
      /* Enable IPv6 on the IP instance. */
      status = nxd_ipv6_enable(&ip_0);
   
      /* Check for enable errors.  */
      if (status)
      {
  
         error_counter++;
         return;
      }
      /* Enable ICMPv6 on the IP instance. */
      status = nxd_icmp_enable(&ip_0);
  
      /* Check for enable errors.  */
      if (status)
      {
  
         error_counter++;
         return;
      }
  
      agent_ipv6_address.nxd_ip_address.v6[3] = 0x101;
      agent_ipv6_address.nxd_ip_address.v6[2] = 0x0;
      agent_ipv6_address.nxd_ip_address.v6[1] = 0x0000f101;
      agent_ipv6_address.nxd_ip_address.v6[0] = 0x20010db8;
      agent_ipv6_address.nxd_ip_version = NX_IP_VERSION_V6;
  
      /* Set the primary interface for our DNS IPv6 addresses. */
      iface_index = 0;
  
      /* This assumes we are using the primary network interface (index 0). */
      status = nxd_ipv6_address_set(&ip_0, iface_index, NX_NULL, 10, &address_index);
  
      /* Check for link local address set error.  */
      if (status) 
      {
  
         error_counter++;
         return;
      }
  
      /* Set the host global IP address. We are assuming a 64 
         bit prefix here but this can be any value (< 128). */
      status = nxd_ipv6_address_set(&ip_0, iface_index, &agent_ipv6_address, 64, 
                                    &address_index);
  
      /* Check for global address set error.  */
      if (status) 
      {
  
         error_counter++;
         return;
      }

      /* Wait while NetX Duo validates the link local and global address. */
      tx_thread_sleep(500);
#endif
  
#ifdef AUTHENTICATION_REQUIRED

      /* Create an authentication key.  */
      nx_snmp_agent_md5_key_create(&my_agent, "authpassword", &my_authentication_key);
  
      /* Use the authentication key.  */
      nx_snmp_agent_authenticate_key_use(&my_agent, &my_authentication_key);
#endif
  
#ifdef PRIVACY_REQUIRED
  
      /* Create a privacy key.  */
      nx_snmp_agent_md5_key_create(&my_agent, "privpassword", &my_privacy_key);
  
      /* Use the privacy key.  */
      nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);
#endif
  
      /* Start the SNMP instance.  */
      nx_snmp_agent_start(&my_agent);
  
}
  
/* Define the application's GET processing routine.  */
  
UINT    mib2_get_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
      printf("SNMP Manager GET Request For:  %s", object_requested);
  
      /* Loop through the sample MIB to see if we have information for the supplied 
         variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the matching entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Was it found?  */
         if (status == NX_SUCCESS)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SUCCESS)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
      /* Determine if the entry has a get function.  */
      if (mib2_mib[i].object_get_callback)
      {
  
         /* Yes, call the get function.  */
         status =  (mib2_mib[i].object_get_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
      }
      else
      {
  
         printf(" NO GET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's GETNEXT processing routine.  */
  
UINT    mib2_getnext_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                                NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
   printf("SNMP Manager GETNEXT Request For:  %s", object_requested);
  
   /* Loop through the sample MIB to see if we have information for the supplied 
      variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the next entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Is the next entry the mib greater?  */
         if (status == NX_SNMP_NEXT_ENTRY)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SNMP_NEXT_ENTRY)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
  
      /* Copy the new name into the object.  */
      nx_snmp_object_copy(mib2_mib[i].object_name, object_requested);
  
      printf(" Next Name is: %s", object_requested);
  
      /* Determine if the entry has a get function.  */
      if (mib2_mib[i].object_get_callback)
      {
  
         /* Yes, call the get function.  */
         status =  (mib2_mib[i].object_get_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
  
         /* Determine if the object data indicates an end-of-mib condition.  */
         if (object_data -> nx_snmp_object_data_type == NX_SNMP_END_OF_MIB_VIEW)
         {
  
            /* Copy the name supplied in the mib table.  */
            nx_snmp_object_copy(mib2_mib[i].object_value_ptr, object_requested);
         }
      }
      else
      {
  
         printf(" NO GET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's SET processing routine.  */
  
UINT    mib2_set_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *object_requested, 
                            NX_SNMP_OBJECT_DATA *object_data)
{
  
UINT    i;
UINT    status;
  
  
   printf("SNMP Manager SET Request For:  %s", object_requested);
  
   /* Loop through the sample MIB to see if we have information for the supplied variable.  */
      i =  0;
      status =  NX_SNMP_ERROR;
      while (mib2_mib[i].object_name)
      {
  
         /* See if we have found the matching entry.  */
         status =  nx_snmp_object_compare(object_requested, mib2_mib[i].object_name);
  
         /* Was it found?  */
         if (status == NX_SUCCESS)
         {
  
            /* Yes it was found.  */
            break;
         }
  
         /* Move to the next index.  */
         i++;
      }
  
      /* Determine if a not found condition is present.  */
      if (status != NX_SUCCESS)
      {
  
         printf(" NO SUCH NAME!\n");
  
         /* The object was not found - return an error.  */
         return(NX_SNMP_ERROR_NOSUCHNAME);
      }
  
  
      /* Determine if the entry has a set function.  */
      if (mib2_mib[i].object_set_callback)
      {
  
         /* Yes, call the set function.  */
         status =  (mib2_mib[i].object_set_callback)(mib2_mib[i].object_value_ptr, 
                                                     object_data);
      }
      else
      {
  
         printf(" NO SET FUNCTION!");
  
         /* No get function, return no access.  */
         status =  NX_SNMP_ERROR_NOACCESS;
      }
  
      printf("\n");

      /* Return the status.  */
      return(status);
}
  
  
/* Define the application's authentication routine.  */
  
UINT  mib2_username_processing(NX_SNMP_AGENT *agent_ptr, UCHAR *username)
{
  
      printf("Username is:  %s\n", username);
  
      /* Update MIB-2 objects. In this example, it is only the SNMP objects.  */
      mib2_variable_update(&ip_0, &my_agent);
  
      /* No authentication is done, just return success!  */
      return(NX_SUCCESS);
}
  
  
/* Define the application's update routine.  */ 
  
VOID  mib2_variable_update(NX_IP *ip_ptr, NX_SNMP_AGENT *agent_ptr)
{
  
      /* Update the snmp parameters.  */
      snmpInPkts =                agent_ptr -> nx_snmp_agent_packets_received;
      snmpOutPkts =               agent_ptr -> nx_snmp_agent_packets_sent;
      snmpInBadVersions =         agent_ptr -> nx_snmp_agent_invalid_version;
      snmpInBadCommunityNames =   agent_ptr -> nx_snmp_agent_authentication_errors;
      snmpInBadCommunityUsers =   agent_ptr -> nx_snmp_agent_username_errors; 
      snmpInASNParseErrs =        agent_ptr -> nx_snmp_agent_internal_errors;
      snmpInTotalReqVars =        agent_ptr -> nx_snmp_agent_total_get_variables;
      snmpInTotalSetVars =        agent_ptr -> nx_snmp_agent_total_set_variables;
      snmpInGetRequests =         agent_ptr -> nx_snmp_agent_get_requests;
      snmpInGetNexts =            agent_ptr -> nx_snmp_agent_getnext_requests;
      snmpInSetRequests =         agent_ptr -> nx_snmp_agent_set_requests;
      snmpOutTooBigs =            agent_ptr -> nx_snmp_agent_too_big_errors;
      snmpOutNoSuchNames =        agent_ptr -> nx_snmp_agent_no_such_name_errors;
      snmpOutBadValues =          agent_ptr -> nx_snmp_agent_bad_value_errors;
      snmpOutGenErrs =            agent_ptr -> nx_snmp_agent_general_errors;
      snmpOutTraps =              agent_ptr -> nx_snmp_agent_traps_sent;
}   
```
図 1.0 NetX Duo で SNMP エージェントを使用する例

## <a name="configuration-options"></a>構成オプション

NetX Duo 用に SNMP を構築するためのいくつかの構成オプションがあります。 以下に示すすべてのオプションの一覧で、それぞれのオプションについて詳しく説明します。  
  
| 定義                     | 意味                                                                                                                                                                                                                                                                        |
|----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **NX_SNMP_AGENT_PRIORITY**     | SNMP エージェント スレッドの優先度。 既定では、この値は 16 に定義されており、優先度 16 を示します。                                                                                                                                                                         |
| **NX_SNMP_TYPE_OF_SERVICE**    | SNMP UDP 応答に必要なサービスの種類。 既定では、この値は NX_IP_NORMAL に定義されており、通常の IP パケット サービスを示します。 この定義を、*nxd_snmp.h.* を含める前にアプリケーションで設定できます。                                                       |
| **NX_SNMP_FRAGMENT_OPTION**    | SNMP UDP 要求のフラグメント有効化。 既定では、この値は NX_DONT_FRAGMENT で、SNMP UDP のフラグメント化が無効になります。 この定義を、*nxd_snmp.h.* を含める前にアプリケーションで設定できます。                                                                                 |
| **NX_SNMP_TIME_TO_LIVE**       | 期限が切れるまでの有効期間を指定します。 既定値は 0x80 に設定されていますが、*nxd_snmp.h* を含める前に再定義できます。                                                                                                                                         |
| **NX_SNMP_AGENT_TIMEOUT**      | 内部サービスが中断する ThreadX ティックの数を指定します。 既定値は 100 に設定されていますが、*nxd_snmp.h* を含める前に再定義できます。                                                                                                         |
| **NX_SNMP_MAX_OCTET_STRING**   | SNMP エージェントのオクテット文字列で許容される最大バイト数を指定します。 既定値は 255 に設定されていますが、*nxd_snmp.h* を含める前に再定義できます。                                                                                                    |
| **NX_SNMP_MAX_CONTEXT_STRING** | SNMP エージェントのコンテキスト エンジン文字列の最大バイト数を指定します。 既定値は 32 に設定されていますが、*nxd_snmp.h* を含める前に再定義できます。                                                                                                    |
| **NX_SNMP_MAX_USER_NAME**      | ユーザー名 (コミュニティ文字列を含む) の最大バイト数を指定します。 既定値は 64 に設定されていますが、*nxd_snmp.h* を含める前に再定義できます。                                                                                                      |
| **NX_SNMP_MAX_SECURITY_KEY**   | セキュリティ キー文字列で許容されるバイト数を指定します。 既定値は 64 に設定されていますが、*nxd_snmp.h* を含める前に再定義できます。                                                                                                                          |
| **NX_SNMP_PACKET_SIZE**        | SNMP エージェント作成時に指定されたプール内のパケットの最小サイズを指定します。 最小サイズは、完全な SNMP ペイロードをひとつのパケットに含められるようにするために必要です。 既定値は 560 に設定されていますが、*nxd_snmp.h* を含める前に再定義できます。 |
| **NX_SNMP_AGENT_PORT**         | SNMP マネージャー要求を受け取る UDP ポートを指定します。 既定のポートは UDP ポート 161 ですが、*nxd_snmp.h* を含める前に再定義できます。                                                                                                                             |
| **NX_SNMP_MANAGER_TRAP_PORT**  | SNMP エージェントのトラップ要求の送信先 UDP ポートを指定します。 既定のポートは UDP ポート 162 ですが、*nxd_snmp.h* を含める前に再定義できます。                                                                                                                           |
| **NX_SNMP_MAX_TRAP_NAME**      | トラップ メッセージと共に送信されるユーザー名を保持する配列のサイズを指定します。 既定値は 64 です。                                                                                                                                                                         |
| **NX_SNMP_MAX_TRAP_KEY**       | トラップ メッセージの認証およびプライバシー キーのサイズを指定します。 既定値は 64 です。                                                                                                                                                                          |
| **NX_SNMP_TIME_INTERVAL**      | これにより、SNMP 受信パケットの処理間に SNMP スレッド タスクによって実行されるスリープ間隔 (タイマー刻み) が決まります。 既定値は 100 です。 このスリープ期間中、ホスト アプリケーションは SNMP API サービスにアクセスできます。                                           |
| **NX_SNMP_DISABLE_V1**         | 定義されると、これにより *nxd_snmp.c* のすべての SNMP バージョン 1 処理が削除されます。 既定では、これは定義されていません。                                                                                                                                                                         |
| **NX_SNMP_DISABLE_V2**         | 定義されると、これにより *nxd_snmp.c* のすべての SNMP バージョン 2 処理が削除されます。 既定では、これは定義されていません。                                                                                                                                                                         |
| **NX_SNMP_DISABLE_V3**         | 定義されると、これにより *nxd_snmp.c* のすべての SNMPv3 処理が削除されます。 既定では、これは定義されていません。                                                                                                                                                                                 |