---
title: "DataGrid のスタイルとテンプレート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ControlTemplate [WPF], DataGrid"
  - "DataGrid [WPF], スタイルおよびテンプレート"
  - "パーツ [WPF], DataGrid"
  - "状態 [WPF], DataGrid"
  - "スタイル [WPF], DataGrid"
  - "テンプレート [WPF], DataGrid"
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# DataGrid のスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.DataGrid> コントロールのスタイルおよびテンプレートについて説明します。  既定の <xref:System.Windows.Controls.ControlTemplate> に変更を加えることで、コントロールに独自の外観を設定できます。  詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## DataGrid のパーツ  
 次の表は、<xref:System.Windows.Controls.DataGrid> コントロールの名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|列ヘッダーが含まれる行。|  
  
 <xref:System.Windows.Controls.DataGrid> の <xref:System.Windows.Controls.ControlTemplate> を作成するときに、テンプレートの <xref:System.Windows.Controls.ScrollViewer> 内に <xref:System.Windows.Controls.ItemsPresenter> が含まれる場合があります。  <xref:System.Windows.Controls.ItemsPresenter> により、<xref:System.Windows.Controls.DataGrid> の各項目が表示されます。また、<xref:System.Windows.Controls.ScrollViewer> により、コントロール内でスクロールできるようになります。  <xref:System.Windows.Controls.ItemsPresenter> が <xref:System.Windows.Controls.ScrollViewer> の直接の子でない場合は、<xref:System.Windows.Controls.ItemsPresenter> に `ItemsPresenter` という名前を付ける必要があります。  
  
 <xref:System.Windows.Controls.DataGrid> の既定のテンプレートには、<xref:System.Windows.Controls.ScrollViewer> コントロールが含まれています。  <xref:System.Windows.Controls.ScrollViewer> で定義されたパーツの詳細については、「[ScrollViewer のスタイルとテンプレート](../../../../docs/framework/wpf/controls/scrollviewer-styles-and-templates.md)」を参照してください。  
  
## DataGrid の状態  
 次の表は、<xref:System.Windows.Controls.DataGrid> コントロールの表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Normal|CommonStates|既定の状態です。|  
|Disabled|CommonStates|コントロールが無効になっています。|  
|InvalidFocused|ValidationStates|コントロールは有効ではありませんが、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールは有効ではなく、フォーカスはありません。|  
|Valid|ValidationStates|コントロールが有効です。|  
  
## DataGridCell のパーツ  
 <xref:System.Windows.Controls.DataGridCell> 要素には、名前付きのパーツは存在しません。  
  
## DataGridCell の状態  
 次の表は、<xref:System.Windows.Controls.DataGridCell> 要素の表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Normal|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターは、セルの上に置かれています。|  
|Focused|FocusStates|セルにフォーカスがあります。|  
|Unfocused|FocusStates|セルにフォーカスがありません。|  
|Current|CurrentStates|セルは現在のセルです。|  
|Regular|CurrentStates|セルは現在のセルではありません。|  
|表示|InteractionStates|セルは表示モードです。|  
|編集|InteractionStates|セルは編集モードです。|  
|Selected|SelectionStates|セルが選択されています。|  
|Unselected|SelectionStates|セルは選択されていません。|  
|InvalidFocused|ValidationStates|セルは有効ではありませんが、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|セルは有効ではなく、フォーカスはありません。|  
|Valid|ValidationStates|セルは有効です。|  
  
## DataGridRow のパーツ  
 <xref:System.Windows.Controls.DataGridRow> 要素には、名前付きのパーツは存在しません。  
  
## DataGridRow の状態  
 次の表は、<xref:System.Windows.Controls.DataGridRow> 要素の表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Normal|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターは、行の上に置かれています。|  
|MouseOver\_Editing|CommonStates|マウス ポインターは行の上に置かれ、行は編集モードです。|  
|MouseOver\_Selected|CommonStates|マウス ポインターは行の上に置かれ、行が選択されています。|  
|MouseOver\_Unfocused\_Editing|CommonStates|マウス ポインターは行の上に置かれ、行は編集モードで、フォーカスはありません。|  
|MouseOver\_Unfocused\_Selected|CommonStates|マウス ポインターは行の上に置かれ、行が選択され、フォーカスはありません。|  
|Normal\_AlternatingRow|CommonStates|行は交互の行です。|  
|Normal\_Editing|CommonStates|行は編集モードです。|  
|Normal\_Selected|CommonStates|行が選択されています。|  
|Unfocused\_Editing|CommonStates|行は編集モードで、フォーカスはありません。|  
|Unfocused\_Selected|CommonStates|行が選択され、フォーカスはありません。|  
|InvalidFocused|ValidationStates|コントロールは有効ではありませんが、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールは有効ではなく、フォーカスはありません。|  
|Valid|ValidationStates|コントロールが有効です。|  
  
