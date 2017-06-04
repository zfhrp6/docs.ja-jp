---
title: "Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて | Microsoft Docs"
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
  - "データ グリッド"
  - "DataGrid コントロール [Windows フォーム], DataGridView コントロールとの比較"
  - "DataGridView コントロール [Windows フォーム], DataGrid コントロールとの比較"
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて
<xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わる新しいコントロールです。  <xref:System.Windows.Forms.DataGridView> コントロールには、<xref:System.Windows.Forms.DataGrid> コントロールにはない、さまざまな基本機能と高度な機能が用意されています。  さらに、<xref:System.Windows.Forms.DataGridView> コントロールのアーキテクチャにより、<xref:System.Windows.Forms.DataGrid> コントロールよりも簡単に拡張やカスタマイズが行うことができます。  
  
 <xref:System.Windows.Forms.DataGrid> コントロールにはない、<xref:System.Windows.Forms.DataGridView> コントロールの主要な機能のいくつかを次の表に示します。  
  
|DataGridView コントロールの機能|Description|  
|----------------------------|-----------------|  
|複数の列型|<xref:System.Windows.Forms.DataGridView> コントロールには、<xref:System.Windows.Forms.DataGrid> コントロールよりも多くの組み込みの列型が用意されています。  これらの列型は、ほとんどの一般的なシナリオのニーズに適合しますが、<xref:System.Windows.Forms.DataGrid> コントロールの列型よりも拡張や置き換えが簡単です。  詳細については、「[Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)」を参照してください。|  
|複数の方法によるデータ表示|<xref:System.Windows.Forms.DataGrid> コントロールでは、外部データ ソースのデータしか表示できません。  それに対して、<xref:System.Windows.Forms.DataGridView> コントロールは、コントロールに保存されている非バインド データ、バインド データ ソースのデータ、またはバインド データと非バインド データを合わせて表示できます。  また、<xref:System.Windows.Forms.DataGridView> コントロールに仮想モードを実装して、カスタム データ管理を実現することもできます。  詳細については、「[Windows フォーム DataGridView コントロールでのデータ表示モード](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)」を参照してください。|  
|複数の方法によるデータ表示のカスタマイズ|<xref:System.Windows.Forms.DataGridView> コントロールには多くのプロパティとイベントが用意されていて、データの書式設定と表示方法を指定できます。  たとえば、セル、行、および列の外観をそれぞれに含まれるデータに応じて変更したり、あるデータ型のデータを別の型の等価のデータに置き換えたりできます。  詳細については、「[Windows フォーム DataGridView コントロールでのデータの書式設定](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)」を参照してください。|  
|セル、行、列、およびヘッダーの外観と動作を変更する複数のオプション|<xref:System.Windows.Forms.DataGridView> コントロールでは、個々のグリッド コンポーネントを多彩な方法で操作できます。  たとえば、行と列を固定してスクロールできないようにしたり、行、列、およびヘッダーを非表示にしたりできます。また、行、列、およびヘッダーのサイズの調整方法を変更したり、ユーザーが選択する方法を変更したりできます。さらに、個々のセル、行、および列にツールヒントとショートカット メニューを提供したりできます。|  
  
 <xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性と特殊なニーズに対応するために保持されますが、  ほぼすべての用途で、<xref:System.Windows.Forms.DataGridView> コントロールを使用する必要があります。  <xref:System.Windows.Forms.DataGrid> で利用できても、<xref:System.Windows.Forms.DataGridView> コントロールでは利用できない唯一の機能は、関連する 2 つのテーブルの情報を 1 つのコントロールに階層表示する機能です。  マスター\/詳細リレーションシップになっている 2 つのテーブルの情報を表示するには、<xref:System.Windows.Forms.DataGridView> コントロールを 2 つ使用する必要があります。  
  
## DataGridView コントロールへのアップグレード  
 簡単なデータ バインド シナリオで <xref:System.Windows.Forms.DataGrid> コントロールをカスタマイズせずに使用する既存のアプリケーションがある場合は、以前のコントロールを新しいコントロールに置き換えることができます。  これらのコントロールは共に Windows フォーム データ バインディング アーキテクチャを使用しているため、<xref:System.Windows.Forms.DataGridView> は、追加構成の必要なしにバインド データを表示します。  ただし、データを <xref:System.Windows.Forms.BindingSource> コンポーネントにバインドし、このコンポーネントを <xref:System.Windows.Forms.DataGridView> コントロールにバインドすると、向上したデータ バインディング機能を利用することもできます。  詳細については、「[BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)」を参照してください。  
  
 <xref:System.Windows.Forms.DataGridView> コントロールはまったく新しいアーキテクチャを採用しているため、<xref:System.Windows.Forms.DataGridView> コントロールで <xref:System.Windows.Forms.DataGrid> のカスタマイズされた機能を使用できるようにする簡単な変換パスはありません。  しかし、<xref:System.Windows.Forms.DataGridView> コントロールには組み込みの機能が用意されているため、<xref:System.Windows.Forms.DataGrid> でカスタマイズされた機能の多くは必要ありません。  <xref:System.Windows.Forms.DataGrid> コントロール用に作成したカスタム列型を <xref:System.Windows.Forms.DataGridView> コントロールで使用する場合は、新しいアーキテクチャでそれらを再実装する必要があります。  詳細については、「[Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGrid>   
 <xref:System.Windows.Forms.BindingSource>   
 [DataGridView コントロール](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)   
 [DataGrid コントロール](../../../../docs/framework/winforms/controls/datagrid-control-windows-forms.md)   
 [BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [Windows フォーム DataGridView コントロールの列型](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのデータ表示モード](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールでのデータの書式設定](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールのサイズ変更オプション](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロール内の列の並べ替えモード](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールの選択モード](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)   
 [Windows フォーム DataGridView コントロールのカスタマイズ](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)