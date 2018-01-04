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
ms.workload: dotnet
ms.openlocfilehash: bd2a1755ae076369661b2c9a7a2b744961cdb129
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="datepicker"></a><span data-ttu-id="710f9-102">DatePicker</span><span class="sxs-lookup"><span data-stu-id="710f9-102">DatePicker</span></span>
<span data-ttu-id="710f9-103"><xref:System.Windows.Controls.DatePicker>コントロールで日付を選択、入力テキスト フィールドにするか、またはドロップダウン リストを使用して、ユーザーは、<xref:System.Windows.Controls.Calendar>コントロール。</span><span class="sxs-lookup"><span data-stu-id="710f9-103">The <xref:System.Windows.Controls.DatePicker> control allows the user to select a date by either typing it into a text field or by using a drop-down <xref:System.Windows.Controls.Calendar> control.</span></span>  
  
 <span data-ttu-id="710f9-104">次の図は、<xref:System.Windows.Controls.DatePicker>です。</span><span class="sxs-lookup"><span data-stu-id="710f9-104">The following illustration shows a <xref:System.Windows.Controls.DatePicker>.</span></span>  
  
 <span data-ttu-id="710f9-105">![DatePicker コントロール](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span><span class="sxs-lookup"><span data-stu-id="710f9-105">![DatePicker control](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span></span>  
<span data-ttu-id="710f9-106">DatePicker コントロール</span><span class="sxs-lookup"><span data-stu-id="710f9-106">DatePicker Control</span></span>  
  
 <span data-ttu-id="710f9-107">多くは、<xref:System.Windows.Controls.DatePicker>コントロールのプロパティは、その組み込みを管理するため、<xref:System.Windows.Controls.Calendar>と同等のプロパティと同様に関数<xref:System.Windows.Controls.Calendar>です。</span><span class="sxs-lookup"><span data-stu-id="710f9-107">Many of a <xref:System.Windows.Controls.DatePicker> control's properties are for managing its built-in <xref:System.Windows.Controls.Calendar>, and function identically to the equivalent property in <xref:System.Windows.Controls.Calendar>.</span></span> <span data-ttu-id="710f9-108">具体的には、 <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>、および<xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType>プロパティ関数と同じように、<xref:System.Windows.Controls.Calendar>対応します。</span><span class="sxs-lookup"><span data-stu-id="710f9-108">In particular, the <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, and <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> properties function identically to their <xref:System.Windows.Controls.Calendar> counterparts.</span></span> <span data-ttu-id="710f9-109">詳細については、「<xref:System.Windows.Controls.Calendar>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="710f9-109">For more information, see <xref:System.Windows.Controls.Calendar>.</span></span>  
  
 <span data-ttu-id="710f9-110">ユーザーが直接設定するテキスト フィールドに日付を入力、<xref:System.Windows.Controls.DatePicker.Text%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="710f9-110">Users can type a date directly into a text field, which sets the <xref:System.Windows.Controls.DatePicker.Text%2A> property.</span></span> <span data-ttu-id="710f9-111">場合、<xref:System.Windows.Controls.DatePicker>有効な日付を入力した文字列を変換できません、<xref:System.Windows.Controls.DatePicker.DateValidationError>イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="710f9-111">If the <xref:System.Windows.Controls.DatePicker> cannot convert the entered string to a valid date, the <xref:System.Windows.Controls.DatePicker.DateValidationError> event will be raised.</span></span> <span data-ttu-id="710f9-112">イベント ハンドラーが、例外が発生したこの既定では、<xref:System.Windows.Controls.DatePicker.DateValidationError>を設定できます、<xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A>プロパティを`false`と、例外が発生するようにします。</span><span class="sxs-lookup"><span data-stu-id="710f9-112">By default, this causes an exception, but an event handler for <xref:System.Windows.Controls.DatePicker.DateValidationError> can set the <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> property to `false` and prevent an exception from being raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="710f9-113">参照</span><span class="sxs-lookup"><span data-stu-id="710f9-113">See Also</span></span>  
 [<span data-ttu-id="710f9-114">コントロール</span><span class="sxs-lookup"><span data-stu-id="710f9-114">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
 [<span data-ttu-id="710f9-115">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="710f9-115">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
