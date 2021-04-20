---
title: 付録 - ポート固有の例
description: この記事では、ThreadX モジュールのポート固有の例を示します。
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c2324a2057bf2ddb2d255b2ff611d34fc664560a
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549812"
---
# <a name="appendix---port-specific-examples"></a><span data-ttu-id="793fc-103">付録 - ポート固有の例</span><span class="sxs-lookup"><span data-stu-id="793fc-103">Appendix - Port-specific examples</span></span>

## <a name="arm11-processor"></a><span data-ttu-id="793fc-104">ARM11 プロセッサ</span><span class="sxs-lookup"><span data-stu-id="793fc-104">ARM11 processor</span></span>

### <a name="arm11-using-gcc"></a><span data-ttu-id="793fc-105">GCC を使用した ARM11</span><span class="sxs-lookup"><span data-stu-id="793fc-105">ARM11 using GCC</span></span>

#### <a name="module-preamble-for-arm11-using-gcc"></a><span data-ttu-id="793fc-106">GCC を使用した ARM11 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-106">Module preamble for ARM11 using GCC</span></span>

```armasm
    .arm
    .section .preamble, "ax"

    /* Define the module preamble.  */

    .global _txm_module_preamble
_txm_module_preamble:
    .word       0x4D4F4455                                      @ Module ID
    .word       0x5                                             @ Module Major Version
    .word       0x6                                             @ Module Minor Version
    .word       32                                              @ Module Preamble Size in 32-bit words
    .word       0x12345678                                      @ Module ID (application defined)
    .word       0x02000000                                      @ Module Properties where:
                                                                @   Bits 31-24: Compiler ID
                                                                @           0 -> IAR
                                                                @           1 -> ARM
                                                                @           2 -> GNU
    .word       _txm_module_thread_shell_entry - . - 0          @ Module Shell Entry Point
    .word       demo_module_start - . - 0                       @ Module Start Thread Entry Point
    .word       0                                               @ Module Stop Thread Entry Point
    .word       1                                               @ Module Start/Stop Thread Priority
    .word       1024                                            @ Module Start/Stop Thread Stack Size
    .word       _txm_module_callback_request_thread_entry - . - 0   @ Module Callback Thread Entry
    .word       1                                               @ Module Callback Thread Priority
    .word       1024                                            @ Module Callback Thread Stack Size
    .word       __code_size__                                   @ Module Code Size
    .word       __data_size__                                   @ Module Data Size
    .word       0                                               @ Reserved 0
    .word       0                                               @ Reserved 1
    .word       0                                               @ Reserved 2
    .word       0                                               @ Reserved 3
    .word       0                                               @ Reserved 4
    .word       0                                               @ Reserved 5
    .word       0                                               @ Reserved 6
    .word       0                                               @ Reserved 7  
    .word       0                                               @ Reserved 8  
    .word       0                                               @ Reserved 9
    .word       0                                               @ Reserved 10
    .word       0                                               @ Reserved 11
    .word       0                                               @ Reserved 12
    .word       0                                               @ Reserved 13
    .word       0                                               @ Reserved 14
    .word       0                                               @ Reserved 15
```

#### <a name="module-properties-for-arm11-using-gcc"></a><span data-ttu-id="793fc-107">GCC を使用した ARM11 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-107">Module properties for ARM11 using GCC</span></span>

| <span data-ttu-id="793fc-108">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-108">Bit</span></span> | <span data-ttu-id="793fc-109">値</span><span class="sxs-lookup"><span data-stu-id="793fc-109">Value</span></span> | <span data-ttu-id="793fc-110">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-110">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-111">[23-0]</span><span class="sxs-lookup"><span data-stu-id="793fc-111">[23-0]</span></span> | <span data-ttu-id="793fc-112">0</span><span class="sxs-lookup"><span data-stu-id="793fc-112">0</span></span> | <span data-ttu-id="793fc-113">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-113">Reserved</span></span>
| <span data-ttu-id="793fc-114">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-114">[31-24]</span></span> | <br /><span data-ttu-id="793fc-115">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-115">0x00</span></span><br /><span data-ttu-id="793fc-116">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-116">0x01</span></span><br /><span data-ttu-id="793fc-117">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-117">0x02</span></span> | <span data-ttu-id="793fc-118">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-118">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-119">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-119">IAR</span></span><br /><span data-ttu-id="793fc-120">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-120">ARM</span></span><br /><span data-ttu-id="793fc-121">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-121">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-gcc"></a><span data-ttu-id="793fc-122">GCC を使用した ARM11 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-122">Module linker for ARM11 using GCC</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x080F0000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0x64001800, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x080F0000;
  __FLASH_segment_end__   = 0x080FFFFF;
  __RAM_segment_start__   = 0x64001800;
  __RAM_segment_end__     = 0x64011800;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  }
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);

  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-arm11-using-gcc"></a><span data-ttu-id="793fc-123">GCC を使用した ARM11 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-123">Building Modules for ARM11 using GCC</span></span>

<span data-ttu-id="793fc-124">GCC を使用して ARM11 モジュールをビルドする簡単なコマンド ラインの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-124">A simple command-line example for building an ARM11 module using GCC:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 txm_module_preamble.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=arm1136j-s -msingle-pic-base -fPIC -mpic-register=r9 demo_threadx_module.c
arm-none-eabi-ld -A arm1136j-s -T demo_threadx_module.ld txm_module_preamble.o gcc_setup.o demo_threadx_module.o txm.a txm.a -o demo_threadx_module.out -M > demo_threadx_module.map
```

#### <a name="thread-extension-definition-for-arm11-using-gcc"></a><span data-ttu-id="793fc-125">GCC を使用した ARM11 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-125">Thread extension definition for ARM11 using GCC</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-gcc"></a><span data-ttu-id="793fc-126">GCC を使用した ARM11 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-126">Building Module Manager for ARM11 using GCC</span></span>

<span data-ttu-id="793fc-127">例は提供されていません。</span><span class="sxs-lookup"><span data-stu-id="793fc-127">No example is provided.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-gcc"></a><span data-ttu-id="793fc-128">GCC を使用した ARM11 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-128">Attributes for external memory enable API for ARM11 using GCC</span></span>

<span data-ttu-id="793fc-129">この機能はこのポートで有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="793fc-129">This feature not enabled on this port.</span></span>

### <a name="arm11-using-ac5"></a><span data-ttu-id="793fc-130">AC5 を使用した ARM11</span><span class="sxs-lookup"><span data-stu-id="793fc-130">ARM11 using AC5</span></span>

#### <a name="module-preamble-for-arm11-using-ac5"></a><span data-ttu-id="793fc-131">AC5 を使用した ARM11 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-131">Module preamble for ARM11 using AC5</span></span>

```armasm
    AREA  Init, CODE, READONLY

;    /* Define public symbols.  */

    EXPORT __txm_module_preamble

;    /* Define application-specific start/stop entry points for the module.  */

    IMPORT demo_module_start

;    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|

