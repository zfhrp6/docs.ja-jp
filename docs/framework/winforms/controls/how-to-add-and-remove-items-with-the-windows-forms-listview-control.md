---
title: "方法 : Windows フォーム ListView コントロールで項目を追加および削除する | Microsoft Docs"
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
  - "リスト ビュー, 追加 (リスト項目を)"
  - "ListView コントロール [Windows フォーム], 追加 (リスト項目を)"
  - "ListView コントロール [Windows フォーム], データの読み込み"
ms.assetid: 1b35a80a-edd8-495f-a807-a28c4aae52c6
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : Windows フォーム ListView コントロールで項目を追加および削除する
Windows フォームの <xref:System.Windows.Forms.ListView> コントロールに項目を追加するには、項目を指定し、その項目にプロパティを割り当てます。  リスト項目の追加または削除は、いつでも実行できます。  
  
### プログラムによって項目を追加するには  
  
1.  <xref:System.Windows.Forms.ListView.Items%2A> プロパティの <xref:System.Windows.Forms.ListView.ListViewItemCollection.Add%2A> メソッドを使用します。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#11)]  
  
### プログラムによって項目を削除するには  
  
1.  <xref:System.Windows.Forms.ListView.Items%2A> プロパティの <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> メソッドまたは <xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> メソッドを使用します。  <xref:System.Windows.Forms.ListView.ListViewItemCollection.RemoveAt%2A> メソッドは 1 つの項目を削除します。<xref:System.Windows.Forms.ListView.ListViewItemCollection.Clear%2A> メソッドはリストのすべての項目を削除します。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#12)]  
  
## 参照  
 <xref:System.Windows.Forms.ListView>   
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)