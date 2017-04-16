---
title: "方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える | Microsoft Docs"
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
  - "CheckedListBox コントロール [Windows フォーム], 並べ替え"
  - "コンボ ボックス, 並べ替え (内容の)"
  - "ComboBox コントロール [Windows フォーム], 並べ替え (内容の)"
  - "リスト ボックス, 並べ替え (内容の)"
  - "ListBox コントロール [Windows フォーム], 並べ替え (内容の)"
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える
Windows フォームのコントロールは、データ連結されているときには並べ替えができません。  並べ替えたデータを表示するには、並べ替えがサポートされているデータ ソースを使用して、並べ替えを行います。  並べ替えがサポートされているデータ ソースには、データ ビュー、データ ビュー マネージャー、および並べ替えられた配列があります。  
  
 コントロールがデータ バインドされていない場合、並べ替えができます。  
  
### リストを並べ替えるには  
  
1.  `Sorted`  プロパティを `true` に設定します。  
  
     この設定によって、既存のリスト項目はすべて並べ替えの順序に従って移動されます。  
  
## 参照  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 <xref:System.Windows.Forms.CheckedListBox>   
 [Windows フォームでのデータ バインド](../../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [方法 : Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)   
 [ListBox の代わりに Windows フォーム ComboBox を使用する場合](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)   
 [オプションのリストを表示するための Windows フォーム コントロール](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)