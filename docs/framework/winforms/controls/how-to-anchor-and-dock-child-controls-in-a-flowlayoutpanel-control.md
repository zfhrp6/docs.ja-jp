---
title: "方法 : FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする | Microsoft Docs"
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
  - "子コントロール, 固定およびドッキング"
  - "コントロール [Windows フォーム], 子"
  - "FlowLayoutPanel コントロール [Windows フォーム], 子コントロール"
  - "レイアウト [Windows フォーム], 子コントロール"
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする
<xref:System.Windows.Forms.FlowLayoutPanel> コントロールは、子コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティと <xref:System.Windows.Forms.Control.Dock%2A> プロパティをサポートします。  
  
### FlowLayoutPanel コントロールで子コントロールを固定およびドッキングするには  
  
1.  フォームで <xref:System.Windows.Forms.FlowLayoutPanel> コントロールを作成します。  
  
2.  <xref:System.Windows.Forms.FlowLayoutPanel> コントロールの <xref:System.Windows.Forms.Control.Width%2A> を 300 に設定し、<xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> を <xref:System.Windows.Forms.FlowDirection> に設定します。  
  
3.  2 つの <xref:System.Windows.Forms.Button> コントロールを作成し、<xref:System.Windows.Forms.FlowLayoutPanel> コントロールに配置します。  
  
4.  最初のボタンの <xref:System.Windows.Forms.Control.Width%2A> を 200 に設定します。  
  
5.  2 番目のボタンの <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle> に設定します。  
  
    > [!NOTE]
    >  2 番目のボタンは、最初のボタンと同じ幅を前提としています。  <xref:System.Windows.Forms.FlowLayoutPanel> コントロールの幅にまたがって伸縮しません。  
  
6.  2 番目のボタンの <xref:System.Windows.Forms.Control.Dock%2A> プロパティを `[なし]` に設定します。  これにより、元の幅のボタンを前提とします。  
  
7.  2 番目のボタンの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティを `[左、右]` に設定します。  
  
    > [!IMPORTANT]
    >  2 番目のボタンは、最初のボタンと同じ幅を前提としています。  <xref:System.Windows.Forms.FlowLayoutPanel> コントロールの幅にまたがって伸縮しません。  これは、<xref:System.Windows.Forms.FlowLayoutPanel> コントロールの固定とドッキングの一般的な規則です。垂直方向のフローについては、<xref:System.Windows.Forms.FlowLayoutPanel> コントロールが、幅の最大の列の子コントロールから暗黙の列の幅を計算します。  <xref:System.Windows.Forms.Control.Anchor%2A> プロパティまたは <xref:System.Windows.Forms.Control.Dock%2A> プロパティを持つこの列のその他のすべてのコントロールが、この暗黙の列に合わせて配置または拡大されます。  この動作は、水平のフロー方向と同様の方法で機能します。  <xref:System.Windows.Forms.FlowLayoutPanel> コントロールは、行で最も高い子コントロールから、暗黙の行の高さを計算して、この行のすべてのドッキングまたは固定の子コントロールは、暗黙の行に合わせて配置またはサイズが変更されます。  
  
## 使用例  
 次の図は、<xref:System.Windows.Forms.FlowLayoutPanel> 内の青のボタンを基準とする相対位置に固定されてドッキングされる 4 つのボタンを示しています。  <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> が <xref:System.Windows.Forms.FlowDirection> です。  
  
 ![FlowLayoutPanel アンカー](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.png "NET\_FLPanchorExp")  
  
 次の図は、<xref:System.Windows.Forms.FlowLayoutPanel> 内の青のボタンを基準とする相対位置に固定されてドッキングされる 4 つのボタンを示しています。  <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> が <xref:System.Windows.Forms.FlowDirection> です。  
  
 ![FlowLayoutPanel アンカー](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.png "VS\_FLPanchor2")  
  
 次のコード例は、<xref:System.Windows.Forms.FlowLayoutPanel> コントロールの <xref:System.Windows.Forms.Button> コントロールにおける様々な <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を示します。  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからのこの例のビルドについては、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。  また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法 : 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.FlowLayoutPanel>   
 [FlowLayoutPanel コントロールの概要](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-overview.md)