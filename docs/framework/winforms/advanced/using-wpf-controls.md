---
title: "WPF コントロールの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e616019d53648058d51a3d0df457b1380aaf3b1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="using-wpf-controls"></a>WPF コントロールの使用
Windows フォーム ベースのアプリケーションでは、Windows Presentation Foundation (WPF) コントロールを使用できます。 これらは、次の 2 つの異なるビュー テクノロジが、相互運用スムーズに動作します。  
  
 Windows フォーム デザイナーでは、Windows Presentation Foundation コントロールをホストするためのビジュアル デ ザイン環境を提供します。 WPF コントロールがという名前を特別な Windows フォーム コントロールでホストされている<xref:System.Windows.Forms.Integration.ElementHost>です。 このコントロールは、フォームのレイアウトに参加して、キーボードとマウスのメッセージを受信する WPF コントロールを使用します。 デザイン時に配置することができます、<xref:System.Windows.Forms.Integration.ElementHost>同様の Windows フォーム コントロールを制御します。  
  
 また、WPF ベースのアプリケーションで Windows フォーム コントロールを使用することができます。 詳細については、次を参照してください。 [WPF デザイナー](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: デザイン時に ElementHost コントロールをコピーして貼り付ける](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 Windows フォーム上の Windows Presentation Foundation コントロールをコピーする方法を示します。  
  
 [チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの配置](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 固定やスナップ線など、Windows フォームのレイアウト機能を使用して、Windows Presentation Foundation コントロールを配置する方法を示します。  
  
 [チュートリアル: デザイン時のホストされている WPF 要素のプロパティの変更](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 Windows フォーム デザイナー間のワークフローを示しています、 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] WPF コントロールのプロパティを変更するためです。  
  
 [チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 Windows フォーム ベースのアプリケーションで使用される Windows Presentation Foundation コントロールを作成する方法を示します。  
  
 [チュートリアル: ElementHost コントロールの別の Windows フォームへのコピーと貼り付け](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 Windows Presentation Foundation コントロールを別の 1 つの Windows フォームにコピーする方法を示します。  
  
 [チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの割り当て](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 フォームに表示する Windows Presentation Foundation コントロールの種類を選択する方法を示します。  
  
 [チュートリアル: WPF コンテンツへのスタイルの適用](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 Windows フォーム デザイナー間のワークフローを示しています、 [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] Windows Presentation Foundation コントロールにスタイルを適用するためです。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 Windows フォーム ベースのアプリケーションで Windows Presentation Foundation コントロールのホストに使用できるクラスについて説明します。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 Windows Presentation Foundation ベースのアプリケーションでホストの Windows フォーム コントロールを使用できるクラスについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 Windows Presentation Foundation と Windows フォームの技術間の相互運用を説明します。  
  
 [WPF デザイナー](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 Windows Presentation Foundation コントロールをデザインする方法について説明[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]です。
