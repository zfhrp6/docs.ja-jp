---
title: "方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールの特定の項目にアクセスする | Microsoft Docs"
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
  - "CheckedListBox コントロール [Windows フォーム], アクセス (項目に)"
  - "コンボ ボックス, アクセス (項目に)"
  - "ComboBox コントロール [Windows フォーム], アクセス (項目に)"
  - "リスト ボックス, アクセス (項目に)"
  - "ListBox コントロール [Windows フォーム], アクセス (項目に)"
  - "ListBox コントロール [Windows フォーム], 返す (項目情報を)"
ms.assetid: 1216742f-bcf9-4ff8-8a62-d7c9053c2b96
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールの特定の項目にアクセスする
Windows フォームのコンボ ボックス、リスト ボックス、またはチェック ボックス付きリスト ボックス内の特定の項目にアクセスすることは、必要不可欠なタスクです。  アクセスすると、リスト内の特定の場所にある項目をプロクラムによって判断できます。  
  
### 特定の項目にアクセスするには  
  
1.  特定の項目のインデックスを使用して、`Items`  コレクションに問い合わせます。  
  
    ```vb  
    Private Function GetItemText(i As Integer) As String  
       ' Return the text of the item using the index:  
       Return ComboBox1.Items(i).ToString  
    End Function  
  
    ```  
  
    ```csharp  
    private string GetItemText(int i)  
    {  
       // Return the text of the item using the index:  
       return (comboBox1.Items[i].ToString());  
    }  
  
    ```  
  
    ```cpp  
    private:  
       String^ GetItemText(int i)  
       {  
          // Return the text of the item using the index:  
          return (comboBox1->Items->Item[i]->ToString());  
       }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms.CheckedListBox>   
 [オプションのリストを表示するための Windows フォーム コントロール](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)