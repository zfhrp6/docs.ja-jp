---
title: '方法 : Windows フォーム上のコントロールをドッキングする'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: 6cb4c982cb4c9e2df8d0335738ca087733209bdc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532324"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="926b5-102">方法 : Windows フォーム上のコントロールをドッキングする</span><span class="sxs-lookup"><span data-stu-id="926b5-102">How to: Dock Controls on Windows Forms</span></span>
<span data-ttu-id="926b5-103">コントロールをフォームの端にドッキングするか、またはコントロールのコンテナー (フォームまたはコンテナー コントロール) を挿入したりします。</span><span class="sxs-lookup"><span data-stu-id="926b5-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="926b5-104">Windows エクスプ ローラーのドッキングなど、その<xref:System.Windows.Forms.TreeView>ウィンドウの左側にあるコントロールとその<xref:System.Windows.Forms.ListView>ウィンドウの右側にあるコントロールです。</span><span class="sxs-lookup"><span data-stu-id="926b5-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="926b5-105">使用して、<xref:System.Windows.Forms.Control.Dock%2A>すべて表示されている Windows フォームのコントロールのドッキングのモードを定義するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="926b5-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="926b5-106">逆の z オーダーでコントロールがドッキングされます。</span><span class="sxs-lookup"><span data-stu-id="926b5-106">Controls are docked in reverse z-order.</span></span>  
  
 <span data-ttu-id="926b5-107"><xref:System.Windows.Forms.Control.Dock%2A>プロパティの対話、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="926b5-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="926b5-108">詳細については、次を参照してください。 [AutoSize プロパティの概要](../../../../docs/framework/winforms/controls/autosize-property-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="926b5-108">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
### <a name="to-dock-a-control"></a><span data-ttu-id="926b5-109">コントロールのドッキング</span><span class="sxs-lookup"><span data-stu-id="926b5-109">To dock a control</span></span>  
  
1.  <span data-ttu-id="926b5-110">ドッキングするコントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="926b5-110">Select the control that you want to dock.</span></span>  
  
2.  <span data-ttu-id="926b5-111">[プロパティ] ウィンドウの右側にある矢印をクリックして、<xref:System.Windows.Forms.Control.Dock%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="926b5-111">In the Properties window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="926b5-112">一連の端と、フォームの中央を表すボックスを示す、エディターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="926b5-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>  
  
3.  <span data-ttu-id="926b5-113">コントロールをドッキングするフォームの端を表すボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="926b5-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="926b5-114">コントロールのフォームまたはコンテナー コントロールの内容を入力するには、中央のボックスをクリックします。</span><span class="sxs-lookup"><span data-stu-id="926b5-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="926b5-115">をクリックして **(なし)** ドッキングを無効にします。</span><span class="sxs-lookup"><span data-stu-id="926b5-115">Click **(none)** to disable docking.</span></span>  
  
     <span data-ttu-id="926b5-116">コントロールがドッキングされた端の境界に合わせてサイズに自動的に変更します。</span><span class="sxs-lookup"><span data-stu-id="926b5-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="926b5-117">継承されたコントロールがある必要があります`Protected`ドッキングできるようにします。</span><span class="sxs-lookup"><span data-stu-id="926b5-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="926b5-118">コントロールのアクセス レベルを変更するには、次のように設定します。 その**修飾子**プロパティ ウィンドウでプロパティです。</span><span class="sxs-lookup"><span data-stu-id="926b5-118">To change the access level of a control, set its **Modifier** property in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="926b5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="926b5-119">See Also</span></span>  
 [<span data-ttu-id="926b5-120">Windows フォーム コントロール</span><span class="sxs-lookup"><span data-stu-id="926b5-120">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="926b5-121">Windows フォームでのコントロールの配置</span><span class="sxs-lookup"><span data-stu-id="926b5-121">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="926b5-122">各 Windows フォーム コントロールのラベル設定とショートカットの作成</span><span class="sxs-lookup"><span data-stu-id="926b5-122">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="926b5-123">Windows フォームで使用するコントロール</span><span class="sxs-lookup"><span data-stu-id="926b5-123">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="926b5-124">Windows フォーム コントロールの機能別一覧</span><span class="sxs-lookup"><span data-stu-id="926b5-124">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [<span data-ttu-id="926b5-125">方法: FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする</span><span class="sxs-lookup"><span data-stu-id="926b5-125">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="926b5-126">方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする</span><span class="sxs-lookup"><span data-stu-id="926b5-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="926b5-127">AutoSize プロパティの概要</span><span class="sxs-lookup"><span data-stu-id="926b5-127">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="926b5-128">方法: Windows フォームにコントロールを固定する</span><span class="sxs-lookup"><span data-stu-id="926b5-128">How to: Anchor Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
