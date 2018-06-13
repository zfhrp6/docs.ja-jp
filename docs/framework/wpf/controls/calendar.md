---
title: 予定表
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Calendar
- Calendar control [WPF]
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
ms.openlocfilehash: b706ec6236b7e3e10865eee9fd32c2eb5a5e7db2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557707"
---
# <a name="calendar"></a>予定表
カレンダーでは、ビジュアルな予定表を使用して日付を選択するユーザーを使用できます。  
  
 A<xref:System.Windows.Controls.Calendar>コントロールをそれ自体にまたはのドロップダウン部分として使用できます、<xref:System.Windows.Controls.DatePicker>コントロール。 詳細については、「<xref:System.Windows.Controls.DatePicker>」を参照してください。  
  
 次の図は 2 つ<xref:System.Windows.Controls.Calendar>と含まない選択とブラック アウト日のいずれかを制御します。  
  
 ![カレンダー コントロール](../../../../docs/framework/wpf/controls/media/ndp-calendarcontrols.png "NDP_CalendarControls")  
予定表コントロール  
  
 次の表は、一般に関連付けられているタスクに関する情報を提供、<xref:System.Windows.Controls.Calendar>です。  
  
|タスク|実装|  
|----------|--------------------|  
|日付を指定するを選択することはできません。|<xref:System.Windows.Controls.Calendar.BlackoutDates%2A> プロパティを使用します。|  
|<xref:System.Windows.Controls.Calendar> 1 か月、年全体、または 10 年を表示します。|設定、<xref:System.Windows.Controls.Calendar.DisplayMode%2A>プロパティを月、年、または 10 年間です。|  
|ユーザーが日付を選択するかどうか、日付の範囲、または日付の複数の範囲を指定します。|使用して、<xref:System.Windows.Controls.Calendar.SelectionMode%2A>です。|  
|日付の範囲を指定する、<xref:System.Windows.Controls.Calendar>が表示されます。|<xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> プロパティおよび <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A> プロパティを使用します。|  
|現在の日付が強調表示されているかどうかを指定します。|<xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> プロパティを使用します。 既定では、<xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A>は`true`します。|  
|サイズを変更、<xref:System.Windows.Controls.Calendar>です。|使用して、<xref:System.Windows.Controls.Viewbox>設定や、<xref:System.Windows.FrameworkElement.LayoutTransform%2A>プロパティを<xref:System.Windows.Media.ScaleTransform>です。 設定する場合、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>のプロパティ、 <xref:System.Windows.Controls.Calendar>、実際のカレンダーでは、そのサイズは変更されません。|  
  
 <xref:System.Windows.Controls.Calendar>コントロールは、マウスまたはキーボードを使用して基本的なナビゲーションを提供します。 次の表は、キーボード ナビゲーションをまとめたものです。  
  
|キーの組み合わせ|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|アクション|  
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|------------|  
|矢印|<xref:System.Windows.Controls.CalendarMode.Month>|変更、<xref:System.Windows.Controls.Calendar.SelectedDate%2A>プロパティ場合、<xref:System.Windows.Controls.Calendar.SelectionMode%2A>プロパティに設定されていない<xref:System.Windows.Controls.CalendarSelectionMode.None>です。|  
|矢印|<xref:System.Windows.Controls.CalendarMode.Year>|変更の月、<xref:System.Windows.Controls.Calendar.DisplayDate%2A>プロパティです。 なお、<xref:System.Windows.Controls.Calendar.SelectedDate%2A>は変わりません。|  
|矢印|<xref:System.Windows.Controls.CalendarMode.Decade>|変更の年、<xref:System.Windows.Controls.Calendar.DisplayDate%2A>です。 なお、<xref:System.Windows.Controls.Calendar.SelectedDate%2A>は変わりません。|  
|SHIFT キーを押しながら方向|<xref:System.Windows.Controls.CalendarMode.Month>|場合<xref:System.Windows.Controls.Calendar.SelectionMode%2A>に設定されていない<xref:System.Windows.Controls.CalendarSelectionMode.SingleDate>または<xref:System.Windows.Controls.CalendarSelectionMode.None>、選択した日付の範囲が広がります。|  
|ホーム|<xref:System.Windows.Controls.CalendarMode.Month>|変更、<xref:System.Windows.Controls.Calendar.SelectedDate%2A>は現在の月の最初の日にします。|  
|ホーム|<xref:System.Windows.Controls.CalendarMode.Year>|変更の月、<xref:System.Windows.Controls.Calendar.DisplayDate%2A>年の最初の月にします。 <xref:System.Windows.Controls.Calendar.SelectedDate%2A>は変わりません。|  
|ホーム|<xref:System.Windows.Controls.CalendarMode.Decade>|変更の年、 <xref:System.Windows.Controls.Calendar.DisplayDate%2A> 10 年間の最初の年にします。 <xref:System.Windows.Controls.Calendar.SelectedDate%2A>は変わりません。|  
|End|<xref:System.Windows.Controls.CalendarMode.Month>|変更、<xref:System.Windows.Controls.Calendar.SelectedDate%2A>は現在の月の最終日にします。|  
|End|<xref:System.Windows.Controls.CalendarMode.Year>|変更の月、<xref:System.Windows.Controls.Calendar.DisplayDate%2A>年の最後の月にします。 <xref:System.Windows.Controls.Calendar.SelectedDate%2A>は変わりません。|  
|End|<xref:System.Windows.Controls.CalendarMode.Decade>|年を変更、 <xref:System.Windows.Controls.Calendar.DisplayDate%2A> 10 年間の最後の年にします。 <xref:System.Windows.Controls.Calendar.SelectedDate%2A>は変わりません。|  
|Ctrl + ↑|どれでも可|次に切り替わります大きい<xref:System.Windows.Controls.Calendar.DisplayMode%2A>です。 場合<xref:System.Windows.Controls.Calendar.DisplayMode%2A>は既に<xref:System.Windows.Controls.CalendarMode.Decade>何もしません。|  
|Ctrl +↓|どれでも可|次に切り替わります小さい<xref:System.Windows.Controls.Calendar.DisplayMode%2A>です。 場合<xref:System.Windows.Controls.Calendar.DisplayMode%2A>は既に<xref:System.Windows.Controls.CalendarMode.Month>何もしません。|  
|Space キーまたは ENTER|<xref:System.Windows.Controls.CalendarMode.Year> または <xref:System.Windows.Controls.CalendarMode.Decade>|スイッチ<xref:System.Windows.Controls.Calendar.DisplayMode%2A>を<xref:System.Windows.Controls.CalendarMode.Month>または<xref:System.Windows.Controls.CalendarMode.Year>フォーカスのあるアイテムによって表されます。|  
  
## <a name="see-also"></a>関連項目  
 [コントロール](../../../../docs/framework/wpf/controls/index.md)  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)
