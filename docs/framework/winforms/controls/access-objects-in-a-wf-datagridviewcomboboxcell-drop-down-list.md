---
title: "方法: Windows フォームの DataGridViewComboBoxCell ドロップダウン リストのオブジェクトにアクセスする"
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
- DataGridView control [Windows Forms], accessing objects in combo box cells
- combo boxes [Windows Forms], in DataGridView control
- combo boxes [Windows Forms], accessing objects in DataGridViewComboBoxCell drop-down lists
ms.assetid: bcbe794a-d1fa-47f8-b5a3-5f085b32097d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d0f4eb14fbb459f6844053507d1eb4f0a46cede3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-access-objects-in-a-windows-forms-datagridviewcomboboxcell-drop-down-list"></a><span data-ttu-id="20808-102">方法: Windows フォームの DataGridViewComboBoxCell ドロップダウン リストのオブジェクトにアクセスする</span><span class="sxs-lookup"><span data-stu-id="20808-102">How to: Access Objects in a Windows Forms DataGridViewComboBoxCell Drop-Down List</span></span>
<span data-ttu-id="20808-103">同様に、<xref:System.Windows.Forms.ComboBox>コントロール、<xref:System.Windows.Forms.DataGridViewComboBoxColumn>と<xref:System.Windows.Forms.DataGridViewComboBoxCell>型では、ドロップダウン リストに任意のオブジェクトを追加できます。</span><span class="sxs-lookup"><span data-stu-id="20808-103">Like the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and <xref:System.Windows.Forms.DataGridViewComboBoxCell> types enable you to add arbitrary objects to their drop-down lists.</span></span> <span data-ttu-id="20808-104">この機能により、個別のコレクションに対応するオブジェクトを格納することがなくドロップダウン リストで複雑な状態を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="20808-104">With this feature, you can represent complex states in a drop-down list without having to store corresponding objects in a separate collection.</span></span>  
  
 <span data-ttu-id="20808-105">異なり、<xref:System.Windows.Forms.ComboBox>コントロール、<xref:System.Windows.Forms.DataGridView>型がない、<xref:System.Windows.Forms.ComboBox.SelectedItem%2A>現在選択されているオブジェクトを取得するためのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="20808-105">Unlike the <xref:System.Windows.Forms.ComboBox> control, the <xref:System.Windows.Forms.DataGridView> types do not have a <xref:System.Windows.Forms.ComboBox.SelectedItem%2A> property for retrieving the currently selected object.</span></span> <span data-ttu-id="20808-106">代わりに、設定する必要があります、<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>または<xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>プロパティをビジネス オブジェクトのプロパティの名前にします。</span><span class="sxs-lookup"><span data-stu-id="20808-106">Instead, you must set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType> property to the name of a property on your business object.</span></span> <span data-ttu-id="20808-107">選択を行ったとき、ユーザー、ビジネス オブジェクトの指定されたプロパティは、セルを設定します<xref:System.Windows.Forms.DataGridViewCell.Value%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="20808-107">When the user makes a selection, the indicated property of the business object sets the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
 <span data-ttu-id="20808-108">セルの値からビジネス オブジェクトを取得する、`ValueMember`プロパティは、ビジネス オブジェクト自体への参照を返すプロパティを示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="20808-108">To retrieve the business object through the cell value, the `ValueMember` property must indicate a property that returns a reference to the business object itself.</span></span> <span data-ttu-id="20808-109">したがって、ビジネス オブジェクトの種類が自分の管理下にない場合は、継承によって型を拡張することによってこのようなプロパティを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="20808-109">Therefore, if the type of the business object is not under your control, you must add such a property by extending the type through inheritance.</span></span>  
  
 <span data-ttu-id="20808-110">次の手順は、ビジネス オブジェクトで、ドロップダウン リストに設定して、セルからオブジェクトを取得する方法を説明<xref:System.Windows.Forms.DataGridViewCell.Value%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="20808-110">The following procedures demonstrate how to populate a drop-down list with business objects and retrieve the objects through the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property.</span></span>  
  
### <a name="to-add-business-objects-to-the-drop-down-list"></a><span data-ttu-id="20808-111">ドロップダウン リストにビジネス オブジェクトを追加するには</span><span class="sxs-lookup"><span data-stu-id="20808-111">To add business objects to the drop-down list</span></span>  
  
1.  <span data-ttu-id="20808-112">新規作成<xref:System.Windows.Forms.DataGridViewComboBoxColumn>設定とその<xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>コレクション。</span><span class="sxs-lookup"><span data-stu-id="20808-112">Create a new <xref:System.Windows.Forms.DataGridViewComboBoxColumn> and populate its <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A> collection.</span></span> <span data-ttu-id="20808-113">列を設定する代わりに、<xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>ビジネス オブジェクトのコレクションにプロパティです。</span><span class="sxs-lookup"><span data-stu-id="20808-113">Alternatively, you can set the column <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property to the collection of business objects.</span></span> <span data-ttu-id="20808-114">その場合は、ただし、追加できません「未割り当て」ドロップダウン リストに、コレクションに対応するビジネス オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="20808-114">In that case, however, you cannot add "unassigned" to the drop-down list without creating a corresponding business object in your collection.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#110)]  
  
