---
title: "TreeView のスタイルとテンプレート | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ControlTemplate [WPF], TreeView"
  - "パーツ [WPF], TreeView"
  - "状態 [WPF], TreeView"
  - "スタイル [WPF], TreeView"
  - "テンプレート [WPF], TreeView"
  - "TreeView [WPF], スタイルおよびテンプレート"
ms.assetid: a49adb77-0202-4caa-b94a-8bb110d7fa9a
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# TreeView のスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.TreeView> コントロールのスタイルおよびテンプレートについて説明します。  既定の <xref:System.Windows.Controls.ControlTemplate> に変更を加えることで、コントロールに独自の外観を設定できます。  詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## TreeView のパーツ  
 <xref:System.Windows.Controls.TreeView> コントロールには、名前付きのパーツは存在しません。  
  
 <xref:System.Windows.Controls.TreeView> の <xref:System.Windows.Controls.ControlTemplate> を作成するときに、テンプレートの <xref:System.Windows.Controls.ScrollViewer> 内に <xref:System.Windows.Controls.ItemsPresenter> が含まれる場合があります。  <xref:System.Windows.Controls.ItemsPresenter> により、<xref:System.Windows.Controls.TreeView> の各項目が表示されます。また、<xref:System.Windows.Controls.ScrollViewer> により、コントロール内でスクロールできるようになります。  <xref:System.Windows.Controls.ItemsPresenter> が <xref:System.Windows.Controls.ScrollViewer> の直接の子でない場合は、<xref:System.Windows.Controls.ItemsPresenter> に `ItemsPresenter` という名前を付ける必要があります。  
  
## TreeView の状態  
 次の表は、<xref:System.Windows.Controls.TreeView> コントロールの表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## TreeViewItem のパーツ  
 次の表は、<xref:System.Windows.Controls.TreeViewItem> コントロールの名前付きパーツの一覧です。  
  
|指定項目|種類|Description|  
|----------|--------|-----------------|  
|PART\_Header|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.Controls.TreeView> コントロールのヘッダーの内容を格納しているビジュアル要素です。|  
  
## TreeViewItem の状態  
 次の表は、<xref:System.Windows.Controls.TreeViewItem> コントロールの表示状態の一覧です。  
  
|VisualState 名|VisualStateGroup 名|Description|  
|-------------------|------------------------|-----------------|  
|Normal|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターは、<xref:System.Windows.Controls.TreeViewItem> の上に置かれています。|  
|Disabled|CommonStates|<xref:System.Windows.Controls.TreeViewItem> が無効になっています。|  
|Focused|FocusStates|<xref:System.Windows.Controls.TreeViewItem> にフォーカスがあります。|  
|Unfocused|FocusStates|<xref:System.Windows.Controls.TreeViewItem> にフォーカスがありません。|  
|Expanded|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> コントロールが展開されています。|  
|Collapsed|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem> コントロールが折りたたまれています。|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> に項目が含まれています。|  
|NoItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem> に項目が含まれていません。|  
|Selected|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> が選択されています。|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> が選択されていますが、アクティブではありません。|  
|Unselected|SelectionStates|<xref:System.Windows.Controls.TreeViewItem> が選択されていません。|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## TreeView ControlTemplate の例  
 <xref:System.Windows.Controls.TreeView> コントロールの <xref:System.Windows.Controls.ControlTemplate> およびその関連付けられた型を定義する方法を次の例に示します。  
  
 [!code-xml[ControlTemplateExamples#TreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
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