---
title: "ScrollViewer のスタイルとテンプレート | Microsoft Docs"
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
  - "ControlTemplate [WPF], ScrollViewer"
  - "パーツ [WPF], ScrollViewer"
  - "ScrollViewer [WPF], スタイルおよびテンプレート"
  - "状態 [WPF], ScrollViewer"
  - "スタイル [WPF], ScrollViewer"
  - "テンプレート [WPF], ScrollViewer"
ms.assetid: dffdd822-ae69-4946-abaf-710860cd65b2
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# ScrollViewer のスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.ScrollViewer> コントロールのスタイルおよびテンプレートについて説明します。  既定の <xref:System.Windows.Controls.ControlTemplate> に変更を加えることで、コントロールに独自の外観を設定できます。  詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## ScrollViewer のパーツ  
 次の表は、<xref:System.Windows.Controls.ScrollViewer> コントロールの名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_ScrollContentPresenter|<xref:System.Windows.Controls.ScrollContentPresenter>|<xref:System.Windows.Controls.ScrollViewer> のコンテンツのプレースホルダーです。|  
|PART\_HorizontalScrollBar|<xref:System.Windows.Controls.Primitives.ScrollBar>|コンテンツを水平方向にスクロールするために使用する <xref:System.Windows.Controls.Primitives.ScrollBar> です。|  
|PART\_VerticalScrollBar|<xref:System.Windows.Controls.Primitives.ScrollBar>|コンテンツを垂直方向にスクロールするために使用する <xref:System.Windows.Controls.Primitives.ScrollBar> です。|  
  
## ScrollViewer の状態  
 次の表は、<xref:System.Windows.Controls.ScrollViewer> コントロールの表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## ScrollViewer ControlTemplate の例  
 次の例は、<xref:System.Windows.Controls.ScrollViewer> コントロールの <xref:System.Windows.Controls.ControlTemplate> を定義する方法を示しています。  
  
 [!code-xml[ControlTemplateExamples#ScrollViewer](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollviewer.xaml#scrollviewer)]  
  
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