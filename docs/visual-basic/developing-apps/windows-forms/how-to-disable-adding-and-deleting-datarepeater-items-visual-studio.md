---
title: "方法 : DataRepeater の項目の追加と削除を無効にする (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b15fe6fb5190855126ffa60ac488aaa74ad9b5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a><span data-ttu-id="99e16-102">方法 : DataRepeater の項目の追加と削除を無効にする (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="99e16-102">How to: Disable Adding and Deleting DataRepeater Items (Visual Studio)</span></span>
<span data-ttu-id="99e16-103">既定では、ユーザーは追加し、項目の削除、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。</span><span class="sxs-lookup"><span data-stu-id="99e16-103">By default, users can add and delete items in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="99e16-104">ユーザーは、CTRL キーを押しながら N キーを押して、新しい項目を追加できるときに、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A>にフォーカスがあるかをクリックして、 **AddNewItem**のボタンでは、<xref:System.Windows.Forms.BindingNavigator>コントロール。</span><span class="sxs-lookup"><span data-stu-id="99e16-104">Users can add a new item by pressing CTRL+N when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **AddNewItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span> <span data-ttu-id="99e16-105">ユーザーがキーを押して、項目を削除できるときに削除、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A>にフォーカスがあるかをクリックして、 **DeleteItem**のボタンでは、<xref:System.Windows.Forms.BindingNavigator>コントロール。</span><span class="sxs-lookup"><span data-stu-id="99e16-105">Users can delete an item by pressing DELETE when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **DeleteItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
 <span data-ttu-id="99e16-106">追加と削除のデザイン時または実行時に無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="99e16-106">You can disable adding and/or deleting at design time or at run time.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a><span data-ttu-id="99e16-107">デザイン時に追加と削除を無効にするには</span><span class="sxs-lookup"><span data-stu-id="99e16-107">To disable adding and deleting at design time</span></span>  
  
1.  <span data-ttu-id="99e16-108">Windows フォーム デザイナーで、選択、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。</span><span class="sxs-lookup"><span data-stu-id="99e16-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="99e16-109">コントロールの下のセクションを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99e16-109">You must select the lower section of the control.</span></span> <span data-ttu-id="99e16-110">項目テンプレートのセクションを選択すると、異なる一連のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="99e16-110">If you select the item template section, a different set of properties will be displayed.</span></span>  
  
2.  <span data-ttu-id="99e16-111">[プロパティ] ウィンドウで、設定、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A>プロパティを**False**です。</span><span class="sxs-lookup"><span data-stu-id="99e16-111">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> property to **False**.</span></span>  
  
3.  <span data-ttu-id="99e16-112">設定、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A>プロパティを**False**です。</span><span class="sxs-lookup"><span data-stu-id="99e16-112">Set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> property to **False**.</span></span>  
  
4.  <span data-ttu-id="99e16-113">Windows フォーム デザイナーで、選択、<xref:System.Windows.Forms.BindingNavigator>コントロールをクリックして、 **AddNewItem**ボタン (に正符号のボタン)。</span><span class="sxs-lookup"><span data-stu-id="99e16-113">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **AddNewItem** button (the button with a plus sign on it).</span></span>  
  
5.  <span data-ttu-id="99e16-114">[プロパティ] ウィンドウで、設定、<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>プロパティを**False**です。</span><span class="sxs-lookup"><span data-stu-id="99e16-114">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
6.  <span data-ttu-id="99e16-115">Windows フォーム デザイナーで、選択、<xref:System.Windows.Forms.BindingNavigator>コントロールをクリックして、 **DeleteItem** (に赤い x 印が付いたボタン) のボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="99e16-115">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **DeleteItem** button (the button with a red X on it).</span></span>  
  
7.  <span data-ttu-id="99e16-116">[プロパティ] ウィンドウで、設定、<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>プロパティを**False**です。</span><span class="sxs-lookup"><span data-stu-id="99e16-116">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
8.  <span data-ttu-id="99e16-117">コンポーネント トレイに次のように選択します。、<xref:System.Windows.Forms.BindingSource>先、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>がバインドされています。</span><span class="sxs-lookup"><span data-stu-id="99e16-117">In the Component Tray, select the <xref:System.Windows.Forms.BindingSource> to which the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is bound.</span></span>  
  
9. <span data-ttu-id="99e16-118">[プロパティ] ウィンドウで、設定、<xref:System.Windows.Forms.BindingSource.AllowNew%2A>プロパティを**False**です。</span><span class="sxs-lookup"><span data-stu-id="99e16-118">In the Properties window, set the <xref:System.Windows.Forms.BindingSource.AllowNew%2A> property to **False**.</span></span>  
  
10. <span data-ttu-id="99e16-119">Windows フォーム デザイナーで、ダブルクリック、 **DeleteItem**ボタン コード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="99e16-119">In the Windows Forms Designer, double-click the **DeleteItem** button to open the Code Editor.</span></span>  
  
11. <span data-ttu-id="99e16-120">イベント ドロップダウン リストで、選択、`BindingNavigatorDeleteItem_EnabledChanged`イベント。</span><span class="sxs-lookup"><span data-stu-id="99e16-120">In the Events drop-down list, select the `BindingNavigatorDeleteItem_EnabledChanged` event.</span></span>  
  
12. <span data-ttu-id="99e16-121">`BindingNavigatorDeleteItem_EnabledChanged` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="99e16-121">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="99e16-122">この手順が必要なのは、現在のレコードが変更されるたびに <xref:System.Windows.Forms.BindingSource> によって **DeleteItem** ボタンが有効になるためです。</span><span class="sxs-lookup"><span data-stu-id="99e16-122">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a><span data-ttu-id="99e16-123">実行時に追加と削除を無効にするには</span><span class="sxs-lookup"><span data-stu-id="99e16-123">To disable adding and deleting at run time</span></span>  
  
1.  <span data-ttu-id="99e16-124">Windows フォーム デザイナーで、フォームをダブルクリックしてコード エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="99e16-124">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="99e16-125">`Form_Load` イベントに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="99e16-125">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  <span data-ttu-id="99e16-126">`BindingNavigatorDeleteItem_EnabledChanged` イベント ハンドラーに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="99e16-126">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="99e16-127">この手順が必要なのは、現在のレコードが変更されるたびに <xref:System.Windows.Forms.BindingSource> によって **DeleteItem** ボタンが有効になるためです。</span><span class="sxs-lookup"><span data-stu-id="99e16-127">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99e16-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="99e16-128">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="99e16-129">DataRepeater コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="99e16-129">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="99e16-130">DataRepeater コントロールのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="99e16-130">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
