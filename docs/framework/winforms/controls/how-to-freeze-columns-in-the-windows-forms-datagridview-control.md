---
title: "方法 : Windows フォーム DataGridView コントロールの列を固定する | Microsoft Docs"
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
  - "列 [Windows フォーム], 固定"
  - "DataGridView コントロール [Windows フォーム], 列 (常に表示される)"
  - "DataGridView コントロール [Windows フォーム], 固定 (列を)"
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : Windows フォーム DataGridView コントロールの列を固定する
ユーザーが Windows フォームの <xref:System.Windows.Forms.DataGridView> コントロールに表示されるデータを確認するときに、1 つの列または列のセットを頻繁に参照しなければならないことがあります。  たとえば、多数の列を含む顧客情報のテーブルを表示するとき、顧客名を常に表示して、その他の列は表示領域外にスクロールするようにできると便利です。  
  
 この動作を実現するために、コントロールの列を固定することができます。  列を固定すると、左側 \(右から左へ記述する言語のスクリプトでは右側\) のすべての列も同様に固定されます。  固定された列は表示されたままになり、その他のすべての列はスクロールできます。  
  
> [!NOTE]
>  列の並べ替えが有効な場合、固定された列は、固定されていない列とは異なるグループとして扱われます。  ユーザーは、どちらかのグループに列を再配置できますが、1 つのグループから別のグループに列を移動することはできません。  
  
 列の <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> プロパティは、列が常にグリッド内で表示されるかどうかを決定します。  
  
 Visual Studio では、このタスクに対するサポートが用意されています。  「[方法 : デザイナーを使用して Windows フォーム DataGridView コントロールの列を固定する](http://msdn.microsoft.com/library/717ss6s6\(v=vs.110\))」も参照してください。  
  
### プログラムで列を固定するには  
  
-   <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=fullName> プロパティを `true` に設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `AddToCartButton` という名前の列を含む `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System?displayProperty=fullName> アセンブリおよび <xref:System.Windows.Forms?displayProperty=fullName> アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView>   
 [Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールの列の並べ替えを有効にする](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)