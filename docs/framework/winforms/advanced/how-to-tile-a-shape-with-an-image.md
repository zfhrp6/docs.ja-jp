---
title: "方法 : イメージを並べたパターンによって図形を塗りつぶす"
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
- texture brushes [Windows Forms], tiling images with
- images [Windows Forms], filling shapes with
- shapes [Windows Forms], tiling with images
- bitmaps [Windows Forms], filling shapes with
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8726322e9443042b76c28e7b4b22ebc51c871bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-tile-a-shape-with-an-image"></a><span data-ttu-id="c7f33-102">方法 : イメージを並べたパターンによって図形を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="c7f33-102">How to: Tile a Shape with an Image</span></span>
<span data-ttu-id="c7f33-103">並べてフロアをカバーするタイルを配置すると同様、塗りつぶし (タイル) 図形を四角形のイメージを互いの横にある配置できます。</span><span class="sxs-lookup"><span data-stu-id="c7f33-103">Just as tiles can be placed next to each other to cover a floor, rectangular images can be placed next to each other to fill (tile) a shape.</span></span> <span data-ttu-id="c7f33-104">図形の内部を並べて表示するには、テクスチャ ブラシを使用します。</span><span class="sxs-lookup"><span data-stu-id="c7f33-104">To tile the interior of a shape, use a texture brush.</span></span> <span data-ttu-id="c7f33-105">構築する場合、<xref:System.Drawing.TextureBrush>オブジェクトのコンス トラクターに渡す引数の 1 つは、<xref:System.Drawing.Image>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c7f33-105">When you construct a <xref:System.Drawing.TextureBrush> object, one of the arguments you pass to the constructor is an <xref:System.Drawing.Image> object.</span></span> <span data-ttu-id="c7f33-106">図形の内部を描画するテクスチャ ブラシを使用する場合は、このイメージの繰り返しコピーで、図形が塗りつぶされます。</span><span class="sxs-lookup"><span data-stu-id="c7f33-106">When you use the texture brush to paint the interior of a shape, the shape is filled with repeated copies of this image.</span></span>  
  
 <span data-ttu-id="c7f33-107">ラップ モード プロパティ、<xref:System.Drawing.TextureBrush>オブジェクトはどのように、画像には、四角形グリッドでそれが繰り返されるを決定します。</span><span class="sxs-lookup"><span data-stu-id="c7f33-107">The wrap mode property of the <xref:System.Drawing.TextureBrush> object determines how the image is oriented as it is repeated in a rectangular grid.</span></span> <span data-ttu-id="c7f33-108">ことができます、グリッド内のタイルがすべて同じ印刷の向き、または、次に反転させる 1 つのグリッド位置からイメージを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c7f33-108">You can make all the tiles in the grid have the same orientation, or you can make the image flip from one grid position to the next.</span></span> <span data-ttu-id="c7f33-109">反転は、水平、垂直、またはその両方です。</span><span class="sxs-lookup"><span data-stu-id="c7f33-109">The flipping can be horizontal, vertical, or both.</span></span> <span data-ttu-id="c7f33-110">次の例は、さまざまな種類の反転を並べて表示します。</span><span class="sxs-lookup"><span data-stu-id="c7f33-110">The following examples demonstrate tiling with different types of flipping.</span></span>  
  
### <a name="to-tile-an-image"></a><span data-ttu-id="c7f33-111">イメージを並べて表示</span><span class="sxs-lookup"><span data-stu-id="c7f33-111">To tile an image</span></span>  
  
