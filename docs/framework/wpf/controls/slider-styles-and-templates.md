---
title: "スライダーのスタイルとテンプレート | Microsoft Docs"
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
  - "ControlTemplate [WPF], スライダー"
  - "パーツ [WPF], スライダー"
  - "Slider [WPF], スタイルおよびテンプレート"
  - "状態 [WPF], スライダー"
  - "スタイル [WPF], スライダー"
  - "テンプレート [WPF], スライダー"
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# スライダーのスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.Slider> コントロールのスタイルおよびテンプレートについて説明します。  既定の <xref:System.Windows.Controls.ControlTemplate> に変更を加えることで、コントロールに独自の外観を設定できます。  詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## Slider のパーツ  
 次の表は、<xref:System.Windows.Controls.Slider> コントロールの名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_Track|<xref:System.Windows.Controls.Primitives.Track>|<xref:System.Windows.Controls.Slider> の位置を示す要素のコンテナー。|  
|PART\_SelectionRange|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.Controls.Slider> に沿って選択範囲を表示する要素。  選択範囲は、<xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> プロパティが `true` の場合にのみ表示されます。|  
  
## Slider の状態  
 次の表は、<xref:System.Windows.Controls.Slider> コントロールの表示状態の一覧です。  
  
|VisualState 名|VisualStateGroup 名|Description|  
|-------------------|------------------------|-----------------|  
|Normal|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されています。|  
|Disabled|CommonStates|コントロールが無効になっています。|  
|Focused|FocusStates|コントロールにフォーカスがあります。|  
|Unfocused|FocusStates|コントロールにフォーカスがありません。|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## Slider ControlTemplate の例  
 次の例は、<xref:System.Windows.Controls.Slider> コントロールの <xref:System.Windows.Controls.ControlTemplate> を定義する方法を示しています。  
  
 [!code-xml[ControlTemplateExamples#Slider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
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