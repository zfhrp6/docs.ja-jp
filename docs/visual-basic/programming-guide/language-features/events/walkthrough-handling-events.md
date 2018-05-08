---
title: イベントの処理 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 0ac3514505ca42870d77317feec30a27e4384e6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-handling-events-visual-basic"></a>チュートリアル: イベントの処理 (Visual Basic)
これは、2 番目のイベントを使用する方法を示す 2 つのトピックです。 最初のトピックでは、[チュートリアル: イベントを宣言して発生](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)、宣言およびイベントを発生させる方法を示します。 このセクションでは、行われるときにイベントを処理するのに方法を示します。 フォームとそのチュートリアルからクラスを使用します。  
  
 `Widget`クラスの例は、従来のイベント処理のステートメントを使用します。 Visual Basic では、イベントの処理の他の手法を提供します。 演習として使用するには、この例を変更することができます、`AddHandler`と`Handles`ステートメントです。  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>ウィジェットのクラスのことですイベントを処理するには  
  
1.  次のコードを配置`Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     `WithEvents`キーワードを指定する変数`mWidget`オブジェクトのイベントを処理するために使用します。 オブジェクトの種類を指定するには、オブジェクトの作成元となるクラスの名前を指定します。  
  
     変数`mWidget`で宣言された`Form1`ため`WithEvents`変数はクラス レベルである必要があります。 これは、配置することでクラスの種類に関係なく当てはまります。  
  
     変数`mblnCancel`、キャンセルに使用、`LongTask`メソッドです。  
  
## <a name="writing-code-to-handle-an-event"></a>イベントを処理するコードの記述  
 使用して変数を宣言するとすぐに`WithEvents`、クラスの左のドロップダウン リストで、変数名が表示されます**コード エディター**です。 選択すると`mWidget`、`Widget`右のドロップダウン リストにクラスのイベントが表示されます。 イベントの対応するプロシージャのプレフィックスを持つイベントを選択すると表示`mWidget`とアンダー スコア。 関連付けられているすべてのイベント プロシージャ、`WithEvents`変数は、プレフィックスとして変数名を指定します。  
  
#### <a name="to-handle-an-event"></a>イベントを処理するには  
  
1.  選択`mWidget`で、左側のドロップダウン リストから、**コード エディター**です。  
  
2.  選択、`PercentDone`右のドロップダウン リストからのイベントです。 **コード エディター**開きます、`mWidget_PercentDone`イベント プロシージャです。  
  
    > [!NOTE]
    >  **コード エディター**は役立ちますが、必須ではない新しいイベント ハンドラーを挿入するためです。 このチュートリアルでは、イベント ハンドラーのコードに直接コピーするより直接的です。  
  
3.  `mWidget_PercentDone` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     ときに、`PercentDone`イベントは、イベントの手順で完了したパーセントが表示されます、`Label`コントロール。 `DoEvents`メソッドにより、再描画するラベルもにより、ユーザーをクリックして、**キャンセル**ボタンをクリックします。  
  
4.  次のコードを追加、`Button2_Click`イベントのハンドラー。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 ユーザーがクリックした場合、**キャンセル**中にボタン`LongTask`が実行されている、`Button2_Click`イベントが実行されるとすぐに、`DoEvents`ステートメントが発生するイベント処理を許可します。 クラス レベルの変数`mblnCancel`に設定されている`True`、および`mWidget_PercentDone`イベントことをテストし、設定、`ByRef Cancel`引数`True`です。  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>WithEvents 変数をオブジェクトに接続します。  
 `Form1` 処理するようになりました設定、`Widget`オブジェクトのイベントです。 すべてのタスクが見つかりません、`Widget`どこかにします。  
  
 変数を宣言するときに`WithEvents`デザイン時にオブジェクトが関連付けられていないこと。 A`WithEvents`変数は、その他のすべてのオブジェクト変数と同じようにします。 オブジェクトを作成しを使って参照を代入する必要がある、`WithEvents`変数。  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>オブジェクトを作成してへの参照を割り当てる  
  
1.  選択 **(Form1 イベント)** で、左側のドロップダウン リストから、**コード エディター**です。  
  
2.  選択、`Load`右のドロップダウン リストからのイベントです。 **コード エディター**開きます、`Form1_Load`イベント プロシージャです。  
  
3.  次のコードを追加、`Form1_Load`イベントを作成する手順、 `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 このコードが実行されると、Visual Basic の作成、`Widget`オブジェクトをイベント 'éú' に関連付けられているイベント プロシージャ`mWidget`です。 した時点で、ときに、`Widget`を発生させますその`PercentDone`イベント、`mWidget_PercentDone`イベント プロシージャを実行します。  
  
