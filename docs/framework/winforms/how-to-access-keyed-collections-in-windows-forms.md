---
title: "方法 : Windows フォームのコレクションにアクセス キーを指定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コレクション, アクセス (キーを使用して)"
  - "キーが指定されたコレクション [Windows フォーム]"
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 方法 : Windows フォームのコレクションにアクセス キーを指定する
-   個々のコレクション項目にはキーでアクセスできます。  この機能は、Windows フォーム アプリケーションによって一般に使用される多数のコレクション クラスに追加されました。  アクセスできるキーが指定されたコレクションのあるコレクション クラスの一部を次の一覧に示します。  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 コレクションの項目に関連付けられるキーは、一般に項目名です。  次の手順では、コレクション クラスを使用し、一般的なタスクを実行する方法を説明します。  
  
### コントロール コレクションの中で入れ子のコントロールを検索し、フォーカスの移動先にします。  
  
-   <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> メソッドと <xref:System.Windows.Forms.Control.Focus%2A> メソッドを使用し、検索してフォーカスの移動先にするコントロール名を指定します。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### イメージ コレクションのイメージにアクセスするには  
  
-   <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> プロパティを使用して、アクセスするイメージ名を指定します。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### タブ ページを選択済みのタブとして設定するには  
  
-   <xref:System.Windows.Forms.TabControl.SelectedTab%2A> プロパティと <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> プロパティを使用し、選択済みのタブとして設定するタブ ページ名を指定します。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## 参照  
 [Windows フォームについて](../../../docs/framework/winforms/getting-started-with-windows-forms.md)   
 [方法 : Windows フォームの ImageList コンポーネントにイメージを追加または削除する](../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)