2.  <span data-ttu-id="20808-115"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> プロパティと <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="20808-115">Set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> and <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> properties.</span></span> <span data-ttu-id="20808-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>ドロップダウン リストに表示するビジネス オブジェクトのプロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="20808-116"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A> indicates the property of the business object to display in the drop-down list.</span></span> <span data-ttu-id="20808-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>ビジネス オブジェクトへの参照を返すプロパティを示します。</span><span class="sxs-lookup"><span data-stu-id="20808-117"><xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> indicates the property that returns a reference to the business object.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#115)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#115](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#115)]  
  
3.  <span data-ttu-id="20808-118">ビジネス オブジェクトの種類が、現在のインスタンスへの参照を返すプロパティが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="20808-118">Make sure that your business object type contains a property that returns a reference to the current instance.</span></span> <span data-ttu-id="20808-119">割り当てられている値は、このプロパティの名前を指定する必要があります<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>前の手順でします。</span><span class="sxs-lookup"><span data-stu-id="20808-119">This property must be named with the value assigned to <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A> in the previous step.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#310)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#310](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#310)]  
  
### <a name="to-retrieve-the-currently-selected-business-object"></a><span data-ttu-id="20808-120">現在選択されているビジネス オブジェクトを取得するには</span><span class="sxs-lookup"><span data-stu-id="20808-120">To retrieve the currently selected business object</span></span>  
  
-   <span data-ttu-id="20808-121">セルを取得<xref:System.Windows.Forms.DataGridViewCell.Value%2A>プロパティであり、ビジネス オブジェクトの種類にキャストします。</span><span class="sxs-lookup"><span data-stu-id="20808-121">Get the cell <xref:System.Windows.Forms.DataGridViewCell.Value%2A> property and cast it to the business object type.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#120)]  
  
## <a name="example"></a><span data-ttu-id="20808-122">例</span><span class="sxs-lookup"><span data-stu-id="20808-122">Example</span></span>  
 <span data-ttu-id="20808-123">完全な例では、ドロップダウン リストでビジネス オブジェクトの使用を示します。</span><span class="sxs-lookup"><span data-stu-id="20808-123">The complete example demonstrates the use of business objects in a drop-down list.</span></span> <span data-ttu-id="20808-124">この例で、<xref:System.Windows.Forms.DataGridView>コントロールのコレクションにバインドする`Task`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="20808-124">In the example, a <xref:System.Windows.Forms.DataGridView> control is bound to a collection of `Task` objects.</span></span> <span data-ttu-id="20808-125">各`Task`オブジェクトには、`AssignedTo`を示すプロパティを`Employee`そのタスクに現在割り当てられているオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="20808-125">Each `Task` object has an `AssignedTo` property that indicates the `Employee` object currently assigned to that task.</span></span> <span data-ttu-id="20808-126">`Assigned To`列が表示されます、`Name`従業員、または「未割り当て」の各プロパティの値が割り当てられている、`Task.AssignedTo`プロパティの値が`null`です。</span><span class="sxs-lookup"><span data-stu-id="20808-126">The `Assigned To` column displays the `Name` property value for each assigned employee, or "unassigned" if the `Task.AssignedTo` property value is `null`.</span></span>  
  
 <span data-ttu-id="20808-127">この例の動作を表示するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="20808-127">To view the behavior of this example, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="20808-128">割り当てを変更、`Assigned To`ドロップ ダウン リストから別の値を選択するか、ctrl キーを押しながらコンボ ボックスのセルに 0 を押すことによって列です。</span><span class="sxs-lookup"><span data-stu-id="20808-128">Change assignments in the `Assigned To` column by selecting different values from the drop-down lists or pressing CTRL+0 in a combo-box cell.</span></span>  
  
2.  <span data-ttu-id="20808-129">をクリックして`Generate Report`を現在の割り当てを表示します。</span><span class="sxs-lookup"><span data-stu-id="20808-129">Click `Generate Report` to display the current assignments.</span></span> <span data-ttu-id="20808-130">これを示しているの変更、`Assigned To`列が自動的に更新、`tasks`コレクション。</span><span class="sxs-lookup"><span data-stu-id="20808-130">This demonstrates that a change in the `Assigned To` column automatically updates the `tasks` collection.</span></span>  
  
3.  <span data-ttu-id="20808-131">クリックして、`Request Status`を呼び出すボタン、 `RequestStatus` 、現在のメソッド`Employee`その行のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="20808-131">Click a `Request Status` button to call the `RequestStatus` method of the current `Employee` object for that row.</span></span> <span data-ttu-id="20808-132">これは、選択したオブジェクトが正常に取得されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="20808-132">This demonstrates that the selected object has been successfully retrieved.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/CS/form1.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridViewComboBoxObjectBinding#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewComboBoxObjectBinding/vb/form1.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="20808-133">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="20808-133">Compiling the Code</span></span>  
 <span data-ttu-id="20808-134">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="20808-134">This example requires:</span></span>  
  
-   <span data-ttu-id="20808-135">System アセンブリおよび System.Windows.Forms アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="20808-135">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20808-136">参照</span><span class="sxs-lookup"><span data-stu-id="20808-136">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewComboBoxCell.ValueMember%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ComboBox>  
 [<span data-ttu-id="20808-137">Windows フォーム DataGridView コントロールでのデータの表示</span><span class="sxs-lookup"><span data-stu-id="20808-137">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)
