---
title: "DataGridView コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "DataGridView"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "バインド コントロール, DataGridView コントロール"
  - "列 [Windows フォーム], DataGridView コントロール"
  - "データ [Windows フォーム], 移動"
  - "データ [Windows フォーム], 並べ替え"
  - "データ バインディング, DataGridView コントロール"
  - "データ グリッド, データ グリッドの概要"
  - "データ ソース, バインド (DataGridView コントロールに)"
  - "DataGridView コントロール [Windows フォーム], DataGridView コントロールの概要"
  - "DataGridView コントロール [Windows フォーム], データ バインディング"
  - "データセット [Windows フォーム], バインド (DataGridView コントロールに)"
  - "グリッド コントロール [Windows フォーム]"
  - "グリッド [Windows フォーム]"
  - "テーブル [Windows フォーム], バインド (DataGridView コントロールに)"
  - "テーブル [Windows フォーム], 表示 (DataGridView コントロール内に)"
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# DataGridView コントロールの概要 (Windows フォーム)
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールを使用すると、さまざまな種類のデータ ソースのデータを表形式で表示したり編集したりできます。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールにデータをバインディングする方法は簡単で直感的であり、多くの場合は、<xref:System.Windows.Forms.DataGridView.DataSource%2A> プロパティを設定するのと同じくらい簡単です。  複数のリストまたはテーブルを含んでいるデータ ソースにバインドするときは、<xref:System.Windows.Forms.DataGridView.DataMember%2A> プロパティに、バインド先のリストまたはテーブルを表す文字列を設定します。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールは Windows フォームの標準データ バインディング モデルをサポートしているので、次の一覧に示すクラスのインスタンスにバインドできます。  
  
-   <xref:System.Collections.IList> インターフェイスを実装しているクラス \(1 次元配列も含む\)  
  
-   <xref:System.ComponentModel.IListSource> インターフェイスを実装しているクラス \(<xref:System.Data.DataTable> クラスや <xref:System.Data.DataSet> クラスなど\)  
  
-   <xref:System.ComponentModel.IBindingList> インターフェイスを実装しているクラス \(<xref:System.ComponentModel.BindingList%601> クラスなど\)  
  
-   <xref:System.ComponentModel.IBindingListView> インターフェイスを実装しているクラス \(<xref:System.Windows.Forms.BindingSource> クラスなど\)  
  
 <xref:System.Windows.Forms.DataGridView> コントロールは、これらのインターフェイスによって返されるオブジェクトのパブリック プロパティへのデータ バインディングをサポートしており、返されるオブジェクトが <xref:System.ComponentModel.ICustomTypeDescriptor> インターフェイスを実装している場合は、このインターフェイスによって返されるプロパティ コレクションへのデータ バインディングもサポートします。  
  
 通常は、<xref:System.Windows.Forms.BindingSource> コンポーネントにバインドし、その <xref:System.Windows.Forms.BindingSource> コンポーネントを別のデータ ソースにバインドするか、ビジネス オブジェクトを使用してこのコンポーネントにデータを設定します。  データ ソースとしては <xref:System.Windows.Forms.BindingSource> コンポーネントを使用することをお勧めします。このコンポーネントはさまざまな種類のデータ ソースにバインドでき、データ バインディングに関する多くの問題を自動的に解決できるからです。  詳細については、「[BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールは、関連付けられたデータ ストアを持たない*非バインド* モードでも使用できます。  バインドされていない <xref:System.Windows.Forms.DataGridView> コントロールを使用するコード例については、「[チュートリアル : バインドされていない Windows フォーム DataGridView コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールは柔軟な設定ができ、拡張性に優れています。また、外観と動作をカスタマイズするためのさまざまなプロパティ、メソッド、およびイベントを備えています。  Windows フォーム アプリケーションで表形式のデータを表示するときには、他の <xref:System.Windows.Forms.DataGrid> などのコントロールを使用する前に、まず <xref:System.Windows.Forms.DataGridView> コントロールを検討してください。  小さなグリッドや読み取り専用の値を表示する場合、または数百万件のレコードを含むテーブルをユーザーが編集できるようにする場合は、<xref:System.Windows.Forms.DataGridView> コントロールを使用すると、プログラミング可能でメモリ効率の良い解決策を実現できます。  
  
## このセクションの内容  
 [DataGridView コントロール テクノロジの概要](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 <xref:System.Windows.Forms.DataGridView> コントロールの概念と関連クラスの使い方についての概要を示します。  
  
 [DataGridView コントロールのアーキテクチャ](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 <xref:System.Windows.Forms.DataGridView> コントロールのアーキテクチャを示し、型階層と継承構造について説明します。  
  
 [DataGridView コントロールのシナリオ](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 <xref:System.Windows.Forms.DataGridView> コントロールが使用される最も一般的なシナリオについて説明します。  
  
 [DataGridView コントロールのコード ディレクトリ](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 <xref:System.Windows.Forms.DataGridView> を使用したさまざまなタスクのコード例へのリンクを示します。  コード例はタスクの種類ごとに分類されています。  
  
## 関連項目  
 [Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 Windows フォーム <xref:System.Windows.Forms.DataGridView> コントロール内で、情報を表示するため、およびユーザーが情報を追加または修正するために使う列の種類について説明します。  
  
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 コントロールの内容を手動で作成する方法と、外部データ ソースから取得する方法についてのトピックを示します。  
  
 [Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <xref:System.Windows.Forms.DataGridView> のセルと行を独自に描画する方法と、セル、列、行の派生型を作成する方法についてのトピックを示します。  
  
 [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 大量のデータを扱うときのパフォーマンスの問題を避けるために、このコントロールを効率的に使用する方法についてのトピックを示します。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.BindingSource>   
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [Windows フォーム DataGridView コントロールの既定の機能](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールの既定のキーボード処理とマウス処理](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)