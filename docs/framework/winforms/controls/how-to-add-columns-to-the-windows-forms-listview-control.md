---
title: "方法 : Windows フォーム ListView コントロールに列を追加する | Microsoft Docs"
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
  - "列 [Windows フォーム], 追加 (ListView コントロールに)"
  - "リスト ビュー, 追加 (列を)"
  - "ListView コントロール [Windows フォーム], 追加 (列ヘッダーを)"
ms.assetid: 79174274-12ee-4a5d-80db-6ec02976d010
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : Windows フォーム ListView コントロールに列を追加する
詳細ビューの <xref:System.Windows.Forms.ListView> コントロールでは、各リスト項目に対して複数の列を表示できます。  複数の列を使用することにより、リストの各項目に関して何種類かの情報を表示できます。  たとえば、ファイル リストに、ファイル名、ファイルの種類、サイズ、およびファイルの最終更新日を表示できます。  作成後に列に情報を設定する方法の詳細については、「[方法 : Windows フォーム ListView コントロールの列にサブ項目を表示する](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)」を参照してください。  
  
### プログラムによって列を追加するには  
  
1.  コントロールの <xref:System.Windows.Forms.ListView.View%2A> プロパティを <xref:System.Windows.Forms.View> に設定します。  
  
2.  リスト ビューの <xref:System.Windows.Forms.ListView.Columns%2A> プロパティの <xref:System.Windows.Forms.ListView.ColumnHeaderCollection.Add%2A> メソッドを使用します。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#31)]  
  
## 参照  
 <xref:System.Windows.Forms.ListView>   
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)