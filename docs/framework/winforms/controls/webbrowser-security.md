---
title: "WebBrowser セキュリティ | Microsoft Docs"
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
  - "セキュリティ [Windows フォーム], WebBrowser コントロール"
  - "WebBrowser コントロール [Windows フォーム], セキュリティ"
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# WebBrowser セキュリティ
<xref:System.Windows.Forms.WebBrowser> コントロールは、完全に信頼されている場合にのみ動作するようにデザインされています。  このコントロールでは、外部 Web サーバーからの HTML コンテンツを表示できるため、スクリプトや Web コントロールの形式でアンマネージ コードが含まれている可能性があります。  この場合に <xref:System.Windows.Forms.WebBrowser> コントロールを使用しても、Internet Explorer を使用する場合と同様に安全ですが、マネージ コントロールである <xref:System.Windows.Forms.WebBrowser> が、アンマネージ コードの実行を妨げることはありません。  
  
 基になる ActiveX の `WebBrowser` コントロールに関するセキュリティ問題の詳細については、「[WebBrowser Control \(WebBrowser コントロール\)](http://go.microsoft.com/fwlink/?LinkId=198812)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.WebBrowser>   
 [WebBrowser コントロールの概要](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)   
 [WebBrowser Control \(WebBrowser コントロール\)](http://go.microsoft.com/fwlink/?LinkId=198812)