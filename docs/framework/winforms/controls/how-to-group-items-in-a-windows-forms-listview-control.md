---
title: "方法 : Windows フォーム ListView コントロールの項目をグループ化する | Microsoft Docs"
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
  - "グループ化"
  - "グループ"
  - "グループ, Windows フォーム コントロールの"
  - "リスト ビュー, グループ化 (項目を)"
  - "一覧, グループ化 (項目を)"
  - "ListView コントロール [Windows フォーム], グループ化 (項目を)"
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# 方法 : Windows フォーム ListView コントロールの項目をグループ化する
<xref:System.Windows.Forms.ListView> コントロールのグループ化機能を使用すると、関連する複数の項目をグループ化して表示できます。  これらのグループは、画面上で、グループ タイトルを含む水平方向のグループ ヘッダーで区切られます。  <xref:System.Windows.Forms.ListView> グループを使って、項目をアルファベット順、日付順、またはその他の論理的なグループにまとめることにより、大きなリストの内部を移動することが簡単になります。  次のイメージは、グループ化した項目の例を示しています。  
  
 ![ListView グループ](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
ListView でグループ化された項目  
  
 グループ化を有効にするには、まず、デザイナーまたはプログラムで、1 つ以上のグループを作成します。  グループを定義した後で、そのグループに <xref:System.Windows.Forms.ListView> 項目を割り当てることができます。  プログラムによって、項目を 1 つのグループから別のグループに移動することもできます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView> を [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] で使用できるのは、アプリケーションから <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName> メソッドを呼び出した場合だけです。  以前のオペレーティング システムでは、グループに関連するコードは無効になり、グループは表示されません。  詳細については、「<xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=fullName>」を参照してください。  
  
### グループを追加するには  
  
1.  <xref:System.Windows.Forms.ListView.Groups%2A> コレクションの <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> メソッドを使用します。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### グループを削除するには  
  
1.  <xref:System.Windows.Forms.ListView.Groups%2A> コレクションの <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> メソッドまたは <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> メソッドを使用します。  
  
     <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> メソッドは 1 つのグループを削除します。<xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> メソッドはリストのすべてのグループを削除します。  
  
    > [!NOTE]
    >  グループを削除しても、そのグループ内の項目は削除されません。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### 項目をグループに割り当てたりグループ間で項目を移動したりするには  
  
1.  個々の項目の <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=fullName> プロパティを設定します。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## 参照  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.ListViewGroup>   
 [ListView コントロール](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/ja-jp/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)   
 [方法 : Windows フォーム ListView コントロールで項目を追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)