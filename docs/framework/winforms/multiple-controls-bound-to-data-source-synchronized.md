---
title: "方法 : 複数のコントロールを 1 つのデータ ソースにバインドして同期状態を保つ"
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
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2573f342530e59fa05e7f24342f251990b2ce47d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a><span data-ttu-id="a8760-102">方法 : 複数のコントロールを 1 つのデータ ソースにバインドして同期状態を保つ</span><span class="sxs-lookup"><span data-stu-id="a8760-102">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>
<span data-ttu-id="a8760-103">Windows フォームでのデータ バインディングを使用する場合に多くの場合は、複数のコントロールが、同じデータ ソースにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="a8760-103">Oftentimes when working with data binding in Windows Forms, multiple controls are bound to the same data source.</span></span> <span data-ttu-id="a8760-104">場合によっては、コントロールのバインド プロパティのデータ ソースと他の同期を保つための余分な手順を実行するために必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="a8760-104">In some cases, it may be necessary to take extra steps to ensure that the bound properties of the controls remain synchronized with each other and the data source.</span></span> <span data-ttu-id="a8760-105">次の手順は、2 つの状況で必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8760-105">These steps are necessary in two situations:</span></span>  
  
-   <span data-ttu-id="a8760-106">データ ソースを実装しない場合<xref:System.ComponentModel.IBindingList>、したがってを生成および<xref:System.ComponentModel.IBindingList.ListChanged>の種類のイベント<xref:System.ComponentModel.ListChangedType.ItemChanged>です。</span><span class="sxs-lookup"><span data-stu-id="a8760-106">If the data source does not implement <xref:System.ComponentModel.IBindingList>, and therefore generate <xref:System.ComponentModel.IBindingList.ListChanged> events of type <xref:System.ComponentModel.ListChangedType.ItemChanged>.</span></span>  
  
-   <span data-ttu-id="a8760-107">場合は、データ ソースを実装して<xref:System.ComponentModel.IEditableObject>です。</span><span class="sxs-lookup"><span data-stu-id="a8760-107">If the data source implements <xref:System.ComponentModel.IEditableObject>.</span></span>  
  
 <span data-ttu-id="a8760-108">前者の場合で使用できます、<xref:System.Windows.Forms.BindingSource>データ ソース コントロールをバインドします。</span><span class="sxs-lookup"><span data-stu-id="a8760-108">In the former case, you can use a <xref:System.Windows.Forms.BindingSource> to bind the data source to the controls.</span></span> <span data-ttu-id="a8760-109">後者の場合でを使用して、<xref:System.Windows.Forms.BindingSource>を処理し、<xref:System.Windows.Forms.BindingSource.BindingComplete>イベントと呼び出し<xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A>、関連する<xref:System.Windows.Forms.BindingManagerBase>です。</span><span class="sxs-lookup"><span data-stu-id="a8760-109">In the latter case, you use a <xref:System.Windows.Forms.BindingSource> and handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and call <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> on the associated <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8760-110">例</span><span class="sxs-lookup"><span data-stu-id="a8760-110">Example</span></span>  
 <span data-ttu-id="a8760-111">次のコード例は、3 つのコントロールをバインドする方法を示します: 2 つのテキスト ボックス コントロールと<xref:System.Windows.Forms.DataGridView>コントロール-内の同じ列に、<xref:System.Data.DataSet>を使用して、<xref:System.Windows.Forms.BindingSource>コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="a8760-111">The following code example demonstrates how to bind three controls—two text-box controls and a <xref:System.Windows.Forms.DataGridView> control—to the same column in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="a8760-112">この例は、処理する方法を示します、<xref:System.Windows.Forms.BindingSource.BindingComplete>イベントを 1 つのテキスト ボックスのテキスト値が変更されたときに、追加のテキスト ボックスを確認してください、<xref:System.Windows.Forms.DataGridView>コントロールは、適切な値で更新されます。</span><span class="sxs-lookup"><span data-stu-id="a8760-112">This example demonstrates how to handle the <xref:System.Windows.Forms.BindingSource.BindingComplete> event and ensure that when the text value of one text box is changed, the additional text box and the <xref:System.Windows.Forms.DataGridView> control are updated with the correct value.</span></span>  
  
 <span data-ttu-id="a8760-113">この例では、<xref:System.Windows.Forms.BindingSource>データ ソースと、コントロールをバインドします。</span><span class="sxs-lookup"><span data-stu-id="a8760-113">The example uses a <xref:System.Windows.Forms.BindingSource> to bind the data source and the controls.</span></span> <span data-ttu-id="a8760-114">コントロールをデータ ソースに直接バインドを取得する代わりに、<xref:System.Windows.Forms.BindingManagerBase>から、フォームのバインドの<xref:System.Windows.Forms.Control.BindingContext%2A>し、処理、<xref:System.Windows.Forms.BindingManagerBase.BindingComplete>イベントを<xref:System.Windows.Forms.BindingManagerBase>です。</span><span class="sxs-lookup"><span data-stu-id="a8760-114">Alternatively, you can bind the controls directly to the data source and retrieve the <xref:System.Windows.Forms.BindingManagerBase> for the binding from the form's <xref:System.Windows.Forms.Control.BindingContext%2A> and then handle the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event for the <xref:System.Windows.Forms.BindingManagerBase>.</span></span> <span data-ttu-id="a8760-115">これを行う方法の例は、ヘルプ ページを参照して、<xref:System.Windows.Forms.BindingManagerBase.BindingComplete>のイベント<xref:System.Windows.Forms.BindingManagerBase>です。</span><span class="sxs-lookup"><span data-stu-id="a8760-115">For an example of how to do this, see the Help page about the <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> event of <xref:System.Windows.Forms.BindingManagerBase>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a8760-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="a8760-116">Compiling the Code</span></span>  
  
-   <span data-ttu-id="a8760-117">このコード例が必要です。</span><span class="sxs-lookup"><span data-stu-id="a8760-117">This code example requires</span></span>  
  
-   <span data-ttu-id="a8760-118"><xref:System>、<xref:System.Windows.Forms>、および <xref:System.Drawing> の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="a8760-118">References to the <xref:System>, <xref:System.Windows.Forms>, and <xref:System.Drawing> assemblies.</span></span>  
  
-   <span data-ttu-id="a8760-119">フォームを<xref:System.Windows.Forms.Form.Load>イベントを処理を呼び出すと、`InitializeControlsAndDataSource`メソッドから、フォームの例では<xref:System.Windows.Forms.Form.Load>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="a8760-119">A form with the <xref:System.Windows.Forms.Form.Load> event handled and a call to the `InitializeControlsAndDataSource` method in the example from the form's <xref:System.Windows.Forms.Form.Load> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8760-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8760-120">See Also</span></span>  
 [<span data-ttu-id="a8760-121">方法: BindingSource コンポーネントを使用してフォーム間でバインド データを共有する</span><span class="sxs-lookup"><span data-stu-id="a8760-121">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 [<span data-ttu-id="a8760-122">Windows フォーム データ バインドの変更通知</span><span class="sxs-lookup"><span data-stu-id="a8760-122">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="a8760-123">データ連結に関連するインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a8760-123">Interfaces Related to Data Binding</span></span>](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 [<span data-ttu-id="a8760-124">Windows フォームでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="a8760-124">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