__txm_module_preamble
        DCD       0x4D4F4455                                        ; Module ID
        DCD       0x5                                               ; Module Major Version
        DCD       0x3                                               ; Module Minor Version
        DCD       32                                                ; Module Preamble Size in 32-bit words
        DCD       0x12345678                                        ; Module ID (application defined)
        DCD       0x01000000                                        ; Module Properties where:
                                                                    ;   Bits 31-24: Compiler ID
                                                                    ;           0 -> IAR
                                                                    ;           1 -> ARM
                                                                    ;           2 -> GNU
                                                                    ;   Bits 23-0:  Reserved
        DCD       _txm_module_thread_shell_entry - . + .            ; Module Shell Entry Point
        DCD       demo_module_start - . + .                         ; Module Start Thread Entry Point
        DCD       0                                                 ; Module Stop Thread Entry Point
        DCD       1                                                 ; Module Start/Stop Thread Priority
        DCD       1024                                              ; Module Start/Stop Thread Stack Size
        DCD       _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
        DCD       1                                                 ; Module Callback Thread Priority
        DCD       1024                                              ; Module Callback Thread Stack Size
        DCD       |Image$$ER_RO$$Length|                            ; Module Code Size
        DCD       0x4000                                            ; Module Data Size - default to 16K (need to make sure this is large enough for module's data needs!)
        DCD       0                                                 ; Reserved 0
        DCD       0                                                 ; Reserved 1
        DCD       0                                                 ; Reserved 2
        DCD       0                                                 ; Reserved 3
        DCD       0                                                 ; Reserved 4
        DCD       0                                                 ; Reserved 5
        DCD       0                                                 ; Reserved 6
        DCD       0                                                 ; Reserved 7
        DCD       0                                                 ; Reserved 8  
        DCD       0                                                 ; Reserved 9
        DCD       0                                                 ; Reserved 10
        DCD       0                                                 ; Reserved 11
        DCD       0                                                 ; Reserved 12
        DCD       0                                                 ; Reserved 13
        DCD       0                                                 ; Reserved 14
        DCD       0                                                 ; Reserved 15

        END
```

#### <a name="module-properties-for-arm11-using-ac5"></a><span data-ttu-id="793fc-132">AC5 を使用した ARM11 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-132">Module properties for ARM11 using AC5</span></span>

| <span data-ttu-id="793fc-133">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-133">Bit</span></span> | <span data-ttu-id="793fc-134">値</span><span class="sxs-lookup"><span data-stu-id="793fc-134">Value</span></span> | <span data-ttu-id="793fc-135">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-135">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-136">[23-0]</span><span class="sxs-lookup"><span data-stu-id="793fc-136">[23-0]</span></span> | <span data-ttu-id="793fc-137">0</span><span class="sxs-lookup"><span data-stu-id="793fc-137">0</span></span> | <span data-ttu-id="793fc-138">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-138">Reserved</span></span>
| <span data-ttu-id="793fc-139">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-139">[31-24]</span></span> | <br /><span data-ttu-id="793fc-140">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-140">0x00</span></span><br /><span data-ttu-id="793fc-141">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-141">0x01</span></span><br /><span data-ttu-id="793fc-142">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-142">0x02</span></span> | <span data-ttu-id="793fc-143">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-143">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-144">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-144">IAR</span></span><br /><span data-ttu-id="793fc-145">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-145">ARM</span></span><br /><span data-ttu-id="793fc-146">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-146">GNU</span></span> |

#### <a name="module-linker-for-arm11-using-ac5"></a><span data-ttu-id="793fc-147">AC5 を使用した ARM11 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-147">Module linker for ARM11 using AC5</span></span>

<span data-ttu-id="793fc-148">コマンド ラインでビルドされます。リンカー ファイルの例はありません。</span><span class="sxs-lookup"><span data-stu-id="793fc-148">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-arm11-using-ac5"></a><span data-ttu-id="793fc-149">AC5 を使用した ARM11 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-149">Building Modules for ARM11 using AC5</span></span>

<span data-ttu-id="793fc-150">AC5 を使用して ARM11 モジュールをビルドする簡単なコマンド ラインの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-150">A simple command-line example for building an ARM11 module using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi txm_module_preamble.s
armcc -g -c -O0 --cpu ARM1136J-S --apcs /interwork --apcs /ropi --apcs /rwpi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-arm11-using-ac5"></a><span data-ttu-id="793fc-151">AC5 を使用した ARM11 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-151">Thread extension definition for ARM11 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;  \
                                VOID    *tx_thread_module_entry_info_ptr;
```

#### <a name="building-module-manager-for-arm11-using-ac5"></a><span data-ttu-id="793fc-152">AC5 を使用した ARM11 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-152">Building Module Manager for ARM11 using AC5</span></span>

<span data-ttu-id="793fc-153">AC5 を使用して ARM11 モジュール マネージャーをビルドする簡単なコマンド ラインの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-153">A simple command-line example for building an ARM11 module manager using AC5:</span></span>

```dos
armasm -g --cpu ARM1136J-S --apcs /interwork tx_initialize_low_level.s
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork demo_threadx_module_manager.c
armcc -g -c -O2 --cpu ARM1136J-S --apcs /interwork module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0 --first tx_initialize_low_level.o(Init) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-arm11-using-ac5"></a><span data-ttu-id="793fc-154">AC5 を使用した ARM11 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-154">Attributes for external memory enable API for ARM11 using AC5</span></span>

<span data-ttu-id="793fc-155">この機能はこのポートで有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="793fc-155">This feature not enabled on this port.</span></span>

## <a name="cortex-a7-processor"></a><span data-ttu-id="793fc-156">Cortex-A7 プロセッサ</span><span class="sxs-lookup"><span data-stu-id="793fc-156">Cortex-A7 processor</span></span>

### <a name="cortex-a7-using-ac5"></a><span data-ttu-id="793fc-157">AC5 を使用した Cortex-A7</span><span class="sxs-lookup"><span data-stu-id="793fc-157">Cortex-A7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-a7-using-ac5"></a><span data-ttu-id="793fc-158">AC5 を使用した Cortex-A7 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-158">Module preamble for Cortex-A7 using AC5</span></span>

```armasm
    AREA  Init, CODE, READONLY

;    /* Define public symbols.  */

    EXPORT __txm_module_preamble

;    /* Define application-specific start/stop entry points for the module.  */

    IMPORT demo_module_start

;    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|

__txm_module_preamble
    DCD       0x4D4F4455                                        ; Module ID
    DCD       0x5                                               ; Module Major Version
    DCD       0x3                                               ; Module Minor Version
    DCD       32                                                ; Module Preamble Size in 32-bit words
    DCD       0x12345678                                        ; Module ID (application defined)
    DCD       0x01000001                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-1:  Reserved
                                                                ;   Bit 0:  0 -> Privileged mode execution (no MMU protection)
                                                                ;           1 -> User mode execution (MMU protection)
    DCD       _txm_module_thread_shell_entry - . + .            ; Module Shell Entry Point
    DCD       demo_module_start - . + .                         ; Module Start Thread Entry Point
    DCD       0                                                 ; Module Stop Thread Entry Point
    DCD       1                                                 ; Module Start/Stop Thread Priority
    DCD       1024                                              ; Module Start/Stop Thread Stack Size
    DCD       _txm_module_callback_request_thread_entry - . + . ; Module Callback Thread Entry
    DCD       1                                                 ; Module Callback Thread Priority
    DCD       1024                                              ; Module Callback Thread Stack Size
    DCD       |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|   ; Module Code Size
    DCD       0x4000                                            ; Module Data Size - default to 16K (need to make sure this is large enough for module's data needs!)
    DCD       0                                                 ; Reserved 0
    DCD       0                                                 ; Reserved 1
    DCD       0                                                 ; Reserved 2
    DCD       0                                                 ; Reserved 3
    DCD       0                                                 ; Reserved 4
    DCD       0                                                 ; Reserved 5
    DCD       0                                                 ; Reserved 6
    DCD       0                                                 ; Reserved 7
    DCD       0                                                 ; Reserved 8
    DCD       0                                                 ; Reserved 9
    DCD       0                                                 ; Reserved 10
    DCD       0                                                 ; Reserved 11
    DCD       0                                                 ; Reserved 12
    DCD       0                                                 ; Reserved 13
    DCD       0                                                 ; Reserved 14
    DCD       0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-a7-using-ac5"></a><span data-ttu-id="793fc-159">AC5 を使用した Cortex-A7 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-159">Module properties for Cortex-A7 using AC5</span></span>

| <span data-ttu-id="793fc-160">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-160">Bit</span></span> | <span data-ttu-id="793fc-161">値</span><span class="sxs-lookup"><span data-stu-id="793fc-161">Value</span></span> | <span data-ttu-id="793fc-162">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-162">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-163">0</span><span class="sxs-lookup"><span data-stu-id="793fc-163">0</span></span> | <span data-ttu-id="793fc-164">0</span><span class="sxs-lookup"><span data-stu-id="793fc-164">0</span></span><br /><span data-ttu-id="793fc-165">1</span><span class="sxs-lookup"><span data-stu-id="793fc-165">1</span></span> | <span data-ttu-id="793fc-166">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-166">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-167">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-167">User mode execution</span></span> |
| <span data-ttu-id="793fc-168">[23-1]</span><span class="sxs-lookup"><span data-stu-id="793fc-168">[23-1]</span></span> | <span data-ttu-id="793fc-169">0</span><span class="sxs-lookup"><span data-stu-id="793fc-169">0</span></span> | <span data-ttu-id="793fc-170">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-170">Reserved</span></span>
| <span data-ttu-id="793fc-171">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-171">[31-24]</span></span> | <br /><span data-ttu-id="793fc-172">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-172">0x00</span></span><br /><span data-ttu-id="793fc-173">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-173">0x01</span></span><br /><span data-ttu-id="793fc-174">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-174">0x02</span></span> | <span data-ttu-id="793fc-175">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-175">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-176">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-176">IAR</span></span><br /><span data-ttu-id="793fc-177">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-177">ARM</span></span><br /><span data-ttu-id="793fc-178">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-178">GNU</span></span> |

#### <a name="module-linker-for-cortex-a7-using-ac5"></a><span data-ttu-id="793fc-179">AC5 を使用した Cortex-A7 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-179">Module linker for Cortex-A7 using AC5</span></span>

<span data-ttu-id="793fc-180">コマンド ラインでビルドされます。リンカー ファイルの例はありません。</span><span class="sxs-lookup"><span data-stu-id="793fc-180">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-a7-using-ac5"></a><span data-ttu-id="793fc-181">AC5 を使用した Cortex-A7 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-181">Building Modules for Cortex-A7 using AC5</span></span>

<span data-ttu-id="793fc-182">AC5 を使用して Cortex-A7 モジュールをビルドする簡単なコマンド ラインの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-182">A simple command-line example for building a Cortex-A7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-a7.no_neon --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi demo_threadx_module.c
armlink -d -o demo_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-a7-using-ac5"></a><span data-ttu-id="793fc-183">AC5 を使用した Cortex-A7 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-183">Thread extension definition for Cortex-A7 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-a7-using-ac5"></a><span data-ttu-id="793fc-184">AC5 を使用した Cortex-A7 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-184">Building Module Manager for Cortex-A7 using AC5</span></span>

<span data-ttu-id="793fc-185">AC5 を使用して Cortex-A7 モジュール マネージャーをビルドする簡単なコマンド ラインの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-185">A simple command-line example for building a Cortex-A7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-a7.no_neon --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-a7.no_neon --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x80000000 --first tx_initialize_low_level.o(VECTORS) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-a7-using-ac5"></a><span data-ttu-id="793fc-186">AC5 を使用した Cortex-A7 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-186">Attributes for external memory enable API for Cortex-A7 using AC5</span></span>

<span data-ttu-id="793fc-187">次の属性を使用して、共有メモリ設定をセットアップできます。</span><span class="sxs-lookup"><span data-stu-id="793fc-187">The following attributes can be used to set up shared memory settings:</span></span>

| <span data-ttu-id="793fc-188">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-188">Attribute parameter</span></span> | <span data-ttu-id="793fc-189">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-189">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-190">TXM_MMU_ATTRIBUTE_XN</span><span class="sxs-lookup"><span data-stu-id="793fc-190">TXM_MMU_ATTRIBUTE_XN</span></span> | <span data-ttu-id="793fc-191">実行しない</span><span class="sxs-lookup"><span data-stu-id="793fc-191">Execute Never</span></span> |
| <span data-ttu-id="793fc-192">TXM_MMU_ATTRIBUTE_B</span><span class="sxs-lookup"><span data-stu-id="793fc-192">TXM_MMU_ATTRIBUTE_B</span></span> | <span data-ttu-id="793fc-193">B 設定</span><span class="sxs-lookup"><span data-stu-id="793fc-193">B setting</span></span> |
| <span data-ttu-id="793fc-194">TXM_MMU_ATTRIBUTE_C</span><span class="sxs-lookup"><span data-stu-id="793fc-194">TXM_MMU_ATTRIBUTE_C</span></span> | <span data-ttu-id="793fc-195">C 設定</span><span class="sxs-lookup"><span data-stu-id="793fc-195">C setting</span></span> |
| <span data-ttu-id="793fc-196">TXM_MMU_ATTRIBUTE_AP</span><span class="sxs-lookup"><span data-stu-id="793fc-196">TXM_MMU_ATTRIBUTE_AP</span></span> | <span data-ttu-id="793fc-197">AP 設定</span><span class="sxs-lookup"><span data-stu-id="793fc-197">AP setting</span></span> |
| <span data-ttu-id="793fc-198">TXM_MMU_ATTRIBUTE_TEX</span><span class="sxs-lookup"><span data-stu-id="793fc-198">TXM_MMU_ATTRIBUTE_TEX</span></span> | <span data-ttu-id="793fc-199">TEX 設定</span><span class="sxs-lookup"><span data-stu-id="793fc-199">TEX setting</span></span> |

<span data-ttu-id="793fc-200">これらの設定の構成方法については、ARM のドキュメントをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="793fc-200">See ARM documentation for how these settings are configured.</span></span>

## <a name="cortex-m3-processor"></a><span data-ttu-id="793fc-201">Cortex-M3 プロセッサ</span><span class="sxs-lookup"><span data-stu-id="793fc-201">Cortex-M3 processor</span></span>

### <a name="cortex-m3-using-ac5"></a><span data-ttu-id="793fc-202">AC5 を使用した Cortex-M3</span><span class="sxs-lookup"><span data-stu-id="793fc-202">Cortex-M3 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac5"></a><span data-ttu-id="793fc-203">AC5 を使用した Cortex-M3 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-203">Module preamble for Cortex-M3 using AC5</span></span>

```armasm
    AREA Init, CODE, READONLY

    PRESERVE8

    ; Define public symbols

    EXPORT __txm_module_preamble

    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start

    ; Define common external references

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          ; Module ID
    DCD     0x6                                                 ; Module Major Version
    DCD     0x1                                                 ; Module Minor Version
    DCD     32                                                  ; Module Preamble Size in 32-bit words
    DCD     0x12345678                                          ; Module ID (application defined)
    DCD     0x01000007                                          ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected)
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              ; Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           ; Module Start Thread Entry Point
    DCD     0                                                   ; Module Stop Thread Entry Point
    DCD     1                                                   ; Module Start/Stop Thread Priority
    DCD     1024                                                ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   ; Module Callback Thread Entry
    DCD     1                                                   ; Module Callback Thread Priority
    DCD     1024                                                ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|         ; Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| ; Module Data Size
    DCD     0                                                   ; Reserved 0
    DCD     0                                                   ; Reserved 1
    DCD     0                                                   ; Reserved 2
    DCD     0                                                   ; Reserved 3
    DCD     0                                                   ; Reserved 4
    DCD     0                                                   ; Reserved 5
    DCD     0                                                   ; Reserved 6
    DCD     0                                                   ; Reserved 7
    DCD     0                                                   ; Reserved 8
    DCD     0                                                   ; Reserved 9
    DCD     0                                                   ; Reserved 10
    DCD     0                                                   ; Reserved 11
    DCD     0                                                   ; Reserved 12
    DCD     0                                                   ; Reserved 13
    DCD     0                                                   ; Reserved 14
    DCD     0                                                   ; Reserved 15

    END

```

#### <a name="module-properties-for-cortex-m3-using-ac5"></a><span data-ttu-id="793fc-204">AC5 を使用した Cortex-M3 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-204">Module properties for Cortex-M3 using AC5</span></span>

| <span data-ttu-id="793fc-205">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-205">Bit</span></span> | <span data-ttu-id="793fc-206">値</span><span class="sxs-lookup"><span data-stu-id="793fc-206">Value</span></span> | <span data-ttu-id="793fc-207">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-207">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-208">0</span><span class="sxs-lookup"><span data-stu-id="793fc-208">0</span></span> | <span data-ttu-id="793fc-209">0</span><span class="sxs-lookup"><span data-stu-id="793fc-209">0</span></span><br /><span data-ttu-id="793fc-210">1</span><span class="sxs-lookup"><span data-stu-id="793fc-210">1</span></span> | <span data-ttu-id="793fc-211">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-211">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-212">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-212">User mode execution</span></span> |
| <span data-ttu-id="793fc-213">1</span><span class="sxs-lookup"><span data-stu-id="793fc-213">1</span></span> | <span data-ttu-id="793fc-214">0</span><span class="sxs-lookup"><span data-stu-id="793fc-214">0</span></span><br /><span data-ttu-id="793fc-215">1</span><span class="sxs-lookup"><span data-stu-id="793fc-215">1</span></span> | <span data-ttu-id="793fc-216">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-216">No MPU protection</span></span><br /><span data-ttu-id="793fc-217">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-217">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-218">2</span><span class="sxs-lookup"><span data-stu-id="793fc-218">2</span></span> | <span data-ttu-id="793fc-219">0</span><span class="sxs-lookup"><span data-stu-id="793fc-219">0</span></span><br /><span data-ttu-id="793fc-220">1</span><span class="sxs-lookup"><span data-stu-id="793fc-220">1</span></span> | <span data-ttu-id="793fc-221">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-221">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-222">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-222">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-223">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-223">[23-3]</span></span> | <span data-ttu-id="793fc-224">0</span><span class="sxs-lookup"><span data-stu-id="793fc-224">0</span></span> | <span data-ttu-id="793fc-225">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-225">Reserved</span></span>
| <span data-ttu-id="793fc-226">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-226">[31-24]</span></span> | <br /><span data-ttu-id="793fc-227">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-227">0x00</span></span><br /><span data-ttu-id="793fc-228">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-228">0x01</span></span><br /><span data-ttu-id="793fc-229">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-229">0x02</span></span> | <span data-ttu-id="793fc-230">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-230">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-231">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-231">IAR</span></span><br /><span data-ttu-id="793fc-232">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-232">ARM</span></span><br /><span data-ttu-id="793fc-233">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-233">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac5"></a><span data-ttu-id="793fc-234">AC5 を使用した Cortex-M3 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-234">Module linker for Cortex-M3 using AC5</span></span>

<span data-ttu-id="793fc-235">リンカー ファイルの例はまだ提供されていません。リンク設定はコマンド ラインで実行されます。</span><span class="sxs-lookup"><span data-stu-id="793fc-235">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="793fc-236">次のセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="793fc-236">See next section.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac5"></a><span data-ttu-id="793fc-237">AC5 を使用した Cortex-M3 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-237">Building Modules for Cortex-M3 using AC5</span></span>

<span data-ttu-id="793fc-238">ビルド スクリプトの例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-238">An example build script is provided:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m3 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m3-using-ac5"></a><span data-ttu-id="793fc-239">AC5 を使用した Cortex-M3 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-239">Thread extension definition for Cortex-M3 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-ac5"></a><span data-ttu-id="793fc-240">AC5 を使用した Cortex-M3 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-240">Building Module Manager for Cortex-M3 using AC5</span></span>

<span data-ttu-id="793fc-241">build_threadx_module_manager_demo.bat の例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-241">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpu=cortex-m3 --apcs=interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m3 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac5"></a><span data-ttu-id="793fc-242">AC5 を使用した Cortex-M3 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-242">Attributes for external memory enable API for Cortex-M3 using AC5</span></span>

<span data-ttu-id="793fc-243">モジュールは常に共有メモリへの読み取りアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="793fc-243">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="793fc-244">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-244">Attribute parameter</span></span> | <span data-ttu-id="793fc-245">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-245">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-246">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-247">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-247">Write access</span></span> |

### <a name="cortex-m3-using-ac6"></a><span data-ttu-id="793fc-248">AC6 を使用した Cortex-M3</span><span class="sxs-lookup"><span data-stu-id="793fc-248">Cortex-M3 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m3-using-ac6"></a><span data-ttu-id="793fc-249">AC6 を使用した Cortex-M3 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-249">Module preamble for Cortex-M3 using AC6</span></span>

```armasm
    .text
    .align 4
    .syntax unified
    .section Init
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    .dc.l   0x10000                                             // Module Code Size
    .dc.l   0x10000                                             // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m3-using-ac6"></a><span data-ttu-id="793fc-250">AC6 を使用した Cortex-M3 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-250">Module properties for Cortex-M3 using AC6</span></span>

| <span data-ttu-id="793fc-251">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-251">Bit</span></span> | <span data-ttu-id="793fc-252">値</span><span class="sxs-lookup"><span data-stu-id="793fc-252">Value</span></span> | <span data-ttu-id="793fc-253">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-253">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-254">0</span><span class="sxs-lookup"><span data-stu-id="793fc-254">0</span></span> | <span data-ttu-id="793fc-255">0</span><span class="sxs-lookup"><span data-stu-id="793fc-255">0</span></span><br /><span data-ttu-id="793fc-256">1</span><span class="sxs-lookup"><span data-stu-id="793fc-256">1</span></span> | <span data-ttu-id="793fc-257">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-257">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-258">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-258">User mode execution</span></span> |
| <span data-ttu-id="793fc-259">1</span><span class="sxs-lookup"><span data-stu-id="793fc-259">1</span></span> | <span data-ttu-id="793fc-260">0</span><span class="sxs-lookup"><span data-stu-id="793fc-260">0</span></span><br /><span data-ttu-id="793fc-261">1</span><span class="sxs-lookup"><span data-stu-id="793fc-261">1</span></span> | <span data-ttu-id="793fc-262">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-262">No MPU protection</span></span><br /><span data-ttu-id="793fc-263">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-263">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-264">2</span><span class="sxs-lookup"><span data-stu-id="793fc-264">2</span></span> | <span data-ttu-id="793fc-265">0</span><span class="sxs-lookup"><span data-stu-id="793fc-265">0</span></span><br /><span data-ttu-id="793fc-266">1</span><span class="sxs-lookup"><span data-stu-id="793fc-266">1</span></span> | <span data-ttu-id="793fc-267">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-267">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-268">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-268">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-269">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-269">[23-3]</span></span> | <span data-ttu-id="793fc-270">0</span><span class="sxs-lookup"><span data-stu-id="793fc-270">0</span></span> | <span data-ttu-id="793fc-271">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-271">Reserved</span></span>
| <span data-ttu-id="793fc-272">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-272">[31-24]</span></span> | <br /><span data-ttu-id="793fc-273">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-273">0x00</span></span><br /><span data-ttu-id="793fc-274">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-274">0x01</span></span><br /><span data-ttu-id="793fc-275">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-275">0x02</span></span> | <span data-ttu-id="793fc-276">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-276">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-277">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-277">IAR</span></span><br /><span data-ttu-id="793fc-278">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-278">ARM</span></span><br /><span data-ttu-id="793fc-279">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-279">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-ac6"></a><span data-ttu-id="793fc-280">AC6 を使用した Cortex-M3 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-280">Module linker for Cortex-M3 using AC6</span></span>

<span data-ttu-id="793fc-281">リンカー ファイルが使用されていません。</span><span class="sxs-lookup"><span data-stu-id="793fc-281">No linker file is used.</span></span> <span data-ttu-id="793fc-282">プロジェクトの設定をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="793fc-282">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m3-using-ac6"></a><span data-ttu-id="793fc-283">AC6 を使用した Cortex-M3 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-283">Building Modules for Cortex-M3 using AC6</span></span>

<span data-ttu-id="793fc-284">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-284">An example workspace is provided.</span></span> <span data-ttu-id="793fc-285">ThreadX ライブラリ、ThreadX モジュール ライブラリ、サンプル モジュール プロジェクト、およびサンプル モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-285">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-ac6"></a><span data-ttu-id="793fc-286">AC6 を使用した Cortex-M3 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-286">Thread extension definition for Cortex-M3 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-ac6"></a><span data-ttu-id="793fc-287">AC6 を使用した Cortex-M3 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-287">Building Module Manager for Cortex-M3 using AC6</span></span>

<span data-ttu-id="793fc-288">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-288">An example workspace is provided.</span></span> <span data-ttu-id="793fc-289">ThreadX ライブラリ、ThreadX モジュール ライブラリ、サンプル モジュール プロジェクト、およびサンプル モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-289">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-ac6"></a><span data-ttu-id="793fc-290">AC6 を使用した Cortex-M3 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-290">Attributes for external memory enable API for Cortex-M3 using AC6</span></span>

<span data-ttu-id="793fc-291">モジュールは常に共有メモリへの読み取りアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="793fc-291">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="793fc-292">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-292">Attribute parameter</span></span> | <span data-ttu-id="793fc-293">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-293">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-294">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-295">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-295">Write access</span></span> |

### <a name="cortex-m3-using-gnu"></a><span data-ttu-id="793fc-296">GNU を使用した Cortex-M3</span><span class="sxs-lookup"><span data-stu-id="793fc-296">Cortex-M3 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m3-using-gnu"></a><span data-ttu-id="793fc-297">GNU を使用した Cortex-M3 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-297">Module preamble for Cortex-M3 using GNU</span></span>

```armasm
    .text
    .align 4
    .syntax unified

    /* Define public symbols.  */
    .global __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    .global demo_module_start

    /* Define common external refrences.  */
    .global _txm_module_thread_shell_entry
    .global _txm_module_callback_request_thread_entry

__txm_module_preamble:
    .dc.l      0x4D4F4455                                       // Module ID
    .dc.l      0x6                                              // Module Major Version
    .dc.l      0x1                                              // Module Minor Version
    .dc.l      32                                               // Module Preamble Size in 32-bit words
    .dc.l      0x12345678                                       // Module ID (application defined)
    .dc.l      0x02000007                                       // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    .dc.l      _txm_module_thread_shell_entry - . - 0           // Module Shell Entry Point
    .dc.l      demo_module_start - . - 0                        // Module Start Thread Entry Point
    .dc.l      0                                                // Module Stop Thread Entry Point 
    .dc.l      1                                                // Module Start/Stop Thread Priority
    .dc.l      1024                                             // Module Start/Stop Thread Stack Size
    .dc.l      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    .dc.l      1                                                // Module Callback Thread Priority
    .dc.l      1024                                             // Module Callback Thread Stack Size
    .dc.l      __code_size__                                    // Module Code Size
    .dc.l      __data_size__                                    // Module Data Size
    .dc.l      0                                                // Reserved 0
    .dc.l      0                                                // Reserved 1
    .dc.l      0                                                // Reserved 2
    .dc.l      0                                                // Reserved 3
    .dc.l      0                                                // Reserved 4
    .dc.l      0                                                // Reserved 5
    .dc.l      0                                                // Reserved 6
    .dc.l      0                                                // Reserved 7
    .dc.l      0                                                // Reserved 8
    .dc.l      0                                                // Reserved 9
    .dc.l      0                                                // Reserved 10
    .dc.l      0                                                // Reserved 11
    .dc.l      0                                                // Reserved 12
    .dc.l      0                                                // Reserved 13
    .dc.l      0                                                // Reserved 14
    .dc.l      0                                                // Reserved 15

```

#### <a name="module-properties-for-cortex-m3-using-gnu"></a><span data-ttu-id="793fc-298">GNU を使用した Cortex-M3 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-298">Module properties for Cortex-M3 using GNU</span></span>

| <span data-ttu-id="793fc-299">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-299">Bit</span></span> | <span data-ttu-id="793fc-300">値</span><span class="sxs-lookup"><span data-stu-id="793fc-300">Value</span></span> | <span data-ttu-id="793fc-301">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-301">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-302">0</span><span class="sxs-lookup"><span data-stu-id="793fc-302">0</span></span> | <span data-ttu-id="793fc-303">0</span><span class="sxs-lookup"><span data-stu-id="793fc-303">0</span></span><br /><span data-ttu-id="793fc-304">1</span><span class="sxs-lookup"><span data-stu-id="793fc-304">1</span></span> | <span data-ttu-id="793fc-305">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-305">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-306">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-306">User mode execution</span></span> |
| <span data-ttu-id="793fc-307">1</span><span class="sxs-lookup"><span data-stu-id="793fc-307">1</span></span> | <span data-ttu-id="793fc-308">0</span><span class="sxs-lookup"><span data-stu-id="793fc-308">0</span></span><br /><span data-ttu-id="793fc-309">1</span><span class="sxs-lookup"><span data-stu-id="793fc-309">1</span></span> | <span data-ttu-id="793fc-310">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-310">No MPU protection</span></span><br /><span data-ttu-id="793fc-311">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-311">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-312">2</span><span class="sxs-lookup"><span data-stu-id="793fc-312">2</span></span> | <span data-ttu-id="793fc-313">0</span><span class="sxs-lookup"><span data-stu-id="793fc-313">0</span></span><br /><span data-ttu-id="793fc-314">1</span><span class="sxs-lookup"><span data-stu-id="793fc-314">1</span></span> | <span data-ttu-id="793fc-315">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-315">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-316">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-316">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-317">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-317">[23-3]</span></span> | <span data-ttu-id="793fc-318">0</span><span class="sxs-lookup"><span data-stu-id="793fc-318">0</span></span> | <span data-ttu-id="793fc-319">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-319">Reserved</span></span>
| <span data-ttu-id="793fc-320">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-320">[31-24]</span></span> | <br /><span data-ttu-id="793fc-321">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-321">0x00</span></span><br /><span data-ttu-id="793fc-322">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-322">0x01</span></span><br /><span data-ttu-id="793fc-323">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-323">0x02</span></span> | <span data-ttu-id="793fc-324">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-324">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-325">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-325">IAR</span></span><br /><span data-ttu-id="793fc-326">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-326">ARM</span></span><br /><span data-ttu-id="793fc-327">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-327">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-gnu"></a><span data-ttu-id="793fc-328">GNU を使用した Cortex-M3 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-328">Module linker for Cortex-M3 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m3-using-gnu"></a><span data-ttu-id="793fc-329">GNU を使用した Cortex-M3 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-329">Building Modules for Cortex-M3 using GNU</span></span>

<span data-ttu-id="793fc-330">build_threadx_module_sample.bat を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-330">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m3 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m3-using-gnu"></a><span data-ttu-id="793fc-331">GNU を使用した Cortex-M3 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-331">Thread extension definition for Cortex-M3 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m3-using-gnu"></a><span data-ttu-id="793fc-332">GNU を使用した Cortex-M3 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-332">Building Module Manager for Cortex-M3 using GNU</span></span>

<span data-ttu-id="793fc-333">build_threadx_module_manager_sample.bat を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-333">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m3 -mthumb cortexm_crt0.S
arm-none-eabi-ld -A cortex-m3 -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a  libc.a -o sample_threadx_module_manager.axf -M > sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-gnu"></a><span data-ttu-id="793fc-334">GNU を使用した Cortex-M3 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-334">Attributes for external memory enable API for Cortex-M3 using GNU</span></span>

<span data-ttu-id="793fc-335">モジュールは常に共有メモリへの読み取りアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="793fc-335">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="793fc-336">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-336">Attribute parameter</span></span> | <span data-ttu-id="793fc-337">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-337">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-338">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-339">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-339">Write access</span></span> |

### <a name="cortex-m3-using-iar"></a><span data-ttu-id="793fc-340">IAR を使用した Cortex-M3</span><span class="sxs-lookup"><span data-stu-id="793fc-340">Cortex-M3 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m3-using-iar"></a><span data-ttu-id="793fc-341">IAR を使用した Cortex-M3 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-341">Module preamble for Cortex-M3 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m3-using-iar"></a><span data-ttu-id="793fc-342">IAR を使用した Cortex-M3 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-342">Module properties for Cortex-M3 using IAR</span></span>

| <span data-ttu-id="793fc-343">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-343">Bit</span></span> | <span data-ttu-id="793fc-344">値</span><span class="sxs-lookup"><span data-stu-id="793fc-344">Value</span></span> | <span data-ttu-id="793fc-345">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-345">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-346">0</span><span class="sxs-lookup"><span data-stu-id="793fc-346">0</span></span> | <span data-ttu-id="793fc-347">0</span><span class="sxs-lookup"><span data-stu-id="793fc-347">0</span></span><br /><span data-ttu-id="793fc-348">1</span><span class="sxs-lookup"><span data-stu-id="793fc-348">1</span></span> | <span data-ttu-id="793fc-349">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-349">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-350">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-350">User mode execution</span></span> |
| <span data-ttu-id="793fc-351">1</span><span class="sxs-lookup"><span data-stu-id="793fc-351">1</span></span> | <span data-ttu-id="793fc-352">0</span><span class="sxs-lookup"><span data-stu-id="793fc-352">0</span></span><br /><span data-ttu-id="793fc-353">1</span><span class="sxs-lookup"><span data-stu-id="793fc-353">1</span></span> | <span data-ttu-id="793fc-354">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-354">No MPU protection</span></span><br /><span data-ttu-id="793fc-355">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-355">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-356">2</span><span class="sxs-lookup"><span data-stu-id="793fc-356">2</span></span> | <span data-ttu-id="793fc-357">0</span><span class="sxs-lookup"><span data-stu-id="793fc-357">0</span></span><br /><span data-ttu-id="793fc-358">1</span><span class="sxs-lookup"><span data-stu-id="793fc-358">1</span></span> | <span data-ttu-id="793fc-359">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-359">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-360">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-360">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-361">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-361">[23-3]</span></span> | <span data-ttu-id="793fc-362">0</span><span class="sxs-lookup"><span data-stu-id="793fc-362">0</span></span> | <span data-ttu-id="793fc-363">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-363">Reserved</span></span>
| <span data-ttu-id="793fc-364">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-364">[31-24]</span></span> | <br /><span data-ttu-id="793fc-365">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-365">0x00</span></span><br /><span data-ttu-id="793fc-366">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-366">0x01</span></span><br /><span data-ttu-id="793fc-367">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-367">0x02</span></span> | <span data-ttu-id="793fc-368">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-368">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-369">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-369">IAR</span></span><br /><span data-ttu-id="793fc-370">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-370">ARM</span></span><br /><span data-ttu-id="793fc-371">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-371">GNU</span></span> |

#### <a name="module-linker-for-cortex-m3-using-iar"></a><span data-ttu-id="793fc-372">IAR を使用した Cortex-M3 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-372">Module linker for Cortex-M3 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble_stm32f2xx.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m3-using-iar"></a><span data-ttu-id="793fc-373">IAR を使用した Cortex-M3 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-373">Building Modules for Cortex-M3 using IAR</span></span>

<span data-ttu-id="793fc-374">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-374">An example workspace is provided.</span></span> <span data-ttu-id="793fc-375">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-375">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m3-using-iar"></a><span data-ttu-id="793fc-376">IAR を使用した Cortex-M3 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-376">Thread extension definition for Cortex-M3 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m3-using-iar"></a><span data-ttu-id="793fc-377">IAR を使用した Cortex-M3 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-377">Building Module Manager for Cortex-M3 using IAR</span></span>

<span data-ttu-id="793fc-378">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-378">An example workspace is provided.</span></span> <span data-ttu-id="793fc-379">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-379">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m3-using-iar"></a><span data-ttu-id="793fc-380">IAR を使用した Cortex-M3 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-380">Attributes for external memory enable API for Cortex-M3 using IAR</span></span>

<span data-ttu-id="793fc-381">モジュールは常に共有メモリへの読み取りアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="793fc-381">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="793fc-382">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-382">Attribute parameter</span></span> | <span data-ttu-id="793fc-383">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-383">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-384">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-385">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-385">Write access</span></span> |

## <a name="cortex-m33-processor"></a><span data-ttu-id="793fc-386">Cortex-M33 プロセッサ</span><span class="sxs-lookup"><span data-stu-id="793fc-386">Cortex-M33 processor</span></span>

### <a name="cortex-m33-using-ac6"></a><span data-ttu-id="793fc-387">AC6 を使用した Cortex-M33</span><span class="sxs-lookup"><span data-stu-id="793fc-387">Cortex-M33 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m33-using-ac6"></a><span data-ttu-id="793fc-388">AC6 を使用した Cortex-M33 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-388">Module preamble for Cortex-M33 using AC6</span></span>

```c
    .text
    .align 4
    .syntax unified
    .section RESET
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    //the tools can't add two symbols together, but it should look like this:
    //.dc.l   Image$$ER_RO$$Length + Image$$ER_RW$$Length         // Module Code Size
    //.dc.l   Image$$ER_RW$$Length + Image$$ER_ZI$$ZI$$Length     // Module Data Size
    //so instead we'll define hard values:
    .dc.l   0x4000                                              // Module Code Size
    .dc.l   0x4000                                              // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m33-using-ac6"></a><span data-ttu-id="793fc-389">AC6 を使用した Cortex-M33 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-389">Module properties for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="793fc-390">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-390">Bit</span></span> | <span data-ttu-id="793fc-391">値</span><span class="sxs-lookup"><span data-stu-id="793fc-391">Value</span></span> | <span data-ttu-id="793fc-392">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-392">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-393">0</span><span class="sxs-lookup"><span data-stu-id="793fc-393">0</span></span> | <span data-ttu-id="793fc-394">0</span><span class="sxs-lookup"><span data-stu-id="793fc-394">0</span></span><br /><span data-ttu-id="793fc-395">1</span><span class="sxs-lookup"><span data-stu-id="793fc-395">1</span></span> | <span data-ttu-id="793fc-396">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-396">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-397">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-397">User mode execution</span></span> |
| <span data-ttu-id="793fc-398">1</span><span class="sxs-lookup"><span data-stu-id="793fc-398">1</span></span> | <span data-ttu-id="793fc-399">0</span><span class="sxs-lookup"><span data-stu-id="793fc-399">0</span></span><br /><span data-ttu-id="793fc-400">1</span><span class="sxs-lookup"><span data-stu-id="793fc-400">1</span></span> | <span data-ttu-id="793fc-401">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-401">No MPU protection</span></span><br /><span data-ttu-id="793fc-402">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-402">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-403">2</span><span class="sxs-lookup"><span data-stu-id="793fc-403">2</span></span> | <span data-ttu-id="793fc-404">0</span><span class="sxs-lookup"><span data-stu-id="793fc-404">0</span></span><br /><span data-ttu-id="793fc-405">1</span><span class="sxs-lookup"><span data-stu-id="793fc-405">1</span></span> | <span data-ttu-id="793fc-406">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-406">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-407">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-407">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-408">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-408">[23-3]</span></span> | <span data-ttu-id="793fc-409">0</span><span class="sxs-lookup"><span data-stu-id="793fc-409">0</span></span> | <span data-ttu-id="793fc-410">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-410">Reserved</span></span>
| <span data-ttu-id="793fc-411">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-411">[31-24]</span></span> | <br /><span data-ttu-id="793fc-412">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-412">0x00</span></span><br /><span data-ttu-id="793fc-413">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-413">0x01</span></span><br /><span data-ttu-id="793fc-414">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-414">0x02</span></span> | <span data-ttu-id="793fc-415">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-415">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-416">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-416">IAR</span></span><br /><span data-ttu-id="793fc-417">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-417">ARM</span></span><br /><span data-ttu-id="793fc-418">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-418">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-ac6"></a><span data-ttu-id="793fc-419">AC6 を使用した Cortex-M33 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-419">Module linker for Cortex-M33 using AC6</span></span>

<span data-ttu-id="793fc-420">Keil ツールチェーンに必要なリンカー ファイルがありません。</span><span class="sxs-lookup"><span data-stu-id="793fc-420">No linker file needed for Keil toolchain.</span></span> <span data-ttu-id="793fc-421">サンプル プロジェクト内のビルド設定をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="793fc-421">See build settings in example project.</span></span>
<span data-ttu-id="793fc-422">重要なリンカー オプションを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-422">Important linker options are listed below:</span></span>

```c
--entry demo_module_start --first __txm_module_preamble
```

#### <a name="building-modules-for-cortex-m33-using-ac6"></a><span data-ttu-id="793fc-423">AC6 を使用した Cortex-M33 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-423">Building Modules for Cortex-M33 using AC6</span></span>

<span data-ttu-id="793fc-424">コンパイラの設定:</span><span class="sxs-lookup"><span data-stu-id="793fc-424">Compiler settings:</span></span>

```c
-xc -std=c99 --target=arm-arm-none-eabi -mcpu=cortex-m33 -mfpu=fpv5-sp-d16 -mfloat-abi=hard -c
-fno-rtti -funsigned-char -fshort-enums -fshort-wchar
-mlittle-endian -gdwarf-3 -fropi -frwpi -O1 -ffunction-sections -Wno-packed -Wno-missing-variable-declarations -Wno-missing-prototypes -Wno-missing-noreturn -Wno-sign-conversion -Wno-nonportable-include-path -Wno-reserved-id-macro -Wno-unused-macros -Wno-documentation-unknown-command -Wno-documentation -Wno-license-management -Wno-parentheses-equality -I ../../../../../common_modules/inc -I ../../../../../common/inc -I ../../../../../ports_module/cortex_m33/ac6/inc -I ../demo_secure_zone
-I./RTE/_FVP_Simulation_Model
-IC:/Users/your_path/AppData/Local/Arm/Packs/ARM/CMSIS/5.5.1/CMSIS/Core/Include
-IC:/Users/your_path/AppData/Local/Arm/Packs/ARM/CMSIS/5.5.1/Device/ARM/ARMCM33/Include
-D__UVISION_VERSION="531" -D_RTE_ -DARMCM33_DSP_FP_TZ -D_RTE_
-o ./Objects/*.o -MD
```

#### <a name="thread-extension-definition-for-cortex-m33-using-ac6"></a><span data-ttu-id="793fc-425">AC6 を使用した Cortex-M33 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-425">Thread extension definition for Cortex-M33 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2                   VOID    *tx_thread_module_instance_ptr;         \
                                                VOID    *tx_thread_module_entry_info_ptr;       \
                                                ULONG   tx_thread_module_current_user_mode;     \
                                                ULONG   tx_thread_module_user_mode;             \
                                                ULONG   tx_thread_module_saved_lr;              \
                                                VOID    *tx_thread_module_kernel_stack_start;   \
                                                VOID    *tx_thread_module_kernel_stack_end;     \
                                                ULONG   tx_thread_module_kernel_stack_size;     \
                                                VOID    *tx_thread_module_stack_ptr;            \
                                                VOID    *tx_thread_module_stack_start;          \
                                                VOID    *tx_thread_module_stack_end;            \
                                                ULONG   tx_thread_module_stack_size;            \
                                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m33-using-ac6"></a><span data-ttu-id="793fc-426">AC6 を使用した Cortex-M33 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-426">Building Module Manager for Cortex-M33 using AC6</span></span>

<span data-ttu-id="793fc-427">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-427">An example workspace is provided.</span></span> <span data-ttu-id="793fc-428">ThreadX ライブラリ、ThreadX モジュール ライブラリ、sample_threadx_module プロジェクト、および demo_threadx_non-secure_zone プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-428">Build the ThreadX library, ThreadX Modules library, sample_threadx_module project, and demo_threadx_non-secure_zone project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-ac6"></a><span data-ttu-id="793fc-429">AC6 を使用した Cortex-M33 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-429">Attributes for external memory enable API for Cortex-M33 using AC6</span></span>

| <span data-ttu-id="793fc-430">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-430">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="793fc-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="793fc-431">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="793fc-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="793fc-432">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="793fc-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="793fc-433">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="793fc-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-434">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="793fc-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="793fc-435">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-gnu"></a><span data-ttu-id="793fc-436">GNU を使用した Cortex-M33</span><span class="sxs-lookup"><span data-stu-id="793fc-436">Cortex-M33 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m33-using-gnu"></a><span data-ttu-id="793fc-437">GNU を使用した Cortex-M33 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-437">Module preamble for Cortex-M33 using GNU</span></span>

#### <a name="module-properties-for-cortex-m33-using-gnu"></a><span data-ttu-id="793fc-438">GNU を使用した Cortex-M33 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-438">Module properties for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="793fc-439">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-439">Bit</span></span> | <span data-ttu-id="793fc-440">値</span><span class="sxs-lookup"><span data-stu-id="793fc-440">Value</span></span> | <span data-ttu-id="793fc-441">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-441">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-442">0</span><span class="sxs-lookup"><span data-stu-id="793fc-442">0</span></span> | <span data-ttu-id="793fc-443">0</span><span class="sxs-lookup"><span data-stu-id="793fc-443">0</span></span><br /><span data-ttu-id="793fc-444">1</span><span class="sxs-lookup"><span data-stu-id="793fc-444">1</span></span> | <span data-ttu-id="793fc-445">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-445">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-446">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-446">User mode execution</span></span> |
| <span data-ttu-id="793fc-447">1</span><span class="sxs-lookup"><span data-stu-id="793fc-447">1</span></span> | <span data-ttu-id="793fc-448">0</span><span class="sxs-lookup"><span data-stu-id="793fc-448">0</span></span><br /><span data-ttu-id="793fc-449">1</span><span class="sxs-lookup"><span data-stu-id="793fc-449">1</span></span> | <span data-ttu-id="793fc-450">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-450">No MPU protection</span></span><br /><span data-ttu-id="793fc-451">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-451">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-452">2</span><span class="sxs-lookup"><span data-stu-id="793fc-452">2</span></span> | <span data-ttu-id="793fc-453">0</span><span class="sxs-lookup"><span data-stu-id="793fc-453">0</span></span><br /><span data-ttu-id="793fc-454">1</span><span class="sxs-lookup"><span data-stu-id="793fc-454">1</span></span> | <span data-ttu-id="793fc-455">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-455">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-456">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-456">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-457">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-457">[23-3]</span></span> | <span data-ttu-id="793fc-458">0</span><span class="sxs-lookup"><span data-stu-id="793fc-458">0</span></span> | <span data-ttu-id="793fc-459">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-459">Reserved</span></span>
| <span data-ttu-id="793fc-460">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-460">[31-24]</span></span> | <br /><span data-ttu-id="793fc-461">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-461">0x00</span></span><br /><span data-ttu-id="793fc-462">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-462">0x01</span></span><br /><span data-ttu-id="793fc-463">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-463">0x02</span></span> | <span data-ttu-id="793fc-464">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-464">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-465">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-465">IAR</span></span><br /><span data-ttu-id="793fc-466">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-466">ARM</span></span><br /><span data-ttu-id="793fc-467">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-467">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-gnu"></a><span data-ttu-id="793fc-468">GNU を使用した Cortex-M33 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-468">Module linker for Cortex-M33 using GNU</span></span>

#### <a name="building-modules-for-cortex-m33-using-gnu"></a><span data-ttu-id="793fc-469">GNU を使用した Cortex-M33 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-469">Building Modules for Cortex-M33 using GNU</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-gnu"></a><span data-ttu-id="793fc-470">GNU を使用した Cortex-M33 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-470">Thread extension definition for Cortex-M33 using GNU</span></span>

#### <a name="building-module-manager-for-cortex-m33-using-gnu"></a><span data-ttu-id="793fc-471">GNU を使用した Cortex-M33 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-471">Building Module Manager for Cortex-M33 using GNU</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-gnu"></a><span data-ttu-id="793fc-472">GNU を使用した Cortex-M33 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-472">Attributes for external memory enable API for Cortex-M33 using GNU</span></span>

| <span data-ttu-id="793fc-473">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-473">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="793fc-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="793fc-474">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="793fc-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="793fc-475">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="793fc-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="793fc-476">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="793fc-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-477">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="793fc-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="793fc-478">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

### <a name="cortex-m33-using-iar"></a><span data-ttu-id="793fc-479">IAR を使用した Cortex-M33</span><span class="sxs-lookup"><span data-stu-id="793fc-479">Cortex-M33 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m33-using-iar"></a><span data-ttu-id="793fc-480">IAR を使用した Cortex-M33 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-480">Module preamble for Cortex-M33 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external refrences.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x6                                               // Module Major Version
    DC32      0x1                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    DC32      _txm_module_thread_shell_entry - . - 0            // Module Shell Entry Point
    DC32      demo_module_start - . - 0                         // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END

```

#### <a name="module-properties-for-cortex-m33-using-iar"></a><span data-ttu-id="793fc-481">IAR を使用した Cortex-M33 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-481">Module properties for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="793fc-482">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-482">Bit</span></span> | <span data-ttu-id="793fc-483">値</span><span class="sxs-lookup"><span data-stu-id="793fc-483">Value</span></span> | <span data-ttu-id="793fc-484">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-484">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-485">0</span><span class="sxs-lookup"><span data-stu-id="793fc-485">0</span></span> | <span data-ttu-id="793fc-486">0</span><span class="sxs-lookup"><span data-stu-id="793fc-486">0</span></span><br /><span data-ttu-id="793fc-487">1</span><span class="sxs-lookup"><span data-stu-id="793fc-487">1</span></span> | <span data-ttu-id="793fc-488">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-488">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-489">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-489">User mode execution</span></span> |
| <span data-ttu-id="793fc-490">1</span><span class="sxs-lookup"><span data-stu-id="793fc-490">1</span></span> | <span data-ttu-id="793fc-491">0</span><span class="sxs-lookup"><span data-stu-id="793fc-491">0</span></span><br /><span data-ttu-id="793fc-492">1</span><span class="sxs-lookup"><span data-stu-id="793fc-492">1</span></span> | <span data-ttu-id="793fc-493">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-493">No MPU protection</span></span><br /><span data-ttu-id="793fc-494">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-494">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-495">2</span><span class="sxs-lookup"><span data-stu-id="793fc-495">2</span></span> | <span data-ttu-id="793fc-496">0</span><span class="sxs-lookup"><span data-stu-id="793fc-496">0</span></span><br /><span data-ttu-id="793fc-497">1</span><span class="sxs-lookup"><span data-stu-id="793fc-497">1</span></span> | <span data-ttu-id="793fc-498">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-498">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-499">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-499">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-500">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-500">[23-3]</span></span> | <span data-ttu-id="793fc-501">0</span><span class="sxs-lookup"><span data-stu-id="793fc-501">0</span></span> | <span data-ttu-id="793fc-502">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-502">Reserved</span></span>
| <span data-ttu-id="793fc-503">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-503">[31-24]</span></span> | <br /><span data-ttu-id="793fc-504">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-504">0x00</span></span><br /><span data-ttu-id="793fc-505">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-505">0x01</span></span><br /><span data-ttu-id="793fc-506">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-506">0x02</span></span> | <span data-ttu-id="793fc-507">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-507">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-508">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-508">IAR</span></span><br /><span data-ttu-id="793fc-509">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-509">ARM</span></span><br /><span data-ttu-id="793fc-510">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-510">GNU</span></span> |

#### <a name="module-linker-for-cortex-m33-using-iar"></a><span data-ttu-id="793fc-511">IAR を使用した Cortex-M33 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-511">Module linker for Cortex-M33 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order 
{ 
  ro object txm_module_preamble.o,
  ro, 
  ro data 
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m33-using-iar"></a><span data-ttu-id="793fc-512">IAR を使用した Cortex-M33 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-512">Building Modules for Cortex-M33 using IAR</span></span>

#### <a name="thread-extension-definition-for-cortex-m33-using-iar"></a><span data-ttu-id="793fc-513">IAR を使用した Cortex-M33 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-513">Thread extension definition for Cortex-M33 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2                   VOID    *tx_thread_module_instance_ptr;         \
                                                VOID    *tx_thread_module_entry_info_ptr;       \
                                                ULONG   tx_thread_module_current_user_mode;     \
                                                ULONG   tx_thread_module_user_mode;             \
                                                ULONG   tx_thread_module_saved_lr;              \
                                                VOID    *tx_thread_module_kernel_stack_start;   \
                                                VOID    *tx_thread_module_kernel_stack_end;     \
                                                ULONG   tx_thread_module_kernel_stack_size;     \
                                                VOID    *tx_thread_module_stack_ptr;            \
                                                VOID    *tx_thread_module_stack_start;          \
                                                VOID    *tx_thread_module_stack_end;            \
                                                ULONG   tx_thread_module_stack_size;            \
                                                VOID    *tx_thread_module_reserved;             \
                                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m33-using-iar"></a><span data-ttu-id="793fc-514">IAR を使用した Cortex-M33 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-514">Building Module Manager for Cortex-M33 using IAR</span></span>

<span data-ttu-id="793fc-515">ワークスペースの例はまだ提供されていません。</span><span class="sxs-lookup"><span data-stu-id="793fc-515">An example workspace is not yet provided.</span></span> <span data-ttu-id="793fc-516">近日対応予定。</span><span class="sxs-lookup"><span data-stu-id="793fc-516">Coming soon.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m33-using-iar"></a><span data-ttu-id="793fc-517">IAR を使用した Cortex-M33 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-517">Attributes for external memory enable API for Cortex-M33 using IAR</span></span>

| <span data-ttu-id="793fc-518">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-518">Attribute parameter</span></span> |
|---|
| <span data-ttu-id="793fc-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="793fc-519">TXM_MODULE_ATTRIBUTE_NON_SHAREABLE</span></span> |
| <span data-ttu-id="793fc-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="793fc-520">TXM_MODULE_ATTRIBUTE_OUTER_SHAREABLE</span></span> |
| <span data-ttu-id="793fc-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span><span class="sxs-lookup"><span data-stu-id="793fc-521">TXM_MODULE_ATTRIBUTE_INNER_SHAREABLE</span></span> |
| <span data-ttu-id="793fc-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-522">TXM_MODULE_ATTRIBUTE_READ_WRITE</span></span> |
| <span data-ttu-id="793fc-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="793fc-523">TXM_MODULE_ATTRIBUTE_READ_ONLY</span></span> |

## <a name="cortex-m4-processor"></a><span data-ttu-id="793fc-524">Cortex-M4 プロセッサ</span><span class="sxs-lookup"><span data-stu-id="793fc-524">Cortex-M4 processor</span></span>

### <a name="cortex-m4-using-ac5"></a><span data-ttu-id="793fc-525">AC5 を使用した Cortex-M4</span><span class="sxs-lookup"><span data-stu-id="793fc-525">Cortex-M4 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac5"></a><span data-ttu-id="793fc-526">AC5 を使用した Cortex-M4 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-526">Module preamble for Cortex-M4 using AC5</span></span>

```armasm
    AREA Init, CODE, READONLY

    PRESERVE8

    /* Define public symbols.  */

    EXPORT __txm_module_preamble

    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start

    /* Define common external references.  */

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          // Module ID
    DCD     0x6                                                 // Module Major Version
    DCD     0x1                                                 // Module Minor Version
    DCD     32                                                  // Module Preamble Size in 32-bit words
    DCD     0x12345678                                          // Module ID (application defined)
    DCD     0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              // Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    DCD     0                                                   // Module Stop Thread Entry Point
    DCD     1                                                   // Module Start/Stop Thread Priority
    DCD     1024                                                // Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   // Module Callback Thread Entry
    DCD     1                                                   // Module Callback Thread Priority
    DCD     1024                                                // Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|     // Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| // Module Data Size
    DCD     0                                                   // Reserved 0
    DCD     0                                                   // Reserved 1
    DCD     0                                                   // Reserved 2
    DCD     0                                                   // Reserved 3
    DCD     0                                                   // Reserved 4
    DCD     0                                                   // Reserved 5
    DCD     0                                                   // Reserved 6
    DCD     0                                                   // Reserved 7
    DCD     0                                                   // Reserved 8
    DCD     0                                                   // Reserved 9
    DCD     0                                                   // Reserved 10
    DCD     0                                                   // Reserved 11
    DCD     0                                                   // Reserved 12
    DCD     0                                                   // Reserved 13
    DCD     0                                                   // Reserved 14
    DCD     0                                                   // Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m4-using-ac5"></a><span data-ttu-id="793fc-527">AC5 を使用した Cortex-M4 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-527">Module properties for Cortex-M4 using AC5</span></span>

| <span data-ttu-id="793fc-528">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-528">Bit</span></span> | <span data-ttu-id="793fc-529">値</span><span class="sxs-lookup"><span data-stu-id="793fc-529">Value</span></span> | <span data-ttu-id="793fc-530">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-530">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-531">0</span><span class="sxs-lookup"><span data-stu-id="793fc-531">0</span></span> | <span data-ttu-id="793fc-532">0</span><span class="sxs-lookup"><span data-stu-id="793fc-532">0</span></span><br /><span data-ttu-id="793fc-533">1</span><span class="sxs-lookup"><span data-stu-id="793fc-533">1</span></span> | <span data-ttu-id="793fc-534">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-534">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-535">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-535">User mode execution</span></span> |
| <span data-ttu-id="793fc-536">1</span><span class="sxs-lookup"><span data-stu-id="793fc-536">1</span></span> | <span data-ttu-id="793fc-537">0</span><span class="sxs-lookup"><span data-stu-id="793fc-537">0</span></span><br /><span data-ttu-id="793fc-538">1</span><span class="sxs-lookup"><span data-stu-id="793fc-538">1</span></span> | <span data-ttu-id="793fc-539">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-539">No MPU protection</span></span><br /><span data-ttu-id="793fc-540">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-540">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-541">2</span><span class="sxs-lookup"><span data-stu-id="793fc-541">2</span></span> | <span data-ttu-id="793fc-542">0</span><span class="sxs-lookup"><span data-stu-id="793fc-542">0</span></span><br /><span data-ttu-id="793fc-543">1</span><span class="sxs-lookup"><span data-stu-id="793fc-543">1</span></span> | <span data-ttu-id="793fc-544">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-544">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-545">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-545">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-546">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-546">[23-3]</span></span> | <span data-ttu-id="793fc-547">0</span><span class="sxs-lookup"><span data-stu-id="793fc-547">0</span></span> | <span data-ttu-id="793fc-548">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-548">Reserved</span></span>
| <span data-ttu-id="793fc-549">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-549">[31-24]</span></span> | <br /><span data-ttu-id="793fc-550">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-550">0x00</span></span><br /><span data-ttu-id="793fc-551">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-551">0x01</span></span><br /><span data-ttu-id="793fc-552">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-552">0x02</span></span> | <span data-ttu-id="793fc-553">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-553">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-554">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-554">IAR</span></span><br /><span data-ttu-id="793fc-555">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-555">ARM</span></span><br /><span data-ttu-id="793fc-556">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-556">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac5"></a><span data-ttu-id="793fc-557">AC5 を使用した Cortex-M4 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-557">Module linker for Cortex-M4 using AC5</span></span>

<span data-ttu-id="793fc-558">リンカー ファイルの例はまだ提供されていません。リンク設定はコマンド ラインで実行されます。</span><span class="sxs-lookup"><span data-stu-id="793fc-558">No example linker file is provided; linking is done on the command line.</span></span> <span data-ttu-id="793fc-559">次のセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="793fc-559">See next section.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac5"></a><span data-ttu-id="793fc-560">AC5 を使用した Cortex-M4 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-560">Building Modules for Cortex-M4 using AC5</span></span>

<span data-ttu-id="793fc-561">build_threadx_module_demo.bat の例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-561">See example build_threadx_module_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork/ropi/rwpi txm_module_preamble.S
armcc  -g --cpu=cortex-m4 --fpu=vfpv4 -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro=0x30000 --rw=0x40000 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m4-using-ac5"></a><span data-ttu-id="793fc-562">AC5 を使用した Cortex-M4 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-562">Thread extension definition for Cortex-M4 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-ac5"></a><span data-ttu-id="793fc-563">AC5 を使用した Cortex-M4 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-563">Building Module Manager for Cortex-M4 using AC5</span></span>

<span data-ttu-id="793fc-564">build_threadx_module_manager_demo.bat の例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-564">See example build_threadx_module_manager_demo.bat:</span></span>

```dos
armasm -g --cpreproc --cpu=cortex-m4 --fpu=vfpv4 --apcs=/interwork tx_initialize_low_level.S
armcc -g --cpu=cortex-m4 --fpu=vfpv4 -c -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module_manager.c
armlink -d -o sample_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list sample_threadx_module_manager.map tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac5"></a><span data-ttu-id="793fc-565">AC5 を使用した Cortex-M4 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-565">Attributes for external memory enable API for Cortex-M4 using AC5</span></span>

<span data-ttu-id="793fc-566">モジュールは常に共有メモリへの読み取りアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="793fc-566">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="793fc-567">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-567">Attribute parameter</span></span> | <span data-ttu-id="793fc-568">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-568">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-569">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-570">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-570">Write access</span></span> |

### <a name="cortex-m4-using-ac6"></a><span data-ttu-id="793fc-571">AC6 を使用した Cortex-M4</span><span class="sxs-lookup"><span data-stu-id="793fc-571">Cortex-M4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-m4-using-ac6"></a><span data-ttu-id="793fc-572">AC6 を使用した Cortex-M4 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-572">Module preamble for Cortex-M4 using AC6</span></span>

```armasm
    .text
    .align 4
    .syntax unified
    .section Init
    
    // Define public symbols
    .global __txm_module_preamble

    // Define application-specific start/stop entry points for the module
    .global demo_module_start

    // Define common external references
    .global  _txm_module_thread_shell_entry
    .global  _txm_module_callback_request_thread_entry

    .eabi_attribute Tag_ABI_PCS_RO_data, 1
    .eabi_attribute Tag_ABI_PCS_R9_use,  1
    .eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
    .dc.l   0x4D4F4455                                          // Module ID
    .dc.l   0x6                                                 // Module Major Version
    .dc.l   0x1                                                 // Module Minor Version
    .dc.l   32                                                  // Module Preamble Size in 32-bit words
    .dc.l   0x12345678                                          // Module ID (application defined)
    .dc.l   0x01000007                                          // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    .dc.l   _txm_module_thread_shell_entry - __txm_module_preamble // Module Shell Entry Point
    .dc.l   demo_module_start - __txm_module_preamble           // Module Start Thread Entry Point
    .dc.l   0                                                   // Module Stop Thread Entry Point
    .dc.l   1                                                   // Module Start/Stop Thread Priority
    .dc.l   1024                                                // Module Start/Stop Thread Stack Size
    .dc.l   _txm_module_callback_request_thread_entry - __txm_module_preamble // Module Callback Thread Entry
    .dc.l   1                                                   // Module Callback Thread Priority
    .dc.l   1024                                                // Module Callback Thread Stack Size
    .dc.l   0x10000                                             // Module Code Size
    .dc.l   0x10000                                             // Module Data Size
    .dc.l   0                                                   // Reserved 0
    .dc.l   0                                                   // Reserved 1
    .dc.l   0                                                   // Reserved 2
    .dc.l   0                                                   // Reserved 3
    .dc.l   0                                                   // Reserved 4
    .dc.l   0                                                   // Reserved 5
    .dc.l   0                                                   // Reserved 6
    .dc.l   0                                                   // Reserved 7
    .dc.l   0                                                   // Reserved 8
    .dc.l   0                                                   // Reserved 9
    .dc.l   0                                                   // Reserved 10
    .dc.l   0                                                   // Reserved 11
    .dc.l   0                                                   // Reserved 12
    .dc.l   0                                                   // Reserved 13
    .dc.l   0                                                   // Reserved 14
    .dc.l   0                                                   // Reserved 15
```

#### <a name="module-properties-for-cortex-m4-using-ac6"></a><span data-ttu-id="793fc-573">AC6 を使用した Cortex-M4 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-573">Module properties for Cortex-M4 using AC6</span></span>

| <span data-ttu-id="793fc-574">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-574">Bit</span></span> | <span data-ttu-id="793fc-575">値</span><span class="sxs-lookup"><span data-stu-id="793fc-575">Value</span></span> | <span data-ttu-id="793fc-576">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-576">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-577">0</span><span class="sxs-lookup"><span data-stu-id="793fc-577">0</span></span> | <span data-ttu-id="793fc-578">0</span><span class="sxs-lookup"><span data-stu-id="793fc-578">0</span></span><br /><span data-ttu-id="793fc-579">1</span><span class="sxs-lookup"><span data-stu-id="793fc-579">1</span></span> | <span data-ttu-id="793fc-580">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-580">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-581">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-581">User mode execution</span></span> |
| <span data-ttu-id="793fc-582">1</span><span class="sxs-lookup"><span data-stu-id="793fc-582">1</span></span> | <span data-ttu-id="793fc-583">0</span><span class="sxs-lookup"><span data-stu-id="793fc-583">0</span></span><br /><span data-ttu-id="793fc-584">1</span><span class="sxs-lookup"><span data-stu-id="793fc-584">1</span></span> | <span data-ttu-id="793fc-585">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-585">No MPU protection</span></span><br /><span data-ttu-id="793fc-586">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-586">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-587">2</span><span class="sxs-lookup"><span data-stu-id="793fc-587">2</span></span> | <span data-ttu-id="793fc-588">0</span><span class="sxs-lookup"><span data-stu-id="793fc-588">0</span></span><br /><span data-ttu-id="793fc-589">1</span><span class="sxs-lookup"><span data-stu-id="793fc-589">1</span></span> | <span data-ttu-id="793fc-590">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-590">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-591">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-591">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-592">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-592">[23-3]</span></span> | <span data-ttu-id="793fc-593">0</span><span class="sxs-lookup"><span data-stu-id="793fc-593">0</span></span> | <span data-ttu-id="793fc-594">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-594">Reserved</span></span>
| <span data-ttu-id="793fc-595">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-595">[31-24]</span></span> | <br /><span data-ttu-id="793fc-596">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-596">0x00</span></span><br /><span data-ttu-id="793fc-597">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-597">0x01</span></span><br /><span data-ttu-id="793fc-598">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-598">0x02</span></span> | <span data-ttu-id="793fc-599">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-599">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-600">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-600">IAR</span></span><br /><span data-ttu-id="793fc-601">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-601">ARM</span></span><br /><span data-ttu-id="793fc-602">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-602">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-ac6"></a><span data-ttu-id="793fc-603">AC6 を使用した Cortex-M4 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-603">Module linker for Cortex-M4 using AC6</span></span>

<span data-ttu-id="793fc-604">リンカー ファイルが使用されていません。</span><span class="sxs-lookup"><span data-stu-id="793fc-604">No linker file is used.</span></span> <span data-ttu-id="793fc-605">プロジェクトの設定をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="793fc-605">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m4-using-ac6"></a><span data-ttu-id="793fc-606">AC6 を使用した Cortex-M4 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-606">Building Modules for Cortex-M4 using AC6</span></span>

<span data-ttu-id="793fc-607">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-607">An example workspace is provided.</span></span> <span data-ttu-id="793fc-608">ThreadX ライブラリ、ThreadX モジュール ライブラリ、サンプル モジュール プロジェクト、およびサンプル モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-608">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-ac6"></a><span data-ttu-id="793fc-609">AC6 を使用した Cortex-M4 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-609">Thread extension definition for Cortex-M4 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-ac6"></a><span data-ttu-id="793fc-610">AC6 を使用した Cortex-M4 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-610">Building Module Manager for Cortex-M4 using AC6</span></span>

<span data-ttu-id="793fc-611">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-611">An example workspace is provided.</span></span> <span data-ttu-id="793fc-612">ThreadX ライブラリ、ThreadX モジュール ライブラリ、サンプル モジュール プロジェクト、およびサンプル モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-612">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-ac6"></a><span data-ttu-id="793fc-613">AC6 を使用した Cortex-M4 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-613">Attributes for external memory enable API for Cortex-M4 using AC6</span></span>

<span data-ttu-id="793fc-614">モジュールは常に共有メモリへの読み取りアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="793fc-614">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="793fc-615">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-615">Attribute parameter</span></span> | <span data-ttu-id="793fc-616">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-616">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-617">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-618">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-618">Write access</span></span> |

### <a name="cortex-m4-using-gnu"></a><span data-ttu-id="793fc-619">GNU を使用した Cortex-M4</span><span class="sxs-lookup"><span data-stu-id="793fc-619">Cortex-M4 using GNU</span></span>

#### <a name="module-preamble-for-cortex-m4-using-gnu"></a><span data-ttu-id="793fc-620">GNU を使用した Cortex-M4 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-620">Module preamble for Cortex-M4 using GNU</span></span>

```armasm
    .text
    .align 4
    .syntax unified

    /* Define public symbols.  */
    .global __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    .global demo_module_start

    /* Define common external refrences.  */
    .global _txm_module_thread_shell_entry
    .global _txm_module_callback_request_thread_entry

__txm_module_preamble:
    .dc.l      0x4D4F4455                                       // Module ID
    .dc.l      0x6                                              // Module Major Version
    .dc.l      0x1                                              // Module Minor Version
    .dc.l      32                                               // Module Preamble Size in 32-bit words
    .dc.l      0x12345678                                       // Module ID (application defined)
    .dc.l      0x02000007                                       // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bits 23-3: Reserved
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
    .dc.l      _txm_module_thread_shell_entry - . - 0           // Module Shell Entry Point
    .dc.l      demo_module_start - . - 0                        // Module Start Thread Entry Point
    .dc.l      0                                                // Module Stop Thread Entry Point 
    .dc.l      1                                                // Module Start/Stop Thread Priority
    .dc.l      1024                                             // Module Start/Stop Thread Stack Size
    .dc.l      _txm_module_callback_request_thread_entry - . - 0 // Module Callback Thread Entry
    .dc.l      1                                                // Module Callback Thread Priority
    .dc.l      1024                                             // Module Callback Thread Stack Size
    .dc.l      __code_size__                                    // Module Code Size
    .dc.l      __data_size__                                    // Module Data Size
    .dc.l      0                                                // Reserved 0
    .dc.l      0                                                // Reserved 1
    .dc.l      0                                                // Reserved 2
    .dc.l      0                                                // Reserved 3
    .dc.l      0                                                // Reserved 4
    .dc.l      0                                                // Reserved 5
    .dc.l      0                                                // Reserved 6
    .dc.l      0                                                // Reserved 7
    .dc.l      0                                                // Reserved 8
    .dc.l      0                                                // Reserved 9
    .dc.l      0                                                // Reserved 10
    .dc.l      0                                                // Reserved 11
    .dc.l      0                                                // Reserved 12
    .dc.l      0                                                // Reserved 13
    .dc.l      0                                                // Reserved 14
    .dc.l      0                                                // Reserved 15
```

#### <a name="module-properties-for-cortex-m4-using-gnu"></a><span data-ttu-id="793fc-621">GNU を使用した Cortex-M4 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-621">Module properties for Cortex-M4 using GNU</span></span>

| <span data-ttu-id="793fc-622">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-622">Bit</span></span> | <span data-ttu-id="793fc-623">値</span><span class="sxs-lookup"><span data-stu-id="793fc-623">Value</span></span> | <span data-ttu-id="793fc-624">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-624">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-625">0</span><span class="sxs-lookup"><span data-stu-id="793fc-625">0</span></span> | <span data-ttu-id="793fc-626">0</span><span class="sxs-lookup"><span data-stu-id="793fc-626">0</span></span><br /><span data-ttu-id="793fc-627">1</span><span class="sxs-lookup"><span data-stu-id="793fc-627">1</span></span> | <span data-ttu-id="793fc-628">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-628">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-629">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-629">User mode execution</span></span> |
| <span data-ttu-id="793fc-630">1</span><span class="sxs-lookup"><span data-stu-id="793fc-630">1</span></span> | <span data-ttu-id="793fc-631">0</span><span class="sxs-lookup"><span data-stu-id="793fc-631">0</span></span><br /><span data-ttu-id="793fc-632">1</span><span class="sxs-lookup"><span data-stu-id="793fc-632">1</span></span> | <span data-ttu-id="793fc-633">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-633">No MPU protection</span></span><br /><span data-ttu-id="793fc-634">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-634">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-635">2</span><span class="sxs-lookup"><span data-stu-id="793fc-635">2</span></span> | <span data-ttu-id="793fc-636">0</span><span class="sxs-lookup"><span data-stu-id="793fc-636">0</span></span><br /><span data-ttu-id="793fc-637">1</span><span class="sxs-lookup"><span data-stu-id="793fc-637">1</span></span> | <span data-ttu-id="793fc-638">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-638">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-639">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-639">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-640">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-640">[23-3]</span></span> | <span data-ttu-id="793fc-641">0</span><span class="sxs-lookup"><span data-stu-id="793fc-641">0</span></span> | <span data-ttu-id="793fc-642">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-642">Reserved</span></span>
| <span data-ttu-id="793fc-643">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-643">[31-24]</span></span> | <br /><span data-ttu-id="793fc-644">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-644">0x00</span></span><br /><span data-ttu-id="793fc-645">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-645">0x01</span></span><br /><span data-ttu-id="793fc-646">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-646">0x02</span></span> | <span data-ttu-id="793fc-647">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-647">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-648">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-648">IAR</span></span><br /><span data-ttu-id="793fc-649">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-649">ARM</span></span><br /><span data-ttu-id="793fc-650">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-650">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-gnu"></a><span data-ttu-id="793fc-651">GNU を使用した Cortex-M4 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-651">Module linker for Cortex-M4 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m4-using-gnu"></a><span data-ttu-id="793fc-652">GNU を使用した Cortex-M4 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-652">Building Modules for Cortex-M4 using GNU</span></span>

<span data-ttu-id="793fc-653">build_threadx_module_sample.bat を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-653">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m4 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m4-using-gnu"></a><span data-ttu-id="793fc-654">GNU を使用した Cortex-M4 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-654">Thread extension definition for Cortex-M4 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m4-using-gnu"></a><span data-ttu-id="793fc-655">GNU を使用した Cortex-M4 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-655">Building Module Manager for Cortex-M4 using GNU</span></span>

<span data-ttu-id="793fc-656">build_threadx_module_manager_sample.bat を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-656">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_vectors.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb tx_initialize_low_level.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -g -mcpu=cortex-m4 -mfloat-abi=hard -mfpu=vfpv4 -mthumb -T sample_threadx.ld -ereset_handler -nostartfiles -o sample_threadx_module_manager.out -Wl,-Map=sample_threadx_module_manager.map cortexm_vectors.o cortexm_crt0.o tx_initialize_low_level.o sample_threadx_module_manager.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-gnu"></a><span data-ttu-id="793fc-657">GNU を使用した Cortex-M4 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-657">Attributes for external memory enable API for Cortex-M4 using GNU</span></span>

<span data-ttu-id="793fc-658">モジュールは常に共有メモリへの読み取りアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="793fc-658">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="793fc-659">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-659">Attribute parameter</span></span> | <span data-ttu-id="793fc-660">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-660">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-661">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-662">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-662">Write access</span></span> |

### <a name="cortex-m4-using-iar"></a><span data-ttu-id="793fc-663">IAR を使用した Cortex-M4</span><span class="sxs-lookup"><span data-stu-id="793fc-663">Cortex-M4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m4-using-iar"></a><span data-ttu-id="793fc-664">IAR を使用した Cortex-M4 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-664">Module preamble for Cortex-M4 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m4-using-iar"></a><span data-ttu-id="793fc-665">IAR を使用した Cortex-M4 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-665">Module properties for Cortex-M4 using IAR</span></span>

| <span data-ttu-id="793fc-666">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-666">Bit</span></span> | <span data-ttu-id="793fc-667">値</span><span class="sxs-lookup"><span data-stu-id="793fc-667">Value</span></span> | <span data-ttu-id="793fc-668">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-668">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-669">0</span><span class="sxs-lookup"><span data-stu-id="793fc-669">0</span></span> | <span data-ttu-id="793fc-670">0</span><span class="sxs-lookup"><span data-stu-id="793fc-670">0</span></span><br /><span data-ttu-id="793fc-671">1</span><span class="sxs-lookup"><span data-stu-id="793fc-671">1</span></span> | <span data-ttu-id="793fc-672">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-672">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-673">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-673">User mode execution</span></span> |
| <span data-ttu-id="793fc-674">1</span><span class="sxs-lookup"><span data-stu-id="793fc-674">1</span></span> | <span data-ttu-id="793fc-675">0</span><span class="sxs-lookup"><span data-stu-id="793fc-675">0</span></span><br /><span data-ttu-id="793fc-676">1</span><span class="sxs-lookup"><span data-stu-id="793fc-676">1</span></span> | <span data-ttu-id="793fc-677">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-677">No MPU protection</span></span><br /><span data-ttu-id="793fc-678">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-678">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-679">2</span><span class="sxs-lookup"><span data-stu-id="793fc-679">2</span></span> | <span data-ttu-id="793fc-680">0</span><span class="sxs-lookup"><span data-stu-id="793fc-680">0</span></span><br /><span data-ttu-id="793fc-681">1</span><span class="sxs-lookup"><span data-stu-id="793fc-681">1</span></span> | <span data-ttu-id="793fc-682">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-682">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-683">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-683">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-684">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-684">[23-3]</span></span> | <span data-ttu-id="793fc-685">0</span><span class="sxs-lookup"><span data-stu-id="793fc-685">0</span></span> | <span data-ttu-id="793fc-686">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-686">Reserved</span></span>
| <span data-ttu-id="793fc-687">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-687">[31-24]</span></span> | <br /><span data-ttu-id="793fc-688">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-688">0x00</span></span><br /><span data-ttu-id="793fc-689">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-689">0x01</span></span><br /><span data-ttu-id="793fc-690">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-690">0x02</span></span> | <span data-ttu-id="793fc-691">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-691">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-692">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-692">IAR</span></span><br /><span data-ttu-id="793fc-693">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-693">ARM</span></span><br /><span data-ttu-id="793fc-694">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-694">GNU</span></span> |

#### <a name="module-linker-for-cortex-m4-using-iar"></a><span data-ttu-id="793fc-695">IAR を使用した Cortex-M4 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-695">Module linker for Cortex-M4 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__ = 0x0;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x080f0000;
define symbol __ICFEDIT_region_ROM_end__   = 0x080fffff;
define symbol __ICFEDIT_region_RAM_start__ = 0x64002800;
define symbol __ICFEDIT_region_RAM_end__   = 0x64100000;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

//define block CSTACK    with alignment = 8, size = __ICFEDIT_size_cstack__   { };
//define block SVC_STACK with alignment = 8, size = __ICFEDIT_size_svcstack__ { };
//define block IRQ_STACK with alignment = 8, size = __ICFEDIT_size_irqstack__ { };
//define block FIQ_STACK with alignment = 8, size = __ICFEDIT_size_fiqstack__ { };
//define block UND_STACK with alignment = 8, size = __ICFEDIT_size_undstack__ { };
//define block ABT_STACK with alignment = 8, size = __ICFEDIT_size_abtstack__ { };
define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

//place at address mem:__ICFEDIT_intvec_start__ { readonly section .intvec };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble_stm32f4xx.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m4-using-iar"></a><span data-ttu-id="793fc-696">IAR を使用した Cortex-M4 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-696">Building Modules for Cortex-M4 using IAR</span></span>

<span data-ttu-id="793fc-697">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-697">An example workspace is provided.</span></span> <span data-ttu-id="793fc-698">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-698">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m4-using-iar"></a><span data-ttu-id="793fc-699">IAR を使用した Cortex-M4 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-699">Thread extension definition for Cortex-M4 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m4-using-iar"></a><span data-ttu-id="793fc-700">IAR を使用した Cortex-M4 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-700">Building Module Manager for Cortex-M4 using IAR</span></span>

<span data-ttu-id="793fc-701">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-701">An example workspace is provided.</span></span> <span data-ttu-id="793fc-702">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-702">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m4-using-iar"></a><span data-ttu-id="793fc-703">IAR を使用した Cortex-M4 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-703">Attributes for external memory enable API for Cortex-M4 using IAR</span></span>

<span data-ttu-id="793fc-704">モジュールは常に共有メモリへの読み取りアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="793fc-704">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="793fc-705">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-705">Attribute parameter</span></span> | <span data-ttu-id="793fc-706">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-706">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-707">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-708">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-708">Write access</span></span> |

## <a name="cortex-m7-processor"></a><span data-ttu-id="793fc-709">Cortex-M7 プロセッサ</span><span class="sxs-lookup"><span data-stu-id="793fc-709">Cortex-M7 processor</span></span>

### <a name="cortex-m7-using-ac5"></a><span data-ttu-id="793fc-710">AC5 を使用した Cortex-M7</span><span class="sxs-lookup"><span data-stu-id="793fc-710">Cortex-M7 using AC5</span></span>

#### <a name="module-preamble-for-cortex-m7-using-ac5"></a><span data-ttu-id="793fc-711">AC5 を使用した Cortex-M7 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-711">Module preamble for Cortex-M7 using AC5</span></span>

```c
    AREA Init, CODE, READONLY

    PRESERVE8

    ; Define public symbols

    EXPORT __txm_module_preamble


    ; Define application-specific start/stop entry points for the module

    EXTERN demo_module_start


    ; Define common external references

    IMPORT  _txm_module_thread_shell_entry
    IMPORT  _txm_module_callback_request_thread_entry
    IMPORT  |Image$$ER_RO$$Length|
    IMPORT  |Image$$ER_RW$$Length|
    IMPORT  |Image$$ER_RW$$RW$$Length|
    IMPORT  |Image$$ER_RW$$ZI$$Length|
    IMPORT  |Image$$ER_ZI$$ZI$$Length|

__txm_module_preamble
    DCD     0x4D4F4455                                          ; Module ID
    DCD     0x5                                                 ; Module Major Version
    DCD     0x6                                                 ; Module Minor Version
    DCD     32                                                  ; Module Preamble Size in 32-bit words
    DCD     0x12345678                                          ; Module ID (application defined)
    DCD     0x01000007                                          ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected)
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
    DCD     _txm_module_thread_shell_entry - __txm_module_preamble              ; Module Shell Entry Point
    DCD     demo_module_start - __txm_module_preamble           ; Module Start Thread Entry Point
    DCD     0                                                   ; Module Stop Thread Entry Point
    DCD     1                                                   ; Module Start/Stop Thread Priority
    DCD     1024                                                ; Module Start/Stop Thread Stack Size
    DCD     _txm_module_callback_request_thread_entry - __txm_module_preamble   ; Module Callback Thread Entry
    DCD     1                                                   ; Module Callback Thread Priority
    DCD     1024                                                ; Module Callback Thread Stack Size
    DCD     |Image$$ER_RO$$Length| + |Image$$ER_RW$$Length|         ; Module Code Size
    DCD     |Image$$ER_RW$$Length| + |Image$$ER_ZI$$ZI$$Length| ; Module Data Size
    DCD     0                                                   ; Reserved 0
    DCD     0                                                   ; Reserved 1
    DCD     0                                                   ; Reserved 2
    DCD     0                                                   ; Reserved 3
    DCD     0                                                   ; Reserved 4
    DCD     0                                                   ; Reserved 5
    DCD     0                                                   ; Reserved 6
    DCD     0                                                   ; Reserved 7
    DCD     0                                                   ; Reserved 8
    DCD     0                                                   ; Reserved 9
    DCD     0                                                   ; Reserved 10
    DCD     0                                                   ; Reserved 11
    DCD     0                                                   ; Reserved 12
    DCD     0                                                   ; Reserved 13
    DCD     0                                                   ; Reserved 14
    DCD     0                                                   ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m7-using-ac5"></a><span data-ttu-id="793fc-712">AC5 を使用した Cortex-M7 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-712">Module properties for Cortex-M7 using AC5</span></span>

| <span data-ttu-id="793fc-713">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-713">Bit</span></span> | <span data-ttu-id="793fc-714">値</span><span class="sxs-lookup"><span data-stu-id="793fc-714">Value</span></span> | <span data-ttu-id="793fc-715">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-715">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-716">0</span><span class="sxs-lookup"><span data-stu-id="793fc-716">0</span></span> | <span data-ttu-id="793fc-717">0</span><span class="sxs-lookup"><span data-stu-id="793fc-717">0</span></span><br /><span data-ttu-id="793fc-718">1</span><span class="sxs-lookup"><span data-stu-id="793fc-718">1</span></span> | <span data-ttu-id="793fc-719">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-719">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-720">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-720">User mode execution</span></span> |
| <span data-ttu-id="793fc-721">1</span><span class="sxs-lookup"><span data-stu-id="793fc-721">1</span></span> | <span data-ttu-id="793fc-722">0</span><span class="sxs-lookup"><span data-stu-id="793fc-722">0</span></span><br /><span data-ttu-id="793fc-723">1</span><span class="sxs-lookup"><span data-stu-id="793fc-723">1</span></span> | <span data-ttu-id="793fc-724">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-724">No MPU protection</span></span><br /><span data-ttu-id="793fc-725">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-725">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-726">2</span><span class="sxs-lookup"><span data-stu-id="793fc-726">2</span></span> | <span data-ttu-id="793fc-727">0</span><span class="sxs-lookup"><span data-stu-id="793fc-727">0</span></span><br /><span data-ttu-id="793fc-728">1</span><span class="sxs-lookup"><span data-stu-id="793fc-728">1</span></span> | <span data-ttu-id="793fc-729">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-729">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-730">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-730">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-731">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-731">[23-3]</span></span> | <span data-ttu-id="793fc-732">0</span><span class="sxs-lookup"><span data-stu-id="793fc-732">0</span></span> | <span data-ttu-id="793fc-733">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-733">Reserved</span></span>
| <span data-ttu-id="793fc-734">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-734">[31-24]</span></span> | <br /><span data-ttu-id="793fc-735">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-735">0x00</span></span><br /><span data-ttu-id="793fc-736">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-736">0x01</span></span><br /><span data-ttu-id="793fc-737">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-737">0x02</span></span> | <span data-ttu-id="793fc-738">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-738">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-739">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-739">IAR</span></span><br /><span data-ttu-id="793fc-740">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-740">ARM</span></span><br /><span data-ttu-id="793fc-741">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-741">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac5"></a><span data-ttu-id="793fc-742">AC5 を使用した Cortex-M7 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-742">Module linker for Cortex-M7 using AC5</span></span>

<span data-ttu-id="793fc-743">コマンド ラインでビルドされます。リンカー ファイルの例はありません。</span><span class="sxs-lookup"><span data-stu-id="793fc-743">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac5"></a><span data-ttu-id="793fc-744">AC5 を使用した Cortex-M7 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-744">Building Modules for Cortex-M7 using AC5</span></span>

<span data-ttu-id="793fc-745">AC5 を使用して Cortex-M7 モジュールをビルドする簡単なコマンド ラインの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-745">A simple command-line example for building a Cortex-M7 module using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=/interwork/ropi/rwpi txm_module_preamble.s
armcc  -g --cpu=cortex-m7 --fpu=softvfp -c --apcs=/interwork/ropi/rwpi --lower_ropi -I../inc -I../../../../common_modules/inc -I../../../../common_modules/module_manager/inc -I../../../../common/inc sample_threadx_module.c
armlink -d -o sample_threadx_module.axf --elf --ro 0 --first txm_module_preamble.o(Init) --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --list sample_threadx_module.map txm_module_preamble.o sample_threadx_module.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-m7-using-ac5"></a><span data-ttu-id="793fc-746">AC5 を使用した Cortex-M7 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-746">Thread extension definition for Cortex-M7 using AC5</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-ac5"></a><span data-ttu-id="793fc-747">AC5 を使用した Cortex-M7 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-747">Building Module Manager for Cortex-M7 using AC5</span></span>

<span data-ttu-id="793fc-748">AC5 を使用して Cortex-M7 モジュール マネージャーをビルドする簡単なコマンド ラインの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-748">A simple command-line example for building a Cortex-M7 module manager using AC5:</span></span>

```dos
armasm -g --cpu=cortex-m7 --fpu=softvfp --apcs=interwork tx_initialize_low_level.s
armcc -g --cpu=cortex-m7 --fpu=softvfp -c demo_threadx_module_manager.c
armcc -g --cpu=cortex-m7 --fpu=softvfp -c module_code.c
armlink -d -o demo_threadx_module_manager.axf --elf --ro 0x00000000 --first tx_initialize_low_level.o(RESET) --remove --map --symbols --list demo_threadx_module_manager.map tx_initialize_low_level.o demo_threadx_module_manager.o module_code.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac5"></a><span data-ttu-id="793fc-749">AC5 を使用した Cortex-M7 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-749">Attributes for external memory enable API for Cortex-M7 using AC5</span></span>

### <a name="cortex-m7-using-ac6"></a><span data-ttu-id="793fc-750">AC6 を使用した Cortex-M7</span><span class="sxs-lookup"><span data-stu-id="793fc-750">Cortex-M7 using AC6</span></span>

#### <a name="module-properties-for-cortex-m7-using-ac6"></a><span data-ttu-id="793fc-751">AC6 を使用した Cortex-M7 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-751">Module properties for Cortex-M7 using AC6</span></span>

| <span data-ttu-id="793fc-752">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-752">Bit</span></span> | <span data-ttu-id="793fc-753">値</span><span class="sxs-lookup"><span data-stu-id="793fc-753">Value</span></span> | <span data-ttu-id="793fc-754">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-754">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-755">0</span><span class="sxs-lookup"><span data-stu-id="793fc-755">0</span></span> | <span data-ttu-id="793fc-756">0</span><span class="sxs-lookup"><span data-stu-id="793fc-756">0</span></span><br /><span data-ttu-id="793fc-757">1</span><span class="sxs-lookup"><span data-stu-id="793fc-757">1</span></span> | <span data-ttu-id="793fc-758">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-758">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-759">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-759">User mode execution</span></span> |
| <span data-ttu-id="793fc-760">1</span><span class="sxs-lookup"><span data-stu-id="793fc-760">1</span></span> | <span data-ttu-id="793fc-761">0</span><span class="sxs-lookup"><span data-stu-id="793fc-761">0</span></span><br /><span data-ttu-id="793fc-762">1</span><span class="sxs-lookup"><span data-stu-id="793fc-762">1</span></span> | <span data-ttu-id="793fc-763">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-763">No MPU protection</span></span><br /><span data-ttu-id="793fc-764">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-764">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-765">2</span><span class="sxs-lookup"><span data-stu-id="793fc-765">2</span></span> | <span data-ttu-id="793fc-766">0</span><span class="sxs-lookup"><span data-stu-id="793fc-766">0</span></span><br /><span data-ttu-id="793fc-767">1</span><span class="sxs-lookup"><span data-stu-id="793fc-767">1</span></span> | <span data-ttu-id="793fc-768">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-768">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-769">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-769">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-770">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-770">[23-3]</span></span> | <span data-ttu-id="793fc-771">0</span><span class="sxs-lookup"><span data-stu-id="793fc-771">0</span></span> | <span data-ttu-id="793fc-772">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-772">Reserved</span></span>
| <span data-ttu-id="793fc-773">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-773">[31-24]</span></span> | <br /><span data-ttu-id="793fc-774">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-774">0x00</span></span><br /><span data-ttu-id="793fc-775">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-775">0x01</span></span><br /><span data-ttu-id="793fc-776">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-776">0x02</span></span> | <span data-ttu-id="793fc-777">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-777">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-778">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-778">IAR</span></span><br /><span data-ttu-id="793fc-779">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-779">ARM</span></span><br /><span data-ttu-id="793fc-780">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-780">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-ac6"></a><span data-ttu-id="793fc-781">AC6 を使用した Cortex-M7 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-781">Module linker for Cortex-M7 using AC6</span></span>

<span data-ttu-id="793fc-782">リンカー ファイルが使用されていません。</span><span class="sxs-lookup"><span data-stu-id="793fc-782">No linker file is used.</span></span> <span data-ttu-id="793fc-783">プロジェクトの設定をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="793fc-783">See project settings.</span></span>

#### <a name="building-modules-for-cortex-m7-using-ac6"></a><span data-ttu-id="793fc-784">AC6 を使用した Cortex-M7 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-784">Building Modules for Cortex-M7 using AC6</span></span>

<span data-ttu-id="793fc-785">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-785">An example workspace is provided.</span></span> <span data-ttu-id="793fc-786">ThreadX ライブラリ、ThreadX モジュール ライブラリ、サンプル モジュール プロジェクト、およびサンプル モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-786">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-ac6"></a><span data-ttu-id="793fc-787">AC6 を使用した Cortex-M7 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-787">Thread extension definition for Cortex-M7 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-ac6"></a><span data-ttu-id="793fc-788">AC6 を使用した Cortex-M7 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-788">Building Module Manager for Cortex-M7 using AC6</span></span>

<span data-ttu-id="793fc-789">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-789">An example workspace is provided.</span></span> <span data-ttu-id="793fc-790">ThreadX ライブラリ、ThreadX モジュール ライブラリ、サンプル モジュール プロジェクト、およびサンプル モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-790">Build the ThreadX library, ThreadX Modules library, sample module project, and sample module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-ac6"></a><span data-ttu-id="793fc-791">AC6 を使用した Cortex-M7 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-791">Attributes for external memory enable API for Cortex-M7 using AC6</span></span>

<span data-ttu-id="793fc-792">モジュールは常に共有メモリへの読み取りアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="793fc-792">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="793fc-793">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-793">Attribute parameter</span></span> | <span data-ttu-id="793fc-794">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-794">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-795">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-796">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-796">Write access</span></span> |

### <a name="cortex-m7-using-gnu"></a><span data-ttu-id="793fc-797">GNU を使用した Cortex-M7</span><span class="sxs-lookup"><span data-stu-id="793fc-797">Cortex-M7 using GNU</span></span>

#### <a name="module-properties-for-cortex-m7-using-gnu"></a><span data-ttu-id="793fc-798">GNU を使用した Cortex-M7 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-798">Module properties for Cortex-M7 using GNU</span></span>

| <span data-ttu-id="793fc-799">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-799">Bit</span></span> | <span data-ttu-id="793fc-800">値</span><span class="sxs-lookup"><span data-stu-id="793fc-800">Value</span></span> | <span data-ttu-id="793fc-801">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-801">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-802">0</span><span class="sxs-lookup"><span data-stu-id="793fc-802">0</span></span> | <span data-ttu-id="793fc-803">0</span><span class="sxs-lookup"><span data-stu-id="793fc-803">0</span></span><br /><span data-ttu-id="793fc-804">1</span><span class="sxs-lookup"><span data-stu-id="793fc-804">1</span></span> | <span data-ttu-id="793fc-805">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-805">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-806">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-806">User mode execution</span></span> |
| <span data-ttu-id="793fc-807">1</span><span class="sxs-lookup"><span data-stu-id="793fc-807">1</span></span> | <span data-ttu-id="793fc-808">0</span><span class="sxs-lookup"><span data-stu-id="793fc-808">0</span></span><br /><span data-ttu-id="793fc-809">1</span><span class="sxs-lookup"><span data-stu-id="793fc-809">1</span></span> | <span data-ttu-id="793fc-810">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-810">No MPU protection</span></span><br /><span data-ttu-id="793fc-811">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-811">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-812">2</span><span class="sxs-lookup"><span data-stu-id="793fc-812">2</span></span> | <span data-ttu-id="793fc-813">0</span><span class="sxs-lookup"><span data-stu-id="793fc-813">0</span></span><br /><span data-ttu-id="793fc-814">1</span><span class="sxs-lookup"><span data-stu-id="793fc-814">1</span></span> | <span data-ttu-id="793fc-815">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-815">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-816">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-816">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-817">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-817">[23-3]</span></span> | <span data-ttu-id="793fc-818">0</span><span class="sxs-lookup"><span data-stu-id="793fc-818">0</span></span> | <span data-ttu-id="793fc-819">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-819">Reserved</span></span>
| <span data-ttu-id="793fc-820">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-820">[31-24]</span></span> | <br /><span data-ttu-id="793fc-821">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-821">0x00</span></span><br /><span data-ttu-id="793fc-822">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-822">0x01</span></span><br /><span data-ttu-id="793fc-823">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-823">0x02</span></span> | <span data-ttu-id="793fc-824">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-824">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-825">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-825">IAR</span></span><br /><span data-ttu-id="793fc-826">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-826">ARM</span></span><br /><span data-ttu-id="793fc-827">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-827">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-gnu"></a><span data-ttu-id="793fc-828">GNU を使用した Cortex-M7 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-828">Module linker for Cortex-M7 using GNU</span></span>

```c
MEMORY
{
  FLASH (rx) : ORIGIN = 0x00030000, LENGTH = 0x00010000
  RAM   (wx) : ORIGIN = 0, LENGTH = 0x00100000
}


SECTIONS
{
  __FLASH_segment_start__ = 0x00030000;
  __FLASH_segment_end__   = 0x00040000;
  __RAM_segment_start__   = 0;
  __RAM_segment_end__     = 0x8000;

  __HEAPSIZE__ = 128;

  __preamble_load_start__ = __FLASH_segment_start__;
  .preamble __FLASH_segment_start__ : AT(__FLASH_segment_start__)
  {
    __preamble_start__ = .;
    *(.preamble .preamble.*)
  }
  __preamble_end__ = __preamble_start__ + SIZEOF(.preamble);

  __dynsym_load_start__ =  ALIGN(__preamble_end__ , 4);
  .dynsym ALIGN(__dynsym_load_start__ , 4) : AT(ALIGN(__dynsym_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynsym))
    KEEP (*(.dynsym*))
    . = ALIGN(4);
  }
  __dynsym_end__ = __dynsym_load_start__ + SIZEOF(.dynsym);

  __dynstr_load_start__ =  ALIGN(__dynsym_end__ , 4);
  .dynstr ALIGN(__dynstr_load_start__ , 4) : AT(ALIGN(__dynstr_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.dynstr))
    KEEP (*(.dynstr*))
    . = ALIGN(4);
  }
  __dynstr_end__ = __dynstr_load_start__ + SIZEOF(.dynstr);

  __reldyn_load_start__ =  ALIGN(__dynstr_end__ , 4);
  .rel.dyn ALIGN(__reldyn_load_start__ , 4) : AT(ALIGN(__reldyn_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.dyn))
    KEEP (*(.rel.dyn*))
    . = ALIGN(4);
  }
  __reldyn_end__ = __reldyn_load_start__ + SIZEOF(.rel.dyn);

  __relplt_load_start__ =  ALIGN(__reldyn_end__ , 4);
  .rel.plt ALIGN(__relplt_load_start__ , 4) : AT(ALIGN(__relplt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.rel.plt))
    KEEP (*(.rel.plt*))
    . = ALIGN(4);
  }
  __relplt_end__ = __relplt_load_start__ + SIZEOF(.rel.plt);

  __plt_load_start__ =  ALIGN(__relplt_end__ , 4);
  .plt ALIGN(__plt_load_start__ , 4) : AT(ALIGN(__plt_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.plt))
    KEEP (*(.plt*))
    . = ALIGN(4);
  }
  __plt_end__ = __plt_load_start__ + SIZEOF(.plt);

  __interp_load_start__ =  ALIGN(__plt_end__ , 4);
  .interp ALIGN(__interp_load_start__ , 4) : AT(ALIGN(__interp_load_start__ , 4))
  {
    . = ALIGN(4);
    KEEP (*(.interp))
    KEEP (*(.interp*))
    . = ALIGN(4);
  }
  __interp_end__ = __interp_load_start__ + SIZEOF(.interp);

  __hash_load_start__ =  ALIGN(__interp_end__ , 4);
  .hash ALIGN(__hash_load_start__ , 4) : AT(ALIGN(__hash_load_start__, 4))
  {
    . = ALIGN(4);
    KEEP (*(.hash))
    KEEP (*(.hash*))
    . = ALIGN(4);
  }
  __hash_end__ = __hash_load_start__ + SIZEOF(.hash);

  __text_load_start__ =  ALIGN(__hash_end__ , 4);
  .text ALIGN(__text_load_start__ , 4) : AT(ALIGN(__text_load_start__, 4))
  {
    __text_start__ = .;
    *(.text .text.* .glue_7t .glue_7 .gnu.linkonce.t.* .gcc_except_table  )
  }
  __text_end__ = __text_start__ + SIZEOF(.text);

  __dtors_load_start__ = ALIGN(__text_end__ , 4);
  .dtors ALIGN(__text_end__ , 4) : AT(ALIGN(__text_end__ , 4))
  {
    __dtors_start__ = .;
    KEEP (*(SORT(.dtors.*))) KEEP (*(.dtors))
  }
  __dtors_end__ = __dtors_start__ + SIZEOF(.dtors);

  __ctors_load_start__ = ALIGN(__dtors_end__ , 4);
  .ctors ALIGN(__dtors_end__ , 4) : AT(ALIGN(__dtors_end__ , 4))
  {
    __ctors_start__ = .;
    KEEP (*(SORT(.ctors.*))) KEEP (*(.ctors))
  }
  __ctors_end__ = __ctors_start__ + SIZEOF(.ctors);

  __got_load_start__ = ALIGN(__ctors_end__ , 4);
  .got ALIGN(__ctors_end__ , 4) : AT(ALIGN(__ctors_end__ , 4))
  {
    . = ALIGN(4);
    _sgot = .;
    KEEP (*(.got))
    KEEP (*(.got*))
    . = ALIGN(4);
    _egot = .;
  } 
  __got_end__ =  __got_load_start__ + SIZEOF(.got);

  __rodata_load_start__ = ALIGN(__got_end__ , 4);
  .rodata ALIGN(__got_end__ , 4) : AT(ALIGN(__got_end__ , 4))
  {
    __rodata_start__ = .;
    *(.rodata .rodata.* .gnu.linkonce.r.*)
  }
  __rodata_end__ = __rodata_start__ + SIZEOF(.rodata);
 
  __code_size__ =  __rodata_end__ - __FLASH_segment_start__;

  __fast_load_start__ = ALIGN(__rodata_end__ , 4);

  __fast_load_end__ = __fast_load_start__ + SIZEOF(.fast);

  __new_got_start__ = ALIGN(__RAM_segment_start__ , 4);

  __new_got_end__ =  __new_got_start__ + SIZEOF(.got);

  .fast ALIGN(__new_got_end__ , 4) : AT(ALIGN(__rodata_end__ , 4))
  {
    __fast_start__ = .;
    *(.fast .fast.*)
  }
  __fast_end__ = __fast_start__ + SIZEOF(.fast);

  .fast_run ALIGN(__fast_end__ , 4) (NOLOAD) :
  {
    __fast_run_start__ = .;
    . = MAX(__fast_run_start__ + SIZEOF(.fast), .);
  }
  __fast_run_end__ = __fast_run_start__ + SIZEOF(.fast_run);

  __data_load_start__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4);
  .data ALIGN(__fast_run_end__ , 4) : AT(ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4))
  {
    __data_start__ = .;
    *(.data .data.* .gnu.linkonce.d.*)
  }
  __data_end__ = __data_start__ + SIZEOF(.data);

  __data_load_end__ = __data_load_start__ + SIZEOF(.data);

  __FLASH_segment_used_end__ = ALIGN(__fast_load_start__ + SIZEOF(.fast) , 4) + SIZEOF(.data);

  .data_run ALIGN(__fast_run_end__ , 4) (NOLOAD) :
  {
    __data_run_start__ = .;
    . = MAX(__data_run_start__ + SIZEOF(.data), .);
  }
  __data_run_end__ = __data_run_start__ + SIZEOF(.data_run);

  __bss_load_start__ = ALIGN(__data_run_end__ , 4);
  .bss ALIGN(__data_run_end__ , 4) (NOLOAD) : AT(ALIGN(__data_run_end__ , 4))
  {
    __bss_start__ = .;
    *(.bss .bss.* .gnu.linkonce.b.*) *(COMMON)
  }
  __bss_end__ = __bss_start__ + SIZEOF(.bss);

  __non_init_load_start__ = ALIGN(__bss_end__ , 4);
  .non_init ALIGN(__bss_end__ , 4) (NOLOAD) : AT(ALIGN(__bss_end__ , 4))
  {
    __non_init_start__ = .;
    *(.non_init .non_init.*)
  }
  __non_init_end__ = __non_init_start__ + SIZEOF(.non_init);

  __heap_load_start__ = ALIGN(__non_init_end__ , 4);
  .heap ALIGN(__non_init_end__ , 4) (NOLOAD) : AT(ALIGN(__non_init_end__ , 4))
  {
    __heap_start__ = .;
    *(.heap)
    . = ALIGN(MAX(__heap_start__ + __HEAPSIZE__ , .), 4);
  }
  __heap_end__ = __heap_start__ + SIZEOF(.heap);

  __data_size__ =  __heap_end__ - __RAM_segment_start__;

}
```

#### <a name="building-modules-for-cortex-m7-using-gnu"></a><span data-ttu-id="793fc-829">GNU を使用した Cortex-M7 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-829">Building Modules for Cortex-M7 using GNU</span></span>

<span data-ttu-id="793fc-830">build_threadx_module_sample.bat を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-830">See build_threadx_module_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base txm_module_preamble.s
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base gcc_setup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -fpie -fno-plt -mpic-data-is-text-relative -msingle-pic-base -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module.c
arm-none-eabi-ld -A cortex-m7 -T sample_threadx_module.ld txm_module_preamble.o gcc_setup.o sample_threadx_module.o -e _txm_module_thread_shell_entry txm.a -o sample_threadx_module.axf -M > sample_threadx_module.map
```

