---
title: "方法 : Windows フォームの DateTimePicker コントロールを使用してカスタム形式で日付を表示する | Microsoft Docs"
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
  - "日付, 表示 (DateTimePicker コントロール内に)"
  - "DateTimePicker コントロール [Windows フォーム], 表示スタイル"
  - "例 [Windows フォーム], DateTimePicker コントロール"
ms.assetid: 39767691-2d2b-46b6-a663-b7901e581a6e
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォームの DateTimePicker コントロールを使用してカスタム形式で日付を表示する
Windows フォームの <xref:System.Windows.Forms.DateTimePicker> コントロールでは、コントロールに表示される日付および時刻の形式を柔軟に指定できます。  <xref:System.Windows.Forms.DateTimePicker.Format%2A> プロパティを使用して定義済みの形式を選択できます。定義済みの形式の一覧については、<xref:System.Windows.Forms.DateTimePickerFormat> に関するトピックを参照してください。  定義済みの形式の中に目的に適したものがない場合は、形式指定文字を使用して独自の形式スタイルを作成できます。形式指定文字の一覧については、<xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> に関するトピックを参照してください。  
  
### カスタム形式を表示するには  
  
1.  <xref:System.Windows.Forms.DateTimePicker.Format%2A> プロパティを `DateTimePickerFormat.Custom` に設定します。  
  
2.  <xref:System.Windows.Forms.DateTimePicker.CustomFormat%2A> プロパティを書式指定文字列に設定します。  
  
    ```vb  
    DateTimePicker1.Format = DateTimePickerFormat.Custom  
    ' Display the date as "Mon 27 Feb 2012".  
    DateTimePicker1.CustomFormat = "ddd dd MMM yyyy"  
  
    ```  
  
    ```csharp  
    dateTimePicker1.Format = DateTimePickerFormat.Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1.CustomFormat = "ddd dd MMM yyyy";  
  
    ```  
  
    ```cpp  
    dateTimePicker1->Format = DateTimePickerFormat::Custom;  
    // Display the date as "Mon 27 Feb 2012".  
    dateTimePicker1->CustomFormat = "ddd dd MMM yyyy";  
    ```  
  
### 形式を設定した値にテキストを追加するには  
  
1.  "M" などの形式指定文字および ":" などの区切り記号を除く文字は、単一引用符で囲んでください。  たとえば、次の形式指定文字列は、英語 \(U.S.\) のカルチャでは現在の日付を "Today is: 05:30:31 Friday March 02, 2012" の形式で表示します。  
  
    ```vb  
    DateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy"  
  
    ```  
  
    ```csharp  
    dateTimePicker1.CustomFormat = "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
  
    ```  
  
    ```cpp  
    dateTimePicker1->CustomFormat =  
       "'Today is:' hh:mm:ss dddd MMMM dd, yyyy";  
    ```  
  
     カルチャ設定に従って、単一引用符で囲まれていない文字は変更される場合があります。  たとえば、上記の形式指定文字列は、英語 \(U.S.\) のカルチャでは現在の日付を "Today is: 05:30:31 Friday March 02, 2012" の形式で表示します。  最初のコロンが単一引用符で囲まれていることに注意してください。これは、"hh:mm:ss" のコロンのように区切り文字として使用しているのではないからです。  他のカルチャでは、"Today is: 05.30.31 Friday March 02, 2012" という形式で表示される場合もあります。  
  
## 参照  
 [DateTimePicker コントロール](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)   
 [方法 : Windows フォームの DateTimePicker コントロールを使用して日付を設定および取得する](../../../../docs/framework/winforms/controls/how-to-set-and-return-dates-with-the-windows-forms-datetimepicker-control.md)