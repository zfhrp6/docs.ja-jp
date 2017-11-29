---
title: "WebBrowser セキュリティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WebBrowser control [Windows Forms], security
- security [Windows Forms], WebBrowser control
ms.assetid: 0968846e-48ee-485a-9797-65b5b9a622f8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0d84f0c70619324bbbd38a2961914f88ac42671
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="webbrowser-security"></a><span data-ttu-id="79f1f-102">WebBrowser セキュリティ</span><span class="sxs-lookup"><span data-stu-id="79f1f-102">WebBrowser Security</span></span>
<span data-ttu-id="79f1f-103"><xref:System.Windows.Forms.WebBrowser>コントロールが完全信頼でのみで動作するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="79f1f-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="79f1f-104">コントロールに表示される HTML コンテンツは、外部の Web サーバーから取得でき、スクリプトや Web コントロールの形式でアンマネージ コードを含めることがあります。</span><span class="sxs-lookup"><span data-stu-id="79f1f-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="79f1f-105">使用する場合、<xref:System.Windows.Forms.WebBrowser>この状況では、コントロール内のコントロールが Internet Explorer である場合は、管理ですがよりも安全性<xref:System.Windows.Forms.WebBrowser>コントロールが実行されてからこのようなアンマネージ コードを妨げません。</span><span class="sxs-lookup"><span data-stu-id="79f1f-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="79f1f-106">基になる ActiveX に関連するセキュリティ問題の詳細については`WebBrowser`を制御しを参照してください[WebBrowser コントロール](http://go.microsoft.com/fwlink/?LinkId=198812)です。</span><span class="sxs-lookup"><span data-stu-id="79f1f-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](http://go.microsoft.com/fwlink/?LinkId=198812).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f1f-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="79f1f-107">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 [<span data-ttu-id="79f1f-108">WebBrowser コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="79f1f-108">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [<span data-ttu-id="79f1f-109">WebBrowser コントロール</span><span class="sxs-lookup"><span data-stu-id="79f1f-109">WebBrowser Control</span></span>](http://go.microsoft.com/fwlink/?LinkId=198812)
