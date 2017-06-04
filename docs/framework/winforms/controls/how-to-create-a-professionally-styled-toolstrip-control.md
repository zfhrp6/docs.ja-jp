---
title: "方法 : プロフェッショナル スタイルの ToolStrip コントロールを作成する | Microsoft Docs"
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
  - "ツール バー [Windows フォーム]"
  - "ToolStrip コントロール [Windows フォーム]"
  - "ToolStripProfessionalRenderer クラス [Windows フォーム]"
  - "ToolStripRenderer クラス [Windows フォーム]"
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : プロフェッショナル スタイルの ToolStrip コントロールを作成する
<xref:System.Windows.Forms.ToolStripProfessionalRenderer> 型から派生する独自のクラスを記述することで、アプリケーションの <xref:System.Windows.Forms.ToolStrip> コントロールにプロフェッショナルな外観と動作 \(操作性\) を与えることができます。  
  
 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] に、この機能の広範なサポートがあります。  
  
 [チュートリアル : プロフェッショナル スタイルの ToolStrip コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).  
  
## 使用例  
 次のコード例では、<xref:System.Windows.Forms.ToolStrip> コントロールを使用して、Microsoft® Outlook® の**ナビゲーション ウィンドウ**に似た複合コントロールを作成する方法について説明します。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System.Drawing アセンブリおよび System.Windows.Forms アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法の詳細については、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。  また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[チュートリアル : プロフェッショナル スタイルの ToolStrip コントロールの作成](http://msdn.microsoft.com/library/ms233664\(v=vs.110\))」も参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 [ToolStrip コントロール](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)   
 [方法 : フォームに標準メニュー項目を追加する](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)