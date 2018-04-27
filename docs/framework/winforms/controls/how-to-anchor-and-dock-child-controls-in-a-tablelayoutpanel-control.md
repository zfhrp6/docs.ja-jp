---
title: '方法 : TableLayoutPanel コントロールで子コントロールを固定およびドッキングする'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cb27454582dd4f3b299893c13b1202b33d9cacb9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a><span data-ttu-id="29eec-102">方法 : TableLayoutPanel コントロールで子コントロールを固定およびドッキングする</span><span class="sxs-lookup"><span data-stu-id="29eec-102">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>
<span data-ttu-id="29eec-103"><xref:System.Windows.Forms.TableLayoutPanel> コントロールは、子コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティと <xref:System.Windows.Forms.Control.Dock%2A> プロパティをサポートします。</span><span class="sxs-lookup"><span data-stu-id="29eec-103">The <xref:System.Windows.Forms.TableLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="29eec-104">TableLayoutPanel のセル内の子コントロールを揃えるには</span><span class="sxs-lookup"><span data-stu-id="29eec-104">To align a child control in a TableLayoutPanel cell</span></span>  
  
1.  <span data-ttu-id="29eec-105">フォームで <xref:System.Windows.Forms.TableLayoutPanel> コントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="29eec-105">Create a <xref:System.Windows.Forms.TableLayoutPanel> control on your form.</span></span>  
  
2.  <span data-ttu-id="29eec-106">値を設定、<xref:System.Windows.Forms.TableLayoutPanel>コントロールの<xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>と<xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>プロパティ**1**です。</span><span class="sxs-lookup"><span data-stu-id="29eec-106">Set the value of the <xref:System.Windows.Forms.TableLayoutPanel> control's <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> and <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> properties to **1**.</span></span>  
  
3.  <span data-ttu-id="29eec-107"><xref:System.Windows.Forms.TableLayoutPanel> コントロールで <xref:System.Windows.Forms.Button> コントロールを作成します。</span><span class="sxs-lookup"><span data-stu-id="29eec-107">Create a <xref:System.Windows.Forms.Button> control in the <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span> <span data-ttu-id="29eec-108"><xref:System.Windows.Forms.Button> がセルの左上隅を占有します。</span><span class="sxs-lookup"><span data-stu-id="29eec-108">The <xref:System.Windows.Forms.Button> occupies the upper-left corner of the cell.</span></span>  
  
4.  <span data-ttu-id="29eec-109"><xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Left` に変更します。</span><span class="sxs-lookup"><span data-stu-id="29eec-109">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left`.</span></span> <span data-ttu-id="29eec-110"><xref:System.Windows.Forms.Button> コントロールが、セルの左罫線に合うように移動します。</span><span class="sxs-lookup"><span data-stu-id="29eec-110">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29eec-111">この動作は、他のコンテナー コントロールの動作と異なります。</span><span class="sxs-lookup"><span data-stu-id="29eec-111">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="29eec-112">他のコンテナー コントロールでは、<xref:System.Windows.Forms.Control.Anchor%2A> プロパティが設定されてと子コントロールは移動せず、固定されたコントロールと親コンテナーの境界間の距離は、<xref:System.Windows.Forms.Control.Anchor%2A> プロパティが設定されたときに固定されます。</span><span class="sxs-lookup"><span data-stu-id="29eec-112">In other container controls, the child control does not move when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set, and the distance between the anchored control and the parent container's boundary is fixed at the time the <xref:System.Windows.Forms.Control.Anchor%2A> property is set.</span></span>  
  
5.  <span data-ttu-id="29eec-113"><xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Top, Left` に変更します。</span><span class="sxs-lookup"><span data-stu-id="29eec-113">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Left`.</span></span> <span data-ttu-id="29eec-114"><xref:System.Windows.Forms.Button> コントロールがセルの左上隅を占有するよう移動します。</span><span class="sxs-lookup"><span data-stu-id="29eec-114">The <xref:System.Windows.Forms.Button> control moves to occupy the top-left corner of the cell.</span></span>  
  
