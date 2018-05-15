---
title: '方法 : カラー行列を使用して単一色を変換する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image colors [Windows Forms], transforming
- color matrices [Windows Forms], using
ms.assetid: 44df4556-a433-49c0-ac0f-9a12063a5860
ms.openlocfilehash: 741259fcf853c82dfd13b43edc92e50d8767887b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-color-matrix-to-transform-a-single-color"></a><span data-ttu-id="78ac9-102">方法 : カラー行列を使用して単一色を変換する</span><span class="sxs-lookup"><span data-stu-id="78ac9-102">How to: Use a Color Matrix to Transform a Single Color</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="78ac9-103"> 提供、<xref:System.Drawing.Image>と<xref:System.Drawing.Bitmap>を格納して、画像を操作するためのクラスです。</span><span class="sxs-lookup"><span data-stu-id="78ac9-103"> provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="78ac9-104"><xref:System.Drawing.Image> および<xref:System.Drawing.Bitmap>オブジェクトに格納する 32 ビット数値として各ピクセルの色: 赤、緑、青、および alpha にそれぞれ 8 ビットです。</span><span class="sxs-lookup"><span data-stu-id="78ac9-104"><xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects store the color of each pixel as a 32-bit number: 8 bits each for red, green, blue, and alpha.</span></span> <span data-ttu-id="78ac9-105">4 つのコンポーネントのそれぞれは、0 ~ 255 の輝度がないと 255 は最大の輝度を表す、0 から番号です。</span><span class="sxs-lookup"><span data-stu-id="78ac9-105">Each of the four components is a number from 0 through 255, with 0 representing no intensity and 255 representing full intensity.</span></span> <span data-ttu-id="78ac9-106">アルファ コンポーネントは、色の透明度を指定します。 0 は完全に透過的であり、255 は完全に不透明です。</span><span class="sxs-lookup"><span data-stu-id="78ac9-106">The alpha component specifies the transparency of the color: 0 is fully transparent, and 255 is fully opaque.</span></span>  
  
 <span data-ttu-id="78ac9-107">カラー ベクターは、(赤、緑、青、alpha) 形式の 4 タプルです。</span><span class="sxs-lookup"><span data-stu-id="78ac9-107">A color vector is a 4-tuple of the form (red, green, blue, alpha).</span></span> <span data-ttu-id="78ac9-108">たとえば、色ベクトル (0、255, 0, 255) が存在せず、赤または青、緑を輝度が完全では不透明な色を表します。</span><span class="sxs-lookup"><span data-stu-id="78ac9-108">For example, the color vector (0, 255, 0, 255) represents an opaque color that has no red or blue, but has green at full intensity.</span></span>  
  
 <span data-ttu-id="78ac9-109">色を表すための別の規則は、最大の輝度番号 1 を使用します。</span><span class="sxs-lookup"><span data-stu-id="78ac9-109">Another convention for representing colors uses the number 1 for full intensity.</span></span> <span data-ttu-id="78ac9-110">その規則を使用して、前の段落で説明されている色で表されます (0、1, 0, 1) のベクトル。</span><span class="sxs-lookup"><span data-stu-id="78ac9-110">Using that convention, the color described in the preceding paragraph would be represented by the vector (0, 1, 0, 1).</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="78ac9-111"> 色の変換を実行するときは、最大の輝度を 1 の規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="78ac9-111"> uses the convention of 1 as full intensity when it performs color transformations.</span></span>  
  
 <span data-ttu-id="78ac9-112">4 × 4 行列によって色ベクトルを乗算することによって、カラー ベクターに (回転、スケーリング、および、like) の線形変換を適用できます。</span><span class="sxs-lookup"><span data-stu-id="78ac9-112">You can apply linear transformations (rotation, scaling, and the like) to color vectors by multiplying the color vectors by a 4×4 matrix.</span></span> <span data-ttu-id="78ac9-113">ただし、線形変換を実行するのに 4 × 4 行列を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="78ac9-113">However, you cannot use a 4×4 matrix to perform a translation (nonlinear).</span></span> <span data-ttu-id="78ac9-114">各色ベクター ダミー 5 番目の座標 (たとえば、番号 1) を追加する場合は、線形変換および変換の任意の組み合わせを適用する 5 × 5 マトリックスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="78ac9-114">If you add a dummy fifth coordinate (for example, the number 1) to each of the color vectors, you can use a 5×5 matrix to apply any combination of linear transformations and translations.</span></span> <span data-ttu-id="78ac9-115">続いて平行線形変換の変換は、アフィン変換と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="78ac9-115">A transformation consisting of a linear transformation followed by a translation is called an affine transformation.</span></span>  
  
 <span data-ttu-id="78ac9-116">たとえば、色 (0.2、0.0、0.4, 1.0) で起動して次の変換を適用するとします。</span><span class="sxs-lookup"><span data-stu-id="78ac9-116">For example, suppose you want to start with the color (0.2, 0.0, 0.4, 1.0) and apply the following transformations:</span></span>  
  
1.  <span data-ttu-id="78ac9-117">赤の成分倍精度浮動小数点</span><span class="sxs-lookup"><span data-stu-id="78ac9-117">Double the red component</span></span>  
  
