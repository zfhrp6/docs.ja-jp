---
title: "ToolBar のスタイルとテンプレート | Microsoft Docs"
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
  - "ControlTemplate [WPF], ToolBar"
  - "パーツ [WPF], ToolBar"
  - "状態 [WPF], ToolBar"
  - "スタイル [WPF], ToolBar"
  - "テンプレート [WPF], ToolBar"
  - "ToolBar [WPF], スタイルおよびテンプレート"
ms.assetid: bd875f46-4690-46f5-81e0-f11a9822484f
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# ToolBar のスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.ToolBar> コントロールのスタイルおよびテンプレートについて説明します。  既定の <xref:System.Windows.Controls.ControlTemplate> に変更を加えることで、コントロールに独自の外観を設定できます。  詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## ToolBar のパーツ  
 次の表は、<xref:System.Windows.Controls.ToolBar> コントロールの名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_ToolBarPanel|<xref:System.Windows.Controls.Primitives.ToolBarPanel>|<xref:System.Windows.Controls.ToolBar> のコントロールを格納しているオブジェクトです。|  
|PART\_ToolBarOverflowPanel|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|<xref:System.Windows.Controls.ToolBar> のオーバーフロー領域にあるコントロールを格納するオブジェクトです。|  
  
 <xref:System.Windows.Controls.ToolBar> の <xref:System.Windows.Controls.ControlTemplate> を作成するときに、テンプレートの <xref:System.Windows.Controls.ScrollViewer> 内に <xref:System.Windows.Controls.ItemsPresenter> が含まれる場合があります。  <xref:System.Windows.Controls.ItemsPresenter> により、<xref:System.Windows.Controls.ToolBar> の各項目が表示されます。また、<xref:System.Windows.Controls.ScrollViewer> により、コントロール内でスクロールできるようになります。  <xref:System.Windows.Controls.ItemsPresenter> が <xref:System.Windows.Controls.ScrollViewer> の直接の子でない場合は、<xref:System.Windows.Controls.ItemsPresenter> に `ItemsPresenter` という名前を付ける必要があります。  
  
## ToolBar の状態  
 次の表は、<xref:System.Windows.Controls.ToolBar> コントロールの表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## ToolBar ControlTemplate の例  
 次の例は、<xref:System.Windows.Controls.ToolBar> コントロールの <xref:System.Windows.Controls.ControlTemplate> を定義する方法を示しています。  
  
 [!code-xml[ControlTemplateExamples#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/toolbar.xaml#toolbar)]  
  
 前の例では、次の 1 つ以上のリソースを使用しています。  
  
 [!code-xml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 サンプル全体については、[ControlTemplate を使用したスタイル設定のサンプル](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。  
  
## 参照  
 <xref:System.Windows.FrameworkElement.Style%2A>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [コントロールのスタイルとテンプレート](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)   
 [コントロールのカスタマイズ](../../../../docs/framework/wpf/controls/control-customization.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)