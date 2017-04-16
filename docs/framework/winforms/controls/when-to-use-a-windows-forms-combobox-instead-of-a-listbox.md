---
title: "ListBox の代わりに Windows フォーム ComboBox を使用する場合 | Microsoft Docs"
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
  - "バインド コントロール, コンボ ボックス"
  - "コンボ ボックス, 比較 (リスト ボックスと)"
  - "ComboBox コントロール [Windows フォーム], 比較 (ListBox と)"
  - "ListBox コントロール [Windows フォーム], アクセス (項目に)"
  - "ListBox コントロール [Windows フォーム], 追加と削除 (項目を)"
  - "ListBox コントロール [Windows フォーム], および ComboBox"
  - "ListCount プロパティ"
  - "ListIndex プロパティ"
  - "Windows フォーム コントロール, データ バインド"
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# ListBox の代わりに Windows フォーム ComboBox を使用する場合
<xref:System.Windows.Forms.ComboBox> コントロールと <xref:System.Windows.Forms.ListBox> コントロールは動作が似ており、置き換えることができる場合もあります。  ただし、各コントロールには、それぞれに適した用途があります。  
  
 通常、コンボ ボックスは選択可能な値を単に示す場合に使用し、リスト ボックスは選択可能な値をリスト上の項目に限定する場合に使用します。  リストにない値を入力できるように、コンボ ボックスにはテキスト ボックス フィールドが含まれます。  ただし、<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> プロパティを <xref:System.Windows.Forms.ComboBoxStyle> に設定している場合は除きます。  その場合は、最初の文字を入力すると、コントロールによって項目が選択されます。  
  
 また、コンボ ボックスを使用すると、フォーム上の領域を節約できます。  ユーザーが下向きの矢印をクリックするまでリスト全体が表示されないため、リスト ボックスを配置できない小さな領域でも、コンボ ボックスを簡単に配置できます。  ただし、<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> プロパティが <xref:System.Windows.Forms.ComboBoxStyle> に設定されている場合、リスト全体が表示されるため、コンボ ボックスはリスト ボックスよりも大きい領域を占めることになります。  
  
## 参照  
 <xref:System.Windows.Forms.ComboBox>   
 <xref:System.Windows.Forms.ListBox>   
 [方法 : Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)   
 [方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)   
 [オプションのリストを表示するための Windows フォーム コントロール](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)