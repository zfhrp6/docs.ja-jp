---
title: "方法 : Windows フォームの MonthCalendar コントロールの外観を変更する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "例 [Windows フォーム], 予定表コントロール"
  - "MonthBackColor プロパティ"
  - "MonthCalendar コントロール [Windows フォーム], 書式指定 (表示を)"
  - "TitleBackColor プロパティ"
  - "TitleForeColor プロパティ"
  - "TrailingForeColor プロパティ"
ms.assetid: d09b95c9-e108-4608-9b31-b9100c0677bf
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : Windows フォームの MonthCalendar コントロールの外観を変更する
Windows フォームの <xref:System.Windows.Forms.MonthCalendar> コントロールでは、さまざまな方法でカレンダーの外観をカスタマイズできます。  たとえば、配色を変更したり、週番号や現在の日付の表示と非表示を切り替えたりできます。  
  
### 月間予定表の配色を変更するには  
  
-   <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>、<xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>、<xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> などのプロパティを設定します。  <xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A> プロパティは、曜日を示すフォントの色も決定します。  <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> プロパティは、表示月の前後の月に属する日付の色を決定します。  
  
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
    >  Windows Vista 以降では、テーマによっては、プロパティを設定してもカレンダーの外観が変更されない場合があります。  たとえば、Aero テーマを使用するように Windows が設定されている場合は、<xref:System.Windows.Forms.MonthCalendar.BackColor%2A>、<xref:System.Windows.Forms.MonthCalendar.TitleBackColor%2A>、<xref:System.Windows.Forms.MonthCalendar.TitleForeColor%2A>、または <xref:System.Windows.Forms.MonthCalendar.TrailingForeColor%2A> プロパティを設定しても効力はありません。  これは、更新版のカレンダーが、実行時に現在のオペレーティング システムのテーマから取得された外観でレンダリングされるためです。  これらのプロパティを使用して以前のバージョンのカレンダーを有効にする場合は、アプリケーションの visual スタイルを無効にすることができます。  visual スタイルを無効にすると、アプリケーションの他のコントロールの外観と動作に影響する可能性があります。  Visual Basic で visual スタイルを無効にするには、プロジェクト デザイナーを開いて、**\[XP Visual スタイルを有効にする\]** チェック ボックスをオフにします。  C\# で visual スタイルを無効にするには、Program.cs を開いて、`Application.EnableVisualStyles();` をコメント アウトします。  visual スタイルの詳細については、「[How to: Enable Windows XP Visual Styles](http://msdn.microsoft.com/ja-jp/0a038ade-31cf-4e56-9cfe-7a1e6b83b57f)」を参照してください。  
  
### コントロールの下部に現在の日付を表示するには  
  
-   <xref:System.Windows.Forms.MonthCalendar.ShowToday%2A> プロパティを `true` に設定します。  フォームをダブルクリックしたときに今日の日付の表示と非表示を切り替える例を次に示します。  
  
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
  
     \([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]、[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]\) フォームのコンストラクターに次のコードを挿入してイベント ハンドラーを登録します。  
  
    ```csharp  
    this.DoubleClick += new System.EventHandler(this.Form1_DoubleClick);  
    ```  
  
    ```cpp  
    this->DoubleClick += gcnew System::EventHandler(this,  
       &Form1::Form1_DoubleClick);  
    ```  
  
### 週番号を表示するには  
  
-   <xref:System.Windows.Forms.MonthCalendar.ShowWeekNumbers%2A> プロパティを `true` に設定します。  このプロパティは、コードまたは \[プロパティ\] ウィンドウで設定できます。  
  
     週番号は、週の最初の日の左側に別の列として表示されます。  
  
    ```vb  
    MonthCalendar1.ShowWeekNumbers = True  
    ```  
  
    ```csharp  
    monthCalendar1.ShowWeekNumbers = true;  
    ```  
  
    ```cpp  
    monthCalendar1->ShowWeekNumbers = true;  
    ```  
  
## 参照  
 [MonthCalendar コントロール](../../../../docs/framework/winforms/controls/monthcalendar-control-windows-forms.md)   
 [方法 : Windows フォームの MonthCalendar コントロールで日付の範囲を選択する](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)   
 [方法 : Windows フォームの MonthCalendar コントロールを使用して特定の日付を太字で表示する](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)   
 [方法 : Windows フォームの MonthCalendar コントロールにおいて複数の月を表示する](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)