-   <span data-ttu-id="c7f33-112">この例では、次の 75 × 75 イメージを使用して、200 × 200 四角形を並べて表示します。</span><span class="sxs-lookup"><span data-stu-id="c7f33-112">This example uses the following 75×75 image to tile a 200×200 rectangle.</span></span>  
  
 <span data-ttu-id="c7f33-113">![タイル 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")</span><span class="sxs-lookup"><span data-stu-id="c7f33-113">![Tile 1](../../../../docs/framework/winforms/advanced/media/tile1.gif "tile1")</span></span>  
  
-   <span data-ttu-id="c7f33-114">次の図は、四角形がイメージを並べて表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c7f33-114">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="c7f33-115">すべてのタイルが同じ方向; にあることに注意してください。切り替えることはありません。</span><span class="sxs-lookup"><span data-stu-id="c7f33-115">Note that all tiles have the same orientation; there is no flipping.</span></span>  
  
 <span data-ttu-id="c7f33-116">![タイル 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")</span><span class="sxs-lookup"><span data-stu-id="c7f33-116">![Tile 2](../../../../docs/framework/winforms/advanced/media/tile2.gif "tile2")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### <a name="to-flip-an-image-horizontally-while-tiling"></a><span data-ttu-id="c7f33-117">水平方向に並べて表示するときにイメージを反転するには</span><span class="sxs-lookup"><span data-stu-id="c7f33-117">To flip an image horizontally while tiling</span></span>  
  
-   <span data-ttu-id="c7f33-118">この例では、同じ 75 × 75 イメージを使用して、200 × 200 四角形の塗りつぶし。</span><span class="sxs-lookup"><span data-stu-id="c7f33-118">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="c7f33-119">ラップ モードは、イメージを水平方向に反転に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c7f33-119">The wrap mode is set to flip the image horizontally.</span></span> <span data-ttu-id="c7f33-120">次の図は、四角形がイメージを並べて表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c7f33-120">The following illustration shows how the rectangle is tiled with the image.</span></span> <span data-ttu-id="c7f33-121">特定の行ごとに 1 つのタイルから移動すると、イメージは水平方向に反転注意してください。</span><span class="sxs-lookup"><span data-stu-id="c7f33-121">Note that as you move from one tile to the next in a given row, the image is flipped horizontally.</span></span>  
  
 <span data-ttu-id="c7f33-122">![タイル 3 の](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")</span><span class="sxs-lookup"><span data-stu-id="c7f33-122">![Tile 3](../../../../docs/framework/winforms/advanced/media/tile3.gif "tile3")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### <a name="to-flip-an-image-vertically-while-tiling"></a><span data-ttu-id="c7f33-123">垂直方向に並べて表示するときにイメージを反転するには</span><span class="sxs-lookup"><span data-stu-id="c7f33-123">To flip an image vertically while tiling</span></span>  
  
-   <span data-ttu-id="c7f33-124">この例では、同じ 75 × 75 イメージを使用して、200 × 200 四角形の塗りつぶし。</span><span class="sxs-lookup"><span data-stu-id="c7f33-124">This example uses the same 75×75 image to fill a 200×200 rectangle.</span></span> <span data-ttu-id="c7f33-125">ラップ モードは、イメージを垂直方向に反転に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c7f33-125">The wrap mode is set to flip the image vertically.</span></span>  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### <a name="to-flip-an-image-horizontally-and-vertically-while-tiling"></a><span data-ttu-id="c7f33-126">並べて表示するとき、イメージを水平方向および垂直方向に反転するには</span><span class="sxs-lookup"><span data-stu-id="c7f33-126">To flip an image horizontally and vertically while tiling</span></span>  
  
-   <span data-ttu-id="c7f33-127">この例では、同じ 75 × 75 イメージを使用して、200 × 200 四角形を並べて表示します。</span><span class="sxs-lookup"><span data-stu-id="c7f33-127">This example uses the same 75×75 image to tile a 200×200 rectangle.</span></span> <span data-ttu-id="c7f33-128">ラップ モードは、上下左右反転イメージ両方に設定されます。</span><span class="sxs-lookup"><span data-stu-id="c7f33-128">The wrap mode is set to flip the image both horizontally and vertically.</span></span> <span data-ttu-id="c7f33-129">次の図は、四角形がイメージを並べて表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c7f33-129">The following illustration shows how the rectangle is tiled by the image.</span></span> <span data-ttu-id="c7f33-130">1 つのタイルから次の特定の行に移動する、イメージは水平方向に反転しすると、イメージが垂直方向に反転させるように 1 つのタイルから特定の列で次に移動することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c7f33-130">Note that as you move from one tile to the next in a given row, the image is flipped horizontally, and as you move from one tile to the next in a given column, the image is flipped vertically.</span></span>  
  
 <span data-ttu-id="c7f33-131">![5 をタイル](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")</span><span class="sxs-lookup"><span data-stu-id="c7f33-131">![Tile 5](../../../../docs/framework/winforms/advanced/media/tile5.gif "tile5")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="c7f33-132">参照</span><span class="sxs-lookup"><span data-stu-id="c7f33-132">See Also</span></span>  
 [<span data-ttu-id="c7f33-133">ブラシを使用した図形の塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="c7f33-133">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
