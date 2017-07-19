---
title: "方法 : Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "CheckedListBox コントロール [Windows フォーム], 追加と削除 (項目を)"
  - "コンボ ボックス, 追加 (アイテムを)"
  - "コンボ ボックス, 削除 (項目を)"
  - "ComboBox コントロール [Windows フォーム], 追加と削除 (項目を)"
  - "リスト ボックス, 追加 (アイテムを)"
  - "リスト ボックス, 削除 (項目を)"
  - "ListBox コントロール [Windows フォーム], 追加と削除 (項目を)"
ms.assetid: 7224c8d2-4118-443e-ae1e-d7c17d1e69ee
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する
Windows フォームのコンボ ボックス、リスト ボックス、およびチェック ボックス付きリスト ボックスは、さまざまなデータ ソースにバインドできます。このため、これらのコントロールに項目を追加する方法はいくつかあります。  ここでは、データ バインディングの必要がない、最も簡単な方法を示します。  通常、表示される項目は文字列ですが、任意のオブジェクトを使用することもできます。  コントロールに表示されているテキストは、オブジェクトの `ToString`  メソッドが返した値です。  
  
### 項目を追加するには  
  
1.  `ObjectCollection` クラスの `Add` メソッドを使用して、文字列またはオブジェクトを一覧に追加します。  コレクションは、`Items`  プロパティを使用して参照します。  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     または  
  
2.  `Insert`  メソッドを使用して、文字列またはオブジェクトをリスト内の任意の場所に挿入します。  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     または  
  
3.  `Items`  コレクションに配列全体を割り当てます。  
  
    ```vb  
    Dim ItemObject(9) As System.Object  
    Dim i As Integer  
       For i = 0 To 9  
       ItemObject(i) = "Item" & i  
    Next i  
    ListBox1.Items.AddRange(ItemObject)  
  
    ```  
  
    ```csharp  
    System.Object[] ItemObject = new System.Object[10];  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = "Item" + i;  
    }  
    listBox1.Items.AddRange(ItemObject);  
  
    ```  
  
    ```cpp  
    Array<System::Object^>^ ItemObject = gcnew Array<System::Object^>(10);  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = String::Concat("Item", i.ToString());  
    }  
    listBox1->Items->AddRange(ItemObject);  
    ```  
  
### 項目を削除するには  
  
1.  項目を削除するには、`Remove`  メソッドまたは `RemoveAt`  メソッドを呼び出します。  
  
     `Remove` に削除する項目を指定するには1 とおりの引数があります。`RemoveAt`指定したインデックス番号で項目を削除します。  
  
    ```vb  
    ' To remove item with index 0:  
    ComboBox1.Items.RemoveAt(0)  
    ' To remove currently selected item:  
    ComboBox1.Items.Remove(ComboBox1.SelectedItem)  
    ' To remove "Tokyo" item:  
    ComboBox1.Items.Remove("Tokyo")  
  
    ```  
  
    ```csharp  
    // To remove item with index 0:  
    comboBox1.Items.RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1.Items.Remove(comboBox1.SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1.Items.Remove("Tokyo");  
  
    ```  
  
    ```cpp  
    // To remove item with index 0:  
    comboBox1->Items->RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1->Items->Remove(comboBox1->SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1->Items->Remove("Tokyo");  
    ```  
  
### すべての項目を削除するには  
  
1.  `Clear` メソッドを呼び出して、コレクションからすべての項目を削除します。  
  
    ```vb  
    ListBox1.Items.Clear()  
  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms.CheckedListBox>   
 [方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)   
 [ListBox の代わりに Windows フォーム ComboBox を使用する場合](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)   
 [オプションのリストを表示するための Windows フォーム コントロール](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)