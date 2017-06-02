---
title: "方法 : Windows フォーム ListView コントロールの列にサブ項目を表示する | Microsoft Docs"
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
  - "詳細ビュー"
  - "リスト項目"
  - "ListView コントロール [Windows フォーム], 追加 (ListSubItems を)"
  - "サブアイテム"
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Windows フォーム ListView コントロールの列にサブ項目を表示する
Windows フォームの <xref:System.Windows.Forms.ListView> コントロールは、詳細ビュー モードの場合、各項目に対して追加のテキスト \(サブ項目\) を表示できます。  最初の列には、項目のテキスト \(従業員番号など\) が表示されます。  2 番目、3 番目、それ以降の列には、関連付けられた 1 番目、2 番目、それ以降のサブ項目が表示されます。  
  
### リスト項目にサブ項目を追加するには  
  
1.  必要な列を追加します。  最初の列には項目の <xref:System.Windows.Forms.ListView.Text%2A> プロパティが表示されるため、必要なサブ項目数よりも 1 つ多い数の列が必要です。  列の追加については、「[方法 : Windows フォーム ListView コントロールに列を追加する](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)」を参照してください。  
  
2.  項目の <xref:System.Windows.Forms.ListViewItem.SubItems%2A> プロパティから返されたコレクションの <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> メソッドを呼び出します。  リストの項目に対して従業員の名前と所属部門を設定するコードの例を次に示します。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## 参照  
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [方法 : Windows フォーム ListView コントロールで項目を追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロールに列を追加する](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロールのアイコンを表示する](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)   
 [方法 : TreeView コントロールまたは ListView コントロール \(Windows フォーム\) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)