2.  <span data-ttu-id="78ac9-118">赤、緑、および青のコンポーネントを 0.2 を追加します。</span><span class="sxs-lookup"><span data-stu-id="78ac9-118">Add 0.2 to the red, green, and blue components</span></span>  
  
 <span data-ttu-id="78ac9-119">次行列乗算では、変換のペアを順に実行します。</span><span class="sxs-lookup"><span data-stu-id="78ac9-119">The following matrix multiplication will perform the pair of transformations in the order listed.</span></span>  
  
 <span data-ttu-id="78ac9-120">![色の変更](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span><span class="sxs-lookup"><span data-stu-id="78ac9-120">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring01.gif "recoloring01")</span></span>  
  
 <span data-ttu-id="78ac9-121">カラー行列の要素は、行と列 (0 から始まる) インデックス付けられます。</span><span class="sxs-lookup"><span data-stu-id="78ac9-121">The elements of a color matrix are indexed (zero-based) by row and then column.</span></span> <span data-ttu-id="78ac9-122">たとえば、5 番目の行およびマトリックス M の 3 列目のエントリは、M [4] [2] で表されます。</span><span class="sxs-lookup"><span data-stu-id="78ac9-122">For example, the entry in the fifth row and third column of matrix M is denoted by M[4][2].</span></span>  
  
 <span data-ttu-id="78ac9-123">5 × 5 単位行列で、次の図に示す) は、対角線上の 1 と 0 それ以外の場所がします。</span><span class="sxs-lookup"><span data-stu-id="78ac9-123">The 5×5 identity matrix (shown in the following illustration) has 1s on the diagonal and 0s everywhere else.</span></span> <span data-ttu-id="78ac9-124">単位行列でカラー ベクトルを乗算する場合、色のベクターは変更されません。</span><span class="sxs-lookup"><span data-stu-id="78ac9-124">If you multiply a color vector by the identity matrix, the color vector does not change.</span></span> <span data-ttu-id="78ac9-125">カラー変換の行列を形成する便利な方法では、単位行列で開始し、少しの変更を必要な変換を生成します。</span><span class="sxs-lookup"><span data-stu-id="78ac9-125">A convenient way to form the matrix of a color transformation is to start with the identity matrix and make a small change that produces the desired transformation.</span></span>  
  
 <span data-ttu-id="78ac9-126">![色の変更](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span><span class="sxs-lookup"><span data-stu-id="78ac9-126">![Recoloring](../../../../docs/framework/winforms/advanced/media/recoloring02.gif "recoloring02")</span></span>  
  
 <span data-ttu-id="78ac9-127">マトリックスと変換の詳細については、次を参照してください。[座標系と変換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)です。</span><span class="sxs-lookup"><span data-stu-id="78ac9-127">For a more detailed discussion of matrices and transformations, see [Coordinate Systems and Transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="78ac9-128">例</span><span class="sxs-lookup"><span data-stu-id="78ac9-128">Example</span></span>  
 <span data-ttu-id="78ac9-129">次の例は、1 つのすべての色 (0.2、0.0、0.4, 1.0) は、前の段落で説明した変換を適用するイメージ。</span><span class="sxs-lookup"><span data-stu-id="78ac9-129">The following example takes an image that is all one color (0.2, 0.0, 0.4, 1.0) and applies the transformation described in the preceding paragraphs.</span></span>  
  
 <span data-ttu-id="78ac9-130">次の図は、右側の左側に元のイメージと変換後のイメージを示します。</span><span class="sxs-lookup"><span data-stu-id="78ac9-130">The following illustration shows the original image on the left and the transformed image on the right.</span></span>  
  
 <span data-ttu-id="78ac9-131">![色](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span><span class="sxs-lookup"><span data-stu-id="78ac9-131">![Colors](../../../../docs/framework/winforms/advanced/media/colortrans1.png "colortrans1")</span></span>  
  
 <span data-ttu-id="78ac9-132">次の例のコードでは、次の手順を使用して、色の変更を実行します。</span><span class="sxs-lookup"><span data-stu-id="78ac9-132">The code in the following example uses the following steps to perform the recoloring:</span></span>  
  
1.  <span data-ttu-id="78ac9-133">初期化、<xref:System.Drawing.Imaging.ColorMatrix>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="78ac9-133">Initialize a <xref:System.Drawing.Imaging.ColorMatrix> object.</span></span>  
  
2.  <span data-ttu-id="78ac9-134">作成、<xref:System.Drawing.Imaging.ImageAttributes>オブジェクトを渡す、<xref:System.Drawing.Imaging.ColorMatrix>オブジェクトを<xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A>のメソッド、<xref:System.Drawing.Imaging.ImageAttributes>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="78ac9-134">Create an <xref:System.Drawing.Imaging.ImageAttributes> object and pass the <xref:System.Drawing.Imaging.ColorMatrix> object to the <xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A> method of the <xref:System.Drawing.Imaging.ImageAttributes> object.</span></span>  
  
3.  <span data-ttu-id="78ac9-135">渡す、<xref:System.Drawing.Imaging.ImageAttributes>オブジェクトを<xref:System.Drawing.Graphics.DrawImage%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="78ac9-135">Pass the <xref:System.Drawing.Imaging.ImageAttributes> object to the <xref:System.Drawing.Graphics.DrawImage%2A> method of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.RecoloringImages#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="78ac9-136">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="78ac9-136">Compiling the Code</span></span>  
 <span data-ttu-id="78ac9-137">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="78ac9-137">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ac9-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="78ac9-138">See Also</span></span>  
 [<span data-ttu-id="78ac9-139">イメージの色の変更</span><span class="sxs-lookup"><span data-stu-id="78ac9-139">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [<span data-ttu-id="78ac9-140">座標系と変換</span><span class="sxs-lookup"><span data-stu-id="78ac9-140">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
