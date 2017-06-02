---
title: "DatePicker のスタイルとテンプレート | Microsoft Docs"
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
  - "ControlTemplate [WPF], DatePicker"
  - "DatePicker [WPF], スタイルおよびテンプレート"
  - "パーツ [WPF], DatePicker"
  - "状態 [WPF], DatePicker"
  - "スタイル [WPF], DatePicker"
  - "テンプレート [WPF], DatePicker"
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# DatePicker のスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.DatePicker> コントロールのスタイルおよびテンプレートについて説明します。  既定の <xref:System.Windows.Controls.ControlTemplate> に変更を加えることで、コントロールに独自の外観を設定できます。  詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## DatePicker のパーツ  
 次の表は、<xref:System.Windows.Controls.DatePicker> コントロールの名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_Root|<xref:System.Windows.Controls.Grid>|コントロールのルートです。|  
|PART\_Button|<xref:System.Windows.Controls.Button>|<xref:System.Windows.Controls.Calendar> を開いたり閉じたりするボタンです。|  
|PART\_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|日付を入力できるテキスト ボックスです。|  
|PART\_Popup|<xref:System.Windows.Controls.Primitives.Popup>|<xref:System.Windows.Controls.DatePicker> コントロールのポップアップです。|  
  
## DatePicker の状態  
 次の表は、<xref:System.Windows.Controls.DatePicker> コントロールの表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Normal|CommonStates|既定の状態です。|  
|Disabled|CommonStates|<xref:System.Windows.Controls.DatePicker> が無効になっています。|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## DatePickerTextBox のパーツ  
 次の表は、<xref:System.Windows.Controls.Primitives.DatePickerTextBox> コントロールの名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_Watermark|<xref:System.Windows.Controls.ContentControl>|<xref:System.Windows.Controls.DatePicker> の初期化テキストを格納する要素です。|  
|PART\_ContentElement|<xref:System.Windows.FrameworkElement>|<xref:System.Windows.FrameworkElement> 要素を含むことができるビジュアル要素です。  <xref:System.Windows.Controls.TextBox> のテキストは、この要素内に表示されます。|  
  
## DatePickerTextBox の状態  
 次の表は、<xref:System.Windows.Controls.Primitives.DatePickerTextBox> コントロールの表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Normal|CommonStates|既定の状態です。|  
|Disabled|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox> が無効になっています。|  
|MouseOver|CommonStates|マウス ポインターは、<xref:System.Windows.Controls.Primitives.DatePickerTextBox> の上に置かれています。|  
|ReadOnly|CommonStates|ユーザーは、<xref:System.Windows.Controls.Primitives.DatePickerTextBox> 内のテキストを変更できません。|  
|Focused|FocusStates|コントロールにフォーカスがあります。|  
|Unfocused|FocusStates|コントロールにフォーカスがありません。|  
|Watermarked|WatermarkStates|コントロールに初期化テキストが表示されます。  ユーザーがテキストを入力していないか日付を選択していないときの <xref:System.Windows.Controls.Primitives.DatePickerTextBox> の状態です。|  
|Unwatermarked|WatermarkStates|ユーザーが <xref:System.Windows.Controls.Primitives.DatePickerTextBox> にテキストを入力したか、<xref:System.Windows.Controls.DatePicker> で日付を選択しました。|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## DatePicker ControlTemplate の例  
 次の例は、<xref:System.Windows.Controls.DatePicker> コントロールの <xref:System.Windows.Controls.ControlTemplate> を定義する方法を示しています。  
  
 [!code-xml[ControlTemplateExamples#DatePicker](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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