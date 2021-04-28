---
title: 第 10 章 - 顧客ユーザー イベント
description: この章では、ユーザー定義イベント、およびそのようなイベントのカスタム アイコンと情報フィールドを作成する方法について説明します。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 635c2d79922de9d5649bab841ae946cac862056c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812422"
---
# <a name="chapter-10---customer-user-events"></a>第 10 章 - 顧客ユーザー イベント

この章では、ユーザー定義イベント、およびそのようなイベントのカスタム アイコンと情報フィールドを作成する方法について説明します。 この章は以下のセクションで構成されています。 

## <a name="inserting-user-defined-events"></a>ユーザー定義イベントの挿入

ThreadX では、開発者が独自のユーザー定義イベントをログに記録できるので、さらに有用な情報を提供して TraceX でグラフィカルに表示できます。 ユーザー定義イベント番号の範囲は、

**TX_TRACE_USER_EVENT_START** (4096) から **TX_TRACE_USER_EVENT_END** (65535) までです。 トレース バッファーにイベントを配置するには、第 5 章で定義されている ***tx_trace_user_event_insert*** を使用します。 次の呼び出し例では、2 つのユーザー定義イベント (イベント 4096 とイベント 4098) をターゲットの現在のトレース バッファーに挿入します。

```c
tx_trace_user_event_insert(4096, 1, 2, 3, 4);
tx_trace_user_event_insert(4098,0x100,0x200,0x300,0x400);
```

## <a name="default-display-of-user-defined-events"></a>ユーザー定義イベントの既定の表示

![ユーザー定義イベント アイコン](./media/user-guide/tx-events/image0.png)

既定では、TraceX には、第 6 章で説明した既定のユーザー定義イベント アイコンを使用して、すべてのユーザー イベントが表示されます。 図 28 は、前の ***tx_trace_user_event_insert*** の例でイベント バッファーに配置された、イベント 452 と 453 の既定のユーザー定義イベント アイコンを示しています。

![ユーザー定義イベントの既定の表示のスクリーンショット。](./media/user-guide/10.1.png)
**図 28**

さらに、ユーザー定義イベントの詳細情報も提供されます。 図 29 では、イベント番号が 4096 のイベント 452 の詳細なイベント情報が表示されています。そこには、指定された 4 つの情報フィールドが示されています。

![ユーザー定義イベントの詳細表示のスクリーンショット。](./media/user-guide/10.2.png)
**図 29**

## <a name="defining-custom-user-defined-event-icons"></a>ユーザー定義イベントのカスタム アイコンの定義

TraceX では、ユーザー定義イベントのカスタム アイコンとカスタム情報フィールド ラベルを作成することもできます。 この機能を実現するには、***tracex_custom trxc** _ 構成ファイルにイベント アイコンの仕様を追加します。 このファイルは、ユーザー定義の TraceX インストール ディレクトリ (既定では c:\Azure_RTOS\TraceX) の _ *_CustomEvents_** サブディレクトリにあります。 ディレクトリ パスの例を図 30 に示します。

![ディレクトリ パスの例のスクリーンショット。](./media/user-guide/custom_events_folder.png)
**図 30**

***tracex_custom.trxc*** カスタム イベント構成ファイルは、0 個以上のカスタム イベント定義を含む単純な ASCII テキスト ファイルです。 ファイルの形式を次に示します。

```c
//Comments
**Start **
[custom event definition(s)] **End **
```

Start と End の間の行を使用して、カスタム イベントを定義します (1 行につき 1 つ)。 TraceX には、カスタム イベントが定義されていない ("Start" ラベルと "End" ラベルの間に何もない)、このファイルのテンプレート バージョンが用意されています。 カスタム イベント定義の形式は次のとおりです。

**number, name, abbreviation, top_color, bottom_color, label1, label2, label2, label4**

各値の説明:

- number: ユーザー定義イベント番号 (4096 から 65535) を定義します。</th>
- name: ユーザー定義イベントの論理名を定義します。</td>
- abbreviation: ユーザー定義イベントの略称 (2 文字) を定義します。</td>
- top_color: アイコンの上半分の RGB 値 (かっこ内の 3 桁の数値) を定義します。 一般的な RGB 定義は次のとおりです。
  - 黒 = (0,0,0)       
  - 白 = (255,255,255)
  - 赤 = (255,0,0)     
  - 緑 = (0,255,0)     
  - 青 = (0,0,255)     
  - 黄 = (255,255,0)   
  - シアン = (0,255,255)   
  - マゼンタ = (255,0,255)   
  RGB 仕様を使用すると、ユーザーは各ユーザー定義アイコンにさまざまな色を指定できます。 RGB カラー定義の詳細については、 https://en.wikipedia.org/wiki/RGB#Digital_representations をご覧ください。
- botton_color: アイコンの下半分の RGB 値 (かっこ内の 3 桁の数値) を定義します。
- label1: _ *_tx_trace_user_event_insert_** 呼び出しで指定された ***info_field_1** _ のラベル。
- label2: _ *_tx_trace_user_event_insert_** 呼び出しで指定された ***info_field_2** _ のラベル。
- label3: _ *_tx_trace_user_event_insert_** 呼び出しで指定された ***info_field_3** _ のラベル。
- label4: _ *_tx_trace_user_event_insert_** 呼び出しで指定された ***info_field_4** _ のラベル。

この章で使用する 2 つのユーザー定義イベントの定義例を図 31 に示します。 まず、***tracex_custom. trxc** _ ファイルの 5 行目でイベント 4096 が定義されています。 この定義では、ユーザー定義イベント 4096 に _*First_User_Event** という名前が付けられ、2 文字の略称として **FE** が指定されています。また、アイコンの上部に赤、下部に緑が指定され、情報フィールドに **First_Info1**、**First_Info2**、**First_Info3**、**First_Info4** という名前が付けられています。 ユーザー定義イベント 4098 も、**_tracex_custom.trxc_** の 6 行目で同様に定義されています。

![ユーザー定義イベントの定義例のスクリーンショット。](./media/user-guide/10.4.png)
**図 31**

***tracex_custom.trxc** _ ファイルは初期化中に TraceX によって読み取られるため、カスタム アイコンの定義を有効にするには、TraceX を終了して再起動する必要があります。 図 32 では、_*_tracex_custom. trxc_** で定義されているカスタム イベント アイコンを使用して、ユーザー定義イベント 452 と 453 が TraceX に表示されています。

![カスタム イベント アイコンを使用したユーザー定義イベントの TraceX での表示のスクリーンショット。](./media/user-guide/10.5.png)
**図 32**

ダブルクリックまたはマウスでのポイントによってイベントを選択するか、現在のイベントのボタンをクリックすると、カスタム イベント定義の追加情報が表示されます。 図 33 は、イベント 452 をダブルクリックで選択した状態を示しています。 イベント名と情報フィールドは、***tracex_custom trxc*** に追加された定義例とすべて一致しています。

![イベントをダブルクリックで選択した状態を示すスクリーンショット。](./media/user-guide/10.6.png)
**図 33**
