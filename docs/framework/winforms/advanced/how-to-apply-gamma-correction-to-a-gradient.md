---
title: '方法 : グラデーションに対してガンマ補正を適用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
ms.openlocfilehash: 9c3c9c5c63194b1dee8314a1ef96497a8b78b5ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520735"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a><span data-ttu-id="8e5e3-102">方法 : グラデーションに対してガンマ補正を適用する</span><span class="sxs-lookup"><span data-stu-id="8e5e3-102">How to: Apply Gamma Correction to a Gradient</span></span>
<span data-ttu-id="8e5e3-103">ブラシの設定を線形グラデーション ブラシのガンマ補正を有効にする<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="8e5e3-103">You can enable gamma correction for a linear gradient brush by setting the brush's <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `true`.</span></span> <span data-ttu-id="8e5e3-104">ガンマ補正を無効に設定できます、<xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A>プロパティを`false`です。</span><span class="sxs-lookup"><span data-stu-id="8e5e3-104">You can disable gamma correction by setting the <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> property to `false`.</span></span> <span data-ttu-id="8e5e3-105">既定では、ガンマ補正が無効です。</span><span class="sxs-lookup"><span data-stu-id="8e5e3-105">Gamma correction is disabled by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e5e3-106">例</span><span class="sxs-lookup"><span data-stu-id="8e5e3-106">Example</span></span>  
 <span data-ttu-id="8e5e3-107">この例では、線形グラデーション ブラシを作成し、そのブラシを使用して 2 つの四角形を入力します。</span><span class="sxs-lookup"><span data-stu-id="8e5e3-107">The example creates a linear gradient brush and uses that brush to fill two rectangles.</span></span> <span data-ttu-id="8e5e3-108">最初の四角形はガンマ補正を適用せず、ガンマ補正と 2 つ目の四角形が格納されます。</span><span class="sxs-lookup"><span data-stu-id="8e5e3-108">The first rectangle is filled without gamma correction, and the second rectangle is filled with gamma correction.</span></span>  
  
 <span data-ttu-id="8e5e3-109">次の図は、次の 2 つの塗りつぶされた四角形を示します。</span><span class="sxs-lookup"><span data-stu-id="8e5e3-109">The following illustration shows the two filled rectangles.</span></span> <span data-ttu-id="8e5e3-110">ガンマ補正を持たない場合、最上位の四角形は、中央で淡色表示します。</span><span class="sxs-lookup"><span data-stu-id="8e5e3-110">The top rectangle, which does not have gamma correction, appears dark in the middle.</span></span> <span data-ttu-id="8e5e3-111">複数の uniform 濃度ガンマ補正は、下の四角形が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8e5e3-111">The bottom rectangle, which has gamma correction, appears to have more uniform intensity.</span></span>  
  
 <span data-ttu-id="8e5e3-112">![グラデーション](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")</span><span class="sxs-lookup"><span data-stu-id="8e5e3-112">![Gradient](../../../../docs/framework/winforms/advanced/media/gammagradient1.png "gammagradient1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8e5e3-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="8e5e3-113">Compiling the Code</span></span>  
 <span data-ttu-id="8e5e3-114">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="8e5e3-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e5e3-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8e5e3-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.LinearGradientBrush>  
 [<span data-ttu-id="8e5e3-116">グラデーション ブラシを使用した図形の塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="8e5e3-116">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
