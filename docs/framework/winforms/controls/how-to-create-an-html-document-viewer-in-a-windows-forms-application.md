---
title: "方法 : Windows フォーム アプリケーションで HTML ドキュメントビューアーを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ドキュメント ビューアー"
  - "WebBrowser コントロール [Windows フォーム], 作成 (HTML ドキュメント ビューアーを)"
  - "Windows フォーム, 作成 (ドキュメント ビューアーを)"
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Windows フォーム アプリケーションで HTML ドキュメントビューアーを作成する
<xref:System.Windows.Forms.WebBrowser> コントロールを使用すると、インターネット Web ブラウザーの全機能を使用することなく、HTML ドキュメントを表示および印刷できます。  このコントロールは、信頼できない Web コントロールや、悪意のあるスクリプト コードを含む可能性のある Web ページの読み込みをユーザーに許可することなく、HTML の書式設定機能を利用する場合に便利です。  このように、<xref:System.Windows.Forms.WebBrowser> コントロールの機能を制限して、HTML 電子メール ビューアーとして使用したり、アプリケーションで HTML 形式のヘルプを表示したりできます。  
  
### HTML ドキュメント ビューアーを作成するには  
  
1.  <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> プロパティを `false` に設定して、<xref:System.Windows.Forms.WebBrowser> コントロールにファイルをドロップしたときに、そのファイルが開かないようにします。  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  <xref:System.Windows.Forms.WebBrowser.Url%2A> プロパティを最初のファイルを表示する位置に設定します。  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   `webBrowser1` という名前の <xref:System.Windows.Forms.WebBrowser> コントロール。  
  
-   `System` アセンブリおよび `System.Windows.Forms` アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.WebBrowser>   
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>   
 <xref:System.Windows.Forms.WebBrowser.Url%2A>   
 [WebBrowser コントロールの概要](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)   
 [WebBrowser セキュリティ](../../../../docs/framework/winforms/controls/webbrowser-security.md)   
 [方法 : WebBrowser コントロールで URL に移動する](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)   
 [方法 : WebBrowser コントロールを使用して印刷する](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)