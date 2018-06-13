---
title: DatePicker
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
ms.openlocfilehash: 910ce09bfad6a46e3d96784b980ee4175c3d26a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550070"
---
# <a name="datepicker"></a>DatePicker
<xref:System.Windows.Controls.DatePicker>コントロールで日付を選択、入力テキスト フィールドにするか、またはドロップダウン リストを使用して、ユーザーは、<xref:System.Windows.Controls.Calendar>コントロール。  
  
 次の図は、<xref:System.Windows.Controls.DatePicker>です。  
  
 ![DatePicker コントロール](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")  
DatePicker コントロール  
  
 多くは、<xref:System.Windows.Controls.DatePicker>コントロールのプロパティは、その組み込みを管理するため、<xref:System.Windows.Controls.Calendar>と同等のプロパティと同様に関数<xref:System.Windows.Controls.Calendar>です。 具体的には、 <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>、および<xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType>プロパティ関数と同じように、<xref:System.Windows.Controls.Calendar>対応します。 詳細については、「<xref:System.Windows.Controls.Calendar>」を参照してください。  
  
 ユーザーが直接設定するテキスト フィールドに日付を入力、<xref:System.Windows.Controls.DatePicker.Text%2A>プロパティです。 場合、<xref:System.Windows.Controls.DatePicker>有効な日付を入力した文字列を変換できません、<xref:System.Windows.Controls.DatePicker.DateValidationError>イベントが発生します。 イベント ハンドラーが、例外が発生したこの既定では、<xref:System.Windows.Controls.DatePicker.DateValidationError>を設定できます、<xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A>プロパティを`false`と、例外が発生するようにします。  
  
## <a name="see-also"></a>関連項目  
 [コントロール](../../../../docs/framework/wpf/controls/index.md)  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)
