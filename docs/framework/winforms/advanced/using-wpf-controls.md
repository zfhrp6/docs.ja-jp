---
title: "WPF コントロールの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "相互運用性 [WPF]"
  - "Windows フォーム デザイナー, 相互運用 (WPF との)"
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# WPF コントロールの使用
Windows フォーム ベースのアプリケーションでは Windows Presentation Foundation \(WPF\) コントロールを使用できます。  2 つの異なるビュー テクノロジがありますが、円滑に相互運用できます。  
  
 Windows フォーム デザイナーは、Windows Presentation Foundation コントロールをホストするビジュアル デザイン環境を提供します。  WPF コントロールは、<xref:System.Windows.Forms.Integration.ElementHost> という名前の特別な Windows フォーム コントロールによってホストされます。  このコントロールを使用すると、WPF コントロールが、フォームのレイアウトの一部になったり、キーボードやマウスのメッセージを受信したりできるようになります。  デザイン時には、<xref:System.Windows.Forms.Integration.ElementHost> コントロールを他の Windows フォーム コントロールと同じように配置できます。  
  
 Windows フォーム コントロールは、WPF ベースのアプリケーションでも使用できます。  詳細については、「[WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)」を参照してください。  
  
## このセクションの内容  
 [方法 : デザイン時に ElementHost コントロールをコピーして貼り付ける](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 Windows Presentation Foundation コントロールを Windows フォーム上でコピーする方法について説明します。  
  
 [チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの配置](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 固定やスナップ線などの Windows フォームのレイアウト機能を使用して Windows Presentation Foundation コントロールを配置する方法について説明します。  
  
 [チュートリアル: デザイン時のホストされている WPF 要素のプロパティの変更](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 WPF コントロールでプロパティを変更するための、Windows フォーム デザイナーと [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] との間のワークフローについて説明します。  
  
 [チュートリアル: デザイン時の Windows フォームでの新しい WPF コンテンツの作成](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 Windows フォーム ベースのアプリケーションで使用するための Windows Presentation Foundation コントロールの作成方法について説明します。  
  
 [チュートリアル : ElementHost コントロールの別の Windows フォームへのコピーと貼り付け](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 Windows Presentation Foundation コントロールを Windows フォーム間でコピーする方法について説明します。  
  
 [チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの割り当て](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 フォームに表示する Windows Presentation Foundation コントロール型の選択方法について説明します。  
  
 [チュートリアル: WPF コンテンツへのスタイルの適用](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 Windows Presentation Foundation コントロールにスタイルを適用するための、Windows フォーム デザイナーと [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] との間のワークフローについて説明します。  
  
## 関連項目  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 Windows Presentation Foundation コントロールを Windows フォーム ベースのアプリケーションでホストするために使用できるクラスについて説明します。  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 Windows フォーム コントロールを Windows Presentation Foundation ベースのアプリケーションでホストするために使用できるクラスについて説明します。  
  
## 関連項目  
 [移行と相互運用性](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 Windows Presentation Foundation テクノロジと Windows フォーム テクノロジとの間の相互運用について説明します。  
  
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)  
 Windows Presentation Foundation コントロールを [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でデザインする方法について説明します。