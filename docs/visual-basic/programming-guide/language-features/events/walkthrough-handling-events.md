---
title: "イベントの処理 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword, walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 17cd0bddbe8c89cf60e19f3f2af6f448ad465d70
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-handling-events-visual-basic"></a>チュートリアル: イベントの処理 (Visual Basic)
これは、2 番目のイベントを使用する方法を示す&2; つのトピックです。 最初のトピックでは、[チュートリアル: イベントの宣言と発生](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)を宣言し、イベントを発生させる方法について説明します。 このセクションでは、フォームとそのチュートリアルからクラスを使用して、行われるときにイベントを処理する方法を示します。  
  
 `Widget`クラスの例は、従来のイベント処理のステートメントを使用します。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]イベントを操作するためには、その他の手法を提供します。 演習として使用するには、この例を変更することができます、`AddHandler`と`Handles`ステートメントです。  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>ウィジェット クラスのことですイベントを処理するには  
  
1.  次のコードを配置`Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&4;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     `WithEvents`キーワードを指定する変数`mWidget`オブジェクトのイベントを処理するために使用します。 オブジェクトの種類を指定するには、オブジェクトの作成元となるクラスの名前を指定します。  
  
     変数`mWidget`で宣言された`Form1`ため`WithEvents`変数はクラス レベルである必要があります。 これは配置することでクラスの種類に関係なく当てはまります。  
  
     変数`mblnCancel`、キャンセルに使用、`LongTask`メソッドです。  
  
## <a name="writing-code-to-handle-an-event"></a>イベントを処理するコードの記述  
 使用して変数を宣言するとすぐに`WithEvents`、クラスの左側のドロップダウン リストに表示される変数名**コード エディター**します。 選択すると`mWidget`、`Widget`クラスのイベントが右のドロップダウン リストに表示されます。 イベントの対応するプロシージャのプレフィックスを持つイベントを選択すると表示`mWidget`とアンダー スコア。 関連付けられているすべてのイベント プロシージャ、`WithEvents`変数は、プレフィックスとして変数名に付与されます。  
  
#### <a name="to-handle-an-event"></a>イベントを処理するには  
  
1.  選択`mWidget`で、左側のドロップダウン リストから、**コード エディター**します。  
  
2.  選択、`PercentDone`右のドロップダウン リストからのイベントです。 **コード エディター**が開き、`mWidget_PercentDone`イベント プロシージャです。  
  
    > [!NOTE]
    >  **コード エディター**は役立ちますが、必須ではない新しいイベント ハンドラーを挿入するためです。 このチュートリアルでは、イベント ハンドラーのコードに直接コピーするより直接的です。  
  
3.  `mWidget_PercentDone` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#5;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     ときに、`PercentDone`イベントは、イベント プロシージャが完了の割合を表示、`Label`コントロールです。 `DoEvents`メソッドを使用して、ラベルを再描画し、また、ユーザーがクリックすること、**キャンセル** ボタンをクリックします。  
  
4.  次のコードを追加、`Button2_Click`イベント ハンドラー。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&6;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 ユーザーがクリックした場合、**キャンセル**中にボタン`LongTask`が実行されている、`Button2_Click`イベントが実行されるとすぐに、`DoEvents`ステートメントで発生するイベントの処理を使用できます。 クラス レベルの変数`mblnCancel`に設定されている`True`、および`mWidget_PercentDone`イベントことをテストし、設定、`ByRef Cancel`引数`True`します。  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>WithEvents 変数をオブジェクトに接続します。  
 `Form1`今すぐ処理する設定、`Widget`オブジェクトのイベントです。 あとは検索する、`Widget`どこかにします。  
  
 変数を宣言するときに`WithEvents`デザイン時にオブジェクトが関連付けられていないことです。 A`WithEvents`変数は、その他のすべてのオブジェクト変数と同じようにします。 オブジェクトを作成してにへの参照を割り当てる必要がある、`WithEvents`変数です。  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>オブジェクトを作成してへの参照を割り当てる  
  
1.  選択**(Form1 イベント)**で、左側のドロップダウン リストから、**コード エディター**します。  
  
2.  選択、`Load`右のドロップダウン リストからのイベントです。 **コード エディター**が開き、`Form1_Load`イベント プロシージャです。  
  
3.  次のコードを追加、`Form1_Load`イベントを作成する手順、 `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#7;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 このコードの実行時に[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を作成、`Widget`オブジェクトおよびに関連付けられているイベント プロシージャにそのイベントを接続する`mWidget`です。 した時点で、ときに、`Widget`を発生させますその`PercentDone`、イベント、`mWidget_PercentDone`イベント プロシージャを実行します。  
  