#### <a name="thread-extension-definition-for-cortex-m7-using-gnu"></a><span data-ttu-id="793fc-831">GNU を使用した Cortex-M7 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-831">Thread extension definition for Cortex-M7 using GNU</span></span>

```c
#define TX_THREAD_EXTENSION_2               VOID    *tx_thread_module_instance_ptr;         \
                                            VOID    *tx_thread_module_entry_info_ptr;       \
                                            ULONG   tx_thread_module_current_user_mode;     \
                                            ULONG   tx_thread_module_user_mode;             \
                                            ULONG   tx_thread_module_saved_lr;              \
                                            VOID    *tx_thread_module_kernel_stack_start;   \
                                            VOID    *tx_thread_module_kernel_stack_end;     \
                                            ULONG   tx_thread_module_kernel_stack_size;     \
                                            VOID    *tx_thread_module_stack_ptr;            \
                                            VOID    *tx_thread_module_stack_start;          \
                                            VOID    *tx_thread_module_stack_end;            \
                                            ULONG   tx_thread_module_stack_size;            \
                                            VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-m7-using-gnu"></a><span data-ttu-id="793fc-832">GNU を使用した Cortex-M7 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-832">Building Module Manager for Cortex-M7 using GNU</span></span>

<span data-ttu-id="793fc-833">build_threadx_module_manager_sample.bat を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-833">See build_threadx_module_manager_sample.bat:</span></span>

```dos
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -I..\inc -I..\..\..\..\common\inc -I..\..\..\..\common_modules\inc sample_threadx_module_manager.c
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb tx_simulator_startup.S
arm-none-eabi-gcc -c -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb cortexm_crt0.S
arm-none-eabi-gcc -g -mcpu=cortex-m7 -mfloat-abi=hard -mfpu=fpv5-d16 -mthumb -nostartfiles -ereset_handler -T sample_threadx.ld tx_simulator_startup.o cortexm_crt0.o sample_threadx_module_manager.o tx.a -o sample_threadx_module_manager.axf -Wl,-Map=sample_threadx_module_manager.map
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-gnu"></a><span data-ttu-id="793fc-834">GNU を使用した Cortex-M7 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-834">Attributes for external memory enable API for Cortex-M7 using GNU</span></span>

