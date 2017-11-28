---
title: "方法: アプリケーションの起動時または終了時にメッセージをログに記録する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event logs, shutdown
- My.Application.Log object, logging
- Startup event [Visual Basic]
- event logs, startup
- Shutdown event [Visual Basic]
- My.Log object, logging
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16235e245fd71f16edb67003cf237bcee3a6855e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-log-messages-when-the-application-starts-or-shuts-down-visual-basic"></a>方法: アプリケーションの起動時または終了時にメッセージをログに記録する (Visual Basic)
`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報をログに記録できます。 この例では、 `My.Application.Log.WriteEntry` イベントおよび `Startup` イベントで `Shutdown` メソッドを使用してトレース情報を書き込む方法を示します。  
  
### <a name="to-access-the-applications-event-handler-code"></a>アプリケーションのイベント ハンドラー コードにアクセスするには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。  
  
2.  **[アプリケーション]** タブをクリックします。  
  
3.  **[アプリケーション イベントの表示]** をクリックしてコード エディターを開きます。  
  
     ApplicationEvents.vb ファイルが開かれます。  
  
### <a name="to-log-messages-when-the-application-starts"></a>アプリケーションの起動時にメッセージをログに記録するには  
  
1.  コード エディターで ApplicationEvents.vb ファイルを開きます。 **[全般]** メニューの **[MyApplication イベント]**をクリックします。  
  
2.  **[宣言]** メニューの **[スタートアップ]**をクリックします。  
  
     アプリケーションでは、メイン アプリケーションの実行前に <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> イベントが発生します。  
  
3.  `My.Application.Log.WriteEntry` イベント ハンドラーに `Startup` メソッドを追加します。  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_1.vb)]  
  
### <a name="to-log-messages-when-the-application-shuts-down"></a>アプリケーションの終了時にメッセージをログに記録するには  
  
1.  コード エディターで ApplicationEvents.vb ファイルを開きます。 **[全般]** メニューの **[MyApplication イベント]**をクリックします。  
  
2.  **[宣言]** メニューの **[シャットダウン]**をクリックします。  
  
     アプリケーションでは、メイン アプリケーションが実行された後、終了前に <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> イベントが発生します。  
  
3.  `My.Application.Log.WriteEntry` イベント ハンドラーに `Shutdown` メソッドを追加します。  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_2.vb)]  
  
## <a name="example"></a>例  
 **プロジェクト デザイナー** を使用して、コード エディターでアプリケーション イベントにアクセスできます。 詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/how-to-log-messages-when-the-application-starts-or-shuts-down_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