## DataGridRowHeader のパーツ  
 次の表は、<xref:System.Windows.Controls.Primitives.DataGridRowHeader> 要素の名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|行ヘッダーのサイズを上端から変更する場合に使用する要素です。|  
|PART\_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|行ヘッダーのサイズを下端から変更する場合に使用する要素です。|  
  
## DataGridRowHeader の状態  
 次の表は、<xref:System.Windows.Controls.Primitives.DataGridRowHeader> 要素の表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Normal|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターは、行の上に置かれています。|  
|MouseOver\_CurrentRow|CommonStates|マウス ポインターは行の上に置かれ、行は現在の行です。|  
|MouseOver\_CurrentRow\_Selected|CommonStates|マウス ポインターは行の上に置かれ、行は現在の行で、選択されています。|  
|MouseOver\_EditingRow|CommonStates|マウス ポインターは行の上に置かれ、行は編集モードです。|  
|MouseOver\_Selected|CommonStates|マウス ポインターは行の上に置かれ、行が選択されています。|  
|MouseOver\_Unfocused\_CurrentRow\_Selected|CommonStates|マウス ポインターは行の上に置かれ、行は現在の行で、選択され、フォーカスはありません。|  
|MouseOver\_Unfocused\_EditingRow|CommonStates|マウス ポインターは行の上に置かれ、行は編集モードで、フォーカスはありません。|  
|MouseOver\_Unfocused\_Selected|CommonStates|マウス ポインターは行の上に置かれ、行が選択され、フォーカスはありません。|  
|Normal\_CurrentRow|CommonStates|行は現在の行です。|  
|Normal\_CurrentRow\_Selected|CommonStates|行は現在の行で、選択されています。|  
|Normal\_EditingRow|CommonStates|行は編集モードです。|  
|Normal\_Selected|CommonStates|行が選択されています。|  
|Unfocused\_CurrentRow\_Selected|CommonStates|行は現在の行で、選択され、フォーカスはありません。|  
|Unfocused\_EditingRow|CommonStates|行は編集モードで、フォーカスはありません。|  
|Unfocused\_Selected|CommonStates|行が選択され、フォーカスはありません。|  
|InvalidFocused|ValidationStates|コントロールは有効ではありませんが、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールは有効ではなく、フォーカスはありません。|  
|Valid|ValidationStates|コントロールが有効です。|  
  
## DataGridColumnHeadersPresenter のパーツ  
 次の表は、<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> 要素の名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|列ヘッダーのプレースホルダーです。|  
  
## DataGridColumnHeadersPresenter の状態  
 次の表は、<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter> 要素の表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|InvalidFocused|ValidationStates|セルは有効ではありませんが、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|セルは有効ではなく、フォーカスはありません。|  
|Valid|ValidationStates|セルは有効です。|  
  
## DataGridColumnHeader のパーツ  
 次の表は、<xref:System.Windows.Controls.Primitives.DataGridColumnHeader> 要素の名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|列ヘッダーのサイズを左端から変更する場合に使用する要素です。|  
|PART\_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|列ヘッダーのサイズを右端から変更する場合に使用する要素です。|  
  
## DataGridColumnHeader の状態  
 次の表は、<xref:System.Windows.Controls.Primitives.DataGridColumnHeader> 要素の表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Normal|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されています。|  
|Pressed|CommonStates|コントロールが押されています。|  
|SortAscending|SortStates|列は昇順に並べ替えられます。|  
|SortDescending|SortStates|列は降順に並べ替えられます。|  
|Unsorted|SortStates|列は並べ替えられません。|  
|InvalidFocused|ValidationStates|コントロールは有効ではありませんが、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールは有効ではなく、フォーカスはありません。|  
|Valid|ValidationStates|コントロールが有効です。|  
  
## DataGrid ControlTemplate の例  
 <xref:System.Windows.Controls.DataGrid> コントロールの <xref:System.Windows.Controls.ControlTemplate> およびその関連付けられた型を定義する方法を次の例に示します。  
  
 [!code-xml[ControlTemplateExamples#DataGrid](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
 前の例では、次の 1 つ以上のリソースを使用しています。  
  
 [!code-xml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 サンプル全体については、「[ControlTemplate を使用したスタイル設定のサンプル](http://go.microsoft.com/fwlink/?LinkID=160041)」を参照してください。.  
  
## 参照  
 <xref:System.Windows.FrameworkElement.Style%2A>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [コントロールのスタイルとテンプレート](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)   
 [コントロールのカスタマイズ](../../../../docs/framework/wpf/controls/control-customization.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)