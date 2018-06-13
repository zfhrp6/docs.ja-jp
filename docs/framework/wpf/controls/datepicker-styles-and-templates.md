---
title: DatePicker スタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
ms.openlocfilehash: b50716cc83114fea5120b12659668437ac9bd6da
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457737"
---
# <a name="datepicker-styles-and-templates"></a>DatePicker スタイルとテンプレート
このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Controls.DatePicker>コントロール。 既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。 詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="datepicker-parts"></a>DatePicker 部分  
 次の表に、名前付きのパーツの<xref:System.Windows.Controls.DatePicker>コントロール。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|コントロールのルートです。|  
|PART_Button|<xref:System.Windows.Controls.Button>|開いたり閉じたりするボタン、<xref:System.Windows.Controls.Calendar>です。|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|日付を入力できるテキスト ボックスです。|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|ポップアップを<xref:System.Windows.Controls.DatePicker>コントロール。|  
  
## <a name="datepicker-states"></a>DatePicker 状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Controls.DatePicker>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|無効|CommonStates|<xref:System.Windows.Controls.DatePicker>は無効になります。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="datepickertextbox-parts"></a>DatePickerTextBox 部分  
 次の表に、名前付きのパーツの<xref:System.Windows.Controls.Primitives.DatePickerTextBox>コントロール。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|最初のテキストを格納する要素、<xref:System.Windows.Controls.DatePicker>です。|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|視覚的要素を含むことができます、<xref:System.Windows.FrameworkElement>です。 テキスト、<xref:System.Windows.Controls.TextBox>はこの要素に表示されます。|  
  
## <a name="datepickertextbox-states"></a>DatePickerTextBox 状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Controls.Primitives.DatePickerTextBox>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|無効|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>は無効になります。|  
|MouseOver|CommonStates|マウス ポインターを置いた、<xref:System.Windows.Controls.Primitives.DatePickerTextBox>です。|  
|ReadOnly|CommonStates|ユーザーが内のテキストを変更できない、<xref:System.Windows.Controls.Primitives.DatePickerTextBox>です。|  
|フォーカスされている|FocusStates|コントロールにフォーカスがあります。|  
|フォーカスされていない|FocusStates|コントロールにフォーカスがありません。|  
|目標を設定|WatermarkStates|コントロールには、その最初のテキストが表示されます。  <xref:System.Windows.Controls.Primitives.DatePickerTextBox>ユーザーがいないテキストを入力または日付を選択した場合は、状態です。|  
|Unwatermarked|WatermarkStates|ユーザーがテキストを入力、<xref:System.Windows.Controls.Primitives.DatePickerTextBox>で日付を選択したか、<xref:System.Windows.Controls.DatePicker>です。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="datepicker-controltemplate-example"></a>DatePicker ControlTemplate の例  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.DatePicker>コントロール。  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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
