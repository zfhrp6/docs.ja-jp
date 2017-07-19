---
title: "カレンダーのスタイルとテンプレート | Microsoft Docs"
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
  - "Calendar [WPF], スタイルおよびテンプレート"
  - "ControlTemplate [WPF], Calendar"
  - "パーツ [WPF], Calendar"
  - "状態 [WPF], Calendar"
  - "スタイル [WPF], Calendar"
  - "テンプレート [WPF], Calendar"
ms.assetid: f4fcf046-7a8f-41b8-b5a8-534b64e0345c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# カレンダーのスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.Calendar> コントロールのスタイルおよびテンプレートについて説明します。  既定の <xref:System.Windows.Controls.ControlTemplate> に変更を加えることで、コントロールに独自の外観を設定できます。  詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## Calendar のパーツ  
 次の表は、<xref:System.Windows.Controls.Calendar> コントロールの名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|<xref:System.Windows.Controls.Calendar> に現在表示されている月または年。|  
|PART\_Root|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Primitives.CalendarItem> を格納するパネル。|  
  
## Calendar の状態  
 次の表は、<xref:System.Windows.Controls.Calendar> コントロールの表示状態の一覧です。  
  
|VisualState 名|VisualStateGroup 名|Description|  
|-------------------|------------------------|-----------------|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## CalendarItem のパーツ  
 次の表は、<xref:System.Windows.Controls.Primitives.CalendarItem> コントロールの名前付きパーツの一覧です。  
  
||||  
|-|-|-|  
|指定項目|種類|Description|  
|PART\_Root|<xref:System.Windows.FrameworkElement>|コントロールのルートです。|  
|PART\_PreviousButton|<xref:System.Windows.Controls.Button>|このボタンをクリックすると、カレンダーの前のページを表示します。|  
|PART\_NextButton|<xref:System.Windows.Controls.Button>|このボタンをクリックすると、カレンダーの次のページを表示します。|  
|PART\_HeaderButton|<xref:System.Windows.Controls.Button>|月モード、年モード、および 10 年単位モードを切り替えるボタンです。|  
|PART\_MonthView|<xref:System.Windows.Controls.Grid>|月モードの場合にコンテンツをホストします。|  
|PART\_YearView|<xref:System.Windows.Controls.Grid>|年モードか 10 年単位のモードの場合にコンテンツをホストします。|  
|PART\_DisabledVisual|<xref:System.Windows.FrameworkElement>|無効な状態のオーバーレイ。|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|視覚的な構造を表す <xref:System.Windows.DataTemplate>。|  
  
## CalendarItem の状態  
 次の表は、<xref:System.Windows.Controls.Primitives.CalendarItem> コントロールの表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Normal State|CommonStates|既定の状態です。|  
|Disabled State|CommonStates|<xref:System.Windows.UIElement.IsEnabled%2A> プロパティが `false` であるときの予定表の状態。|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## CalendarDayButton のパーツ  
 <xref:System.Windows.Controls.Primitives.CalendarDayButton> コントロールには、名前付きのパーツは存在しません。  
  
## CalendarDayButton の状態  
 次の表は、<xref:System.Windows.Controls.Primitives.CalendarDayButton> コントロールの表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Normal|CommonStates|既定の状態です。|  
|Disabled|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> が無効になっています。|  
|MouseOver|CommonStates|マウス ポインターは、<xref:System.Windows.Controls.Primitives.CalendarDayButton> の上に置かれています。|  
|Pressed|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton> が押されています。|  
|Selected|SelectionStates|ボタンが選択されています。|  
|Unselected|SelectionStates|ボタンが選択されていません。|  
|CalendarButtonFocused|CalendarButtonFocusStates|ボタンにフォーカスがあります。|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|ボタンにフォーカスがありません。|  
|Focused|FocusStates|ボタンにフォーカスがあります。|  
|Unfocused|FocusStates|ボタンにフォーカスがありません。|  
|Active|ActiveStates|ボタンがアクティブです。|  
|Inactive|ActiveStates|ボタンがアクティブではありません。|  
|RegularDay|DayStates|ボタンが <xref:System.DateTime.Today%2A?displayProperty=fullName> を表していません。|  
|Today|DayStates|ボタンが <xref:System.DateTime.Today%2A?displayProperty=fullName> を表しています。|  
|NormalDay|BlackoutDayStates|このボタンは、選択できる日を表します。|  
|BlackoutDay|BlackoutDayStates|このボタンは、選択できない日を表します。|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## CalendarButton のパーツ  
 <xref:System.Windows.Controls.Primitives.CalendarButton> コントロールには、名前付きのパーツは存在しません。  
  
## CalendarButton の状態  
 次の表は、<xref:System.Windows.Controls.Primitives.CalendarButton> コントロールの表示状態の一覧です。  
  
||||  
|-|-|-|  
|VisualState 名|VisualStateGroup 名|Description|  
|Normal|CommonStates|既定の状態です。|  
|Disabled|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> が無効になっています。|  
|MouseOver|CommonStates|マウス ポインターは、<xref:System.Windows.Controls.Primitives.CalendarButton> の上に置かれています。|  
|Pressed|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton> が押されています。|  
|Selected|SelectionStates|ボタンが選択されています。|  
|Unselected|SelectionStates|ボタンが選択されていません。|  
|CalendarButtonFocused|CalendarButtonFocusStates|ボタンにフォーカスがあります。|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|ボタンにフォーカスがありません。|  
|Focused|FocusStates|ボタンにフォーカスがあります。|  
|Unfocused|FocusStates|ボタンにフォーカスがありません。|  
|Active|ActiveStates|ボタンがアクティブです。|  
|Inactive|ActiveStates|ボタンがアクティブではありません。|  
|Valid|ValidationStates|このコントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `false` です。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> 添付プロパティは `true` で、コントロールにはフォーカスがありません。|  
  
## Calendar ControlTemplate の例  
 次の例は、<xref:System.Windows.Controls.Calendar> コントロールの <xref:System.Windows.Controls.ControlTemplate> と関連の型を定義する方法を示しています。  
  
 [!code-xml[ControlTemplateExamples#Calendar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
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