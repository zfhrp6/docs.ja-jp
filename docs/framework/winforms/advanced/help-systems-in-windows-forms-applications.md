---
title: "Windows フォーム アプリケーションのヘルプ システム | Microsoft Docs"
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
  - "ヘルプ, 追加 (Windows アプリケーションに)"
  - "ヘルプ, Windows フォーム"
  - "HelpProvider コンポーネント [Windows フォーム], 用意 (ヘルプを Windows アプリケーションに)"
  - "ポップ ヒント ヘルプ"
  - "Windows アプリケーション, 用意 (ヘルプ システムを)"
ms.assetid: 2a96a278-432c-41fc-9e3c-5bfedf5e1267
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Windows フォーム アプリケーションのヘルプ システム
アプリケーションの開発者として、ユーザーに対する最も重要な配慮の 1 つは、役に立つヘルプ システムをアプリケーションに用意することです。  操作がわからないときや、混乱したときにユーザーが頼りにするのは、ヘルプ システムです。  Windows ベースのアプリケーションには、[HelpProvider コンポーネント](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) を使用することで簡単にヘルプ システムを用意できます。  
  
## さまざまな種類のヘルプ  
 Windows フォームの <xref:System.Windows.Forms.HelpProvider> コンポーネントは、HTML Help 1.x ヘルプ ファイル \(HTML Help Workshop で生成した .chm ファイル、または .htm ファイル\) を Windows ベースのアプリケーションに関連付けるために使用します。  <xref:System.Windows.Forms.HelpProvider> コンポーネントにより、Windows フォームのコントロール、または固有のコントロールに状況依存のヘルプを用意できます。  さらに、<xref:System.Windows.Forms.HelpProvider> コンポーネントは目次、索引、検索機能のメイン ページなど、ヘルプ ファイルの特定の領域を開くことができます。  <xref:System.Windows.Forms.HelpProvider> コンポーネントに関する一般的な情報については、「[HelpProvider コンポーネントの概要](../../../../docs/framework/winforms/controls/helpprovider-component-overview-windows-forms.md)」を参照してください。  <xref:System.Windows.Forms.HelpProvider> コンポーネントを使用して Windows フォーム上にポップアップ ヘルプを表示する方法については、「[方法 : ポップアップ ヘルプを表示する](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)」を参照してください。  <xref:System.Windows.Forms.ToolTip> コンポーネントを使用してコントロール固有のヘルプを表示する方法については、「[ツールヒントを使用したコントロールのヘルプ](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)」を参照してください。  
  
 HTML Help Workshop で HTML Help 1.x ファイルを生成できます。  HTML Help の詳細については、MSDN の HTML Help Workshop または他の HTML Help のトピックを参照してください。  
  
## 参照  
 [Windows フォームでのヘルプの統合](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)   
 [HelpProvider コンポーネント](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md)   
 [ToolTip コンポーネント](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)   
 [Windows フォームの概要](../../../../docs/framework/winforms/windows-forms-overview.md)   
 [Windows フォーム](../../../../docs/framework/winforms/index.md)