---
title: "方法 : DataRepeater コントロールに非バインド コントロールを表示する (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3e96219f0ea8b8198967e9fa3c6e5afb824352db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="c5d5e-102">方法 : DataRepeater コントロールに非バインド コントロールを表示する (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="c5d5e-102">How to: Display Unbound Controls in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="c5d5e-103">だけでなく、バインドされたコントロールを他のコントロールを追加することがあります、 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>、静的ラベル内の各項目に繰り返し表示されるイメージなど、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。</span><span class="sxs-lookup"><span data-stu-id="c5d5e-103">In addition to bound controls, you may want to add other controls to a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, such as a static label or an image that is repeated on each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5d5e-104">少なくとも 1 つのバインドされたコントロールも必要、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>または実行時に何が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5d5e-104">You must also have at least one bound control on the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> or nothing will be displayed at run time.</span></span>  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a><span data-ttu-id="c5d5e-105">DataRepeater にバインドされていないコントロールを追加するには</span><span class="sxs-lookup"><span data-stu-id="c5d5e-105">To add unbound controls to a DataRepeater</span></span>  
  
1.  <span data-ttu-id="c5d5e-106">ドラッグ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>から制御、 **Visual Basic PowerPacks**  タブで、**ツールボックス**フォームまたはコンテナー コントロールにします。</span><span class="sxs-lookup"><span data-stu-id="c5d5e-106">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** to a form or container control.</span></span>  
  
2.  <span data-ttu-id="c5d5e-107">サイズにサイズ変更および位置のハンドルをドラッグし、コントロールを配置します。</span><span class="sxs-lookup"><span data-stu-id="c5d5e-107">Drag the sizing and position handles to size and position the control.</span></span>  
  
     <span data-ttu-id="c5d5e-108">またサイズし、変更することで、コントロールを配置、**サイズ**と**位置**プロパティ ウィンドウでプロパティです。</span><span class="sxs-lookup"><span data-stu-id="c5d5e-108">You can also size and position the control by changing the **Size** and **Position** properties in the Properties window.</span></span>  
  
3.  <span data-ttu-id="c5d5e-109">少なくとも 1 つのデータ バインド コントロールを追加、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。</span><span class="sxs-lookup"><span data-stu-id="c5d5e-109">Add at least one data-bound control to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="c5d5e-110">詳細については、次を参照してください。[する方法: DataRepeater コントロールにバインドされているデータを表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)です。</span><span class="sxs-lookup"><span data-stu-id="c5d5e-110">For more information, see [How to: Display Bound Data in a DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).</span></span>  
  
4.  <span data-ttu-id="c5d5e-111">コントロールをドラッグ、**ツールボックス**、項目テンプレート領域の上に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。</span><span class="sxs-lookup"><span data-stu-id="c5d5e-111">Drag a control from the **Toolbox** onto the item template region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="c5d5e-112">コントロールに 2 つの四角形の領域があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c5d5e-112">Note that the control has two rectangular regions.</span></span> <span data-ttu-id="c5d5e-113">内部の領域は、*項目テンプレート*; 内の各項目のテンプレートに追加されたコントロールは繰り返されます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>実行時にコントロールできます。</span><span class="sxs-lookup"><span data-stu-id="c5d5e-113">The inner region is the *item template*; controls added to the template will be repeated in each item in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at run time.</span></span> <span data-ttu-id="c5d5e-114">外部の領域は、*ビューポート*、ここで、アイテムを表示する以外の場合はこの領域に追加されるコントロールは、実行時に表示されません。</span><span class="sxs-lookup"><span data-stu-id="c5d5e-114">The outer region is the *viewport*, where the items will be displayed; controls that are added to this region will not be displayed at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5d5e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5d5e-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [<span data-ttu-id="c5d5e-116">DataRepeater コントロールの概要</span><span class="sxs-lookup"><span data-stu-id="c5d5e-116">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="c5d5e-117">DataRepeater コントロールのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c5d5e-117">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="c5d5e-118">方法: DataRepeater コントロールに、バインドされたデータを表示する</span><span class="sxs-lookup"><span data-stu-id="c5d5e-118">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="c5d5e-119">方法: 2 つの DataRepeater コントロール (Visual Studio) を使用してマスター/詳細フォームを作成します。</span><span class="sxs-lookup"><span data-stu-id="c5d5e-119">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="c5d5e-120">方法: DataRepeater コントロールの外観を変更する</span><span class="sxs-lookup"><span data-stu-id="c5d5e-120">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
