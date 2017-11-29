---
title: "方法: Visual Basic で例外をログに記録する"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, logging
- exceptions, tracking
ms.assetid: a26c60e2-ae39-444a-aebb-33eccadc0eeb
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 320bc5d06f4c8e673745b600fd369af287fe8105
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-log-exceptions-in-visual-basic"></a>方法: Visual Basic で例外をログに記録する
`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生した例外に関する情報をログに記録できます。 以下の例では、`My.Application.Log.WriteException` メソッドを使用して、明示的にキャッチした例外および未処理の例外をログに記録する方法を示します。  
  
 トレース情報をログに記録するには、`My.Application.Log.WriteEntry` メソッドを使用します。 詳細については、「<xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>」を参照してください。  
  
### <a name="to-log-a-handled-exception"></a>処理した例外をログに記録するには  
  
1.  例外情報を生成するメソッドを作成します。  
  
     [!code-vb[VbVbalrMyApplicationLog#9](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_1.vb)]  
  
2.  `Try...Catch` ブロックを使用して例外をキャッチします。  
  
     [!code-vb[VbVbalrMyApplicationLog#6](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_2.vb)]  
  
3.  例外が発生する可能性のあるコードを `Try` ブロックに記述します。  
  
     `Dim` 行と `MsgBox` 行のコメントを解除すると、<xref:System.NullReferenceException> 例外が発生します。  
  
     [!code-vb[VbVbalrMyApplicationLog#7](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_3.vb)]  
  
4.  `Catch` ブロックで、`My.Application.Log.WriteException` メソッドを使用して例外情報を書き込みます。  
  
     [!code-vb[VbVbalrMyApplicationLog#8](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_4.vb)]  
  
     次の例は、処理した例外をログに記録するコード全体を示しています。  
  
     [!code-vb[VbVbalrMyApplicationLog#10](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_5.vb)]  
  
### <a name="to-log-an-unhandled-exception"></a>未処理の例外をログに記録するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  **[アプリケーション]** タブをクリックします。  
  
3.  **[アプリケーション イベントの表示]** をクリックしてコード エディターを開きます。  
  
     ApplicationEvents.vb ファイルが開かれます。  
  
4.  コード エディターで ApplicationEvents.vb ファイルを開きます。 **[全般]** メニューの **[MyApplication イベント]**をクリックします。  
  
5.  **[宣言]** メニューの **[UnhandledException]** をクリックします。  
  
     アプリケーションでは、メイン アプリケーションの実行前に <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.UnhandledException> イベントが発生します。  
  
6.  `My.Application.Log.WriteException` イベント ハンドラーに `UnhandledException` メソッドを追加します。  
  
     [!code-vb[VbVbalrMyApplicationLog#4](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_6.vb)]  
  
     次の例は、未処理の例外をログに記録するためのコード全体を示しています。  
  
     [!code-vb[VbVbalrMyApplicationLog#5](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-exceptions_7.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [方法: ログ メッセージを書き込む](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [チュートリアル : My.Application.Log による情報の書き込み先の確認](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)  
 [チュートリアル : My.Application.Log による情報の書き込み先の変更](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
