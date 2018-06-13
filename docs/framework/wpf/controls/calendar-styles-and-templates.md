---
title: カレンダーのスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Calendar
- templates [WPF], Calendar
- states [WPF], Calendar
- parts [WPF], Calendar
- Calendar [WPF], styles and templates
- ControlTemplate [WPF], Calendar
ms.assetid: f4fcf046-7a8f-41b8-b5a8-534b64e0345c
ms.openlocfilehash: 5398828d1526436ab5abbbd2e87515018b0cd8bf
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457525"
---
# <a name="calendar-styles-and-templates"></a>カレンダーのスタイルとテンプレート
このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Calendar>コントロール。 既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。 詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="calendar-parts"></a>カレンダーのパーツ  
 次の表に、名前付きのパーツの<xref:System.Windows.Controls.Calendar>コントロール。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|現在表示されている月または年に、<xref:System.Windows.Controls.Calendar>です。|  
|PART_Root|<xref:System.Windows.Controls.Panel>|含むパネル、<xref:System.Windows.Controls.Primitives.CalendarItem>です。|  
  
## <a name="calendar-states"></a>カレンダーの状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Calendar>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|----------------------|---------------------------|-----------------|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="calendaritem-parts"></a>カレンダー項目部分  
 次の表に、名前付きのパーツの<xref:System.Windows.Controls.Primitives.CalendarItem>コントロール。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|コントロールのルートです。|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|クリックされたときに、予定表の前のページを表示するボタンをクリックします。|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|クリックされたときに、予定表の次のページを表示するボタンをクリックします。|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|このボタンは、月モード、年モード、および 10 年間モードを切り替えることができます。|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|月のモードのときにコンテンツをホストします。|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|年、または 10 年間のモードの場合にコンテンツをホストします。|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|無効状態のオーバーレイです。|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|<xref:System.Windows.DataTemplate>視覚的な構造を説明します。|  
  
## <a name="calendaritem-states"></a>カレンダー項目の状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.CalendarItem>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|通常の状態|CommonStates|既定の状態です。|  
|状態が無効|CommonStates|カレンダーの状態と、<xref:System.Windows.UIElement.IsEnabled%2A>プロパティは`false`します。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="calendardaybutton-parts"></a>CalendarDayButton 部分  
 <xref:System.Windows.Controls.Primitives.CalendarDayButton>コントロールには、その名前付きの部分はありません。  
  
## <a name="calendardaybutton-states"></a>CalendarDayButton 状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.CalendarDayButton>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|無効|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton>は無効になります。|  
|MouseOver|CommonStates|マウス ポインターを置いた、<xref:System.Windows.Controls.Primitives.CalendarDayButton>です。|  
|押されている|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton>が押されました。|  
|選択済み|SelectionStates|ボタンが選択されます。|  
|未選択|SelectionStates|ボタンが選択されていません。|  
|CalendarButtonFocused|CalendarButtonFocusStates|ボタンには、フォーカスがあります。|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|ボタンにフォーカスがないです。|  
|フォーカスされている|FocusStates|ボタンには、フォーカスがあります。|  
|フォーカスされていない|FocusStates|ボタンにフォーカスがないです。|  
|アクティブ|ActiveStates|ボタンがアクティブです。|  
|非アクティブ|ActiveStates|ボタンがアクティブではできません。|  
|RegularDay|DayStates|ボタンを表さない<xref:System.DateTime.Today%2A?displayProperty=nameWithType>です。|  
|今日|DayStates|ボタンを表す<xref:System.DateTime.Today%2A?displayProperty=nameWithType>です。|  
|NormalDay|BlackoutDayStates|ボタンは、選択可能な日を表します。|  
|BlackoutDay|BlackoutDayStates|ボタンは、選択できない日付を表します。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="calendarbutton-parts"></a>CalendarButton 部分  
 <xref:System.Windows.Controls.Primitives.CalendarButton>コントロールには、その名前付きの部分はありません。  
  
## <a name="calendarbutton-states"></a>CalendarButton 状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.CalendarButton>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|無効|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton>は無効になります。|  
|MouseOver|CommonStates|マウス ポインターを置いた、<xref:System.Windows.Controls.Primitives.CalendarButton>です。|  
|押されている|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton>が押されました。|  
|選択済み|SelectionStates|ボタンが選択されます。|  
|未選択|SelectionStates|ボタンが選択されていません。|  
|CalendarButtonFocused|CalendarButtonFocusStates|ボタンには、フォーカスがあります。|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|ボタンにフォーカスがないです。|  
|フォーカスされている|FocusStates|ボタンには、フォーカスがあります。|  
|フォーカスされていない|FocusStates|ボタンにフォーカスがないです。|  
|アクティブ|ActiveStates|ボタンがアクティブです。|  
|非アクティブ|ActiveStates|ボタンがアクティブではできません。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="calendar-controltemplate-example"></a>カレンダー ControlTemplate の例  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Calendar>コントロールと関連する型。  
  
 [!code-xaml[ControlTemplateExamples#Calendar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
 前の例では、次のリソースの 1 つ以上を使用します。  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [コントロールのスタイルとテンプレート](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [コントロールのカスタマイズ](../../../../docs/framework/wpf/controls/control-customization.md)  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
