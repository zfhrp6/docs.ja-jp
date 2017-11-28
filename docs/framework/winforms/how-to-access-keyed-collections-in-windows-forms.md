---
title: "方法: Windows フォームのコレクションにアクセス キーを指定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2bca9b56f37c815bfa9f1520467ae0ae864c14ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="a9fc0-102">方法: Windows フォームのコレクションにアクセス キーを指定する</span><span class="sxs-lookup"><span data-stu-id="a9fc0-102">How to: Access Keyed Collections in Windows Forms</span></span>
-   <span data-ttu-id="a9fc0-103">個々 のコレクション アイテムは、キーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a9fc0-103">You can access individual collection items by key.</span></span> <span data-ttu-id="a9fc0-104">この機能が Windows フォーム アプリケーションでよく使用される多くのコレクション クラスに追加されました。</span><span class="sxs-lookup"><span data-stu-id="a9fc0-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="a9fc0-105">キー付きコレクションがアクセス可能なコレクション クラスの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a9fc0-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
-   <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
-   <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
-   <xref:System.Windows.Forms.Control.ControlCollection>  
  
-   <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
-   <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="a9fc0-106">コレクション内の項目に関連付けられたキーは、通常、項目の名前です。</span><span class="sxs-lookup"><span data-stu-id="a9fc0-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="a9fc0-107">次の手順では、コレクション クラスを使用して、一般的なタスクを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a9fc0-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="a9fc0-108">見つけて、制御コレクション内の入れ子になったコントロールにフォーカスを移動する</span><span class="sxs-lookup"><span data-stu-id="a9fc0-108">To find and give focus to a nested control in a control collection</span></span>  
  
-   <span data-ttu-id="a9fc0-109">使用して、<xref:System.Windows.Forms.Control.ControlCollection.Find%2A>と<xref:System.Windows.Forms.Control.Focus%2A>メソッドを検索し、フォーカスを移動するコントロールの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a9fc0-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="a9fc0-110">イメージ コレクション内のイメージにアクセスするには</span><span class="sxs-lookup"><span data-stu-id="a9fc0-110">To access an image in an image collection</span></span>  
  
-   <span data-ttu-id="a9fc0-111">使用して、<xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A>プロパティにアクセスするイメージの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a9fc0-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="a9fc0-112">選択されているタブとしてタブ ページを設定するには</span><span class="sxs-lookup"><span data-stu-id="a9fc0-112">To set a tab page as the selected tab</span></span>  
  
-   <span data-ttu-id="a9fc0-113">使用して、<xref:System.Windows.Forms.TabControl.SelectedTab%2A>と共に、<xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A>プロパティを選択したタブとして設定 タブ ページの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a9fc0-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a9fc0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9fc0-114">See Also</span></span>  
 [<span data-ttu-id="a9fc0-115">Windows フォームについて</span><span class="sxs-lookup"><span data-stu-id="a9fc0-115">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [<span data-ttu-id="a9fc0-116">方法: Windows フォームの ImageList コンポーネントにイメージを追加または削除する</span><span class="sxs-lookup"><span data-stu-id="a9fc0-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
