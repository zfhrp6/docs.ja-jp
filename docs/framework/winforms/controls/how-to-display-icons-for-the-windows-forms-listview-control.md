---
title: "方法 : Windows フォーム ListView コントロールのアイコンを表示する | Microsoft Docs"
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
  - "アイコン, 表示 (ListView コントロールの)"
  - "ImageList コンポーネント [Windows フォーム], ListView コントロールを含む"
  - "リスト ビュー, 表示 (アイコンを)"
  - "一覧, 表示 (アイコンを)"
  - "ListView コントロール [Windows フォーム], 表示 (アイコンを)"
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォーム ListView コントロールのアイコンを表示する
Windows フォーム <xref:System.Windows.Forms.ListView> \(リスト ビュー\) コントロールには、3 つのイメージ リストからアイコンを表示できます。  List、Details、および SmallIcon ビューでは、<xref:System.Windows.Forms.ListView.SmallImageList%2A> プロパティに指定されたイメージ リストのイメージが表示されます。  LargeIcon \(大きいアイコン\) ビューでは、<xref:System.Windows.Forms.ListView.LargeImageList%2A> プロパティに指定されたイメージ リストのイメージが表示されます。  リスト ビューでは、大きいアイコンまたは小さいアイコンの横に、<xref:System.Windows.Forms.ListView.StateImageList%2A> プロパティに設定された別のアイコンを表示できます。  イメージ リストの詳細については、「[ImageList コンポーネント](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)」および「[方法 : Windows フォームの ImageList コンポーネントにイメージを追加または削除する](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)」を参照してください。  
  
### リスト ビューにイメージを表示するには  
  
1.  適切なプロパティ \(<xref:System.Windows.Forms.ListView.SmallImageList%2A>、<xref:System.Windows.Forms.ListView.LargeImageList%2A>、または <xref:System.Windows.Forms.ListView.StateImageList%2A>\) を、使用する既存の <xref:System.Windows.Forms.ImageList> コンポーネントに設定します。  
  
     これらのプロパティは、デザイナーの \[プロパティ\] ウィンドウで設定するか、またはコードで設定できます。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2.  アイコンが関連付けられているリスト項目のそれぞれに対して、<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> プロパティまたは <xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A> プロパティを設定します。  
  
     これらのプロパティは、コードで設定するか、または **ListViewItem コレクション エディター**で設定できます。  **ListViewItem コレクション エディター**を開くには、**\[プロパティ\]** ウィンドウの <xref:System.Windows.Forms.ListView.Items%2A> プロパティの横にある省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックします。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## 参照  
 [ListView コントロールの概要](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [方法 : Windows フォーム ListView コントロールで項目を追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [方法 : Windows フォーム ListView コントロールに列を追加する](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)   
 [方法 : TreeView コントロールまたは ListView コントロール \(Windows フォーム\) にカスタム情報を追加する](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)   
 [ImageList コンポーネント](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)