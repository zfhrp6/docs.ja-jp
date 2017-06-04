---
title: "方法 : ListView コントロールに検索機能を追加する | Microsoft Docs"
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
  - "リスト ビュー, 有効化 (検索を)"
  - "一覧, 有効化 (検索を)"
  - "ListView コントロール [Windows フォーム], 追加 (検索機能を)"
  - "検索, 追加 (ListView コントロールに検索機能を)"
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : ListView コントロールに検索機能を追加する
<xref:System.Windows.Forms.ListView> コントロールで大きな項目リストを使用するときは、多くの場合、ユーザーに検索機能を提供する必要があります。  <xref:System.Windows.Forms.ListView> コントロールは、テキスト一致および位置検索という 2 つの方法でこの機能を提供します。  
  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A> メソッドを使用すると、検索文字列とオプションの開始インデックスと終了インデックスを指定して、リスト ビューや詳細ビューの <xref:System.Windows.Forms.ListView> でテキスト検索を実行できます。  これと対照的に、<xref:System.Windows.Forms.ListView.FindNearestItem%2A> メソッドを使用すると、x 座標と y 座標および検索方向を指定して、アイコン ビューや並べて表示ビューの <xref:System.Windows.Forms.ListView> で項目を検索できます。  
  
### テキストを使用して項目を検索するには  
  
1.  <xref:System.Windows.Forms.ListView.View%2A> プロパティを <xref:System.Windows.Forms.View> または <xref:System.Windows.Forms.View> に設定して <xref:System.Windows.Forms.ListView> を作成し、<xref:System.Windows.Forms.ListView> に項目を設定します。  
  
2.  <xref:System.Windows.Forms.ListView.FindItemWithText%2A> メソッドを呼び出して、検索項目のテキストを渡します。  
  
3.  次のコード例は、基本的な <xref:System.Windows.Forms.ListView> を作成して項目を設定し、ユーザーによるテキスト入力を使用してリスト内の項目を検索する方法を示しています。  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### x 座標と y 座標を使用して項目を検索するには  
  
1.  <xref:System.Windows.Forms.View> プロパティを <xref:System.Windows.Forms.View> または <xref:System.Windows.Forms.View> に設定して <xref:System.Windows.Forms.ListView> を作成し、<xref:System.Windows.Forms.ListView> に項目を設定します。  
  
2.  <xref:System.Windows.Forms.ListView.FindNearestItem%2A> メソッドを呼び出して、適切な x 座標と y 座標および検索方向を渡します。  
  
3.  次のコード例は、基本アイコン <xref:System.Windows.Forms.ListView> を作成して項目を設定し、<xref:System.Windows.Forms.Control.MouseDown> イベントをキャプチャして、最も近い項目を上方向に検索する方法を示しています。  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## 参照  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>   
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>   
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [方法 : Windows フォーム ListView コントロールで項目を追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)