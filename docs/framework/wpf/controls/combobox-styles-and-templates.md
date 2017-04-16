---
title: "ComboBox のスタイルとテンプレート | Microsoft Docs"
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
  - "ComboBox [WPF], スタイルおよびテンプレート"
  - "ControlTemplate [WPF], ComboBox"
  - "パーツ [WPF], ComboBox"
  - "状態 [WPF], ComboBox"
  - "スタイル [WPF], ComboBox"
  - "テンプレート [WPF], ComboBox"
ms.assetid: b0662fa1-16d7-4320-b26b-c1804e565a44
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# ComboBox のスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.ComboBox> コントロールのスタイルおよびテンプレートについて説明します。  既定の <xref:System.Windows.Controls.ControlTemplate> に変更を加えることで、コントロールに独自の外観を設定できます。  詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## ComboBox のパーツ  
 次の表は、<xref:System.Windows.Controls.ComboBox> コントロールの名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_EditableTextBox|<xref:System.Windows.Controls.TextBox>|<xref:System.Windows.Controls.ComboBox> のテキストが格納されます。|  
|PART\_Popup|<xref:System.Windows.Controls.Primitives.Popup>|コンボ ボックスの項目を格納するドロップダウンです。|  
  
 <xref:System.Windows.Controls.ComboBox> の <xref:System.Windows.Controls.ControlTemplate> を作成するときに、テンプレートの <xref:System.Windows.Controls.ScrollViewer> 内に <xref:System.Windows.Controls.ItemsPresenter> が含まれる場合があります。  <xref:System.Windows.Controls.ItemsPresenter> により、<xref:System.Windows.Controls.ComboBox> の各項目が表示されます。また、<xref:System.Windows.Controls.ScrollViewer> により、コントロール内でスクロールできるようになります。  <xref:System.Windows.Controls.ItemsPresenter> が <xref:System.Windows.Controls.ScrollViewer> の直接の子でない場合は、<xref:System.Windows.Controls.ItemsPresenter> に `ItemsPresenter` という名前を付ける必要があります。  
  
## ComboBox の状態  
 次の表は、<xref:System.Windows.Controls.ComboBox> コントロールの状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Normal|CommonStates|既定の状態です。|  
|Disabled|CommonStates|コントロールが無効になっています。|  
|MouseOver|CommonStates|<xref:System.Windows.Controls.ComboBox> コントロール上にマウス ポインターがあります。|  
|Focused|FocusStates|コントロールにフォーカスがあります。|  
|Unfocused|FocusStates|コントロールにフォーカスがありません。|  
|FocusedDropDown|FocusStates|<xref:System.Windows.Controls.ComboBox> のドロップダウンにフォーカスがあります。|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
|Editable|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> プロパティが `true` である。|  
|Uneditable|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> プロパティが `false` である。|  
  
## ComboBoxItem のパーツ  
 <xref:System.Windows.Controls.ComboBoxItem> コントロールには、名前付きのパーツは存在しません。  
  
## ComboBoxItem の状態  
 次の表は、<xref:System.Windows.Controls.ComboBoxItem> コントロールの状態の一覧です。  
  
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
  
## ComboBox ControlTemplate の例  
 次の例は、<xref:System.Windows.Controls.ComboBox> コントロールの <xref:System.Windows.Controls.ControlTemplate> と関連の型を定義する方法を示しています。  
  
 [!code-xml[ControlTemplateExamples#ComboBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
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