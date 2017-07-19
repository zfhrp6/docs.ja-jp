---
title: "ProgressBar のスタイルとテンプレート | Microsoft Docs"
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
  - "ControlTemplate [WPF], ProgressBar"
  - "パーツ [WPF], ProgressBar"
  - "ProgressBar [WPF], スタイルおよびテンプレート"
  - "状態 [WPF], ProgressBar"
  - "スタイル [WPF], ProgressBar"
  - "テンプレート [WPF], ProgressBar"
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# ProgressBar のスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.ProgressBar> コントロールのスタイルおよびテンプレートについて説明します。  既定の <xref:System.Windows.Controls.ControlTemplate> に変更を加えることで、コントロールに独自の外観を設定できます。  詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## ProgressBar のパーツ  
 次の表は、<xref:System.Windows.Controls.ProgressBar> コントロールの名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_Indicator|<xref:System.Windows.FrameworkElement>|進行状況を示すオブジェクトです。|  
|PART\_Track|<xref:System.Windows.FrameworkElement>|プログレス インジケーターのパスを定義するオブジェクトです。|  
|PART\_GlowRect|<xref:System.Windows.FrameworkElement>|プログレス バーを拡張するオブジェクトです。|  
  
## ProgressBar の状態  
 次の表は、<xref:System.Windows.Controls.ProgressBar> コントロールの表示状態の一覧です。  
  
|VisualState 名|VisualStateGroup 名|Description|  
|-------------------|------------------------|-----------------|  
|Determinate|CommonStates|<xref:System.Windows.Controls.ProgressBar> は <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> プロパティに基づいて進行状況を報告します。|  
|Indeterminate|CommonStates|<xref:System.Windows.Controls.ProgressBar> は繰り返しパターンを使用して一般的な進行状況を報告します。|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## ProgressBar ControlTemplate の例  
 次の例は、<xref:System.Windows.Controls.ProgressBar> コントロールの <xref:System.Windows.Controls.ControlTemplate> を定義する方法を示しています。  
  
 [!code-xml[ControlTemplateExamples#ProgressBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
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