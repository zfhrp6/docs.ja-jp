---
title: "方法 : TableLayoutPanel コントロールで子コントロールを固定およびドッキングする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "子コントロール, 固定およびドッキング"
  - "コントロール [Windows フォーム], 子"
  - "レイアウト [Windows フォーム], 子コントロール"
  - "TableLayoutPanel コントロール [Windows フォーム], 子コントロール"
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : TableLayoutPanel コントロールで子コントロールを固定およびドッキングする
<xref:System.Windows.Forms.TableLayoutPanel> コントロールは、子コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティと <xref:System.Windows.Forms.Control.Dock%2A> プロパティをサポートします。  
  
### TableLayoutPanel のセル内の子コントロールを揃えるには  
  
1.  フォームで <xref:System.Windows.Forms.TableLayoutPanel> コントロールを作成します。  
  
2.  <xref:System.Windows.Forms.TableLayoutPanel> コントロールの <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> プロパティと <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> プロパティの値を 1 に設定します。  
  
3.  <xref:System.Windows.Forms.TableLayoutPanel> コントロールで <xref:System.Windows.Forms.Button> コントロールを作成します。  <xref:System.Windows.Forms.Button> がセルの左上隅を占有します。  
  
4.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Left` に変更します。  <xref:System.Windows.Forms.Button> コントロールが、セルの左罫線に合うように移動します。  
  
    > [!NOTE]
    >  この動作は、他のコンテナー コントロールの動作と異なります。  他のコンテナー コントロールでは、<xref:System.Windows.Forms.Control.Anchor%2A> プロパティが設定されてと子コントロールは移動せず、固定されたコントロールと親コンテナーの境界間の距離は、<xref:System.Windows.Forms.Control.Anchor%2A> プロパティが設定されたときに固定されます。  
  
5.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Top, Left` に変更します。  <xref:System.Windows.Forms.Button> コントロールがセルの左上隅を占有するよう移動します。  
  
6.  `Top, Right` の値を指定して手順 5 を繰り返し、<xref:System.Windows.Forms.Button> コントロールをセルの右上隅に移動します。  `Bottom, Left` と `Bottom, Right` の値を指定して繰り返します。  
  
### TableLayoutPanel セル内の子コントロールを拡大するには  
  
1.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Left, Right` に変更します。  <xref:System.Windows.Forms.Button> コントロールがサイズ変更され、セルいっぱいに拡大されます。  
  
    > [!NOTE]
    >  この動作は、他のコンテナー コントロールの動作と異なります。  他のコンテナー コントロールでは、<xref:System.Windows.Forms.Control.Anchor%2A> プロパティが `Left, Right` または `Top, Bottom` に設定された場合、子コントロールはサイズ変更されません。  
  
2.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Top, Bottom` に変更します。  <xref:System.Windows.Forms.Button> コントロールがサイズ変更され、セルの上から下まで拡大されます。  
  
3.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Top, Bottom, Left, Right` に変更します。  <xref:System.Windows.Forms.Button> コントロールがセルを満たすようサイズ変更されます。  
  
4.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `None` に変更します。  <xref:System.Windows.Forms.Button> コントロールがサイズ変更され、セルの中央に配置されます。  
  
5.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle> に変更します。  <xref:System.Windows.Forms.Button> コントロールが、セルの左罫線に合うように移動します。  <xref:System.Windows.Forms.Button> コントロールの幅は保持されますが、高さはセルを垂直方向に満たすようサイズ変更されます。  
  
    > [!NOTE]
    >  これは、他のコンテナー コントロール内で発生するのと同じ動作です。  
  
6.  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle> に変更します。  <xref:System.Windows.Forms.Button> コントロールがセルを満たすようサイズ変更されます。  
  
## 使用例  
 次の図は、5 つの個別の <xref:System.Windows.Forms.TableLayoutPanel> のセルに固定されている 5 つのボタンを示しています。  
  
 ![TableLayoutPanel アンカー](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.png "VS\_TLPanchor")  
  
 次の図は、4 つの個別の <xref:System.Windows.Forms.TableLayoutPanel> のセルの隅に固定されている 4 つのボタンを示しています。  
  
 ![TableLayoutPanel アンカー](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.png "VS\_TLPanchor2")  
  
 次の図は、3 つの個別の <xref:System.Windows.Forms.TableLayoutPanel> のセルに固定することで拡大された 3 つのボタンを示しています。  
  
 ![TableLayoutPanel アンカー](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS\_TLPAnchor3")  
  
 次のコード例は、<xref:System.Windows.Forms.TableLayoutPanel> コントロールの <xref:System.Windows.Forms.Button> コントロールにおけるすべての組み合わせの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を示します。  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、および System.Windows.Forms アセンブリへの参照。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからのこの例のビルドについては、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。  コードを新しいプロジェクトに貼り付けることで、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法 : 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.TableLayoutPanel>   
 [TableLayoutPanel コントロール](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)