#### <a name="to-call-the-longtask-method"></a>LongTask メソッドを呼び出す  
  
-   `Button1_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 前に、`LongTask`メソッドを呼び出すことは、完了した割合が表示されますが初期化する必要があります、ラベルと、クラス レベル`Boolean`フラグに設定する必要があります、メソッドの取り消し`False`です。  
  
 `LongTask` タスクの継続時間 12.2 秒の呼び出されます。 `PercentDone`イベントは、1 回すべて 3 分の 1 秒です。 イベントが発生するたびに、`mWidget_PercentDone`イベント プロシージャを実行します。  
  
 ときに`LongTask`が完了したら、`mblnCancel`かどうかをテスト`LongTask`通常は、終了したためが停止している場合、または`mblnCancel`に設定された`True`です。 前者の場合にのみ、完了したパーセントが更新されます。  
  
#### <a name="to-run-the-program"></a>プログラムを実行するには  
  
1.  F5 キーを押してプロジェクトを実行モードにします。  
  
2.  クリックして、**タスクの開始**ボタンをクリックします。 毎回、`PercentDone`イベントは、ラベルは、タスクが完了の割合で更新します。  
  
3.  クリックして、**キャンセル**タスクを停止するボタンをクリックします。 注意しての外観、**キャンセル**ボタンをクリックすると、すぐには変化しません。 `Click`イベントまで発生することはできません、`My.Application.DoEvents`ステートメントにより、イベント処理します。  
  
    > [!NOTE]
    >  `My.Application.DoEvents`の形式として、メソッドがまったく同じ方法でイベントを処理できません。 たとえば、このチュートリアルでは、する必要があります をクリックして、**キャンセル**2 回ボタンをクリックします。 使用することができますを許可するフォームがイベントを直接処理する場合のマルチ スレッド化します。 詳細については、次を参照してください。[スレッド](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)です。  
  
 F11 キーをプログラムを実行して、コードを 1 行ずつ処理するときにあります。 実行に入力する方法がわかります`LongTask`、し、簡単に再入力`Form1`たびに、`PercentDone`イベントが発生します。  
  
 何が起こる場合、実行中のコードに戻ってに`Form1`、`LongTask`メソッドが再び呼び出されたしますか? 場合、スタック オーバーフローが発生する最悪の場合、`LongTask`イベントが発生するたびに呼び出されました。  
  
 変数が発生することができます`mWidget`別のイベントを処理する`Widget`新しいへの参照を割り当てることによってオブジェクト`Widget`に`mWidget`です。 実際には、内のコードを行うことができます`Button1_Click`ボタンをクリックするたびにこの操作を行います。  
  
#### <a name="to-handle-events-for-a-different-widget"></a>さまざまなウィジェットのイベントを処理するには  
  
-   次のコード行を追加、`Button1_Click`を読み取る行のすぐ前の手順`mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 上記のコードが新たに作成`Widget`たびにこのボタンをクリックします。 すぐに、`LongTask`メソッドが完了するへの参照を`Widget`がリリースされると、`Widget`は破棄されます。  
  
 A`WithEvents`変数は、一度に 1 つのオブジェクト参照を含めることができる場合は、異なるを割り当てるよう`Widget`オブジェクトを`mWidget`、前の`Widget`オブジェクトのイベントを処理しなくなります。 場合`mWidget`古いへの参照を含む唯一のオブジェクト変数`Widget`オブジェクトは破棄されます。 いくつかからイベントを処理する場合`Widget`オブジェクトを使用して、`AddHandler`ステートメントを個別に各オブジェクトからのイベントを処理します。  
  
> [!NOTE]
>  だけを宣言できます`WithEvents`、として変数が必要なの配列が`WithEvents`変数はサポートされていません。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル : イベントの宣言と発生](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
