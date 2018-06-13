---
title: '方法 : Windows フォーム CheckedListBox コントロールでオンになっている項目を判断する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- check boxes [Windows Forms], determining checked state
- CheckedListBox control [Windows Forms], determining checked state
ms.assetid: 178b477d-27c9-489c-8914-44a9623a4d41
ms.openlocfilehash: 98b4ef7c4ac73e1560bd5c68f22898e46585d082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531015"
---
# <a name="how-to-determine-checked-items-in-the-windows-forms-checkedlistbox-control"></a><span data-ttu-id="e60f7-102">方法 : Windows フォーム CheckedListBox コントロールでオンになっている項目を判断する</span><span class="sxs-lookup"><span data-stu-id="e60f7-102">How to: Determine Checked Items in the Windows Forms CheckedListBox Control</span></span>
<span data-ttu-id="e60f7-103">Windows フォームでデータを表示する場合、<xref:System.Windows.Forms.CheckedListBox>コントロールすることができますか、コレクションの反復に格納されている、<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>プロパティ、または手順を使用して、一覧から、<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>どの項目がチェックを調べます。</span><span class="sxs-lookup"><span data-stu-id="e60f7-103">When presenting data in a Windows Forms <xref:System.Windows.Forms.CheckedListBox> control, you can either iterate through the collection stored in the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> property, or step through the list using the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method to determine which items are checked.</span></span> <span data-ttu-id="e60f7-104"><xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>メソッドの引数として、項目のインデックス番号を受け取り、返します`true`または`false`です。</span><span class="sxs-lookup"><span data-stu-id="e60f7-104">The <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method takes an item index number as its argument and returns `true` or `false`.</span></span> <span data-ttu-id="e60f7-105">期待するとは対照的、<xref:System.Windows.Forms.ListBox.SelectedItems%2A>と<xref:System.Windows.Forms.ListBox.SelectedIndices%2A>プロパティはどの項目がチェックを決定していません。 項目が強調表示を判断します。</span><span class="sxs-lookup"><span data-stu-id="e60f7-105">Contrary to what you might expect, the <xref:System.Windows.Forms.ListBox.SelectedItems%2A> and <xref:System.Windows.Forms.ListBox.SelectedIndices%2A> properties do not determine which items are checked; they determine which items are highlighted.</span></span>  
  
### <a name="to-determine-checked-items-in-a-checkedlistbox-control"></a><span data-ttu-id="e60f7-106">CheckedListBox コントロールでチェックされた項目を決定するには</span><span class="sxs-lookup"><span data-stu-id="e60f7-106">To determine checked items in a CheckedListBox control</span></span>  
  
1.  <span data-ttu-id="e60f7-107">反復処理する、<xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A>コレクションは 0 から始まるために、0 から始まるコレクション。</span><span class="sxs-lookup"><span data-stu-id="e60f7-107">Iterate through the <xref:System.Windows.Forms.CheckedListBox.CheckedItems%2A> collection, starting at 0 since the collection is zero-based.</span></span> <span data-ttu-id="e60f7-108">このメソッドが表示項目数の一覧で、メモには、全体的なリストではなく、項目がチェックされます。</span><span class="sxs-lookup"><span data-stu-id="e60f7-108">Note that this method will give you the item number in the list of checked items, not the overall list.</span></span> <span data-ttu-id="e60f7-109">次のコードでのようにテキストを表示する場合は、一覧の最初の項目がチェックされないため、2 番目の項目がチェックされて、ように"チェック項目 1 MyListItem2 ="です。</span><span class="sxs-lookup"><span data-stu-id="e60f7-109">So if the first item in the list is not checked and the second item is checked, the code below will display text like "Checked Item 1 = MyListItem2".</span></span>  
  
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
  
     - <span data-ttu-id="e60f7-110">または</span><span class="sxs-lookup"><span data-stu-id="e60f7-110">or -</span></span>  
  
2.  <span data-ttu-id="e60f7-111">ステップ実行、<xref:System.Windows.Forms.CheckedListBox.Items%2A>コレクション、コレクションは、0 から始まるために、0 から始まるおよび呼び出し、<xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A>の各項目に対してメソッドです。</span><span class="sxs-lookup"><span data-stu-id="e60f7-111">Step through the <xref:System.Windows.Forms.CheckedListBox.Items%2A> collection, starting at 0 since the collection is zero-based, and call the <xref:System.Windows.Forms.CheckedListBox.GetItemChecked%2A> method for each item.</span></span> <span data-ttu-id="e60f7-112">このメソッドが表示項目数、一覧全体での先頭の項目リストはチェックされませんので実行して、2 番目の項目がチェックされてのようなものが表示されます"の項目 2 = MyListItem2"です。</span><span class="sxs-lookup"><span data-stu-id="e60f7-112">Note that this method will give you the item number in the overall list, so if the first item in the list is not checked and the second item is checked, it will display something like "Item 2 = MyListItem2".</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e60f7-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="e60f7-113">See Also</span></span>  
 [<span data-ttu-id="e60f7-114">オプションのリストを表示するための Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="e60f7-114">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
