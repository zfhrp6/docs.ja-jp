---
title: DatePicker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd5c7c796ee9d51a216368de3f3b04c10a5a3acd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