<span data-ttu-id="793fc-835">モジュールは常に共有メモリへの読み取りアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="793fc-835">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="793fc-836">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-836">Attribute parameter</span></span> | <span data-ttu-id="793fc-837">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-837">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-838">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-839">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-839">Write access</span></span> |

### <a name="cortex-m7-using-iar"></a><span data-ttu-id="793fc-840">IAR を使用した Cortex-M7</span><span class="sxs-lookup"><span data-stu-id="793fc-840">Cortex-M7 using IAR</span></span>

#### <a name="module-preamble-for-cortex-m7-using-iar"></a><span data-ttu-id="793fc-841">IAR を使用した Cortex-M7 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-841">Module preamble for Cortex-M7 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */

    PUBLIC __txm_module_preamble


    /* Define application-specific start/stop entry points for the module.  */

    EXTERN demo_module_start


    /* Define common external references.  */

    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000007                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-3: Reserved
                                                                ;   Bit 2:  0 -> Disable shared/external memory access
                                                                ;           1 -> Enable shared/external memory access
                                                                ;   Bit 1:  0 -> No MPU protection
                                                                ;           1 -> MPU protection (must have user mode selected - bit 0 set)
                                                                ;   Bit 0:  0 -> Privileged mode execution
                                                                ;           1 -> User mode execution


    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-m7-using-iar"></a><span data-ttu-id="793fc-842">IAR を使用した Cortex-M7 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-842">Module properties for Cortex-M7 using IAR</span></span>