6.  <span data-ttu-id="29eec-115">手順 5 を繰り返し、値の`Top, Right`を移動する、<xref:System.Windows.Forms.Button>セルの右上隅にコントロールできます。</span><span class="sxs-lookup"><span data-stu-id="29eec-115">Repeat step 5 with a value of `Top, Right` to move the <xref:System.Windows.Forms.Button> control to the top-right corner of the cell.</span></span> <span data-ttu-id="29eec-116">`Bottom, Left` と `Bottom, Right` の値を指定して繰り返します。</span><span class="sxs-lookup"><span data-stu-id="29eec-116">Repeat with values of `Bottom, Left` and `Bottom, Right`.</span></span>  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a><span data-ttu-id="29eec-117">TableLayoutPanel セル内の子コントロールを拡大するには</span><span class="sxs-lookup"><span data-stu-id="29eec-117">To stretch a child control in a TableLayoutPanel cell</span></span>  
  
1.  <span data-ttu-id="29eec-118"><xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Left, Right` に変更します。</span><span class="sxs-lookup"><span data-stu-id="29eec-118">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Left, Right`.</span></span> <span data-ttu-id="29eec-119"><xref:System.Windows.Forms.Button> コントロールがサイズ変更され、セルいっぱいに拡大されます。</span><span class="sxs-lookup"><span data-stu-id="29eec-119">The <xref:System.Windows.Forms.Button> control is resized to stretch across the cell.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29eec-120">この動作は、他のコンテナー コントロールの動作と異なります。</span><span class="sxs-lookup"><span data-stu-id="29eec-120">This behavior differs from the behavior of other container controls.</span></span> <span data-ttu-id="29eec-121">他のコンテナー コントロールで子コントロールはときにサイズ変更、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティに設定されている`Left, Right`または`Top, Bottom`です。</span><span class="sxs-lookup"><span data-stu-id="29eec-121">In other container controls, the child control is not resized when the <xref:System.Windows.Forms.Control.Anchor%2A> property is set to `Left, Right` or `Top, Bottom`.</span></span>  
  
2.  <span data-ttu-id="29eec-122"><xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Top, Bottom` に変更します。</span><span class="sxs-lookup"><span data-stu-id="29eec-122">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom`.</span></span> <span data-ttu-id="29eec-123"><xref:System.Windows.Forms.Button> コントロールがサイズ変更され、セルの上から下まで拡大されます。</span><span class="sxs-lookup"><span data-stu-id="29eec-123">The <xref:System.Windows.Forms.Button> control is resized to stretch from the top to the bottom of the cell.</span></span>  
  
3.  <span data-ttu-id="29eec-124"><xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `Top, Bottom, Left, Right` に変更します。</span><span class="sxs-lookup"><span data-stu-id="29eec-124">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `Top, Bottom, Left, Right`.</span></span> <span data-ttu-id="29eec-125"><xref:System.Windows.Forms.Button> コントロールがセルを満たすようサイズ変更されます。</span><span class="sxs-lookup"><span data-stu-id="29eec-125">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
4.  <span data-ttu-id="29eec-126"><xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を `None` に変更します。</span><span class="sxs-lookup"><span data-stu-id="29eec-126">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Anchor%2A> property to `None`.</span></span> <span data-ttu-id="29eec-127"><xref:System.Windows.Forms.Button> コントロールがサイズ変更され、セルの中央に配置されます。</span><span class="sxs-lookup"><span data-stu-id="29eec-127">The <xref:System.Windows.Forms.Button> control is resized and centered in the cell.</span></span>  
  
