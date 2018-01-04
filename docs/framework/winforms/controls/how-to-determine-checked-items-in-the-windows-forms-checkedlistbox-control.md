---
title: "方法 : Windows フォーム CheckedListBox コントロールでオンになっている項目を判断する"
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
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63960740b2fc0cb2c96f9a853480f37857c7901b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a>方法 : Windows フォーム CheckedListBox コントロールでオンになっている項目を判断する
Windows フォームでデータを表示する場合、<xref:System.Windows.Forms.CheckedListBox>コントロールすることができますか、コレクションの反復に格納されている、<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>プロパティ、または手順を使用して、一覧から、<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>どの項目がチェックを調べます。 <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>メソッドの引数として、項目のインデックス番号を受け取り、返します`true`または`false`です。 期待するとは対照的、<xref:System.Windows.Forms.ListBox.SelectedItems%2A>と<xref:System.Windows.Forms.ListBox.SelectedIndices%2A>プロパティはどの項目がチェックを決定していません。 項目が強調表示を判断します。  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a>CheckedListBox コントロールでチェックされた項目を決定するには  
  
1.  反復処理する、<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>コレクションは 0 から始まるために、0 から始まるコレクション。 このメソッドが表示項目数の一覧で、メモには、全体的なリストではなく、項目がチェックされます。 次のコードでのようにテキストを表示する場合は、一覧の最初の項目がチェックされないため、2 番目の項目がチェックされて、ように"チェック項目 1 MyListItem2 ="です。  
  
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
  
     - または  
  
2.  ステップ実行、<xref:System.Windows.Forms.CheckedListBox.Items%2A>コレクション、コレクションは、0 から始まるために、0 から始まるおよび呼び出し、<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>の各項目に対してメソッドです。 このメソッドが表示項目数、一覧全体での先頭の項目リストはチェックされませんので実行して、2 番目の項目がチェックされてのようなものが表示されます"の項目 2 = MyListItem2"です。  
  
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
  
## <a name="see-also"></a>参照  
 [オプションのリストを表示するための Windows フォーム コントロール](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
