---
title: "方法 : ToolStripTextBox を拡大して ToolStrip の残りの幅に合わせる (Windows フォーム) | Microsoft Docs"
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
  - "テキスト ボックス, 拡大 (ToolStrip コントロールを) [Windows フォーム]"
  - "ToolStrip コントロール [Windows フォーム], 拡大 (テキスト ボックスを)"
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : ToolStripTextBox を拡大して ToolStrip の残りの幅に合わせる (Windows フォーム)
<xref:System.Windows.Forms.ToolStrip> コントロールの <xref:System.Windows.Forms.ToolStrip.Stretch%2A> プロパティを `true` に設定すると、コントロールはコンテナーのサイズに合わせて拡大されます。コンテナーのサイズを変更すると、コントロールのサイズも変更されます。  この構成は、<xref:System.Windows.Forms.ToolStripTextBox> などのコントロールの項目を拡大して使用できる領域に合わせる場合や、コントロールのサイズ変更時に項目のサイズを変更する場合に役立ちます。  コントロールの拡大は、Microsoft® Internet Explorer のアドレス バーに似た外観や動作を実装する場合に便利です。  
  
## 使用例  
 次のコード例は、<xref:System.Windows.Forms.ToolStripTextBox> から派生する `ToolStripSpringTextBox` というクラスを作成します。  このクラスでは、<xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> メソッドをオーバーライドして、親の <xref:System.Windows.Forms.ToolStrip> コントロールの幅から他のすべての項目の合計幅を引いた値を求め、使用できる領域の幅を計算します。  また、このコード例は、新しい動作を実行する <xref:System.Windows.Forms.Form> クラスと `Program` クラスも作成します。  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   System、System.Drawing、System.Windows.Forms の各アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ToolStripTextBox>   
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=fullName>   
 [ToolStrip コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)   
 [方法 : StatusStrip 内で Spring プロパティを対話的に使用する](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)