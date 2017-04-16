---
title: "ScrollBar のスタイルとテンプレート | Microsoft Docs"
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
  - "ControlTemplate [WPF], ScrollBar"
  - "パーツ [WPF], ScrollBar"
  - "ScrollBar [WPF], スタイルおよびテンプレート"
  - "状態 [WPF], ScrollBar"
  - "スタイル [WPF], ScrollBar"
  - "テンプレート [WPF], ScrollBar"
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# ScrollBar のスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.Primitives.ScrollBar> コントロールのスタイルおよびテンプレートについて説明します。  既定の <xref:System.Windows.Controls.ControlTemplate> に変更を加えることで、コントロールに独自の外観を設定できます。  詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## ScrollBar のパーツ  
 次の表は、<xref:System.Windows.Controls.Primitives.ScrollBar> コントロールの名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_Track|<xref:System.Windows.Controls.Primitives.Track>|<xref:System.Windows.Controls.Primitives.ScrollBar> の位置を示す要素のコンテナー。|  
  
## ScrollBar の状態  
 次の表は、<xref:System.Windows.Controls.Primitives.ScrollBar> コントロールの表示状態の一覧です。  
  
|VisualState 名|VisualStateGroup 名|Description|  
|-------------------|------------------------|-----------------|  
|Normal|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されています。|  
|Disabled|CommonStates|コントロールが無効になっています。|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## ScrollBar ControlTemplate の例  
 次の例は、<xref:System.Windows.Controls.Primitives.ScrollBar> コントロールの <xref:System.Windows.Controls.ControlTemplate> を定義する方法を示しています。  
  
 [!code-xml[ControlTemplateExamples#ScrollBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
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