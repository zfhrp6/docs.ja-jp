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
ms.workload: dotnet
ms.openlocfilehash: 3985fc9916b3e95e650502ef1f8dc301363b1f90
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="webbrowser-security"></a><span data-ttu-id="35561-102">WebBrowser セキュリティ</span><span class="sxs-lookup"><span data-stu-id="35561-102">WebBrowser Security</span></span>
<span data-ttu-id="35561-103"><xref:System.Windows.Forms.WebBrowser>コントロールが完全信頼でのみで動作するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="35561-103">The <xref:System.Windows.Forms.WebBrowser> control is designed to work in full trust only.</span></span> <span data-ttu-id="35561-104">コントロールに表示される HTML コンテンツは、外部の Web サーバーから取得でき、スクリプトや Web コントロールの形式でアンマネージ コードを含めることがあります。</span><span class="sxs-lookup"><span data-stu-id="35561-104">The HTML content displayed in the control can come from external Web servers and may contain unmanaged code in the form of scripts or Web controls.</span></span> <span data-ttu-id="35561-105">使用する場合、<xref:System.Windows.Forms.WebBrowser>この状況では、コントロール内のコントロールが Internet Explorer である場合は、管理ですがよりも安全性<xref:System.Windows.Forms.WebBrowser>コントロールが実行されてからこのようなアンマネージ コードを妨げません。</span><span class="sxs-lookup"><span data-stu-id="35561-105">If you use the <xref:System.Windows.Forms.WebBrowser> control in this situation, the control is no less secure than Internet Explorer would be, but the managed <xref:System.Windows.Forms.WebBrowser> control does not prevent such unmanaged code from running.</span></span>  
  
 <span data-ttu-id="35561-106">基になる ActiveX に関連するセキュリティ問題の詳細については`WebBrowser`を制御しを参照してください[WebBrowser コントロール](http://go.microsoft.com/fwlink/?LinkId=198812)です。</span><span class="sxs-lookup"><span data-stu-id="35561-106">For more information about security issues relating to the underlying ActiveX `WebBrowser` control, see [WebBrowser Control](http://go.microsoft.com/fwlink/?LinkId=198812).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35561-107">参照</span><span class="sxs-lookup"><span data-stu-id="35561-107">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 [<span data-ttu-id="35561-108">WebBrowser コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="35561-108">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [<span data-ttu-id="35561-109">WebBrowser コントロール</span><span class="sxs-lookup"><span data-stu-id="35561-109">WebBrowser Control</span></span>](http://go.microsoft.com/fwlink/?LinkId=198812)
