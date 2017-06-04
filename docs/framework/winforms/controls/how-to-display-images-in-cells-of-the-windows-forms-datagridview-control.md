---
title: "方法 : Windows フォーム DataGridView コントロールのセルにイメージを表示する | Microsoft Docs"
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
  - "セル, 表示 (イメージを)"
  - "データ グリッド, 表示 (セルにイメージを)"
  - "データ グリッド, 表示 (グリッドに)"
  - "DataGridView コントロール [Windows フォーム], 表示 (イメージを)"
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォーム DataGridView コントロールのセルにイメージを表示する
ピクチャまたはグラフィックは 1 行のデータに表示できる値の 1 つです。  多くの場合、これらのグラフィックスは従業員の写真や会社のロゴなどが使用されます。  
  
 データを <xref:System.Windows.Forms.DataGridView> コントロール内に表示する場合、ピクチャの取り込みは簡単です。  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Drawing.Image> クラスによってサポートされている任意のイメージ形式、および一部のデータベースで使用されている OLE ピクチャ形式をネイティブに処理します。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールのデータ ソースにイメージの列がある場合、これらは <xref:System.Windows.Forms.DataGridView> コントロールによって自動的に表示されます。  
  
 埋め込みリソースからアイコンを抽出し、ビットマップに変換してイメージ列の各セルに表示する方法を次のコード例に示します。  テキストのセルを対応するイメージで置き換える例については、「[方法 : Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 使用例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   `tree.ico` という埋め込まれたアイコン リソース。  
  
-   <xref:System?displayProperty=fullName> アセンブリ、<xref:System.Windows.Forms?displayProperty=fullName> アセンブリ、および <xref:System.Drawing?displayProperty=fullName> アセンブリへの参照。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 [Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)