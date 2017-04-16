---
title: "ListView のスタイルとテンプレート | Microsoft Docs"
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
  - "ControlTemplate [WPF], ListView"
  - "ListView [WPF], スタイルおよびテンプレート"
  - "パーツ [WPF], ListView"
  - "状態 [WPF], ListView"
  - "スタイル [WPF], ListView"
  - "テンプレート [WPF], ListView"
ms.assetid: d2387356-2171-4785-822a-7247e024b4ee
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# ListView のスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.ListView> コントロールのスタイルおよびテンプレートについて説明します。  既定の <xref:System.Windows.Controls.ControlTemplate> に変更を加えることで、コントロールに独自の外観を設定できます。  詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## ListView のパーツ  
 <xref:System.Windows.Controls.ListView> コントロールには、名前付きのパーツは存在しません。  
  
 <xref:System.Windows.Controls.ListView> の <xref:System.Windows.Controls.ControlTemplate> を作成するときに、テンプレートの <xref:System.Windows.Controls.ScrollViewer> 内に <xref:System.Windows.Controls.ItemsPresenter> が含まれる場合があります。  <xref:System.Windows.Controls.ItemsPresenter> により、<xref:System.Windows.Controls.ListView> の各項目が表示されます。また、<xref:System.Windows.Controls.ScrollViewer> により、コントロール内でスクロールできるようになります。  <xref:System.Windows.Controls.ItemsPresenter> が <xref:System.Windows.Controls.ScrollViewer> の直接の子でない場合は、<xref:System.Windows.Controls.ItemsPresenter> に `ItemsPresenter` という名前を付ける必要があります。  
  
## ListView の状態  
 次の表は、<xref:System.Windows.Controls.ListView> コントロールの表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## ListViewItem のパーツ  
 <xref:System.Windows.Controls.ListViewItem> コントロールには、名前付きのパーツは存在しません。  
  
## ListViewItem の状態  
 次の表は、<xref:System.Windows.Controls.ListViewItem> コントロールの状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Normal|CommonStates|既定の状態です。|  
|Disabled|CommonStates|コントロールが無効になっています。|  
|MouseOver|CommonStates|<xref:System.Windows.Controls.ComboBox> コントロール上にマウス ポインターがあります。|  
|Focused|FocusStates|コントロールにフォーカスがあります。|  
|Unfocused|FocusStates|コントロールにフォーカスがありません。|  
|Selected|SelectionStates|項目は選択されています。|  
|Unselected|SelectionStates|項目は選択されていません。|  
|SelectedUnfocused|SelectionStates|項目は選択されていますが、フォーカスはありません。|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## ListView ControlTemplate の例  
 <xref:System.Windows.Controls.ListView> コントロールの <xref:System.Windows.Controls.ControlTemplate> およびその関連付けられた型を定義する方法を次の例に示します。  
  
 [!code-xml[ControlTemplateExamples#ListView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listview.xaml#listview)]  
  
 <xref:System.Windows.Controls.ControlTemplate> の例では、次のリソースを 1 つ以上使用します。  
  
 [!code-xml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 サンプル全体については、[ControlTemplate を使用したスタイル設定のサンプル](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。  
  
## 参照  
 <xref:System.Windows.FrameworkElement.Style%2A>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [コントロールのスタイルとテンプレート](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)   
 [コントロールのカスタマイズ](../../../../docs/framework/wpf/controls/control-customization.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)