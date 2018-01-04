---
title: "方法 : ListView コントロールに検索機能を追加する"
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
- cpp
helpviewer_keywords:
- lists [Windows Forms], enabling searching
- list views [Windows Forms], enabling searching
- ListView control [Windows Forms], adding search capabilities
- searching [Windows Forms], adding search capabilities to ListView control
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 111fc6e4945998c99e63560afab6104f4daf89e8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a><span data-ttu-id="26071-102">方法 : ListView コントロールに検索機能を追加する</span><span class="sxs-lookup"><span data-stu-id="26071-102">How to: Add Search Capabilities to a ListView Control</span></span>
<span data-ttu-id="26071-103">内の項目の大規模な一覧を使用する場合に多くの場合、<xref:System.Windows.Forms.ListView>をユーザーに検索機能を提供するコントロール。</span><span class="sxs-lookup"><span data-stu-id="26071-103">Oftentimes when working with a large list of items in a <xref:System.Windows.Forms.ListView> control, you want to offer search capabilities to the user.</span></span> <span data-ttu-id="26071-104"><xref:System.Windows.Forms.ListView>コントロールは、次の 2 つの異なる方法でこの機能を提供しています。 テキストに一致すると、場所を検索します。</span><span class="sxs-lookup"><span data-stu-id="26071-104">The <xref:System.Windows.Forms.ListView> control offers this capability in two different ways: text matching and location searching.</span></span>  
  
 <span data-ttu-id="26071-105"><xref:System.Windows.Forms.ListView.FindItemWithText%2A>メソッドでは、フルテキスト検索を実行することができます、<xref:System.Windows.Forms.ListView>リスト ビューまたは詳細ビューで、指定された検索文字列と省略可能な開始と終了インデックス。</span><span class="sxs-lookup"><span data-stu-id="26071-105">The <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method allows you to perform a text search on a <xref:System.Windows.Forms.ListView> in list or details view, given a search string and an optional starting and ending index.</span></span> <span data-ttu-id="26071-106">これに対し、<xref:System.Windows.Forms.ListView.FindNearestItem%2A>メソッド内の項目を見つけることができます、<xref:System.Windows.Forms.ListView>アイコンまたはタイル ビューで、一連の x 座標と y 座標と検索する方向を指定します。</span><span class="sxs-lookup"><span data-stu-id="26071-106">In contrast, the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method allows you to find an item in a <xref:System.Windows.Forms.ListView> in icon or tile view, given a set of x- and y-coordinates and a direction to search.</span></span>  
  
### <a name="to-find-an-item-using-text"></a><span data-ttu-id="26071-107">テキストを使用して項目を検索するには</span><span class="sxs-lookup"><span data-stu-id="26071-107">To find an item using text</span></span>  
  
1.  <span data-ttu-id="26071-108">作成、<xref:System.Windows.Forms.ListView>で、<xref:System.Windows.Forms.ListView.View%2A>プロパティに設定<xref:System.Windows.Forms.View.Details>または<xref:System.Windows.Forms.View.List>、および設定し、<xref:System.Windows.Forms.ListView>項目を含むです。</span><span class="sxs-lookup"><span data-stu-id="26071-108">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.ListView.View%2A> property set to <xref:System.Windows.Forms.View.Details> or <xref:System.Windows.Forms.View.List>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="26071-109">呼び出す、<xref:System.Windows.Forms.ListView.FindItemWithText%2A>メソッドを検索するには、項目のテキストを渡すことです。</span><span class="sxs-lookup"><span data-stu-id="26071-109">Call the <xref:System.Windows.Forms.ListView.FindItemWithText%2A> method, passing the text of the item you would like to find.</span></span>  
  
3.  <span data-ttu-id="26071-110">次のコード例は、基本的なを作成する方法を示します<xref:System.Windows.Forms.ListView>項目では、設定、およびユーザーからのテキスト入力一覧の項目の検索を使用しています。</span><span class="sxs-lookup"><span data-stu-id="26071-110">The following code example demonstrates how to create a basic <xref:System.Windows.Forms.ListView>, populate it with items, and use text input from the user to find an item in the list.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a><span data-ttu-id="26071-111">X 座標と y 座標を使用して項目を検索するには</span><span class="sxs-lookup"><span data-stu-id="26071-111">To find an item using x- and y-coordinates</span></span>  
  
1.  <span data-ttu-id="26071-112">作成、<xref:System.Windows.Forms.ListView>で、<xref:System.Windows.Forms.View>プロパティに設定<xref:System.Windows.Forms.View.SmallIcon>または<xref:System.Windows.Forms.View.LargeIcon>、および設定し、<xref:System.Windows.Forms.ListView>項目を含むです。</span><span class="sxs-lookup"><span data-stu-id="26071-112">Create a <xref:System.Windows.Forms.ListView> with the <xref:System.Windows.Forms.View> property set to <xref:System.Windows.Forms.View.SmallIcon> or <xref:System.Windows.Forms.View.LargeIcon>, and then populate the <xref:System.Windows.Forms.ListView> with items.</span></span>  
  
2.  <span data-ttu-id="26071-113">呼び出す、<xref:System.Windows.Forms.ListView.FindNearestItem%2A>を渡し、必要な x 座標と y 座標を検索したい方向メソッドです。</span><span class="sxs-lookup"><span data-stu-id="26071-113">Call the <xref:System.Windows.Forms.ListView.FindNearestItem%2A> method, passing the desired x- and y-coordinates and the direction you would like to search.</span></span>  
  
3.  <span data-ttu-id="26071-114">次のコード例は、基本的なアイコンを作成する方法を示します<xref:System.Windows.Forms.ListView>、そこに項目、およびキャプチャ、<xref:System.Windows.Forms.Control.MouseDown>上で最も近い項目を検索するイベントです。</span><span class="sxs-lookup"><span data-stu-id="26071-114">The following code example demonstrates how to create a basic icon <xref:System.Windows.Forms.ListView>, populate it with items, and capture the <xref:System.Windows.Forms.Control.MouseDown> event to find the nearest item in the up direction.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="26071-115">参照</span><span class="sxs-lookup"><span data-stu-id="26071-115">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>  
 <xref:System.Windows.Forms.ListView.FindNearestItem%2A>  
 [<span data-ttu-id="26071-116">ListView コントロール</span><span class="sxs-lookup"><span data-stu-id="26071-116">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="26071-117">ListView コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="26071-117">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="26071-118">方法: Windows フォーム ListView コントロールで項目を追加および削除する</span><span class="sxs-lookup"><span data-stu-id="26071-118">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
