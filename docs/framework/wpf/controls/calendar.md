---
title: "Calendar | Microsoft Docs"
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
  - "Calendar コントロール [WPF]"
  - "コントロール [WPF], Calendar"
ms.assetid: ee844e4a-eefe-48e2-bd0d-1d82cc5e960b
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# Calendar
カレンダーは、ユーザーがビジュアルな予定表を使用して日付を選択できるコントロールです。  
  
 <xref:System.Windows.Controls.Calendar> コントロールは、単独で使用することも、<xref:System.Windows.Controls.DatePicker> コントロールのドロップダウン部分として使用することもできます。  詳細については、「<xref:System.Windows.Controls.DatePicker>」を参照してください。  
  
 次の図は、2 つの <xref:System.Windows.Controls.Calendar> コントロールを示します。選択したものと暗転表示された日付が、一方には含まれていますが、他方には含まれていません。  
  
 ![予定表コントロール](../../../../docs/framework/wpf/controls/media/ndp-calendarcontrols.png "NDP\_CalendarControls")  
Calendar コントロール  
  
 次の表は、一般的に <xref:System.Windows.Controls.Calendar> に関連付けられているタスクに関する情報を示しています。  
  
|タスク|実装|  
|---------|--------|  
|選択できない日付を指定します。|<xref:System.Windows.Controls.Calendar.BlackoutDates%2A> プロパティを使用します。|  
|<xref:System.Windows.Controls.Calendar> に 1 か月分、1 年分、または 10 年分を表示します。|<xref:System.Windows.Controls.Calendar.DisplayMode%2A> プロパティを月、年、または 10 年に設定します。|  
|ユーザーが日付、日付の範囲、または日付の複数の範囲を選択できるかどうかを指定します。|<xref:System.Windows.Controls.Calendar.SelectionMode%2A> を使用します。|  
|<xref:System.Windows.Controls.Calendar> に表示される日付の範囲を指定します。|<xref:System.Windows.Controls.Calendar.DisplayDateStart%2A> プロパティおよび <xref:System.Windows.Controls.Calendar.DisplayDateEnd%2A> プロパティを使用します。|  
|現在の日付が強調表示されるかどうかを指定します。|<xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> プロパティを使用します。  既定では、<xref:System.Windows.Controls.Calendar.IsTodayHighlighted%2A> は `true` に設定されています。|  
|<xref:System.Windows.Controls.Calendar> のサイズを変更します。|<xref:System.Windows.Controls.Viewbox> を使用するか、<xref:System.Windows.FrameworkElement.LayoutTransform%2A> プロパティを <xref:System.Windows.Media.ScaleTransform> に設定します。  <xref:System.Windows.Controls.Calendar> の <xref:System.Windows.FrameworkElement.Width%2A> プロパティと <xref:System.Windows.FrameworkElement.Height%2A> プロパティを設定した場合、実際の予定表のサイズは変更されない点に注意してください。|  
  
 <xref:System.Windows.Controls.Calendar> コントロールでは、マウスまたはキーボードによる基本的なナビゲーションを使用できます。  キーボード ナビゲーションを次の表にまとめます。  
  
|ショートカット キー|<xref:System.Windows.Controls.Calendar.DisplayMode%2A>|動作|  
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|--------|  
|方向キー|<xref:System.Windows.Controls.CalendarMode>|<xref:System.Windows.Controls.Calendar.SelectionMode%2A> プロパティが <xref:System.Windows.Controls.CalendarSelectionMode> に設定されていない場合、<xref:System.Windows.Controls.Calendar.SelectedDate%2A> プロパティを変更します。|  
|方向キー|<xref:System.Windows.Controls.CalendarMode>|<xref:System.Windows.Controls.Calendar.DisplayDate%2A> プロパティの月を変更します。  <xref:System.Windows.Controls.Calendar.SelectedDate%2A> は変更されません。|  
|方向キー|<xref:System.Windows.Controls.CalendarMode>|<xref:System.Windows.Controls.Calendar.DisplayDate%2A> の年を変更します。  <xref:System.Windows.Controls.Calendar.SelectedDate%2A> は変更されません。|  
|Shift \+ 方向キー|<xref:System.Windows.Controls.CalendarMode>|<xref:System.Windows.Controls.Calendar.SelectionMode%2A> が <xref:System.Windows.Controls.CalendarSelectionMode> または <xref:System.Windows.Controls.CalendarSelectionMode> に設定されていない場合に、日付の選択範囲を拡張します。|  
|Home|<xref:System.Windows.Controls.CalendarMode>|<xref:System.Windows.Controls.Calendar.SelectedDate%2A> を現在の月の最初の日に変更します。|  
|Home|<xref:System.Windows.Controls.CalendarMode>|<xref:System.Windows.Controls.Calendar.DisplayDate%2A> の月を年の最初の月に変更します。  <xref:System.Windows.Controls.Calendar.SelectedDate%2A> は変更されません。|  
|Home|<xref:System.Windows.Controls.CalendarMode>|<xref:System.Windows.Controls.Calendar.DisplayDate%2A> の年を 10 年間の最初の年に変更します。  <xref:System.Windows.Controls.Calendar.SelectedDate%2A> は変更されません。|  
|End|<xref:System.Windows.Controls.CalendarMode>|<xref:System.Windows.Controls.Calendar.SelectedDate%2A> を現在の月の最後の日に変更します。|  
|End|<xref:System.Windows.Controls.CalendarMode>|<xref:System.Windows.Controls.Calendar.DisplayDate%2A> の月を年の最後の月に変更します。  <xref:System.Windows.Controls.Calendar.SelectedDate%2A> は変更されません。|  
|End|<xref:System.Windows.Controls.CalendarMode>|<xref:System.Windows.Controls.Calendar.DisplayDate%2A> の年を 10 年間の最後の年に変更します。  <xref:System.Windows.Controls.Calendar.SelectedDate%2A> は変更されません。|  
|Ctrl \+ ↑|どれでも可|次に大きい <xref:System.Windows.Controls.Calendar.DisplayMode%2A> に切り替えます。  <xref:System.Windows.Controls.Calendar.DisplayMode%2A> が既に <xref:System.Windows.Controls.CalendarMode> の場合には、処理は行われません。|  
|Ctrl \+ ↓|どれでも可|次に小さい <xref:System.Windows.Controls.Calendar.DisplayMode%2A> に切り替えます。  <xref:System.Windows.Controls.Calendar.DisplayMode%2A> が既に <xref:System.Windows.Controls.CalendarMode> の場合には、処理は行われません。|  
|Space キーまたは Enter キー|<xref:System.Windows.Controls.CalendarMode> または <xref:System.Windows.Controls.CalendarMode>|<xref:System.Windows.Controls.Calendar.DisplayMode%2A> を、フォーカスが設定されている項目によって表された <xref:System.Windows.Controls.CalendarMode> または <xref:System.Windows.Controls.CalendarMode> に切り替えます。|  
  
## 参照  
 [コントロール](../../../../docs/framework/wpf/controls/index.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)