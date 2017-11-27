---
title: "イメージの色の変更"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- images [Windows Forms], recoloring
- recoloring images
- examples [Windows Forms], recoloring images
ms.assetid: f28c54fd-9c80-4f6f-b242-55f7ffcda84b
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7f6f432742c966e3f17a7b7fa84628f24109d08e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="recoloring-images"></a><span data-ttu-id="d91b6-102">イメージの色の変更</span><span class="sxs-lookup"><span data-stu-id="d91b6-102">Recoloring Images</span></span>
<span data-ttu-id="d91b6-103">色の変更は、イメージの色を調整するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="d91b6-103">Recoloring is the process of adjusting image colors.</span></span> <span data-ttu-id="d91b6-104">色の変更の例をいくつかは、別、別の色の基準とした色の輝度を調整する、明るさやすべての色コントラストを調整および色をグレースケールに変換する 1 つの色を変更します。</span><span class="sxs-lookup"><span data-stu-id="d91b6-104">Some examples of recoloring are changing one color to another, adjusting a color's intensity relative to another color, adjusting the brightness or contrast of all colors, and converting colors to shades of gray.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d91b6-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d91b6-105">In This Section</span></span>  
 [<span data-ttu-id="d91b6-106">方法: カラー行列を使用して単一色を変換する</span><span class="sxs-lookup"><span data-stu-id="d91b6-106">How to: Use a Color Matrix to Transform a Single Color</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-color-matrix-to-transform-a-single-color.md)  
 <span data-ttu-id="d91b6-107">使用したカラー行列変換色について説明します。</span><span class="sxs-lookup"><span data-stu-id="d91b6-107">Discusses using a color matrix to transform a color.</span></span>  
  
 [<span data-ttu-id="d91b6-108">方法: イメージの色を変換する</span><span class="sxs-lookup"><span data-stu-id="d91b6-108">How to: Translate Image Colors</span></span>](../../../../docs/framework/winforms/advanced/how-to-translate-image-colors.md)  
 <span data-ttu-id="d91b6-109">カラー行列を使用する色を変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d91b6-109">Shows how to translate colors using a color matrix.</span></span>  
  
 [<span data-ttu-id="d91b6-110">変換を使用した色のスケーリング</span><span class="sxs-lookup"><span data-stu-id="d91b6-110">Using Transformations to Scale Colors</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-to-scale-colors.md)  
 <span data-ttu-id="d91b6-111">カラー行列を使用して色をスケーリングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d91b6-111">Explains how to scale colors using a color matrix.</span></span>  
  
 [<span data-ttu-id="d91b6-112">方法: 色を回転させる</span><span class="sxs-lookup"><span data-stu-id="d91b6-112">How to: Rotate Colors</span></span>](../../../../docs/framework/winforms/advanced/how-to-rotate-colors.md)  
 <span data-ttu-id="d91b6-113">カラー行列を使用する色を回転する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d91b6-113">Describes how to rotate a color using a color matrix.</span></span>  
  
 [<span data-ttu-id="d91b6-114">方法: 色を傾斜する</span><span class="sxs-lookup"><span data-stu-id="d91b6-114">How to: Shear Colors</span></span>](../../../../docs/framework/winforms/advanced/how-to-shear-colors.md)  
 <span data-ttu-id="d91b6-115">傾斜を定義し、カラー行列を使用する色を傾斜する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d91b6-115">Defines shearing and explains how to shear colors using a color matrix.</span></span>  
  
 [<span data-ttu-id="d91b6-116">方法: カラー リマップ テーブルを使用する</span><span class="sxs-lookup"><span data-stu-id="d91b6-116">How to: Use a Color Remap Table</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-a-color-remap-table.md)  
 <span data-ttu-id="d91b6-117">再マップを定義し、カラー リマップ テーブルを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d91b6-117">Defines remapping and shows how to use a color remap table.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d91b6-118">参照</span><span class="sxs-lookup"><span data-stu-id="d91b6-118">Reference</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <span data-ttu-id="d91b6-119">このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d91b6-119">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.ColorMap>  
 <span data-ttu-id="d91b6-120">このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d91b6-120">Describes this class and contains links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d91b6-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d91b6-121">Related Sections</span></span>  
 [<span data-ttu-id="d91b6-122">イメージ、ビットマップ、メタファイル</span><span class="sxs-lookup"><span data-stu-id="d91b6-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="d91b6-123">各種のイメージに関するトピックの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="d91b6-123">Provides a list of topics regarding the different types of images.</span></span>  
  
 [<span data-ttu-id="d91b6-124">イメージ、ビットマップ、アイコン、およびメタファイルの操作</span><span class="sxs-lookup"><span data-stu-id="d91b6-124">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)  
 <span data-ttu-id="d91b6-125">各種のイメージを使用する方法を説明するトピックの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d91b6-125">Contains a list of topics that show how to use different types of images.</span></span>  
  
 [<span data-ttu-id="d91b6-126">マネージ グラフィックス クラスの使用</span><span class="sxs-lookup"><span data-stu-id="d91b6-126">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 <span data-ttu-id="d91b6-127">マネージ グラフィックス クラスの使用方法を説明するトピックの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="d91b6-127">Contains a list of topics describing how to use managed graphics classes.</span></span>
