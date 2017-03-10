---
title: "方法: アプリケーションの起動時または終了時にメッセージをログに記録する (Visual Basic) | Microsoft Docs"
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
  - "イベント ログ, 終了"
  - "My.Application.Log オブジェクト, ログ記録"
  - "Startup イベント"
  - "イベント ログ, スタートアップ"
  - "Shutdown イベント"
  - "My.Log オブジェクト, ログ記録"
ms.assetid: 67624d05-cddf-48b7-8c36-5c99baa4c621
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# 方法: アプリケーションの起動時または終了時にメッセージをログに記録する (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Application.Log` オブジェクトおよび `My.Log` オブジェクトを使用すると、アプリケーション内で発生したイベントに関する情報をログに記録できます。 この例では、`Startup` イベントおよび `Shutdown` イベントで `My.Application.Log.WriteEntry` メソッドを使用してトレース情報を書き込む方法を示します。  
  
### アプリケーションのイベント ハンドラー コードにアクセスするには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[アプリケーション\]** タブをクリックします。  
  
3.  **\[アプリケーション イベントの表示\]** をクリックしてコード エディターを開きます。  
  
     ApplicationEvents.vb ファイルが開かれます。  
  
### アプリケーションの起動時にメッセージをログに記録するには  
  
1.  コード エディターで ApplicationEvents.vb ファイルを開きます。**\[全般\]** メニューの **\[MyApplication イベント\]** をクリックします。  
  
2.  **\[宣言\]** メニューの **\[スタートアップ\]** をクリックします。  
  
     アプリケーションでは、メイン アプリケーションの実行前に <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup> イベントが発生します。  
  
3.  `Startup` イベント ハンドラーに `My.Application.Log.WriteEntry` メソッドを追加します。  
  
     [!code-vb[VbVbalrMyApplicationLog#1](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/visualbasic/VbVbalrMyApplicationLog/MyEventsFake.vb#1)]  
  
### アプリケーションの終了時にメッセージをログに記録するには  
  
1.  コード エディターで ApplicationEvents.vb ファイルを開きます。**\[全般\]** メニューの **\[MyApplication イベント\]** をクリックします。  
  
2.  **\[宣言\]** メニューの **\[シャットダウン\]** をクリックします。  
  
     アプリケーションでは、メイン アプリケーションが実行された後、終了前に <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown> イベントが発生します。  
  
3.  `Shutdown` イベント ハンドラーに `My.Application.Log.WriteEntry` メソッドを追加します。  
  
     [!code-vb[VbVbalrMyApplicationLog#2](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/visualbasic/VbVbalrMyApplicationLog/MyEventsFake.vb#2)]  
  
## 使用例  
 **プロジェクト デザイナー**を使用して、コード エディターでアプリケーション イベントにアクセスできます。 詳細については、「[\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
 [!code-vb[VbVbalrMyApplicationLog#3](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/visualbasic/VbVbalrMyApplicationLog/MyEventsFake.vb#3)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>   
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>   
 [\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)   
 [アプリケーション ログの使用](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)