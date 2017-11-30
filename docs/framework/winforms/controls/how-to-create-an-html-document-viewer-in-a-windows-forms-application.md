---
title: "方法 : Windows フォーム アプリケーションで HTML ドキュメントビューアーを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e06fbfde68c0d02a94f8c7e4657e2907cd3fa7eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>方法 : Windows フォーム アプリケーションで HTML ドキュメントビューアーを作成する
使用することができます、<xref:System.Windows.Forms.WebBrowser>コントロールを表示し、インターネットの Web ブラウザーの全機能を提供せずに HTML ドキュメントを印刷します。 これは、HTML の書式設定機能を利用する場合、ユーザーは信頼されていない Web コントロールまたは悪意のあるスクリプト コードを含む可能性のある任意の Web ページを読み込むをしないようにする場合に便利です。 機能を制限することができます、 <xref:System.Windows.Forms.WebBrowser> HTML 電子メール ビューアーとして使用するか、アプリケーションで HTML 形式のヘルプを提供するなど、この方法を制御します。  
  
### <a name="to-create-an-html-document-viewer"></a>HTML ドキュメント ビューアーを作成するには  
  
1.  設定、<xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>プロパティを`false`を防ぐために、<xref:System.Windows.Forms.WebBrowser>コントロールにドロップ ファイルを開かない。  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  設定、<xref:System.Windows.Forms.WebBrowser.Url%2A>プロパティを表示する最初のファイルの場所。  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `webBrowser1` という名前の <xref:System.Windows.Forms.WebBrowser> コントロール。  
  
-   `System` アセンブリおよび `System.Windows.Forms` アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>  
 <xref:System.Windows.Forms.WebBrowser.Url%2A>  
 [WebBrowser コントロールの概要](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [WebBrowser セキュリティ](../../../../docs/framework/winforms/controls/webbrowser-security.md)  
 [方法: WebBrowser コントロールで URL に移動する](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [方法: WebBrowser コントロールを使用して印刷する](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
