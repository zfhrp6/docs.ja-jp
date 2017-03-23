---
title: "宣言と発生 (Visual Basic) のイベント |Microsoft ドキュメント"
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
- declarations, events
- events [Visual Basic], walkthroughs
- declaring events, walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events, walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 233673c1d42684b7caa9042d18fb341a1043a31b
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>チュートリアル: イベントの宣言と発生 (Visual Basic)
このチュートリアルを宣言してという名前のクラスのイベントを発生させる方法について説明`Widget`します。 手順を完了すると後、は、関連トピックを確認することができます[チュートリアル: イベントの処理](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)からのイベントを使用する方法を説明`Widget`アプリケーションで、状態情報を入力するオブジェクト。  
  
## <a name="the-widget-class"></a>Widget クラス  
 想定した、`Widget`クラスです。 `Widget`クラスに実行するには時間が長くなるメソッドとする場合、アプリケーションが何らかの完了のインジケーターを配置することです。  
  
 もちろん、行うことができます、`Widget`オブジェクト % 完了ダイアログ ボックスの表示が、そのダイアログ ボックスを使用するすべてのプロジェクトで使用するスタックするし、`Widget`クラスです。 オブジェクト設計の原則は、オブジェクト ハンドル ユーザー インターフェイスを使用して、アプリケーションは、オブジェクトの全体の目的は、フォームまたはダイアログ ボックスを管理する場合を除き、します。  
  
 目的は、`Widget`を追加することが、その他のタスクを実行することです、`PercentDone`イベントおよび let を呼び出すプロシージャ`Widget`メソッド処理がイベントと表示の状態を更新します。 `PercentDone`イベントは、タスクのキャンセル メカニズムも提供できます。  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>このトピックのコード例をビルドするには  
  
1.  新しい[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Windows アプリケーション プロジェクトし、という名前のフォームを作成する`Form1`です。  
  
2.  2 つのボタンとラベルを追加`Form1`します。  
  
3.  次の表に示すように、オブジェクトの名前を付けます。  
  
    |オブジェクト|プロパティ|設定|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|開始タスク|  
    |`Button2`|`Text`|キャンセル|  
    |`Label`|`(Name)`, `Text`|lblPercentDone 0|  
  
4.  **プロジェクト**] メニューの [選択**クラスの追加**という名前のクラスを追加する`Widget.vb`をプロジェクトにします。  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>ウィジェット クラスのイベントを宣言するには  
  
-   使用して、`Event`でイベントを宣言するキーワード、`Widget`クラスです。 イベントがあることに注意してください`ByVal`と`ByRef`、引数として`Widget`の`PercentDone`イベントを示しています。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#1;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 呼び出し元のオブジェクトを受信すると、 `PercentDone` 、イベント、`Percent`引数には、タスクが完了の割合が含まれています。 `Cancel`引数に設定することができます`True`イベントを発生させたメソッドをキャンセルします。  
  
> [!NOTE]
>  イベント引数を宣言するには、次の例外を除き、プロシージャ引数の場合と同様。 イベントを使用できない`Optional`または`ParamArray`引数、およびイベントには戻り値がないです。  
  
 `PercentDone`によってイベントが発生した、`LongTask`のメソッド、`Widget`クラスです。 `LongTask`2 つの引数: 時間の長さメソッドが行う作業、および前に最小の時間間隔を装う`LongTask`させる一時停止、`PercentDone`イベントです。  
  
#### <a name="to-raise-the-percentdone-event"></a>ですイベントを生成するには  
  
1.  アクセスを簡略化する、`Timer`このクラスによって使用されるプロパティを追加、`Imports`ステートメントをクラス モジュールの宣言セクションの上部に上、`Class Widget`ステートメントです。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#2;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  `Widget` クラスに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents&#3;](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 アプリケーションを呼び出すと、 `LongTask` 、メソッド、`Widget`クラスが生成、`PercentDone`イベントすべて`MinimumInterval`秒です。 イベントが返されるときに`LongTask`かどうかをチェック、`Cancel`引数に設定された`True`します。  
  
 いくつかの免責事項は、ここで必要です。 簡略化のため、`LongTask`手順では、事前にわかってタスクにかかるものとします。 これは、ケースではほとんどありません。 何かが起こっているかを示す値を取得するまでに経過する時間数だけでは、多くの場合、最も重要な要素をユーザーに、タスクを均等なサイズのチャンクに分割することは困難ですが、できます。  
  
 このサンプルでは別の問題を見つけられたら可能性があります。 `Timer`プロパティには、午前&0; 時から経過した秒数が返されます。 そのため、アプリケーションから抜け出せなく直前の午前&0; 時に起動された場合。 時間の計測をより慎重な方法はこのなどを考慮に入れるの境界条件に入れるかなどのプロパティを使用して`Now`します。  
  
 これで、`Widget`クラスには、イベントを発生させて、次のように次のチュートリアルに進むことができます。 [チュートリアル: イベントの処理](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)を使用する方法を示します`WithEvents`に、イベント ハンドラーを関連付けるには、`PercentDone`イベントです。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A></xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>   
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A></xref:Microsoft.VisualBasic.DateAndTime.Now%2A>   
 [チュートリアル: イベントの処理](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)   
 [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
