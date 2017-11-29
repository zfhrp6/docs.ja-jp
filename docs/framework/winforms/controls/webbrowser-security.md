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
# <a name="webbrowser-security"></a>WebBrowser セキュリティ
<xref:System.Windows.Forms.WebBrowser>コントロールが完全信頼でのみで動作するように設計されています。 コントロールに表示される HTML コンテンツは、外部の Web サーバーから取得でき、スクリプトや Web コントロールの形式でアンマネージ コードを含めることがあります。 使用する場合、<xref:System.Windows.Forms.WebBrowser>この状況では、コントロール内のコントロールが Internet Explorer である場合は、管理ですがよりも安全性<xref:System.Windows.Forms.WebBrowser>コントロールが実行されてからこのようなアンマネージ コードを妨げません。  
  
 基になる ActiveX に関連するセキュリティ問題の詳細については`WebBrowser`を制御しを参照してください[WebBrowser コントロール](http://go.microsoft.com/fwlink/?LinkId=198812)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.WebBrowser>  
 [WebBrowser コントロールの概要](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [WebBrowser コントロール](http://go.microsoft.com/fwlink/?LinkId=198812)