#### <a name="to-call-the-longtask-method"></a>LongTask メソッドを呼び出す  
  
-   `Button1_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#8;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 前に、`LongTask`メソッドが呼び出されるラベルの表示が完了した割合を初期化する必要があり、クラス レベル`Boolean`フラグに設定するメソッドをキャンセルする必要があります`False`します。  
  
 `LongTask`12.2 秒のタスクの実行時間と呼びます。 `PercentDone`イベントは、1 回ごと&3; 分の&1; 秒です。 このイベントが発生するたびに、`mWidget_PercentDone`イベント プロシージャを実行します。  
  
 `LongTask`が完了したら、`mblnCancel`かどうかをテスト`LongTask`通常は、終了したためが停止している場合、または`mblnCancel`に設定されている`True`します。 前者の場合にのみ、完了したパーセントが更新されます。  
  
#### <a name="to-run-the-program"></a>プログラムを実行するには  
  
1.  F5 キーを押して、プロジェクトを実行モードにします。  
  
2.  クリックして、**タスクの開始** ボタンをクリックします。 毎回、`PercentDone`イベントは、タスクが完了の割合でラベルを更新します。  
  
3.  クリックして、**キャンセル**タスクを停止する ボタンをクリックします。 注意しての外観、**キャンセル**ボタンでは、クリックするとすぐには変化しません。 `Click`までイベントが発生しない、`My.Application.DoEvents`ステートメントでは、イベント処理を使用できます。  
  
    > [!NOTE]
    >  `My.Application.DoEvents`フォームは、メソッドがまったく同じ方法でイベントを処理できません。 たとえば、このチュートリアルでをクリックして、**キャンセル**2 回ボタンをクリックします。 使用できるイベントを直接処理するためのフォームを許可するようにマルチ スレッドです。 詳細については、次を参照してください。[スレッド](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)します。  
  
 F11 キーで、プログラムを実行し、コードを&1; 行ずつ処理するときにあります。 実行に入力する方法がわかります`LongTask`、し、簡単に再入力`Form1`たびに、`PercentDone`イベントが発生します。  
  
 何が起こる場合、実行中のコードに戻る`Form1`、`LongTask`メソッドが再び呼び出されるでしょうか。 場合、スタック オーバーフローが発生する最悪の場合、`LongTask`イベントが発生するたびに呼び出されました。  
  
 変数が発生することができます`mWidget`、別のイベントを処理する`Widget`新しいへの参照を割り当てることによってオブジェクト`Widget`に`mWidget`します。 実際には、コードを行うことができます`Button1_Click`ボタンをクリックするたびにこの操作を行います。  
  
#### <a name="to-handle-events-for-a-different-widget"></a>さまざまなウィジェットのイベントを処理するには  
  
-   次のコード行を追加、`Button1_Click`という行を前の手順`mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#9;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 上記のコードが、新たに作成`Widget`たびにこのボタンをクリックします。 すぐに、`LongTask`メソッドが完了するへの参照、`Widget`がリリースされると、`Widget`が破棄されます。  
  
 A`WithEvents`変数は、一度に&1; つのオブジェクト参照を含めることができますので、異なるを割り当てる場合`Widget`オブジェクトを`mWidget`、前の`Widget`オブジェクトのイベントを処理できなくなります。 場合`mWidget`古いへの参照を含む唯一のオブジェクト変数`Widget`オブジェクトは破棄されます。 いくつかのイベントを処理する場合は、`Widget`オブジェクトを使用して、`AddHandler`とは別に各オブジェクトからイベントを処理するステートメントです。  
  
> [!NOTE]
>  だけを宣言する`WithEvents`変数としてする必要があるの配列が`WithEvents`変数がサポートされていません。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: 宣言とイベントを発生させる](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)   
 [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