5.  <span data-ttu-id="29eec-128"><xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle.Left> に変更します。</span><span class="sxs-lookup"><span data-stu-id="29eec-128">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Left>.</span></span> <span data-ttu-id="29eec-129"><xref:System.Windows.Forms.Button> コントロールが、セルの左罫線に合うように移動します。</span><span class="sxs-lookup"><span data-stu-id="29eec-129">The <xref:System.Windows.Forms.Button> control moves to align with the left border of the cell.</span></span> <span data-ttu-id="29eec-130"><xref:System.Windows.Forms.Button> コントロールの幅は保持されますが、高さはセルを垂直方向に満たすようサイズ変更されます。</span><span class="sxs-lookup"><span data-stu-id="29eec-130">The <xref:System.Windows.Forms.Button> control retains its width, but its height is resized to fill the cell vertically.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="29eec-131">これは、他のコンテナー コントロール内で発生するのと同じ動作です。</span><span class="sxs-lookup"><span data-stu-id="29eec-131">This is the same behavior that occurs in other container controls.</span></span>  
  
6.  <span data-ttu-id="29eec-132"><xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Dock%2A> プロパティの値を <xref:System.Windows.Forms.DockStyle.Fill> に変更します。</span><span class="sxs-lookup"><span data-stu-id="29eec-132">Change the value of the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="29eec-133"><xref:System.Windows.Forms.Button> コントロールがセルを満たすようサイズ変更されます。</span><span class="sxs-lookup"><span data-stu-id="29eec-133">The <xref:System.Windows.Forms.Button> control is resized to fill the cell.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29eec-134">例</span><span class="sxs-lookup"><span data-stu-id="29eec-134">Example</span></span>  
 <span data-ttu-id="29eec-135">次の図は、5 つの個別の <xref:System.Windows.Forms.TableLayoutPanel> のセルに固定されている 5 つのボタンを示しています。</span><span class="sxs-lookup"><span data-stu-id="29eec-135">The following illustration shows five buttons anchored in five separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="29eec-136">![TableLayoutPanel アンカー](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")</span><span class="sxs-lookup"><span data-stu-id="29eec-136">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")</span></span>  
  
 <span data-ttu-id="29eec-137">次の図は、4 つの個別の <xref:System.Windows.Forms.TableLayoutPanel> のセルの隅に固定されている 4 つのボタンを示しています。</span><span class="sxs-lookup"><span data-stu-id="29eec-137">The following illustration shows four buttons anchored in the corners of four separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="29eec-138">![TableLayoutPanel アンカー](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="29eec-138">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")</span></span>  
  
 <span data-ttu-id="29eec-139">次の図は、3 つの個別の <xref:System.Windows.Forms.TableLayoutPanel> のセルに固定することで拡大された 3 つのボタンを示しています。</span><span class="sxs-lookup"><span data-stu-id="29eec-139">The following illustration shows three buttons stretched by anchoring in three separate <xref:System.Windows.Forms.TableLayoutPanel> cells.</span></span>  
  
 <span data-ttu-id="29eec-140">![TableLayoutPanel アンカー](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span><span class="sxs-lookup"><span data-stu-id="29eec-140">![TableLayoutPanel Anchoring](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")</span></span>  
  
 <span data-ttu-id="29eec-141">次のコード例は、<xref:System.Windows.Forms.TableLayoutPanel> コントロールの <xref:System.Windows.Forms.Button> コントロールにおけるすべての組み合わせの <xref:System.Windows.Forms.Control.Anchor%2A> プロパティの値を示します。</span><span class="sxs-lookup"><span data-stu-id="29eec-141">The following code example demonstrates all the combinations of <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.TableLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="29eec-142">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="29eec-142">Compiling the Code</span></span>  
 <span data-ttu-id="29eec-143">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="29eec-143">This example requires:</span></span>  
  
-   <span data-ttu-id="29eec-144">System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="29eec-144">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="29eec-145">Visual Basic または Visual c# のコマンドラインからこの例のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="29eec-145">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="29eec-146">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="29eec-146">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="29eec-147">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="29eec-147">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29eec-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="29eec-148">See Also</span></span>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [<span data-ttu-id="29eec-149">TableLayoutPanel コントロール</span><span class="sxs-lookup"><span data-stu-id="29eec-149">TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
