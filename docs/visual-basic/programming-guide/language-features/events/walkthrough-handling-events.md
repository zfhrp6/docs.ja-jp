---
title: "Walkthrough: Handling Events (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "event handling [Visual Basic], walkthroughs"
  - "walkthroughs [Visual Basic], event handling"
  - "variables [Visual Basic], WithEvents"
  - "events [Visual Basic], walkthroughs"
  - "WithEvents keyword, walkthroughs"
  - "event handlers [Visual Basic], walkthroughs"
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Walkthrough: Handling Events (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このトピックは、イベントの処理方法を示す 2 番目のトピックです。  最初のトピック「[チュートリアル: イベントの宣言と発生](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)」では、イベントの宣言方法と発生方法について説明しました。  ここでは、最初のトピックのチュートリアルのフォームとクラスを使用して、発生したイベントを処理する方法を示します。  
  
 `Widget` クラスの例では、従来のイベント処理ステートメントを使用します。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、これ以外のイベント処理方法も用意されています。  この例を変更して `AddHandler` ステートメントと `Handles` ステートメントを使用することもできます。  
  
### Widget クラスの PercentDone イベントを処理するには  
  
1.  `Form1` に次のコードを記述します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Form1.vb#4)]  
  
     `WithEvents` キーワードは、変数 `mWidget` がオブジェクトのイベントを処理するために使用されることを指定します。  オブジェクトの作成元のクラス名を指定して、オブジェクトの種類を指定します。  
  
     `mWidget` 変数は `Form1` 内で宣言します。`WithEvents` の変数はクラス レベルにする必要があるからです。  別のクラスの場合も同様です。  
  
     変数 `mblnCancel` は、`LongTask` メソッドをキャンセルするために使用されます。  
  
## イベントを処理するコードの記述  
 `WithEvents` を使用して変数を宣言すると、クラスの**コード エディター**の左側のドロップダウン リストに変数名が表示されます。  `mWidget` を選択すると、右側のドロップダウン リストに `Widget` クラスのイベントが表示されます。  イベントを選択すると、対応するイベント プロシージャが表示されます。イベント プロシージャの名前は、先頭に `mWidget` およびアンダースコアが付きます。  `WithEvents` 変数に関連付けられたイベント プロシージャの名前は、すべて先頭に変数名が付きます。  
  
#### イベントを処理するには  
  
1.  **コード エディター**で、左側のドロップダウン リストの `mWidget` をクリックします。  
  
2.  右側のドロップダウン リストの `PercentDone` イベントをクリックします。  **コード エディター**内に `mWidget_PercentDone` イベント プロシージャが表示されます。  
  
    > [!NOTE]
    >  新しいイベント ハンドラーを挿入するときには**コード エディター**を使用すると便利ですが、必須ではありません。  このチュートリアルでは、イベント ハンドラーをコード内に直接コピーした方が簡単です。  
  
3.  `mWidget_PercentDone` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Form1.vb#5)]  
  
     `PercentDone` イベントが発生するたびに、イベント プロシージャは完了したパーセントを `Label` コントロールに表示します。  `DoEvents` メソッドにより、ラベルが再描画され、ユーザーに **\[キャンセル\]** をクリックする機会が与えられます。  
  
4.  `Button2_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Form1.vb#6)]  
  
 `LongTask` の実行中にユーザーが **\[キャンセル\]** をクリックした場合は、`DoEvents` ステートメントによってイベント処理が許可されるとすぐに、`Button2_Click` イベントが実行されます。  クラス レベル変数 `mblnCancel` が `True` に設定され、`mWidget_PercentDone` イベントがこれをテストして、`ByRef Cancel` 引数を `True` に設定します。  
  
## WithEvents 変数のオブジェクトへの接続  
 `Form1` は、`Widget` オブジェクトのイベントを処理するように設定されます。  後は、`Widget` を見つけるだけです。  
  
 デザイン時に変数 `WithEvents` を宣言するときは、どのオブジェクトも関連付けられていません。  `WithEvents` 変数は、他のオブジェクト変数と同じです。  オブジェクトを作成し、`WithEvents` 変数を使用してオブジェクトへの参照を代入する必要があります。  
  
#### オブジェクトを作成し、オブジェクトへの参照を代入するには  
  
1.  **コード エディター**で、左側のドロップダウン リストの **\[\(Form1 イベント\)\]** をクリックします。  
  
2.  右側のドロップダウン リストの `Load` イベントをクリックします。  **コード エディター**内に `Form1_Load` イベント プロシージャが表示されます。  
  
3.  `Form1_Load` イベント プロシージャに次のコードを追加して、`Widget` を作成します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Form1.vb#7)]  
  
 このコードが実行されると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] は `Widget` オブジェクトを作成し、そのイベントを `mWidget` に関連付けられたイベント プロシージャに接続します。  これ以後、`Widget` が `PercentDone` イベントを発生させるたびに、`mWidget_PercentDone` イベント プロシージャが実行されます。  
  
#### **LongTask** メソッドを呼び出すには  
  
-   `Button1_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Form1.vb#8)]  
  
 `LongTask` メソッドを呼び出す前に、完了したパーセントを表示するラベルを初期化する必要があります。また、メソッドをキャンセルするためのクラス レベルの `Boolean` フラグを `False` に設定する必要があります。  
  
 `LongTask` は、12.2 秒のタスク存続期間で呼び出されます。  `PercentDone` イベントは、1\/3 秒ごとに発生します。  イベントが発生するたびに、`mWidget_PercentDone` イベント プロシージャが実行されます。  
  
 `LongTask` の実行が完了すると `mblnCancel` がテストされ、`LongTask` が正常に終了したかどうか、または `mblnCancel` が `True` に設定されたために実行が停止したかどうかが確認されます。  完了したパーセントは、正常に終了したかどうかを確認する場合にだけ更新されます。  
  
#### プログラムを実行するには  
  
1.  **F5** キーを押してプロジェクトを実行モードにします。  
  
2.  **\[タスクの開始\]** をクリックします。  `PercentDone` イベントが発生するたびに、タスクの完了したパーセント値でラベルが更新されます。  
  
3.  **\[キャンセル\]** をクリックして、タスクを停止します。  **\[キャンセル\]** ボタンの外観は、クリックしてもすぐには変化しません。  `My.Application.DoEvents` ステートメントによってイベント処理が許可されるまで、`Click` イベントは発生しません。  
  
    > [!NOTE]
    >  `My.Application.DoEvents` メソッドは、フォームとまったく同じ方法でイベントを処理するわけではありません。  たとえばこのチュートリアルでは、**\[キャンセル\]** を 2 回クリックする必要があります。  フォームがイベントを直接処理するようにするには、マルチスレッドを使用します。  詳細については、「[スレッド](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 プログラムを実行するときに、**F11** キーを押してコードを 1 行ずつ処理すると便利な場合があります。  実行が `LongTask` に移り、`PercentDone` イベントが発生するたびに一時的に実行が `Form1` に移るようすを明確に確認できます。  
  
 実行が `Form1` のコードに戻っているときに、`LongTask` メソッドが再び呼び出された場合、どうなるか考えてください。  最悪の場合、イベントが発生するたびに `LongTask` が呼び出されると、スタック オーバーフローが発生します。  
  
 新しい `Widget` への参照を `mWidget` 変数に代入すると、この `mWidget` 変数に異なる `Widget` オブジェクトのイベントを処理させることができます。  実際、ボタンをクリックするたびに `Button1_Click` のコードを実行させることができます。  
  
#### 異なる Widget のイベントを処理するには  
  
-   `Button1_Click` プロシージャの `mWidget.LongTask(12.2, 0.33)` という行の直前に、次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/visualbasic/VbEventWalkthrough/Form1.vb#9)]  
  
 上記のコードは、ボタンがクリックされるごとに新しい `Widget` を作成します。  `LongTask` メソッドが完了すると、すぐに `Widget` への参照が解放され、`Widget` は破棄されます。  
  
 `WithEvents` 変数には、一度に 1 つのオブジェクト参照しか保持できません。したがって、`mWidget` に別の `Widget` オブジェクトを代入すると、前の `Widget` オブジェクトのイベントは処理されなくなります。  `mWidget` が、前の `Widget` への参照を含む唯一のオブジェクト変数である場合、オブジェクトは破棄されます。  複数の `Widget` オブジェクトからのイベントを処理する場合は、`AddHandler` ステートメントを使用して、各オブジェクトからのイベントを個別に処理します。  
  
> [!NOTE]
>  `WithEvents` 変数は必要な数だけ宣言できますが、`WithEvents` 変数の配列はサポートされません。  
  
## 参照  
 [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)