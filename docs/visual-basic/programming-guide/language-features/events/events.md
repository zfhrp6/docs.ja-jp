---
title: "Events (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "events [Visual Basic], about events"
  - "events [Visual Basic]"
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Events (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

一連のプロシージャが順番に実行されるのが [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] プロジェクトであると思っているかもしれませんが、実際には、ほとんどのプログラムはイベントによって駆動されています。つまり、実行の流れを決定するのは、*イベント*と呼ばれる外部の事象です。  
  
 イベントは重要な出来事が発生したことをアプリケーションに伝えるシグナルです。  たとえば、ユーザーがフォームのコントロールをクリックすると、フォームは `Click` イベントを発生させてイベントを処理するプロシージャを呼び出すことができます。  イベントは、個別のタスクの通信も確立できます。  たとえば、アプリケーションが、並べ替えタスクをメイン アプリケーションとは別に実行するとします。  ユーザーが並べ替えを取り消した場合、アプリケーションは並べ替えプロセスに停止を指示するキャンセル イベントを送信できます。  
  
## イベントの用語と概念  
 ここでは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] のイベントに関連して使用される用語と概念について説明します。  
  
### イベントの宣言  
 次の例に示すように、イベントはクラス、構造体、モジュール、およびインターフェイス内で `Event` キーワードを使用して宣言します。  
  
 [!code-vb[VbVbalrEvents#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_1.vb)]  
  
### イベントの発生  
 イベントは、重要な出来事が発生したことを通知するメッセージと同じです。  メッセージのブロードキャストの動作は、イベントの*発生*と呼ばれます。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] では、次の例に示すように `RaiseEvent` ステートメントを使用してイベントを発生させます。  
  
 [!code-vb[VbVbalrEvents#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_2.vb)]  
  
 イベントが発生する範囲は、イベントを宣言したクラス、モジュール、または構造体の内部に限られます。  たとえば、派生クラスで基本クラスから継承したイベントを発生させることはできません。  
  
### イベント センダー  
 イベントを発生させる機能を持つオブジェクトが*イベント センダー*です。*イベント ソース*とも呼ばれます。  フォーム、コントロール、およびユーザー定義オブジェクトは、イベント センダーの例です。  
  
### イベント ハンドラー  
 *イベント ハンドラー*は、対応するイベントが発生したときに呼び出されるプロシージャです。  シグネチャの一致する任意の有効なサブルーチンをイベント ハンドラーとして使用できます。  ただし、イベント ハンドラーはイベント ソースに値を返すことができないため、関数をイベント ハンドラーとして使用することはできません。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は、イベント ハンドラーに対して、イベント送信元の名前、アンダースコア、およびイベント名を組み合わせた標準名前付け規則を使用します。  たとえば、`button1` という名前のボタンの `Click` イベントは `Sub button1_Click` という名前になります。  
  
> [!NOTE]
>  独自のイベントのイベント ハンドラーを定義する場合は、この名前付け規則を使用することをお勧めしますが、名前付け規則の使用は必須ではありません。任意の有効なサブルーチン名を使用できます。  
  
## イベントとイベント ハンドラーの関連付け  
 イベント ハンドラーを使用できるようにするには、`Handles` ステートメントまたは `AddHandler` ステートメントを使用してイベント ハンドラーをイベントに関連付ける必要があります。  
  
### WithEvents と Handles 句  
 `WithEvents` ステートメントと `Handles` 句を使用すると、イベント ハンドラーの指定を宣言できます。  `WithEvents` キーワードで宣言されたオブジェクトが発生させたイベントは、次の例に示すように、そのイベントの `Handles` ステートメントを持つ任意のプロシージャで処理できます。  
  
 [!code-vb[VbVbalrEvents#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_3.vb)]  
  
 多くの場合、イベント ハンドラーに最も適しているのは `WithEvents` ステートメントと `Handles` 句です。これは、それらが使用する宣言構文によってイベント処理のコーディング、読み取り、およびデバッグが簡単になるためです。  ただし、`WithEvents` 変数の使用には以下の制限があります。  
  
-   `WithEvents` 変数を、オブジェクト変数として使用することはできません。  つまり、この変数をオブジェクト型 \(`Object`\) として宣言することはできません。変数を宣言するときは、クラス名を指定する必要があります。  
  
-   共有イベントはクラスのインスタンスに関連付けられないため、`WithEvents` ``  を使用して、共有イベントを宣言によって処理することはできません。  同様に、`WithEvents` または `Handles` を使用して、イベントを `Structure` から処理することもできません。  どちらの場合にも、`AddHandler` ステートメントを使ってそれらのイベントを処理するようにしてください。  
  
-   `WithEvents` 変数の配列は作成できません。  
  
 `WithEvents` 変数では、1 つのイベント ハンドラーが 1 つ以上の種類のイベント、または 1 つ以上のイベント ハンドラーが同じ種類のイベントを処理することも可能です。  
  
 `Handles` 句はイベントをイベント ハンドラーに関連付ける標準的な方法ですが、関連付けができるのはコンパイル時だけです。  
  
 フォームやコントロールに関連付けられているイベントの場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] が空のイベント ハンドラーを自動的にスタブとして作成し、それをイベントに関連付けることがあります。  たとえば、デザイン モードでフォームのコマンド ボタンをダブルクリックすると、次のコードに示すように、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] はコマンド ボタンに対して空のイベント ハンドラーと `WithEvents` 変数を作成します。  
  
 [!code-vb[VbVbalrEvents#26](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_4.vb)]  
  
### AddHandler と RemoveHandler  
 `AddHandler` ステートメントは、イベント ハンドラーを指定できるという点で `Handles` 句と似ています。  ただし、`AddHandler` を `RemoveHandler` と一緒に使用すると、`Handles` 句よりも柔軟性が増し、イベントに関連付けられたイベント ハンドラーを動的に追加、削除、変更できます。  共有イベントまたは構造体からのイベントを処理する場合は、`AddHandler` を使用する必要があります。  
  
 `AddHandler` は 2 つの引数 \(コントロールなどのイベント センダーから渡されるイベント名およびデリゲートを評価する式\) を使用します。  `AddressOf` ステートメントは常にデリゲートへの参照を返すため、`AddHandler` を使用する場合はデリゲート クラスを明示的に指定する必要がありません。  オブジェクトが発生させたイベントにイベント ハンドラーを関連付ける方法を次の例に示します。  
  
 [!code-vb[VbVbalrEvents#28](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_5.vb)]  
  
 イベント ハンドラーとイベントの接続を解除する `RemoveHandler` では、`AddHandler` と同じ構文を使用します。  次に例を示します。  
  
 [!code-vb[VbVbalrEvents#29](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_6.vb)]  
  
 次の例では、イベントにイベント ハンドラーが関連付けられた状態でイベントが発生しています。  このイベント ハンドラーによりイベントがキャッチされ、メッセージが表示されます。  
  
 その後、最初のイベント ハンドラーが削除され、イベントに別のイベント ハンドラーが関連付けられています。  もう一度イベントが発生すると、別のメッセージが表示されます。  
  
 最後に、2 つ目のイベント ハンドラーが削除され、3 回目のイベントが発生しています。  イベントにはもうイベント ハンドラーが関連付けられていないので、処理は実行されません。  
  
 [!code-vb[VbVbalrEvents#38](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_7.vb)]  
  
## 基本クラスから継承されたイベントの処理  
 *派生クラス*は基本クラスから特性を継承したクラスであり、`Handles` `MyBase` ステートメントを使用して基本クラスが発生させたイベントを処理できます。  
  
#### 基本クラスから継承されたイベントを処理するには  
  
-   イベント ハンドラー プロシージャの宣言の行に `Handles MyBase.`*eventname* ステートメントを追加して、派生クラスにイベント ハンドラーを宣言します。*eventname* は処理する基本クラスのイベント名です。  次に例を示します。  
  
     [!code-vb[VbVbalrEvents#12](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/events_8.vb)]  
  
## 関連項目  
  
|Title|Description|  
|-----------|-----------------|  
|[Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|クラスのイベントを宣言して発生させる方法を操作手順に従って説明します。|  
|[Walkthrough: Handling Events](../Topic/Walkthrough:%20Handling%20Events%20\(Visual%20Basic\).md)|イベント ハンドラー プロシージャの記述方法を示します。|  
|[How to: Declare Custom Events To Avoid Blocking](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|イベント ハンドラーを非同期に呼び出すことができるカスタム イベントの定義方法を示します。|  
|[How to: Declare Custom Events To Conserve Memory](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|イベントを処理するときにだけメモリを消費するカスタム イベントの定義方法を示します。|  
|[Troubleshooting Inherited Event Handlers in Visual Basic](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|継承コンポーネントのイベント ハンドラーで発生する一般的な問題について説明します。|  
|[イベント](../Topic/Handling%20and%20Raising%20Events.md)|[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] のイベント モデルについて概説します。|  
|[Windows フォーム内でのイベント ハンドラーの作成](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)|Windows フォーム オブジェクトに関連付けられているイベントの処理方法について説明します。|  
|[Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)|Visual Basic のデリゲートの概要について説明します。|