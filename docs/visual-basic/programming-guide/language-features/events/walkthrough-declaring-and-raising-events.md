---
title: 宣言と発生イベント (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 67bbf7bc95a0fe1ee8e9c2a6cf07d850d30bb028
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652810"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>チュートリアル: イベントの宣言と発生 (Visual Basic)
このチュートリアルを宣言してという名前のクラスのイベントを発生させる方法について説明`Widget`です。 手順を完了した後可能性がある、関連トピック[チュートリアル: イベントの処理](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)からのイベントを使用する方法が示されます`Widget`アプリケーションの状態情報を提供するオブジェクト。  
  
## <a name="the-widget-class"></a>ウィジェット クラス  
 想定した、`Widget`クラスです。 `Widget`クラス メソッドを実行するには時間がかかることができますがあり、アプリケーションが何らかの完了のインジケーターを配置できます。  
  
 もちろん、行うことができる、`Widget`オブジェクト、完了した割合のダイアログ ボックスに表示されますが、すべてのプロジェクトに使用した場合は、そのダイアログ ボックスで、そのしするスタックは、`Widget`クラスです。 オブジェクトの設計の原則では、ユーザー インターフェイスのオブジェクト ハンドルを使用するアプリケーションなどオブジェクトの全体の目的は、フォームまたはダイアログ ボックスを管理する場合を除き、します。  
  
 目的は、`Widget`を追加する方が適切であるため、他のタスクを実行するには、`PercentDone`イベントと、プロシージャを呼び出すことができます`Widget`'s メソッドで処理イベントと表示状態を更新します。 `PercentDone`イベントは、タスクを取り消すためのメカニズムにも可能です。  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>このトピックのコード例をビルドするには  
  
1.  新しい Visual Basic Windows アプリケーション プロジェクトを開き、という名前のフォームを作成`Form1`です。  
  
2.  2 つのボタンとラベルを追加`Form1`です。  
  
3.  次の表のように、各オブジェクトに名前を付けます。  
  
    |オブジェクト|プロパティ|設定|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|タスクを開始します。|  
    |`Button2`|`Text`|キャンセル|  
    |`Label`|`(Name)`, `Text`|lblPercentDone、0|  
  
4.  **プロジェクト**] メニューの [選択**クラスの追加**という名前のクラスを追加する`Widget.vb`をプロジェクトにします。  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>ウィジェットのクラスのイベントを宣言するには  
  
-   使用して、`Event`でイベントを宣言するキーワード、`Widget`クラスです。 イベントを持つことができる注`ByVal`と`ByRef`、引数として`Widget`の`PercentDone`イベントを示しています。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 呼び出し元のオブジェクトを受け取ると、`PercentDone`イベント、`Percent`引数には、タスクが完了の割合が含まれています。 `Cancel`引数に設定することができます`True`イベントを発生させたメソッドをキャンセルします。  
  
> [!NOTE]
>  次の例外を除き、プロシージャ引数を行う場合と同様、イベント引数を宣言することができます: イベントことはできません`Optional`または`ParamArray`引数、およびイベントに戻り値がありません。  
  
 `PercentDone`によってイベントが発生した、`LongTask`のメソッド、`Widget`クラスです。 `LongTask` 2 つの引数を受け取る: 作業、および処理する前に最小の時間間隔に操作を実行する時間の長さメソッド別人`LongTask`させる一時停止、`PercentDone`イベント。  
  
#### <a name="to-raise-the-percentdone-event"></a>ですイベントを発生させる  
  
1.  アクセスを簡素化する、`Timer`このクラスで使用されるプロパティを追加、`Imports`クラスのモジュールの宣言セクションの先頭にステートメントの上、`Class Widget`ステートメントです。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  `Widget` クラスに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 アプリケーションを呼び出すと、 `LongTask` 、メソッド、`Widget`クラスが生成、`PercentDone`イベントすべて`MinimumInterval`秒です。 イベントが戻るとき、`LongTask`かどうかをチェック、`Cancel`引数に設定された`True`です。  
  
 いくつかの免責事項は、ここで必要です。 簡略化のため、`LongTask`手順の前提条件があらかじめわかってタスクにどのくらい時間がかかります。 これは、ケースではほとんどありません。 何かが行われていることを示す値を取得するまでに経過する時間の量だけでは、多くの場合、最も重要な要素をユーザーに、タスクを均等なサイズのチャンクに分割することは困難ですが、できます。  
  
 このサンプルでは別欠陥を発見が可能性があります。 `Timer`プロパティには、午前 0 時から経過した秒数が返されます。 直前の午前 0 時に起動された場合、アプリケーションとして行き詰まってそのため、します。 時間の計測をより慎重な方法は境界条件これを考慮に入れるに入れるかなどのプロパティを使用して`Now`です。  
  
 これで、`Widget`クラスは、イベントを発生させることができます、次のように次のチュートリアルに進むことができます。 [チュートリアル: イベントの処理](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)を使用する方法を示します`WithEvents`でイベント ハンドラーを関連付ける方法、`PercentDone`イベント。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>  
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>  
 [チュートリアル : イベントの処理](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)  
 [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
