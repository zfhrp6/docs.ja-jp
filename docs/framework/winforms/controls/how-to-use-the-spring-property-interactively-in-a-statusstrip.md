---
title: "方法 : StatusStrip 内で Spring プロパティを対話的に使用する | Microsoft Docs"
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
  - "Spring プロパティ [Windows フォーム]"
  - "ステータス バー, 例"
  - "StatusStrip コントロール [Windows フォーム]"
  - "ToolStrip コントロール [Windows フォーム]"
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : StatusStrip 内で Spring プロパティを対話的に使用する
<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> プロパティを使用して、<xref:System.Windows.Forms.StatusStrip> コントロールに <xref:System.Windows.Forms.ToolStripStatusLabel> コントロールを配置できます。  <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> プロパティは、<xref:System.Windows.Forms.ToolStripStatusLabel> コントロールが <xref:System.Windows.Forms.StatusStrip> コントロールの使用可能な領域を自動的に入力するかどうかを決定します。  
  
## 使用例  
 次のコード例は、<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> プロパティを使用して、<xref:System.Windows.Forms.StatusStrip> コントロールに <xref:System.Windows.Forms.ToolStripStatusLabel> コントロールを配置する方法を示します。  <xref:System.Windows.Forms.ToolStripItem.Click> イベント ハンドラーは、exclusive\-or \(XOR\) 演算を実行して、<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> プロパティの値を切り替えます。  
  
 このコード例を使用するには、アプリケーションをコンパイルして実行し、<xref:System.Windows.Forms.StatusStrip> コントロールの **\[中間 \(スプリング\)\]** をクリックして、<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> プロパティの値を切り替えます。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System.Design、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法の詳細は、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。  また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法 : 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.ToolStripStatusLabel>   
 <xref:System.Windows.Forms.StatusStrip>   
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStripItem>   
 <xref:System.Windows.Forms.ToolStripMenuItem>   
 [ToolStrip コントロール](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)