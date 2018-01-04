---
title: "方法: Windows フォームの MonthCalendar コントロール &#39; を変更する秒外観"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], calendar controls
- MonthCalendar control [Windows Forms], formatting display
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b9c401532fa7a5f09462cf12084f32bca3f721cf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-windows-forms-monthcalendar-control39s-appearance"></a>方法: Windows フォームの MonthCalendar コントロール &#39; を変更する秒外観
Windows フォーム<xref:System.Windows.Forms.MonthCalendar>コントロールでは、さまざまな方法で、カレンダーの外観をカスタマイズすることができます。 たとえば、配色を設定でき、または週の数と現在の日付を非表示に選択できます。  
  
### <a name="to-change-the-month-calendars-color-scheme"></a>月間予定表の配色を変更するには  
  
-   プロパティを設定します。 <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>、<xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>と<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>です。 <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>プロパティが、週の日間も、フォントの色を決定します。 <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>プロパティが表示されている月または数か月の手順の前後の日付の色を決定します。  
  
    ```vb  
    MonthCalendar1.TitleBackColor = System.Drawing.Color.Blue  
    MonthCalendar1.TrailingForeColor = System.Drawing.Color.Red  
    MonthCalendar1.TitleForeColor = System.Drawing.Color.Yellow  
    ```  
  
    ```csharp  
    monthCalendar1.TitleBackColor = System.Drawing.Color.Blue;  
    monthCalendar1.TrailingForeColor = System.Drawing.Color.Red;  
    monthCalendar1.TitleForeColor = System.Drawing.Color.Yellow;  
    ```  
  
    ```cpp  
    monthCalendar1->TitleBackColor = System::Drawing::Color::Blue;  
    monthCalendar1->TrailingForeColor = System::Drawing::Color::Red;  
    monthCalendar1->TitleForeColor = System::Drawing::Color::Yellow;  
    ```  
  
    > [!NOTE]
    >  以降、Windows Vista とは、テーマによって、一部のプロパティを設定変わらないことがあります、カレンダーの外観です。 たとえば、Aero のテーマを使用する Windows を設定すると、設定、 <xref:System.Windows.Forms.MonthCalendar.BackColor%2A>、 <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>、 <xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>、または<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A>プロパティは影響を与えません。 これは、予定表の更新バージョンが実行時に現在のオペレーティング システムのテーマから派生した外観でレンダリングされているためです。 これらのプロパティを使用し、カレンダーの以前のバージョンを有効にする場合は、アプリケーションの visual スタイルが無効にできます。 Visual スタイルを無効にすると、アプリケーションでは、その他のコントロールの動作と外観が影響があります。 Visual Basic での visual スタイルを無効にするには、プロジェクト デザイナーを開きをオフにして、**を有効にする XP の視覚スタイル**チェック ボックスをオンします。 C# での visual スタイルを無効にするには、Program.cs を開きをコメント アウト`Application.EnableVisualStyles();`です。 Visual スタイルの詳細については、次を参照してください。[する方法: Windows XP Visual スタイルを有効にする](http://msdn.microsoft.com/en-us/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f)です。  
  
### <a name="to-display-the-current-date-at-the-bottom-of-the-control"></a>コントロールの下部にある現在の日付を表示するには  
  
-   <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> プロパティを `true` に設定します。 次の例は、今日の日付の形式がダブルクリックされたときの表示を切り替えます。  
  
    ```vb  
    Private Sub Form1_DoubleClick(ByVal sender As Object, _  
    ByVal e As System.EventArgs) Handles MyBase.DoubleClick  
       ' Toggle between True and False.  
       MonthCalendar1.ShowToday = Not MonthCalendar1.ShowToday  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_DoubleClick(object sender, System.EventArgs e)  
    {  
       // Toggle between True and False.  
       monthCalendar1.ShowToday = !monthCalendar1.ShowToday;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void Form1_DoubleClick(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          // Toggle between True and False.  
          monthCalendar1->ShowToday = !monthCalendar1->ShowToday;  
       }  
    ```  
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### <a name="to-display-week-numbers"></a>週番号を表示するには  
  
-   <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> プロパティを `true` に設定します。 [プロパティ] ウィンドウまたはコードでは、このプロパティを設定することができます。  
  
     別の列、週の最初の日の左側に週番号が表示されます。  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## <a name="see-also"></a>参照  
 [MonthCalendar コントロール](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)  
 [方法: Windows フォームの MonthCalendar コントロールで日付の範囲を選択する](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 [方法: Windows フォームの MonthCalendar コントロールを使用して特定の日付を太字で表示する](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 [方法: Windows フォームの MonthCalendar コントロールにおいて複数の月を表示する](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)
