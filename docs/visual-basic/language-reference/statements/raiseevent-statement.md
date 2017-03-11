---
title: "RaiseEvent Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.RaiseEventMethod"
  - "vb.RaiseEvent"
  - "RaiseEvent"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "raising events, RaiseEvent statement"
  - "RaiseEvent statement"
  - "event handlers, connecting events to"
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# RaiseEvent Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

モジュール レベルで宣言されたイベントをクラス、フォーム、またはドキュメントで発生させます。  
  
## 構文  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## 指定項目  
 `eventname`  
 必ず指定します。  発生させるイベントの名前を指定します。  
  
 `argumentlist`  
 省略可能です。  変数、配列、または式をコンマで区切った一覧です。  `argumentlist` 引数は、かっこで囲む必要があります。  引数がない場合、かっこは省略できます。  
  
## 解説  
 `eventname` は必ず指定します。モジュール内で宣言されたイベント名です。  Visual Basic 変数の名前付け規則に従います。  
  
 イベントが発生したモジュールと宣言された場所が異なる場合は、エラーが発生します。  次のコードは、イベントの宣言と、そのイベントが発生するプロシージャの例を示しています。  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#37)]  
  
 モジュール内で明示的に宣言されていないイベントを `RaiseEvent` ステートメントで発生させることはできません。  たとえば、すべてのフォームは <xref:System.Windows.Forms.Form?displayProperty=fullName> から <xref:System.Windows.Forms.Control.Click> イベントを継承していますが、このイベントを派生フォーム内で `RaiseEvent` を使用して発生させることはできません。  フォーム モジュールで `Click` イベントを宣言する場合、このイベントは、フォーム独自の <xref:System.Windows.Forms.Control.Click> イベントをシャドウします。  <xref:System.Windows.Forms.Control.OnClick%2A> メソッドを呼び出して、フォームの <xref:System.Windows.Forms.Control.Click> イベントを呼び出すことができます。  
  
 既定では、Visual Basic 内に定義されているイベントは、それぞれのイベント ハンドラーを接続が確立された順序で発生させます。  イベントには `ByRef` パラメーターを設定できるので、後から接続したプロセスは、それ以前のイベント ハンドラーで変更されたパラメーターを受け取ることがあります。  イベント ハンドラーの実行が終わると、そのイベントを発生させたサブルーチンに制御が戻ります。  
  
> [!NOTE]
>  非共有イベントを宣言したクラスのコンストラクター内では、その非共有イベントを発生させないでください。  そのようなイベントがランタイム エラーを引き起こさない場合でも、それらのイベントが対応するイベント ハンドラーにキャッチされない場合があります。  コンストラクターからイベントを発生させる必要がある場合は、`Shared` 修飾子を使用して共有イベントを作成してください。  
  
> [!NOTE]
>  カスタム イベントを定義すると、イベントの既定の動作を変更できます。  カスタム イベントの場合は、`RaiseEvent` ステートメントはイベントの `RaiseEvent` アクセサーを呼び出します。  カスタム イベントの詳細については、「[Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)」を参照してください。  
  
## 使用例  
 次の例では、イベントを使用して 10 秒から 0 秒までカウントダウンします。  このコードは、イベント関連のいくつかのメソッド、プロパティ、およびステートメントの例を示しています。`RaiseEvent` ステートメントの使用例も含まれています。  
  
 イベントを発生させるクラスをイベント ソース、イベントを処理するメソッドをイベント ハンドラーと呼びます。  イベント ソースには、そこで生成される複数のイベント ハンドラーを設定できます。  クラスでイベントが発生すると、そのイベントは、オブジェクトのインスタンスに対するイベントを処理するために選択されたすべてのクラスで発生します。  
  
 また、この例では、ボタン \(`Button1`\) とテキスト ボックス \(`TextBox1`\) を含んだフォーム \(`Form1`\) を使用します。  ボタンをクリックすると、1 つ目のテキスト ボックスに 10 秒から 0 秒までのカウントダウンが表示されます。  カウントダウンが終わると \(10 秒が経過すると\)、1 つ目のテキスト ボックスに "Done" と表示されます。  
  
 `Form1` のコードでは、フォームの初期状態と終了状態を指定します。  イベント発生時に実行されるコードも含まれます。  
  
 この例を使用するには、新しい Windows アプリケーション プロジェクトを開き、メイン フォームに `Form1` という名前を付け、このフォームに `Button1` という名前のボタンと `TextBox1` という名前のテキスト ボックスを追加します。  続いてフォームを右クリックし、**\[コードの表示\]** をクリックして、コード エディターを開きます。  
  
 `Form1` クラスの宣言セクションに、`WithEvents` 変数を追加します。  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#14)]  
  
## 使用例  
 `Form1` のコードに以下のコードを追加します。  `Form_Load` や `Button_Click` など、重複して存在する可能性のあるプロシージャを置き換えます。  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#15)]  
  
 F5 キーを押して上記のコード例を実行し、**\[Start\]** というラベルのボタンをクリックしてください。  1 つ目のテキスト ボックスが秒のカウントダウンを開始します。  カウントダウンが終わると \(10 秒が経過すると\)、1 つ目のテキスト ボックスに "Done" と表示されます。  
  
> [!NOTE]
>  `My.Application.DoEvents` メソッドは、フォームとまったく同じ方法でイベントを処理するわけではありません。  フォームがイベントを直接処理するようにするには、マルチスレッドを使用します。  詳細については、「[スレッド](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## 参照  
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)   
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)