| <span data-ttu-id="793fc-843">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-843">Bit</span></span> | <span data-ttu-id="793fc-844">値</span><span class="sxs-lookup"><span data-stu-id="793fc-844">Value</span></span> | <span data-ttu-id="793fc-845">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-845">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-846">0</span><span class="sxs-lookup"><span data-stu-id="793fc-846">0</span></span> | <span data-ttu-id="793fc-847">0</span><span class="sxs-lookup"><span data-stu-id="793fc-847">0</span></span><br /><span data-ttu-id="793fc-848">1</span><span class="sxs-lookup"><span data-stu-id="793fc-848">1</span></span> | <span data-ttu-id="793fc-849">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-849">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-850">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-850">User mode execution</span></span> |
| <span data-ttu-id="793fc-851">1</span><span class="sxs-lookup"><span data-stu-id="793fc-851">1</span></span> | <span data-ttu-id="793fc-852">0</span><span class="sxs-lookup"><span data-stu-id="793fc-852">0</span></span><br /><span data-ttu-id="793fc-853">1</span><span class="sxs-lookup"><span data-stu-id="793fc-853">1</span></span> | <span data-ttu-id="793fc-854">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-854">No MPU protection</span></span><br /><span data-ttu-id="793fc-855">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-855">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-856">2</span><span class="sxs-lookup"><span data-stu-id="793fc-856">2</span></span> | <span data-ttu-id="793fc-857">0</span><span class="sxs-lookup"><span data-stu-id="793fc-857">0</span></span><br /><span data-ttu-id="793fc-858">1</span><span class="sxs-lookup"><span data-stu-id="793fc-858">1</span></span> | <span data-ttu-id="793fc-859">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-859">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-860">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-860">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-861">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-861">[23-3]</span></span> | <span data-ttu-id="793fc-862">0</span><span class="sxs-lookup"><span data-stu-id="793fc-862">0</span></span> | <span data-ttu-id="793fc-863">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-863">Reserved</span></span>
| <span data-ttu-id="793fc-864">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-864">[31-24]</span></span> | <br /><span data-ttu-id="793fc-865">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-865">0x00</span></span><br /><span data-ttu-id="793fc-866">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-866">0x01</span></span><br /><span data-ttu-id="793fc-867">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-867">0x02</span></span> | <span data-ttu-id="793fc-868">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-868">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-869">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-869">IAR</span></span><br /><span data-ttu-id="793fc-870">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-870">ARM</span></span><br /><span data-ttu-id="793fc-871">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-871">GNU</span></span> |

