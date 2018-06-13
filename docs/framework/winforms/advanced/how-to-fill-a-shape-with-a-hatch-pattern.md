---
title: '方法 : ハッチ パターンで図形を塗りつぶす'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: 5b6b5b61b83e5be05999099f2cc6b9e715ca35c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521743"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a><span data-ttu-id="6f101-102">方法 : ハッチ パターンで図形を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="6f101-102">How to: Fill a Shape with a Hatch Pattern</span></span>
<span data-ttu-id="6f101-103">2 つの色からハッチ パターンが行われます: バック グラウンドとバック グラウンド上、パターンを形成する、行のいずれかのいずれか。</span><span class="sxs-lookup"><span data-stu-id="6f101-103">A hatch pattern is made from two colors: one for the background and one for the lines that form the pattern over the background.</span></span> <span data-ttu-id="6f101-104">ハッチ パターンで、閉じた図形の塗りつぶし を使用して、<xref:System.Drawing.Drawing2D.HatchBrush>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6f101-104">To fill a closed shape with a hatch pattern, use a <xref:System.Drawing.Drawing2D.HatchBrush> object.</span></span> <span data-ttu-id="6f101-105">次の例では、ハッチ パターンで楕円を塗りつぶす方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6f101-105">The following example demonstrates how to fill an ellipse with a hatch pattern:</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f101-106">例</span><span class="sxs-lookup"><span data-stu-id="6f101-106">Example</span></span>  
 <span data-ttu-id="6f101-107"><xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A>コンス トラクターは、次の 3 つの引数を受け取る: 陰影のスタイル、ハッチの線の色と背景の色。</span><span class="sxs-lookup"><span data-stu-id="6f101-107">The <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> constructor takes three arguments: the hatch style, the color of the hatch line, and the color of the background.</span></span> <span data-ttu-id="6f101-108">陰影のスタイル引数が任意の値を指定できます、<xref:System.Drawing.Drawing2D.HatchStyle>列挙します。</span><span class="sxs-lookup"><span data-stu-id="6f101-108">The hatch style argument can be any value from the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration.</span></span> <span data-ttu-id="6f101-109">50 以上の要素がある、<xref:System.Drawing.Drawing2D.HatchStyle>列挙体です。 これらのいくつか要素は、次の一覧に含まれています。</span><span class="sxs-lookup"><span data-stu-id="6f101-109">There are more than fifty elements in the <xref:System.Drawing.Drawing2D.HatchStyle> enumeration; a few of those elements are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 <span data-ttu-id="6f101-110">次の図は、塗りつぶされた楕円を示します。</span><span class="sxs-lookup"><span data-stu-id="6f101-110">The following illustration shows the filled ellipse.</span></span>  
  
 <span data-ttu-id="6f101-111">![ハッチ パターン](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")</span><span class="sxs-lookup"><span data-stu-id="6f101-111">![Hatch Pattern](../../../../docs/framework/winforms/advanced/media/hatch1.png "hatch1")</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6f101-112">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6f101-112">Compiling the Code</span></span>  
 <span data-ttu-id="6f101-113">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。</span><span class="sxs-lookup"><span data-stu-id="6f101-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f101-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f101-114">See Also</span></span>  
 [<span data-ttu-id="6f101-115">ブラシを使用した図形の塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="6f101-115">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
