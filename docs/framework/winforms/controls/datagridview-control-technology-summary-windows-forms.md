---
title: "DataGridView コントロール テクノロジの概要 (Windows フォーム) | Microsoft Docs"
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
  - "データ グリッド, データ グリッドの概要"
  - "DataGridView コントロール [Windows フォーム], DataGridView コントロールの概要"
ms.assetid: 094498c3-a126-4a3f-83fe-f69e96c7717b
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# DataGridView コントロール テクノロジの概要 (Windows フォーム)
ここでは、`DataGridView` コントロールおよびその使用をサポートしているクラスの概要について説明します。  
  
 データを表形式で表示するというタスクは頻繁に実行されます。  `DataGridView` コントロールは、データをグリッドに表示するための解決策としてデザインされたものです。  
  
## Keywords  
 DataGridView、BindingSource、テーブル、セル、データ バインディング、仮想モード  
  
## 名前空間  
 <xref:System.Windows.Forms?displayProperty=fullName>  
  
 <xref:System.Data?displayProperty=fullName>  
  
## 関連技術  
 `BindingSource`  
  
## 背景  
 ユーザー インターフェイス \(UI\) デザイナーは、表形式のデータをユーザーに表示しなければならない場面に頻繁に遭遇します。  [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] には、データをテーブルまたはグリッドに表示するための方法がいくつか用意されています。  `DataGridView` コントロールは、Windows フォーム アプリケーションで使用できるこの分野の最新機能です。  
  
 `DataGridView` コントロールでは、データ ストア内のデータの行を表示できます。  何種類のものデータ ストアがサポートされています。  データ ストアには、単純な型指定されていないデータ \(1 次元配列など\) を格納することも、型指定されたデータ \(<xref:System.Data.DataSet> など\) を格納することもできます。  詳細については、「[方法 : データを Windows フォーム DataGridView コントロールにバインドする](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)」を参照してください。  
  
 `DataGridView` コントロールには、データを表形式で表示するための強力で柔軟な機能が用意されています。  このコントロールを使用して、小さなデータ セットから非常に大きなデータ セットまでの読み取り専用ビューまたは編集可能ビューを表示できます。  
  
 `DataGridView` コントロールをさまざまな方法で拡張して、アプリケーションにカスタム動作を組み込むことができます。  たとえば、プログラムで独自の並べ替えアルゴリズムを指定したり、独自の種類のセルを作成したりできます。  `DataGridView` コントロールの外観は、いくつかのプロパティを選択することで簡単にカスタマイズできます。  `DataGridView` コントロールはさまざまな種類のデータ ストアをデータ ソースとして使用でき、また、データ ソースをバインドしていない状態でも機能します。  
  
## DataGridView クラスの実装  
 `DataGridView` コントロールの拡張機能を利用するには、いくつかの方法があります。  イベントとプロパティを通じてコントロールのさまざまな側面をカスタマイズできますが、ある種のカスタマイズを行うときには、既存の `DataGridView` クラスから派生した新しいクラスを作成する必要があります。  
  
 最もよく使用される基本クラスは `DataGridViewCell` と `DataGridViewColumn` です。  `DataGridViewCell` またはその任意の子クラスから独自のセル クラスを派生させることができます。  任意の列に任意のセル型を追加できますが、通常は、カスタム セル型のセルを既定でホストする対になる列クラスを `DataGridViewColumn` から派生させます。  
  
 派生セル クラス内で `IDataGridViewEditingCell` インターフェイスを実装すると、編集機能を備えつつ編集モードでコントロールをホストしないセル型を作成できます。  編集モードのセル内でホストできるコントロールを作成するには、<xref:System.Windows.Forms.Control> から派生したクラス内で `IDataGridViewEditingControl` インターフェイスを実装します。  
  
 詳細については、「[方法 : Windows フォーム DataGridView コントロールのセルと列を、それぞれの動作と外観を拡張してカスタマイズする](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)」および「[方法 : Windows フォーム DataGridView Cells でコントロールをホストする](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)」を参照してください。  
  
## DataGridView クラスの概要  
 <xref:System.Windows.Forms>  
  
|テクノロジの領域|クラス\/インターフェイス\/構成要素|  
|--------------|-------------------------|  
|データ バインディング|<xref:System.Windows.Forms.BindingSource>|  
|データ プレゼンテーション|<xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DataGridViewCell> と派生クラス<br /><br /> <xref:System.Windows.Forms.DataGridViewRow> と派生クラス<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> と派生クラス<br /><br /> <xref:System.Windows.Forms.DataGridViewCellStyle>|  
|<xref:System.Windows.Forms.DataGridView> 拡張機能|<xref:System.Windows.Forms.DataGridViewCell> と派生クラス<br /><br /> <xref:System.Windows.Forms.DataGridViewColumn> と派生クラス<br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingCell><br /><br /> <xref:System.Windows.Forms.IDataGridViewEditingControl>|  
  
## 新機能  
 <xref:System.Windows.Forms.DataGridView> コントロールは、Windows フォームで表形式のデータを表示するための完璧な解決策としてデザインされたものです。  新しいアプリケーションを作成しているときは、<xref:System.Windows.Forms.DataGrid> などの他の方法を探す前に、<xref:System.Windows.Forms.DataGridView> コントロールを使用することを検討してください。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールは <xref:System.Windows.Forms.BindingSource> コンポーネントと密接に組み合わせて使用されます。  このコンポーネントはフォームの主要なデータ ソースとしてデザインされたものです。  このコンポーネントは、<xref:System.Windows.Forms.DataGridView> コントロールとデータ ソースとのやり取りをデータ ソースの種類に関係なく管理します。  
  
## 参照  
 [DataGridView コントロールの概要](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)   
 [DataGridView コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)   
 [接続情報の保護](../../../../docs/framework/data/adonet/protecting-connection-information.md)