#### <a name="module-linker-for-cortex-m7-using-iar"></a><span data-ttu-id="793fc-872">IAR を使用した Cortex-M7 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-872">Module linker for Cortex-M7 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\cortex_v1_0.xml" */
/*-Specials-*/
define symbol __ICFEDIT_intvec_start__     = 0x00400000;
/*-Memory Regions-*/
define symbol __ICFEDIT_region_RAM_start__ = 0x20450000;
define symbol __ICFEDIT_region_RAM_end__   = 0x2045f000 -1;
define symbol __ICFEDIT_region_RAM_NOCACHE_start__ = 0x2045f000;
define symbol __ICFEDIT_region_RAM_NOCACHE_end__   = 0x20460000 -1;
define symbol __ICFEDIT_region_ROM_start__ = 0x00500000;
define symbol __ICFEDIT_region_ROM_end__   = 0x00600000 -1;
define symbol __ICFEDIT_region_SDRAM_start__ = 0x70000000;
define symbol __ICFEDIT_region_SDRAM_end__   = 0x70200000 -1;

/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__      = 0x2000;
define symbol __ICFEDIT_size_heap__        = 0x1000;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region RAM_region    = mem:[from __ICFEDIT_region_RAM_start__ to __ICFEDIT_region_RAM_end__];
define region RAM_NOCACHE_region = mem:[from __ICFEDIT_region_RAM_NOCACHE_start__ to __ICFEDIT_region_RAM_NOCACHE_end__];
define region ROM_region    = mem:[from __ICFEDIT_region_ROM_start__ to __ICFEDIT_region_ROM_end__];
define region SDRAM_region  = mem:[from __ICFEDIT_region_SDRAM_start__ to __ICFEDIT_region_SDRAM_end__];

