---
title: '方法: Windows フォームのコレクションにアクセス キーを指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: 59e5cea29ee520b1f13f8fae98ae4042cc86fef7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538729"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a>方法: Windows フォームのコレクションにアクセス キーを指定する
-   個々 のコレクション アイテムは、キーにアクセスできます。 この機能が Windows フォーム アプリケーションでよく使用される多くのコレクション クラスに追加されました。 キー付きコレクションがアクセス可能なコレクション クラスの一部を次に示します。  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 コレクション内の項目に関連付けられたキーは、通常、項目の名前です。 次の手順では、コレクション クラスを使用して、一般的なタスクを実行する方法を示します。  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a>見つけて、制御コレクション内の入れ子になったコントロールにフォーカスを移動する  
  
-   使用して、<xref:System.Windows.Forms.Control.ControlCollection.Find%2A>と<xref:System.Windows.Forms.Control.Focus%2A>メソッドを検索し、フォーカスを移動するコントロールの名前を指定します。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a>イメージ コレクション内のイメージにアクセスするには  
  
-   使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A>プロパティにアクセスするイメージの名前を指定します。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a>選択されているタブとしてタブ ページを設定するには  
  
-   使用して、<xref:System.Windows.Forms.TabControl.SelectedTab%2A>と共に、<xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A>プロパティを選択したタブとして設定 タブ ページの名前を指定します。  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a>関連項目  
 [Windows フォームについて](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [方法: Windows フォームの ImageList コンポーネントにイメージを追加または削除する](../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
