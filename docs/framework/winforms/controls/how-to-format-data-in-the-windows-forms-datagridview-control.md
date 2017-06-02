---
title: "方法 : Windows フォーム DataGridView コントロールのデータの書式を設定する | Microsoft Docs"
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
  - "セル, テキストの配置"
  - "通貨値, 書式設定 (データ グリッド内で)"
  - "データ [Windows フォーム], 書式設定 (DataGridView コントロール内の)"
  - "データ グリッド, 通貨値"
  - "データ グリッド, 日付値"
  - "データ グリッド, 有効化 (ワード ラップを)"
  - "データ グリッド, 書式設定 (データを)"
  - "データ グリッド, テキストの配置"
  - "DataGridView コントロール [Windows フォーム], 書式設定 (データを)"
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : Windows フォーム DataGridView コントロールのデータの書式を設定する
<xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> プロパティを使用した、セル値の基本的な書式設定手順と、コントロール内の特定の列の基本的な書式設定手順を以下に示します。  高度なデータ書式設定については、「[方法 : Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
### 通貨値と日付値の書式を設定するには  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> プロパティを設定します。  列の <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> プロパティを使用して、特定の列の書式を設定するコード例を次に示します。   `UnitPrice`  列の値は、現在のカルチャ固有の通貨書式で表示され、負の値はかっこで囲まれます。   `ShipDate`  列の値は、現在のカルチャ固有の短い日付形式で表示されます。  <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> 値の詳細については、「[型の書式設定](../../../../docs/standard/base-types/formatting-types.md)」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### null データベース値の表示をカスタマイズするには  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> プロパティを設定します。  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> プロパティを使用して、<xref:System.DBNull.Value?displayProperty=fullName> に等しい値を含むすべてのセルに "no entry" と表示するコード例を次に示します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### テキスト ベースのセルでワードラップを有効にするには  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> プロパティに <xref:System.Windows.Forms.DataGridViewTriState> 列挙値のいずれかを設定します。  <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName> プロパティを使用して、コントロール全体にラップ モードを設定するコード例を次に示します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### DataGridView セルのテキスト配置を指定するには  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle> の <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> プロパティに <xref:System.Windows.Forms.DataGridViewContentAlignment> 列挙値のいずれかを設定します。  列の <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> プロパティを使用して、特定の列に配置方法を設定するコード例を次に示します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## 使用例  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## コードのコンパイル  
 これらの例では、次の項目が必要です。  
  
-   `UnitPrice`、`ShipDate`、`CustomerName` という 3 つの列を含む、`dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
-   <xref:System?displayProperty=fullName> アセンブリ、<xref:System.Drawing?displayProperty=fullName> アセンブリ、および <xref:System.Windows.Forms?displayProperty=fullName> アセンブリへの参照。  
  
## 信頼性の高いプログラミング  
 最大のスケーラビリティを引き出すには、同じスタイルを使用している複数の行、列、またはセル間で <xref:System.Windows.Forms.DataGridViewCellStyle> オブジェクトを共有し、各要素に個別のスタイル プロパティを設定しないようにする必要があります。  詳細については、「[Windows フォーム DataGridView コントロールを拡張するための推奨される手順](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewCellStyle>   
 [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのデータの書式設定](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)   
 [方法 : Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)   
 [型の書式設定](../../../../docs/standard/base-types/formatting-types.md)