define block HEAP   with alignment = 8, size = __ICFEDIT_size_heap__   { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-m7-using-iar"></a><span data-ttu-id="793fc-873">IAR を使用した Cortex-M7 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-873">Building Modules for Cortex-M7 using IAR</span></span>

<span data-ttu-id="793fc-874">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-874">An example workspace is provided.</span></span> <span data-ttu-id="793fc-875">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-875">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-m7-using-iar"></a><span data-ttu-id="793fc-876">IAR を使用した Cortex-M7 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-876">Thread extension definition for Cortex-M7 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_saved_lr;              \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-m7-using-iar"></a><span data-ttu-id="793fc-877">IAR を使用した Cortex-M7 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-877">Building Module Manager for Cortex-M7 using IAR</span></span>

<span data-ttu-id="793fc-878">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-878">An example workspace is provided.</span></span> <span data-ttu-id="793fc-879">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-879">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-m7-using-iar"></a><span data-ttu-id="793fc-880">IAR を使用した Cortex-M7 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-880">Attributes for external memory enable API for Cortex-M7 using IAR</span></span>

<span data-ttu-id="793fc-881">モジュールは常に共有メモリへの読み取りアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="793fc-881">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="793fc-882">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-882">Attribute parameter</span></span> | <span data-ttu-id="793fc-883">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-883">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-884">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-885">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-885">Write access</span></span> |

## <a name="cortex-r4-processor"></a><span data-ttu-id="793fc-886">Cortex-R4 プロセッサ</span><span class="sxs-lookup"><span data-stu-id="793fc-886">Cortex-R4 processor</span></span>

### <a name="cortex-r4-using-ac6"></a><span data-ttu-id="793fc-887">AC6 を使用した Cortex-R4</span><span class="sxs-lookup"><span data-stu-id="793fc-887">Cortex-R4 using AC6</span></span>

#### <a name="module-preamble-for-cortex-r4-using-ac6"></a><span data-ttu-id="793fc-888">AC6 を使用した Cortex-R4 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-888">Module preamble for Cortex-R4 using AC6</span></span>

```c
    .text

/* Define common external references.  */

.global     _txm_module_thread_shell_entry
.global     demo_module_start
.global     _txm_module_callback_request_thread_entry
.global     Image$$ER_RO$$Length
.global     Image$$ER_RW$$Length
.global     Image$$ER_ZI$$ZI$$Length

/* Stack aligned, ROPI and RWPI, R9 used as data offset register.  */
.eabi_attribute Tag_ABI_align_preserved, 1
.eabi_attribute Tag_ABI_PCS_RO_data, 1
.eabi_attribute Tag_ABI_PCS_R9_use,  1
.eabi_attribute Tag_ABI_PCS_RW_data, 2

__txm_module_preamble:
.word   0x4D4F4455                                          /* Module ID  */
.word   0x5                                                 /* Module Major Version  */
.word   0x3                                                 /* Module Minor Version  */
.word   32                                                  /* Module Preamble Size in 32-bit words  */
.word   0x12345678                                          /* Module ID (application defined)  */
.word   0x01000001                                          /* Module Properties where:
                                                               Bits 31-24: Compiler ID
                                                                       0 -> IAR
                                                                       1 -> RVDS/ARM
                                                                       2 -> GNU
                                                               Bits 23-1:  Reserved
                                                               Bit 0:  0 -> Privileged mode execution (no MMU protection)
                                                                       1 -> User mode execution (MMU protection)  */
.word   _txm_module_thread_shell_entry - __txm_module_preamble  /* Module Shell Entry Point  */
.word   demo_module_start - __txm_module_preamble           /* Module Start Thread Entry Point  */
.word   0                                                   /* Module Stop Thread Entry Point   */
.word   1                                                   /* Module Start/Stop Thread Priority  */
.word   1024                                                /* Module Start/Stop Thread Stack Size  */
.word   _txm_module_callback_request_thread_entry - __txm_module_preamble   /* Module Callback Thread Entry  */
.word   1                                                   /* Module Callback Thread Priority  */
.word   1024                                                /* Module Callback Thread Stack Size  */
.word   9000                                                /* Module Code Size */
.word   11000                                               /* Module Data Size */
.word   0                                                   /* Reserved 0  */
.word   0                                                   /* Reserved 1  */
.word   0                                                   /* Reserved 2  */
.word   0                                                   /* Reserved 3  */
.word   0                                                   /* Reserved 4  */
.word   0                                                   /* Reserved 5  */
.word   0                                                   /* Reserved 6  */
.word   0                                                   /* Reserved 7  */
.word   0                                                   /* Reserved 8  */
.word   0                                                   /* Reserved 9  */
.word   0                                                   /* Reserved 10  */
.word   0                                                   /* Reserved 11  */
.word   0                                                   /* Reserved 12  */
.word   0                                                   /* Reserved 13  */
.word   0                                                   /* Reserved 14  */
.word   0                                                   /* Reserved 15  */
```

#### <a name="module-properties-for-cortex-r4-using-ac6"></a><span data-ttu-id="793fc-889">AC6 を使用した Cortex-R4 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-889">Module properties for Cortex-R4 using AC6</span></span>

| <span data-ttu-id="793fc-890">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-890">Bit</span></span> | <span data-ttu-id="793fc-891">値</span><span class="sxs-lookup"><span data-stu-id="793fc-891">Value</span></span> | <span data-ttu-id="793fc-892">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-892">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-893">0</span><span class="sxs-lookup"><span data-stu-id="793fc-893">0</span></span> | <span data-ttu-id="793fc-894">0</span><span class="sxs-lookup"><span data-stu-id="793fc-894">0</span></span><br /><span data-ttu-id="793fc-895">1</span><span class="sxs-lookup"><span data-stu-id="793fc-895">1</span></span> | <span data-ttu-id="793fc-896">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-896">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-897">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-897">User mode execution</span></span> |
| <span data-ttu-id="793fc-898">[23-1]</span><span class="sxs-lookup"><span data-stu-id="793fc-898">[23-1]</span></span> | <span data-ttu-id="793fc-899">0</span><span class="sxs-lookup"><span data-stu-id="793fc-899">0</span></span> | <span data-ttu-id="793fc-900">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-900">Reserved</span></span>
| <span data-ttu-id="793fc-901">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-901">[31-24]</span></span> | <br /><span data-ttu-id="793fc-902">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-902">0x00</span></span><br /><span data-ttu-id="793fc-903">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-903">0x01</span></span><br /><span data-ttu-id="793fc-904">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-904">0x02</span></span> | <span data-ttu-id="793fc-905">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-905">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-906">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-906">IAR</span></span><br /><span data-ttu-id="793fc-907">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-907">ARM</span></span><br /><span data-ttu-id="793fc-908">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-908">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-ac6"></a><span data-ttu-id="793fc-909">AC6 を使用した Cortex-R4 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-909">Module linker for Cortex-R4 using AC6</span></span>

<span data-ttu-id="793fc-910">コマンド ラインでビルドされます。リンカー ファイルの例はありません。</span><span class="sxs-lookup"><span data-stu-id="793fc-910">Built on command-line, no linker file example.</span></span>

#### <a name="building-modules-for-cortex-r4-using-ac6"></a><span data-ttu-id="793fc-911">AC6 を使用した Cortex-R4 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-911">Building Modules for Cortex-R4 using AC6</span></span>

<span data-ttu-id="793fc-912">AC6 を使用して Cortex-R4 モジュールをビルドする簡単なコマンド ラインの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-912">A simple command-line example for building a Cortex-R4 module using AC6:</span></span>

```dos
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module.c
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 txm_module_preamble.S
armclang -c -g -fropi -frwpi --target=arm-arm-none-eabi -mcpu=cortex-r4 semihosting.c
armlink -d -o demo_threadx_module.axf --elf --ro 0x00100000 --first txm_module_preamble.o --entry=_txm_module_thread_shell_entry --ropi --rwpi --remove --map --symbols --datacompressor=off --list demo_threadx_module.map txm_module_preamble.o demo_threadx_module.o semihosting.o txm.a
```

#### <a name="thread-extension-definition-for-cortex-r4-using-ac6"></a><span data-ttu-id="793fc-913">AC6 を使用した Cortex-R4 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-913">Thread extension definition for Cortex-R4 using AC6</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-cortex-r4-using-ac6"></a><span data-ttu-id="793fc-914">AC6 を使用した Cortex-R4 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-914">Building Module Manager for Cortex-R4 using AC6</span></span>

<span data-ttu-id="793fc-915">AC6 を使用して Cortex-R4 モジュール マネージャーをビルドする簡単なコマンド ラインの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="793fc-915">A simple command-line example for building a Cortex-R4 module manager using AC6:</span></span>

```dos
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 demo_threadx_module_manager.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 timer.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 gic.c
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 tx_initialize_low_level.S
armclang -c -g --target=arm-arm-none-eabi -mcpu=cortex-r4 startup.S
armlink -d -o demo_threadx_module_manager.axf --elf --scatter=demo_threadx.scat --remove --map --symbols --list demo_threadx_module_manager.map startup.o timer.o gic.o demo_threadx_module_manager.o tx_initialize_low_level.o tx.a
```

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-ac6"></a><span data-ttu-id="793fc-916">AC6 を使用した Cortex-R4 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-916">Attributes for external memory enable API for Cortex-R4 using AC6</span></span>

<span data-ttu-id="793fc-917">モジュールは常に共有メモリへの読み取りアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="793fc-917">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="793fc-918">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-918">Attribute parameter</span></span> | <span data-ttu-id="793fc-919">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-919">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-920">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-921">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-921">Write access</span></span> |

### <a name="cortex-r4-using-iar"></a><span data-ttu-id="793fc-922">IAR を使用した Cortex-R4</span><span class="sxs-lookup"><span data-stu-id="793fc-922">Cortex-R4 using IAR</span></span>

#### <a name="module-preamble-for-cortex-r4-using-iar"></a><span data-ttu-id="793fc-923">IAR を使用した Cortex-R4 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-923">Module preamble for Cortex-R4 using IAR</span></span>

```c
    SECTION .text:CODE

    AAPCS INTERWORK, ROPI, RWPI_COMPATIBLE,  VFP_COMPATIBLE
    PRESERVE8

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN demo_module_start

    /* Define common external references.  */
    EXTERN  _txm_module_thread_shell_entry
    EXTERN  _txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        ; Module ID
    DC32      0x5                                               ; Module Major Version
    DC32      0x6                                               ; Module Minor Version
    DC32      32                                                ; Module Preamble Size in 32-bit words
    DC32      0x12345678                                        ; Module ID (application defined)
    DC32      0x00000001                                        ; Module Properties where:
                                                                ;   Bits 31-24: Compiler ID
                                                                ;           0 -> IAR
                                                                ;           1 -> ARM
                                                                ;           2 -> GNU
                                                                ;   Bits 23-1: Reserved
                                                                ;   Bit 0:  0 -> Privileged mode execution (no MPU protection)
                                                                ;           1 -> User mode execution (MPU protection)
    DC32      _txm_module_thread_shell_entry - . - 0            ; Module Shell Entry Point
    DC32      demo_module_start - . - 0                         ; Module Start Thread Entry Point
    DC32      0                                                 ; Module Stop Thread Entry Point
    DC32      1                                                 ; Module Start/Stop Thread Priority
    DC32      1024                                              ; Module Start/Stop Thread Stack Size
    DC32      _txm_module_callback_request_thread_entry - . - 0 ; Module Callback Thread Entry
    DC32      1                                                 ; Module Callback Thread Priority
    DC32      1024                                              ; Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      ; Module Code Size
    DC32      RWPI$$Length                                      ; Module Data Size
    DC32      0                                                 ; Reserved 0
    DC32      0                                                 ; Reserved 1
    DC32      0                                                 ; Reserved 2
    DC32      0                                                 ; Reserved 3
    DC32      0                                                 ; Reserved 4
    DC32      0                                                 ; Reserved 5
    DC32      0                                                 ; Reserved 6
    DC32      0                                                 ; Reserved 7
    DC32      0                                                 ; Reserved 8  
    DC32      0                                                 ; Reserved 9
    DC32      0                                                 ; Reserved 10
    DC32      0                                                 ; Reserved 11
    DC32      0                                                 ; Reserved 12
    DC32      0                                                 ; Reserved 13
    DC32      0                                                 ; Reserved 14
    DC32      0                                                 ; Reserved 15

    END
```

#### <a name="module-properties-for-cortex-r4-using-iar"></a><span data-ttu-id="793fc-924">IAR を使用した Cortex-R4 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-924">Module properties for Cortex-R4 using IAR</span></span>

| <span data-ttu-id="793fc-925">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-925">Bit</span></span> | <span data-ttu-id="793fc-926">値</span><span class="sxs-lookup"><span data-stu-id="793fc-926">Value</span></span> | <span data-ttu-id="793fc-927">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-927">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-928">0</span><span class="sxs-lookup"><span data-stu-id="793fc-928">0</span></span> | <span data-ttu-id="793fc-929">0</span><span class="sxs-lookup"><span data-stu-id="793fc-929">0</span></span><br /><span data-ttu-id="793fc-930">1</span><span class="sxs-lookup"><span data-stu-id="793fc-930">1</span></span> | <span data-ttu-id="793fc-931">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-931">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-932">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-932">User mode execution</span></span> |
| <span data-ttu-id="793fc-933">[23-1]</span><span class="sxs-lookup"><span data-stu-id="793fc-933">[23-1]</span></span> | <span data-ttu-id="793fc-934">0</span><span class="sxs-lookup"><span data-stu-id="793fc-934">0</span></span> | <span data-ttu-id="793fc-935">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-935">Reserved</span></span>
| <span data-ttu-id="793fc-936">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-936">[31-24]</span></span> | <br /><span data-ttu-id="793fc-937">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-937">0x00</span></span><br /><span data-ttu-id="793fc-938">0x01</span><span class="sxs-lookup"><span data-stu-id="793fc-938">0x01</span></span><br /><span data-ttu-id="793fc-939">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-939">0x02</span></span> | <span data-ttu-id="793fc-940">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-940">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-941">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-941">IAR</span></span><br /><span data-ttu-id="793fc-942">ARM</span><span class="sxs-lookup"><span data-stu-id="793fc-942">ARM</span></span><br /><span data-ttu-id="793fc-943">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-943">GNU</span></span> |

#### <a name="module-linker-for-cortex-r4-using-iar"></a><span data-ttu-id="793fc-944">IAR を使用した Cortex-R4 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-944">Module linker for Cortex-R4 using IAR</span></span>

```c
/*###ICF### Section handled by ICF editor, don't touch! ****/
/*-Editor annotation file-*/
/* IcfEditorFile="$TOOLKIT_DIR$\config\ide\IcfEditor\a_v1_0.xml" */
/*-Specials-*/
/*-Memory Regions-*/
define symbol __ICFEDIT_region_ROM_start__ = 0x00100000;
define symbol __ICFEDIT_region_ROM_end__   = 0x0013FFFF;
define symbol __ICFEDIT_region_RAM_start__ = 0x08000000;
define symbol __ICFEDIT_region_RAM_end__   = 0x0800FFFF;
/*-Sizes-*/
define symbol __ICFEDIT_size_cstack__   = 0;
define symbol __ICFEDIT_size_svcstack__ = 0;
define symbol __ICFEDIT_size_irqstack__ = 0;
define symbol __ICFEDIT_size_fiqstack__ = 0;
define symbol __ICFEDIT_size_undstack__ = 0;
define symbol __ICFEDIT_size_abtstack__ = 0;
define symbol __ICFEDIT_size_heap__     = 0x100;
/**** End of ICF editor section. ###ICF###*/

define memory mem with size = 4G;
define region ROM_region   = mem:[from __ICFEDIT_region_ROM_start__   to __ICFEDIT_region_ROM_end__];
define region RAM_region   = mem:[from __ICFEDIT_region_RAM_start__   to __ICFEDIT_region_RAM_end__];

define block HEAP      with alignment = 8, size = __ICFEDIT_size_heap__     { };

initialize by copy { readwrite };
do not initialize  { section .noinit };

define movable block ROPI with alignment = 4, fixed order
{
  ro object txm_module_preamble.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base
{
  rw,
  block HEAP
};

place in ROM_region   { block ROPI };
place in RAM_region   { block RWPI };
```

#### <a name="building-modules-for-cortex-r4-using-iar"></a><span data-ttu-id="793fc-945">IAR を使用した Cortex-R4 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-945">Building Modules for Cortex-R4 using IAR</span></span>

<span data-ttu-id="793fc-946">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-946">An example workspace is provided.</span></span> <span data-ttu-id="793fc-947">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-947">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-cortex-r4-using-iar"></a><span data-ttu-id="793fc-948">IAR を使用した Cortex-R4 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-948">Thread extension definition for Cortex-R4 using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   ULONG   tx_thread_vfp_enable;                   \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-cortex-r4-using-iar"></a><span data-ttu-id="793fc-949">IAR を使用した Cortex-R4 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-949">Building Module Manager for Cortex-R4 using IAR</span></span>

<span data-ttu-id="793fc-950">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-950">An example workspace is provided.</span></span> <span data-ttu-id="793fc-951">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-951">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-cortex-r4-using-iar"></a><span data-ttu-id="793fc-952">IAR を使用した Cortex-R4 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-952">Attributes for external memory enable API for Cortex-R4 using IAR</span></span>

<span data-ttu-id="793fc-953">モジュールは常に共有メモリへの読み取りアクセスが可能です。</span><span class="sxs-lookup"><span data-stu-id="793fc-953">Module always has read access to shared memory.</span></span>

| <span data-ttu-id="793fc-954">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-954">Attribute parameter</span></span> | <span data-ttu-id="793fc-955">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-955">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-956">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-957">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-957">Write access</span></span> |

## <a name="mcf544xx-processor"></a><span data-ttu-id="793fc-958">MCF544xx プロセッサ</span><span class="sxs-lookup"><span data-stu-id="793fc-958">MCF544xx processor</span></span>

### <a name="mcf544xx-using-ghs"></a><span data-ttu-id="793fc-959">GHS を使用した MCF544xx</span><span class="sxs-lookup"><span data-stu-id="793fc-959">MCF544xx using GHS</span></span>

#### <a name="module-preamble-for-mcf544xx-using-ghs"></a><span data-ttu-id="793fc-960">GHS を使用した MCF544xx 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-960">Module preamble for MCF544xx using GHS</span></span>

```c
    SECT    .preamble, x

    /* Define public symbols.  */
    XDEF __txm_module_preamble

__txm_module_preamble:
    DC.L    0x4D4F4455                                  /* Module ID                                */
    DC.L    0x5                                         /* Module Major Version                     */
    DC.L    0x3                                         /* Module Minor Version                     */
    DC.L    32                                          /* Module Preamble Size in 32-bit words     */
    DC.L    0x12345678                                  /* Module ID (application defined)          */
    DC.L    0x03000003                                  /* Module Properties where:                 */
                                                        /* Bits 31-24: Compiler ID                  */
                                                        /*           3 -> GHS                       */
                                                        /* Bits 23-2: Reserved                      */
                                                        /* Bit 1:  0 -> No MMU protection           */
                                                        /*         1 -> MMU protection (must have   */
                                                        /*              user mode selected)         */
                                                        /* Bit 0:  0 -> Supervisor mode execution   */
                                                        /*         1 -> User mode execution         */
    DC.L    _txm_module_thread_shell_entry              /* Module Shell Entry Point                 */
    DC.L    demo_module_start                           /* Module Start Thread Entry Point          */
    DC.L    0                                           /* Module Stop Thread Entry Point           */
    DC.L    1                                           /* Module Start/Stop Thread Priority        */
    DC.L    2048                                        /* Module Start/Stop Thread Stack Size      */
    DC.L    _txm_module_callback_request_thread_entry   /* Module Callback Thread Entry             */
    DC.L    1                                           /* Module Callback Thread Priority          */
    DC.L    2048                                        /* Module Callback Thread Stack Size        */
    DC.L    module_code_size                            /* Module Code Size                         */
    DC.L    module_data_size                            /* Module Data Size                         */
    DC.L    0                                           /* Reserved 0                               */
    DC.L    0                                           /* Reserved 1                               */
    DC.L    0                                           /* Reserved 2                               */
    DC.L    0                                           /* Reserved 3                               */
    DC.L    0                                           /* Reserved 4                               */
    DC.L    0                                           /* Reserved 5                               */
    DC.L    0                                           /* Reserved 6                               */
    DC.L    0                                           /* Reserved 7                               */
    DC.L    0                                           /* Reserved 8                               */
    DC.L    0                                           /* Reserved 9                               */
    DC.L    0                                           /* Reserved 10                              */
    DC.L    0                                           /* Reserved 11                              */
    DC.L    0                                           /* Reserved 12                              */
    DC.L    0                                           /* Reserved 13                              */
    DC.L    0                                           /* Reserved 14                              */
    DC.L    0                                           /* Reserved 15                              */

    END
```

#### <a name="module-properties-for-mcf544xx-using-ghs"></a><span data-ttu-id="793fc-961">GHS を使用した MCF544xx 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-961">Module properties for MCF544xx using GHS</span></span>

| <span data-ttu-id="793fc-962">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-962">Bit</span></span> | <span data-ttu-id="793fc-963">値</span><span class="sxs-lookup"><span data-stu-id="793fc-963">Value</span></span> | <span data-ttu-id="793fc-964">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-964">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-965">0</span><span class="sxs-lookup"><span data-stu-id="793fc-965">0</span></span> | <span data-ttu-id="793fc-966">0</span><span class="sxs-lookup"><span data-stu-id="793fc-966">0</span></span><br /><span data-ttu-id="793fc-967">1</span><span class="sxs-lookup"><span data-stu-id="793fc-967">1</span></span> | <span data-ttu-id="793fc-968">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-968">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-969">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-969">User mode execution</span></span> |
| <span data-ttu-id="793fc-970">1</span><span class="sxs-lookup"><span data-stu-id="793fc-970">1</span></span> | <span data-ttu-id="793fc-971">0</span><span class="sxs-lookup"><span data-stu-id="793fc-971">0</span></span><br /><span data-ttu-id="793fc-972">1</span><span class="sxs-lookup"><span data-stu-id="793fc-972">1</span></span> | <span data-ttu-id="793fc-973">MMU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-973">No MMU protection</span></span><br /><span data-ttu-id="793fc-974">MMU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-974">MMU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-975">2</span><span class="sxs-lookup"><span data-stu-id="793fc-975">2</span></span> | <span data-ttu-id="793fc-976">0</span><span class="sxs-lookup"><span data-stu-id="793fc-976">0</span></span><br /><span data-ttu-id="793fc-977">1</span><span class="sxs-lookup"><span data-stu-id="793fc-977">1</span></span> | <span data-ttu-id="793fc-978">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-978">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-979">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-979">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-980">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-980">[23-3]</span></span> | <span data-ttu-id="793fc-981">0</span><span class="sxs-lookup"><span data-stu-id="793fc-981">0</span></span> | <span data-ttu-id="793fc-982">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-982">Reserved</span></span>
| <span data-ttu-id="793fc-983">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-983">[31-24]</span></span> | <br /><span data-ttu-id="793fc-984">0x03</span><span class="sxs-lookup"><span data-stu-id="793fc-984">0x03</span></span> | <span data-ttu-id="793fc-985">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-985">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-986">GHS</span><span class="sxs-lookup"><span data-stu-id="793fc-986">GHS</span></span> |

#### <a name="module-linker-for-mcf544xx-using-ghs"></a><span data-ttu-id="793fc-987">GHS を使用した MCF544xx 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-987">Module linker for MCF544xx using GHS</span></span>

```c
DEFAULTS {

    heap_reserve =  256
    stack_reserve = 256
}

//
// Program layout for PIC and PID built programs.
//

-sec
{
//
// The data segment
//
    .pidbase                0x00000000 :
    .sdabase                           :
    .sbss                   NOCLEAR    :
    .sdata                             :
    .data                   NOLOAD     :
    .bss                    NOCLEAR    :
    .heap                   ALIGN(16) PAD( heap_reserve +
        // Add space for call-graph profiling if used:
        (isdefined(__ghs_indgcount)?(2000+(sizeof(.text)/2)):0) +
        // Add estimated space for call-count profiling if used:
        (isdefined(__ghs_indmcount)?10000:0) )
                                             :
    .stack      ALIGN(16) PAD(stack_reserve) :

    module_data_size = sizeof(.pidbase) + sizeof(.sdabase) + sizeof(.sbss) + sizeof(.sdata) + sizeof(.data) + sizeof(.bss) + sizeof(.heap) + sizeof(.stack);

//
// The code segment
//

    .picbase                0x00000000 :
    .preamble                          :
    .text                              :
    .syscall                           :
    .fixaddr                           :
    .fixtype                           :
    .rodata                            :
    .ROM.data               ROM(.data) :
    .secinfo                           :

    module_code_size =  endaddr(.secinfo);
}
```

#### <a name="building-modules-for-mcf544xx-using-ghs"></a><span data-ttu-id="793fc-988">GHS を使用した MCF544xx 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-988">Building Modules for MCF544xx using GHS</span></span>

<span data-ttu-id="793fc-989">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-989">An example workspace is provided.</span></span> <span data-ttu-id="793fc-990">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-990">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-mcf544xx-using-ghs"></a><span data-ttu-id="793fc-991">GHS を使用した MCF544xx 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-991">Thread extension definition for MCF544xx using GHS</span></span>

```c
#define TX_THREAD_EXTENSION_2   int     Errno;                                  \
                                VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                ULONG   tx_thread_module_mmu_protection;        \
                                VOID *  tx_thread_module_dispatch_return;       \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;
```

#### <a name="building-module-manager-for-mcf544xx-using-ghs"></a><span data-ttu-id="793fc-992">GHS を使用した MCF544xx 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-992">Building Module Manager for MCF544xx using GHS</span></span>

<span data-ttu-id="793fc-993">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-993">An example workspace is provided.</span></span> <span data-ttu-id="793fc-994">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-994">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-mcf544xx-using-ghs"></a><span data-ttu-id="793fc-995">GHS を使用した MCF544xx 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-995">Attributes for external memory enable API for MCF544xx using GHS</span></span>

<span data-ttu-id="793fc-996">この機能は MCF544xx で有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="793fc-996">This feature not enabled on MCF544xx.</span></span>

## <a name="rx63-processor"></a><span data-ttu-id="793fc-997">RX63 プロセッサ</span><span class="sxs-lookup"><span data-stu-id="793fc-997">RX63 processor</span></span>

### <a name="rx63-using-iar"></a><span data-ttu-id="793fc-998">IAR を使用した RX63</span><span class="sxs-lookup"><span data-stu-id="793fc-998">RX63 using IAR</span></span>

#### <a name="module-preamble-for-rx63-using-iar"></a><span data-ttu-id="793fc-999">IAR を使用した RX63 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-999">Module preamble for RX63 using IAR</span></span>

```c
    /* Alignment of 4 (16-byte) */
    SECTION .text:CODE (4)

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN _demo_module_start

    /* Define common external references.  */
    EXTERN  __txm_module_thread_shell_entry
    EXTERN  __txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x5                                               // Module Major Version
    DC32      0x6                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    DC32      __txm_module_thread_shell_entry - $               // Module Shell Entry Point
    DC32      _demo_module_start - $                            // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      __txm_module_callback_request_thread_entry - $    // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8  
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END
```

#### <a name="module-properties-for-rx63-using-iar"></a><span data-ttu-id="793fc-1000">IAR を使用した RX63 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-1000">Module properties for RX63 using IAR</span></span>

| <span data-ttu-id="793fc-1001">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-1001">Bit</span></span> | <span data-ttu-id="793fc-1002">値</span><span class="sxs-lookup"><span data-stu-id="793fc-1002">Value</span></span> | <span data-ttu-id="793fc-1003">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-1003">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-1004">0</span><span class="sxs-lookup"><span data-stu-id="793fc-1004">0</span></span> | <span data-ttu-id="793fc-1005">0</span><span class="sxs-lookup"><span data-stu-id="793fc-1005">0</span></span><br /><span data-ttu-id="793fc-1006">1</span><span class="sxs-lookup"><span data-stu-id="793fc-1006">1</span></span> | <span data-ttu-id="793fc-1007">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-1007">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-1008">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-1008">User mode execution</span></span> |
| <span data-ttu-id="793fc-1009">1</span><span class="sxs-lookup"><span data-stu-id="793fc-1009">1</span></span> | <span data-ttu-id="793fc-1010">0</span><span class="sxs-lookup"><span data-stu-id="793fc-1010">0</span></span><br /><span data-ttu-id="793fc-1011">1</span><span class="sxs-lookup"><span data-stu-id="793fc-1011">1</span></span> | <span data-ttu-id="793fc-1012">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-1012">No MPU protection</span></span><br /><span data-ttu-id="793fc-1013">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-1013">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-1014">2</span><span class="sxs-lookup"><span data-stu-id="793fc-1014">2</span></span> | <span data-ttu-id="793fc-1015">0</span><span class="sxs-lookup"><span data-stu-id="793fc-1015">0</span></span><br /><span data-ttu-id="793fc-1016">1</span><span class="sxs-lookup"><span data-stu-id="793fc-1016">1</span></span> | <span data-ttu-id="793fc-1017">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-1017">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-1018">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-1018">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-1019">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-1019">[23-3]</span></span> | <span data-ttu-id="793fc-1020">0</span><span class="sxs-lookup"><span data-stu-id="793fc-1020">0</span></span> | <span data-ttu-id="793fc-1021">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-1021">Reserved</span></span>
| <span data-ttu-id="793fc-1022">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-1022">[31-24]</span></span> | <br /><span data-ttu-id="793fc-1023">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-1023">0x00</span></span><br /><span data-ttu-id="793fc-1024">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-1024">0x02</span></span> | <span data-ttu-id="793fc-1025">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-1025">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-1026">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-1026">IAR</span></span><br /><span data-ttu-id="793fc-1027">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-1027">GNU</span></span> |

#### <a name="module-linker-for-rx63-using-iar"></a><span data-ttu-id="793fc-1028">IAR を使用した RX63 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-1028">Module linker for RX63 using IAR</span></span>

```c
//-----------------------------------------------------------------------------
// ILINK command file template for the Renesas RX microcontroller R5F563NB
//-----------------------------------------------------------------------------
define exported symbol __link_file_version_4 = 1;

define memory mem with size = 4G;

// ID Code Protection
define exported symbol __ID_BYTES_1_4   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_5_8   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_9_12  = 0xFFFFFFFF;
define exported symbol __ID_BYTES_13_16 = 0xFFFFFFFF;

// Endian Select Register (MDE)
// Choose between Little endian=0xFFFFFFFF or Big endian=0xFFFFFFF8
define exported symbol __MDES           = 0xFFFFFFFF;

// Option Function Select Register 0 (OFS0)
define exported symbol __OFS0           = 0xFFFFFFFF;

// Option Function Select Register 1 (OFS1)
define exported symbol __OFS1           = 0xFFFFFFFF;

//define region ROM_region16 = mem:[from 0xFFFF8000 to 0xFFFFFFFF];
define region RAM_region16 = mem:[from 0x00010000 to 0x00017FFF];
//define region ROM_region24 = mem:[from 0xFFF00000 to 0xFFFFFFFF];
//define region RAM_region24 = mem:[from 0x00000004 to 0x0001FFFF];
define region ROM_region32 = mem:[from 0xFFF10400 to 0xFFFFFFFF];
//define region RAM_region32 = mem:[from 0x00000004 to 0x0001FFFF];
//define region DATA_FLASH_region = mem:[from 0x00100000 to 0x00107FFF];

initialize by copy { rw, ro section D, ro section D_1, ro section D_2 };
do not initialize  { section .*.noinit };

define block HEAP     with alignment = 4, size = _HEAP_SIZE { };
//define block USTACK   with alignment = 4, size = _USTACK_SIZE { };
//define block ISTACK   with alignment = 4, size = _ISTACK_SIZE { };

//define block STACKS with fixed order { block ISTACK,
//                                       block USTACK };

//place at address mem:0xFFFFFF80 { ro section .nmivec };
//"ROM16":place in ROM_region16        { ro section .code16*,
//                                       ro section .data16* };
//"RAM16":place in RAM_region16        { rw section .data16*,
//                                       rw section __DLIB_PERTHREAD };
//"ROM24":place in ROM_region24        { ro section .code24*,
//                                       ro section .data24* };
//"RAM24":place in RAM_region24        { rw section .data24* };
//"ROM32":place in ROM_region32        { ro };
//"RAM32":place in RAM_region32        { rw,
//                                       ro section D,
//                                       ro section D_1,
//                                       ro section D_2,
//                                       block HEAP,
//                                       block STACKS,
//                                       last section FREEMEM };

//"DATAFLASH":place in DATA_FLASH_region
//                                     { ro section .dataflash* };

define movable block ROPI with alignment = 4, fixed order, static base CB
{
  ro object txm_module_preamble_rx63n.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base SB
{
  rw section .sbdata*,
  rw section .sbrel*,
  rw section __DLIB_PERTHREAD,
  block HEAP
};

place in ROM_region32   { block ROPI };
place in RAM_region16   { block RWPI };
```

#### <a name="building-modules-for-rx63-using-iar"></a><span data-ttu-id="793fc-1029">IAR を使用した RX63 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-1029">Building Modules for RX63 using IAR</span></span>

<span data-ttu-id="793fc-1030">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-1030">An example workspace is provided.</span></span> <span data-ttu-id="793fc-1031">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-1031">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rxrx635n-using-iar"></a><span data-ttu-id="793fc-1032">IAR を使用した RXRX635N 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-1032">Thread extension definition for RXRX635N using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;       \
                                VOID    *tx_thread_module_entry_info_ptr;     \
                                ULONG   tx_thread_module_current_user_mode;   \
                                ULONG   tx_thread_module_user_mode;           \
                                VOID    *tx_thread_module_kernel_stack_start; \
                                VOID    *tx_thread_module_kernel_stack_end;   \
                                ULONG   tx_thread_module_kernel_stack_size;   \
                                VOID    *tx_thread_module_stack_ptr;          \
                                VOID    *tx_thread_module_stack_start;        \
                                VOID    *tx_thread_module_stack_end;          \
                                ULONG   tx_thread_module_stack_size;          \
                                VOID    *tx_thread_module_reserved;           \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-rx63-using-iar"></a><span data-ttu-id="793fc-1033">IAR を使用した RX63 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-1033">Building Module Manager for RX63 using IAR</span></span>

<span data-ttu-id="793fc-1034">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-1034">An example workspace is provided.</span></span> <span data-ttu-id="793fc-1035">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-1035">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx63-using-iar"></a><span data-ttu-id="793fc-1036">IAR を使用した RX63 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-1036">Attributes for external memory enable API for RX63 using IAR</span></span>

| <span data-ttu-id="793fc-1037">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-1037">Attribute Parameter</span></span> | <span data-ttu-id="793fc-1038">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-1038">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="793fc-1039">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="793fc-1040">コードを実行する</span><span class="sxs-lookup"><span data-stu-id="793fc-1040">Execute code</span></span> |
| <span data-ttu-id="793fc-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-1041">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-1042">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-1042">Write access</span></span> |
| <span data-ttu-id="793fc-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="793fc-1043">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="793fc-1044">読み取りアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-1044">Read access</span></span> |

## <a name="rx65n-processor"></a><span data-ttu-id="793fc-1045">RX65N プロセッサ</span><span class="sxs-lookup"><span data-stu-id="793fc-1045">RX65N processor</span></span>

### <a name="rx65n-using-iar"></a><span data-ttu-id="793fc-1046">IAR を使用した RX65N</span><span class="sxs-lookup"><span data-stu-id="793fc-1046">RX65N using IAR</span></span>

#### <a name="module-preamble-for-rx65n-using-iar"></a><span data-ttu-id="793fc-1047">IAR を使用した RX65N 用モジュール プリアンブル</span><span class="sxs-lookup"><span data-stu-id="793fc-1047">Module preamble for RX65N using IAR</span></span>

```c
    /* Alignment of 4 (16-byte) */
    SECTION .text:CODE (4)

    /* Define public symbols.  */
    PUBLIC __txm_module_preamble

    /* Define application-specific start/stop entry points for the module.  */
    EXTERN _demo_module_start

    /* Define common external references.  */
    EXTERN  __txm_module_thread_shell_entry
    EXTERN  __txm_module_callback_request_thread_entry
    EXTERN  ROPI$$Length
    EXTERN  RWPI$$Length

    DATA
__txm_module_preamble:
    DC32      0x4D4F4455                                        // Module ID
    DC32      0x5                                               // Module Major Version
    DC32      0x6                                               // Module Minor Version
    DC32      32                                                // Module Preamble Size in 32-bit words
    DC32      0x12345678                                        // Module ID (application defined)
    DC32      0x00000007                                        // Module Properties where:
                                                                //   Bits 31-24: Compiler ID
                                                                //           0 -> IAR
                                                                //           1 -> ARM
                                                                //           2 -> GNU
                                                                //   Bit 0:  0 -> Privileged mode execution
                                                                //           1 -> User mode execution
                                                                //   Bit 1:  0 -> No MPU protection
                                                                //           1 -> MPU protection (must have user mode selected)
                                                                //   Bit 2:  0 -> Disable shared/external memory access
                                                                //           1 -> Enable shared/external memory access
    DC32      __txm_module_thread_shell_entry - $               // Module Shell Entry Point
    DC32      _demo_module_start - $                            // Module Start Thread Entry Point
    DC32      0                                                 // Module Stop Thread Entry Point
    DC32      1                                                 // Module Start/Stop Thread Priority
    DC32      1024                                              // Module Start/Stop Thread Stack Size
    DC32      __txm_module_callback_request_thread_entry - $    // Module Callback Thread Entry
    DC32      1                                                 // Module Callback Thread Priority
    DC32      1024                                              // Module Callback Thread Stack Size
    DC32      ROPI$$Length                                      // Module Code Size
    DC32      RWPI$$Length                                      // Module Data Size
    DC32      0                                                 // Reserved 0
    DC32      0                                                 // Reserved 1
    DC32      0                                                 // Reserved 2
    DC32      0                                                 // Reserved 3
    DC32      0                                                 // Reserved 4
    DC32      0                                                 // Reserved 5
    DC32      0                                                 // Reserved 6
    DC32      0                                                 // Reserved 7
    DC32      0                                                 // Reserved 8  
    DC32      0                                                 // Reserved 9
    DC32      0                                                 // Reserved 10
    DC32      0                                                 // Reserved 11
    DC32      0                                                 // Reserved 12
    DC32      0                                                 // Reserved 13
    DC32      0                                                 // Reserved 14
    DC32      0                                                 // Reserved 15

    END
```

#### <a name="module-properties-for-rx65n-using-iar"></a><span data-ttu-id="793fc-1048">IAR を使用した RX65N 用モジュール プロパティ</span><span class="sxs-lookup"><span data-stu-id="793fc-1048">Module properties for RX65N using IAR</span></span>

| <span data-ttu-id="793fc-1049">ビット</span><span class="sxs-lookup"><span data-stu-id="793fc-1049">Bit</span></span> | <span data-ttu-id="793fc-1050">値</span><span class="sxs-lookup"><span data-stu-id="793fc-1050">Value</span></span> | <span data-ttu-id="793fc-1051">意味</span><span class="sxs-lookup"><span data-stu-id="793fc-1051">Meaning</span></span> |
|---|---|---|
| <span data-ttu-id="793fc-1052">0</span><span class="sxs-lookup"><span data-stu-id="793fc-1052">0</span></span> | <span data-ttu-id="793fc-1053">0</span><span class="sxs-lookup"><span data-stu-id="793fc-1053">0</span></span><br /><span data-ttu-id="793fc-1054">1</span><span class="sxs-lookup"><span data-stu-id="793fc-1054">1</span></span> | <span data-ttu-id="793fc-1055">特権モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-1055">Privileged mode execution</span></span><br /><span data-ttu-id="793fc-1056">ユーザー モード実行</span><span class="sxs-lookup"><span data-stu-id="793fc-1056">User mode execution</span></span> |
| <span data-ttu-id="793fc-1057">1</span><span class="sxs-lookup"><span data-stu-id="793fc-1057">1</span></span> | <span data-ttu-id="793fc-1058">0</span><span class="sxs-lookup"><span data-stu-id="793fc-1058">0</span></span><br /><span data-ttu-id="793fc-1059">1</span><span class="sxs-lookup"><span data-stu-id="793fc-1059">1</span></span> | <span data-ttu-id="793fc-1060">MPU 保護なし</span><span class="sxs-lookup"><span data-stu-id="793fc-1060">No MPU protection</span></span><br /><span data-ttu-id="793fc-1061">MPU 保護 (ユーザー モードが選択されている必要があります)</span><span class="sxs-lookup"><span data-stu-id="793fc-1061">MPU protection (must have user mode selected)</span></span> |
| <span data-ttu-id="793fc-1062">2</span><span class="sxs-lookup"><span data-stu-id="793fc-1062">2</span></span> | <span data-ttu-id="793fc-1063">0</span><span class="sxs-lookup"><span data-stu-id="793fc-1063">0</span></span><br /><span data-ttu-id="793fc-1064">1</span><span class="sxs-lookup"><span data-stu-id="793fc-1064">1</span></span> | <span data-ttu-id="793fc-1065">共有/外部メモリ アクセスを無効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-1065">Disable shared/external memory access</span></span><br /><span data-ttu-id="793fc-1066">共有/外部メモリ アクセスを有効にする</span><span class="sxs-lookup"><span data-stu-id="793fc-1066">Enable shared/external memory access</span></span> |
| <span data-ttu-id="793fc-1067">[23-3]</span><span class="sxs-lookup"><span data-stu-id="793fc-1067">[23-3]</span></span> | <span data-ttu-id="793fc-1068">0</span><span class="sxs-lookup"><span data-stu-id="793fc-1068">0</span></span> | <span data-ttu-id="793fc-1069">予約されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-1069">Reserved</span></span>
| <span data-ttu-id="793fc-1070">[31-24]</span><span class="sxs-lookup"><span data-stu-id="793fc-1070">[31-24]</span></span> | <br /><span data-ttu-id="793fc-1071">0x00</span><span class="sxs-lookup"><span data-stu-id="793fc-1071">0x00</span></span><br /><span data-ttu-id="793fc-1072">0x02</span><span class="sxs-lookup"><span data-stu-id="793fc-1072">0x02</span></span> | <span data-ttu-id="793fc-1073">**コンパイラ ID**</span><span class="sxs-lookup"><span data-stu-id="793fc-1073">**Compiler ID**</span></span><br /><span data-ttu-id="793fc-1074">IAR</span><span class="sxs-lookup"><span data-stu-id="793fc-1074">IAR</span></span><br /><span data-ttu-id="793fc-1075">GNU</span><span class="sxs-lookup"><span data-stu-id="793fc-1075">GNU</span></span> |

#### <a name="module-linker-for-rx65n-using-iar"></a><span data-ttu-id="793fc-1076">IAR を使用した RX65N 用モジュール リンカー</span><span class="sxs-lookup"><span data-stu-id="793fc-1076">Module linker for RX65N using IAR</span></span>

```c
//-----------------------------------------------------------------------------
// ILINK command file template for the Renesas RX microcontroller R5F565N
//-----------------------------------------------------------------------------
define exported symbol __link_file_version_4 = 1;

define memory mem with size = 4G;

// ID Code Protection
define exported symbol __ID_BYTES_1_4   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_5_8   = 0xFFFFFFFF;
define exported symbol __ID_BYTES_9_12  = 0xFFFFFFFF;
define exported symbol __ID_BYTES_13_16 = 0xFFFFFFFF;

// Endian Select Register (MDE)
// Choose between Little endian=0xFFFFFFFF or Big endian=0xFFFFFFF8
define exported symbol __MDES           = 0xFFFFFFFF;

// Option Function Select Register 0 (OFS0)
define exported symbol __OFS0           = 0xFFFFFFFF;

// Option Function Select Register 1 (OFS1)
define exported symbol __OFS1           = 0xFFFFFFFF;

//define region ROM_region16 = mem:[from 0xFFFF8000 to 0xFFFFFFFF];
define region RAM_region16 = mem:[from 0x00010000 to 0x00017FFF];
//define region ROM_region24 = mem:[from 0xFFF00000 to 0xFFFFFFFF];
//define region RAM_region24 = mem:[from 0x00000004 to 0x0001FFFF];
define region ROM_region32 = mem:[from 0xFFF10400 to 0xFFFFFFFF];
//define region RAM_region32 = mem:[from 0x00000004 to 0x0001FFFF];
//define region DATA_FLASH_region = mem:[from 0x00100000 to 0x00107FFF];

initialize by copy { rw, ro section D, ro section D_1, ro section D_2 };
do not initialize  { section .*.noinit };

define block HEAP     with alignment = 4, size = _HEAP_SIZE { };
//define block USTACK   with alignment = 4, size = _USTACK_SIZE { };
//define block ISTACK   with alignment = 4, size = _ISTACK_SIZE { };

//define block STACKS with fixed order { block ISTACK,
//                                       block USTACK };

//place at address mem:0xFFFFFF80 { ro section .nmivec };
//"ROM16":place in ROM_region16        { ro section .code16*,
//                                       ro section .data16* };
//"RAM16":place in RAM_region16        { rw section .data16*,
//                                       rw section __DLIB_PERTHREAD };
//"ROM24":place in ROM_region24        { ro section .code24*,
//                                       ro section .data24* };
//"RAM24":place in RAM_region24        { rw section .data24* };
//"ROM32":place in ROM_region32        { ro };
//"RAM32":place in RAM_region32        { rw,
//                                       ro section D,
//                                       ro section D_1,
//                                       ro section D_2,
//                                       block HEAP,
//                                       block STACKS,
//                                       last section FREEMEM };

//"DATAFLASH":place in DATA_FLASH_region
//                                     { ro section .dataflash* };

define movable block ROPI with alignment = 4, fixed order, static base CB
{
  ro object txm_module_preamble_rx65n.o,
  ro,
  ro data
};

define movable block RWPI with alignment = 8, fixed order, static base SB
{
  rw section .sbdata*,
  rw section .sbrel*,
  rw section __DLIB_PERTHREAD,
  block HEAP
};

place in ROM_region32   { block ROPI };
place in RAM_region16   { block RWPI };
```

#### <a name="building-modules-for-rx65n-using-iar"></a><span data-ttu-id="793fc-1077">IAR を使用した RX65N 用モジュールのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-1077">Building Modules for RX65N using IAR</span></span>

<span data-ttu-id="793fc-1078">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-1078">An example workspace is provided.</span></span> <span data-ttu-id="793fc-1079">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-1079">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="thread-extension-definition-for-rx65n-using-iar"></a><span data-ttu-id="793fc-1080">IAR を使用した RX65N 用スレッド拡張機能の定義</span><span class="sxs-lookup"><span data-stu-id="793fc-1080">Thread extension definition for RX65N using IAR</span></span>

```c
#define TX_THREAD_EXTENSION_2   VOID    *tx_thread_module_instance_ptr;         \
                                VOID    *tx_thread_module_entry_info_ptr;       \
                                ULONG   tx_thread_module_current_user_mode;     \
                                ULONG   tx_thread_module_user_mode;             \
                                VOID    *tx_thread_module_kernel_stack_start;   \
                                VOID    *tx_thread_module_kernel_stack_end;     \
                                ULONG   tx_thread_module_kernel_stack_size;     \
                                VOID    *tx_thread_module_stack_ptr;            \
                                VOID    *tx_thread_module_stack_start;          \
                                VOID    *tx_thread_module_stack_end;            \
                                ULONG   tx_thread_module_stack_size;            \
                                VOID    *tx_thread_module_reserved;             \
                                VOID    *tx_thread_iar_tls_pointer;
```

#### <a name="building-module-manager-for-rx65n-using-iar"></a><span data-ttu-id="793fc-1081">IAR を使用した RX65N 用モジュール マネージャーのビルド</span><span class="sxs-lookup"><span data-stu-id="793fc-1081">Building Module Manager for RX65N using IAR</span></span>

<span data-ttu-id="793fc-1082">ワークスペースの例が提供されています。</span><span class="sxs-lookup"><span data-stu-id="793fc-1082">An example workspace is provided.</span></span> <span data-ttu-id="793fc-1083">ThreadX ライブラリ、ThreadX モジュール ライブラリ、デモ モジュール プロジェクト、およびデモ モジュール マネージャー プロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="793fc-1083">Build the ThreadX library, ThreadX Modules library, demo module project, and demo module manager project.</span></span>

#### <a name="attributes-for-external-memory-enable-api-for-rx65n-using-iar"></a><span data-ttu-id="793fc-1084">IAR を使用した RX65N 用外部メモリ有効化 API の属性</span><span class="sxs-lookup"><span data-stu-id="793fc-1084">Attributes for external memory enable API for RX65N using IAR</span></span>

| <span data-ttu-id="793fc-1085">属性パラメーター</span><span class="sxs-lookup"><span data-stu-id="793fc-1085">Attribute Parameter</span></span> | <span data-ttu-id="793fc-1086">説明</span><span class="sxs-lookup"><span data-stu-id="793fc-1086">Meaning</span></span> |
|---|---|
| <span data-ttu-id="793fc-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span><span class="sxs-lookup"><span data-stu-id="793fc-1087">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_EXECUTE</span></span> | <span data-ttu-id="793fc-1088">コードを実行する</span><span class="sxs-lookup"><span data-stu-id="793fc-1088">Execute code</span></span> |
| <span data-ttu-id="793fc-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span><span class="sxs-lookup"><span data-stu-id="793fc-1089">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_WRITE</span></span> | <span data-ttu-id="793fc-1090">書き込みアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-1090">Write access</span></span> |
| <span data-ttu-id="793fc-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span><span class="sxs-lookup"><span data-stu-id="793fc-1091">TXM_MODULE_MANAGER_SHARED_ATTRIBUTE_READ</span></span> | <span data-ttu-id="793fc-1092">読み取りアクセス</span><span class="sxs-lookup"><span data-stu-id="793fc-1092">Read access</span></span> |
