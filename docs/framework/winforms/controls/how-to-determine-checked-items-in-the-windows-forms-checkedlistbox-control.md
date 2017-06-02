---
title: "方法 : Windows フォーム CheckedListBox コントロールでオンになっている項目を判断する | Microsoft Docs"
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
  - "チェック ボックス, 判断 (チェック状態を)"
  - "CheckedListBox コントロール [Windows フォーム], 判断 (チェック状態を)"
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォーム CheckedListBox コントロールでオンになっている項目を判断する
Windows フォームの <xref:System.Windows.Forms.CheckedListBox> コントロールにデータを表示する場合は、<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> プロパティに格納されたコレクションに対して反復処理するか、または <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> メソッドを使用してリストをステップ処理することによって、どの項目がオンになっているかを判断できます。  <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> メソッドは、項目のインデックス番号を引数として、`true` または `false` を返します。  <xref:System.Windows.Forms.ListBox.SelectedItems%2A> プロパティおよび <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> プロパティでは、オンになっている項目ではなく、強調表示された項目が判断されます。  
  
### CheckedListBox コントロールでチェック状態の項目を判断するには  
  
1.  <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> コレクションに対して反復処理します。コレクションは配列が 0 から始まるため、0 から検索します。  このメソッドは、一覧全体ではなく、オンにされた項目の一覧について項目番号を取得します。  したがって、一覧の先頭の項目がオフで、2 番目の項目がオンの場合、以下のコードは "Checked Item 1 \= MyListItem2" のようなメッセージを表示します。  
  
    ```vb  
    ' Determine if there are any items checked.  
    If CheckedListBox1.CheckedItems.Count <> 0 Then  
       ' If so, loop through all checked items and print results.  
       Dim x As Integer  
       Dim s As String = ""  
       For x = 0 To CheckedListBox1.CheckedItems.Count - 1  
          s = s & "Checked Item " & (x + 1).ToString & " = " & CheckedListBox1.CheckedItems(x).ToString & ControlChars.CrLf  
       Next x  
       MessageBox.Show(s)  
    End If  
  
    ```  
  
    ```csharp  
    // Determine if there are any items checked.  
    if(checkedListBox1.CheckedItems.Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       string s = "";  
       for(int x = 0; x <= checkedListBox1.CheckedItems.Count - 1 ; x++)  
       {  
          s = s + "Checked Item " + (x+1).ToString() + " = " + checkedListBox1.CheckedItems[x].ToString() + "\n";  
       }  
    MessageBox.Show (s);  
    }  
  
    ```  
  
    ```cpp  
    // Determine if there are any items checked.  
    if(checkedListBox1->CheckedItems->Count != 0)  
    {  
       // If so, loop through all checked items and print results.  
       String ^ s = "";  
       for(int x = 0; x <= checkedListBox1->CheckedItems->Count - 1; x++)  
       {  
          s = String::Concat(s, "Checked Item ", (x+1).ToString(),  
             " = ", checkedListBox1->CheckedItems[x]->ToString(),  
             "\n");  
       }  
       MessageBox::Show(s);  
    }  
    ```  
  
     または  
  
2.  <xref:System.Windows.Forms.CheckedListBox.Items%2A> コレクションをステップ処理します。コレクションは配列が 0 から始まるため、0 から検索します。各項目に対して <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> メソッドを呼び出します。  このメソッドは、一覧全体から項目番号を取得するため、一覧の先頭の項目がオフで、2 番目の項目がオンの場合、このコードは "Item 2 \= MyListItem2" とメッセージを表示します。  
  
    ```vb  
    Dim i As Integer  
    Dim s As String  
    s = "Checked Items:" & ControlChars.CrLf  
    For i = 0 To (CheckedListBox1.Items.Count - 1)  
       If CheckedListBox1.GetItemChecked(i) = True Then  
          s = s & "Item " & (i + 1).ToString & " = " & CheckedListBox1.Items(i).ToString & ControlChars.CrLf  
       End If  
    Next  
    MessageBox.Show(s)  
  
    ```  
  
    ```csharp  
    int i;  
    string s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1.Items.Count-1); i++)  
    {  
       if (checkedListBox1.GetItemChecked(i))  
       {  
          s = s + "Item " + (i+1).ToString() + " = " + checkedListBox1.Items[i].ToString() + "\n";  
       }  
    }  
    MessageBox.Show (s);  
  
    ```  
  
    ```cpp  
    int i;  
    String ^ s;   
    s = "Checked items:\n" ;  
    for (i = 0; i <= (checkedListBox1->Items->Count-1); i++)  
    {  
       if (checkedListBox1->GetItemChecked(i))  
       {  
          s = String::Concat(s, "Item ", (i+1).ToString(), " = ",  
             checkedListBox1->Item[i]->ToString(), "\n");  
       }  
    }  
    MessageBox::Show(s);  
    ```  
  
## 参照  
 [オプションのリストを表示するための Windows フォーム コントロール](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)