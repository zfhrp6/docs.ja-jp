---
title: "ListBox のスタイルとテンプレート | Microsoft Docs"
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
  - "ControlTemplate [WPF], ListBox"
  - "ListBox [WPF], スタイルおよびテンプレート"
  - "パーツ [WPF], ListBox"
  - "状態 [WPF], ListBox"
  - "スタイル [WPF], ListBox"
  - "テンプレート [WPF], ListBox"
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# ListBox のスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.ListBox> コントロールのスタイルおよびテンプレートについて説明します。  既定の <xref:System.Windows.Controls.ControlTemplate> に変更を加えることで、コントロールに独自の外観を設定できます。  詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## ListBox のパーツ  
 <xref:System.Windows.Controls.ListBox> コントロールには、名前付きのパーツは存在しません。  
  
 <xref:System.Windows.Controls.ListBox> の <xref:System.Windows.Controls.ControlTemplate> を作成する際には、テンプレートの <xref:System.Windows.Controls.ScrollViewer> に <xref:System.Windows.Controls.ItemsPresenter> を含めることができます。  <xref:System.Windows.Controls.ItemsPresenter> により、<xref:System.Windows.Controls.ListBox> の各項目が表示されます。また、<xref:System.Windows.Controls.ScrollViewer> により、コントロール内でスクロールできるようになります。  <xref:System.Windows.Controls.ItemsPresenter> が <xref:System.Windows.Controls.ScrollViewer> の直接の子でない場合は、<xref:System.Windows.Controls.ItemsPresenter> に `ItemsPresenter` という名前を付ける必要があります。  
  
## ListBox の状態  
 次の表は、<xref:System.Windows.Controls.ListBox> コントロールの表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Valid|ValidationStates|コントロールが有効です。|  
|InvalidFocused|ValidationStates|コントロールは有効ではありませんが、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールは有効ではなく、フォーカスはありません。|  
  
## ListBoxItem のパーツ  
 <xref:System.Windows.Controls.ListBoxItem> コントロールには、名前付きのパーツは存在しません。  
  
## ListBoxItem の状態  
 次の表は、<xref:System.Windows.Controls.ListBox> コントロールの表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Normal|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されています。|  
|Disabled|CommonStates|項目が無効です。|  
|Focused|FocusStates|項目にフォーカスがあります。|  
|Unfocused|FocusStates|項目にフォーカスがありません。|  
|Unselected|SelectionStates|項目は選択されています。|  
|Selected|SelectionStates|項目は選択されていません。|  
|SelectedUnfocused|SelectionStates|項目は選択されていますが、フォーカスはありません。|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## ListBox ControlTemplate の例  
 次の例は、<xref:System.Windows.Controls.ListBox> コントロールと <xref:System.Windows.Controls.ListBoxItem> コントロールの <xref:System.Windows.Controls.ControlTemplate> を定義する方法を示しています。  
  
 [!code-xml[ControlTemplateExamples#ListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
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