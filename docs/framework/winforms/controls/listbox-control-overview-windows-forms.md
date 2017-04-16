---
title: "ListBox コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "ListBox"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "リスト ボックス, リスト ボックスの概要"
  - "ListBox コントロール [Windows フォーム], ListBox コントロールの概要"
ms.assetid: 37ea226b-6fc8-4c70-936a-c6af4e0cad4c
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# ListBox コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.ListBox> コントロールを使用すると、リストが表示され、ユーザーは 1 つ以上の項目を選択できます。  項目の合計数が表示限度を超えた場合は、<xref:System.Windows.Forms.ListBox> コントロールにスクロール バーが自動的に追加されます。  <xref:System.Windows.Forms.ListBox.MultiColumn%2A> プロパティを `true` に設定した場合は、項目が複数列で表示され、水平スクロール バーが表示されます。  <xref:System.Windows.Forms.ListBox.MultiColumn%2A> プロパティを `false` に設定した場合は、項目が単一列で表示され、垂直スクロール バーが表示されます。  <xref:System.Windows.Forms.ListBox.ScrollAlwaysVisible%2A> を `true` に設定している場合は、項目数に関係なくスクロール バーが表示されます。  <xref:System.Windows.Forms.ListBox.SelectionMode%2A> プロパティでは、一度に選択できるリスト項目の数を指定します。  
  
## ListBox コントロールの変更方法  
 <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> プロパティは、リスト ボックス内で最初に選択した項目に対応する整数値を取得します。  コードの <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 値を変更することによって、選択した項目をプログラムで変更できます。リスト内の対応する項目が、Windows フォーム上に強調表示されます。  選択項目がない場合、<xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 値は \-1 となります。  リストの最初の項目を選択した場合、<xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 値は 0 となります。  複数の項目が選択されている場合、<xref:System.Windows.Forms.ListBox.SelectedIndex%2A> 値は、リストの最上位に表示される選択項目を表します。  <xref:System.Windows.Forms.ListBox.SelectedItem%2A> プロパティは <xref:System.Windows.Forms.ListBox.SelectedIndex%2A> に似ていますが、項目自体 \(通常は文字列値\) を返す点が異なります。  <xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> プロパティは、リスト内の項目数を表します。<xref:System.Windows.Forms.ListBox.SelectedIndex%2A> はゼロから始まるため、<xref:System.Windows.Forms.ListBox.ObjectCollection.Count%2A> プロパティの値は、<xref:System.Windows.Forms.ListBox.SelectedIndex%2A> の最大値よりも常に 1 大きくなります。  
  
 <xref:System.Windows.Forms.ListBox> コントロールの項目を追加または削除するには、<xref:System.Windows.Forms.ListBox.ObjectCollection.Add%2A> メソッド、<xref:System.Windows.Forms.ListBox.ObjectCollection.Insert%2A> メソッド、<xref:System.Windows.Forms.ListBox.ObjectCollection.Clear%2A> メソッド、または <xref:System.Windows.Forms.ListBox.ObjectCollection.Remove%2A> メソッドを使用します。  デザイン時に <xref:System.Windows.Forms.ListBox.Items%2A> プロパティを使用して、リストに項目を追加することもできます。  
  
## 参照  
 <xref:System.Windows.Forms.ListBox>   
 [方法 : Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)   
 [方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)   
 [方法 : Windows フォームの ComboBox または ListBox コントロールをデータにバインドする ](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)   
 [ComboBox コントロールの概要](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)   
 [CheckedListBox コントロールの概要](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)   
 [オプションのリストを表示するための Windows フォーム コントロール](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)   
 [方法 : Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールのルックアップ テーブルを作成する](../../../../docs/framework/winforms/controls/create-a-lookup-table-for-a-wf-combobox-listbox.md)