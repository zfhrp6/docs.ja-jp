---
title: "ComboBox コントロールの概要 (Windows フォーム) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ComboBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コンボ ボックス, コンボ ボックスの概要"
  - "ComboBox コントロール [Windows フォーム], ComboBox コントロールの概要"
  - "ドロップダウン リスト, ComboBox コントロール"
  - "ドロップダウン リスト, Windows フォーム"
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# ComboBox コントロールの概要 (Windows フォーム)
Windows フォーム <xref:System.Windows.Forms.ComboBox> コントロールを使用すると、ドロップダウン コンボ ボックスのデータを表示できます。  既定では、<xref:System.Windows.Forms.ComboBox> コントロールは 2 つの部分に分かれています。上の部分は、リスト項目を入力できるテキスト ボックスです。  下の部分は、項目のリストが表示されるリスト ボックスであり、このボックスから 1 つの項目を選択できます。  その他のスタイルのコンボ ボックスの詳細については、「[ListBox の代わりに Windows フォーム ComboBox を使用する場合](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)」を参照してください。  
  
 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> プロパティは、選択したリスト項目に対応する整数値を返します。  コードの <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 値を変更することによって、選択した項目をプログラムで変更できます。リスト内の対応する項目が、コンボ ボックス内のテキスト ボックスに表示されます。  選択項目がない場合、<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 値は \-1 となります。  リストの最初の項目を選択した場合、<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> 値は 0 となります。  <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> プロパティは <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> に似ていますが、項目自体 \(通常は文字列値\) を返す点が異なります。  <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> プロパティは、リスト内の項目数を表します。<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> はゼロから始まるため、<xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A> プロパティの値は、<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A> の最大値よりも常に 1 大きくなります。  
  
 <xref:System.Windows.Forms.ComboBox> コントロールの項目を追加または削除するには、<xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> メソッド、<xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A> メソッド、<xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A> メソッド、または <xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A> メソッドを使用します。  デザイナーの <xref:System.Windows.Forms.ComboBox.Items%2A> プロパティを使用して、リストに項目を追加することもできます。  
  
## 参照  
 <xref:System.Windows.Forms.ComboBox>   
 [ListBox コントロールの概要](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)   
 [ListBox の代わりに Windows フォーム ComboBox を使用する場合](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)   
 [方法 : Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)   
 [方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)   
 [方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールの特定の項目にアクセスする](../../../../docs/framework/winforms/controls/access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)   
 [方法 : Windows フォームの ComboBox または ListBox コントロールをデータにバインドする ](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)   
 [オプションのリストを表示するための Windows フォーム コントロール](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)   
 [方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールのルックアップ テーブルを作成する](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)