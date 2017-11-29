---
title: "方法 : 直線を接合する"
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
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f02da181d66f7bb26a8414782e42eff2570e6918
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-join-lines"></a><span data-ttu-id="33acf-102">方法 : 直線を接合する</span><span class="sxs-lookup"><span data-stu-id="33acf-102">How to: Join Lines</span></span>
<span data-ttu-id="33acf-103">直線の接合部は、2 本の線の端を満たすことや、重ねてによって形成される一般的な領域です。</span><span class="sxs-lookup"><span data-stu-id="33acf-103">A line join is the common area that is formed by two lines whose ends meet or overlap.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="33acf-104">3 つの結合線を提供します。 つながる、傾斜、およびラウンドです。</span><span class="sxs-lookup"><span data-stu-id="33acf-104"> provides three line join styles: miter, bevel, and round.</span></span> <span data-ttu-id="33acf-105">直線の接合スタイルのプロパティは、<xref:System.Drawing.Pen>クラスです。</span><span class="sxs-lookup"><span data-stu-id="33acf-105">Line join style is a property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="33acf-106">直線の接合スタイルを指定すると、<xref:System.Drawing.Pen>オブジェクトのいずれかで接続されているすべての行への接合スタイルが適用されること<xref:System.Drawing.Drawing2D.GraphicsPath>そのペンを使用して描画オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="33acf-106">When you specify a line join style for a <xref:System.Drawing.Pen> object, that join style will be applied to all the connected lines in any <xref:System.Drawing.Drawing2D.GraphicsPath> object drawn using that pen.</span></span>  
  
 <span data-ttu-id="33acf-107">次の図は、直線の面取りの結合の例の結果を示します。</span><span class="sxs-lookup"><span data-stu-id="33acf-107">The following illustration shows the results of the beveled line join example.</span></span>  
  
 <span data-ttu-id="33acf-108">![ペン](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span><span class="sxs-lookup"><span data-stu-id="33acf-108">![Pens](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")</span></span>  
  
## <a name="example"></a><span data-ttu-id="33acf-109">例</span><span class="sxs-lookup"><span data-stu-id="33acf-109">Example</span></span>  
 <span data-ttu-id="33acf-110">直線の接合スタイルを使用して指定することができます、<xref:System.Drawing.Pen.LineJoin%2A>のプロパティ、<xref:System.Drawing.Pen>クラスです。</span><span class="sxs-lookup"><span data-stu-id="33acf-110">You can specify the line join style by using the <xref:System.Drawing.Pen.LineJoin%2A> property of the <xref:System.Drawing.Pen> class.</span></span> <span data-ttu-id="33acf-111">この例では、水平方向と垂直の線の間での傾斜した直線の接合を示します。</span><span class="sxs-lookup"><span data-stu-id="33acf-111">The example demonstrates a beveled line join between a horizontal line and a vertical line.</span></span> <span data-ttu-id="33acf-112">次のコードでは、値に<xref:System.Drawing.Drawing2D.LineJoin.Bevel>に割り当てられている、<xref:System.Drawing.Pen.LineJoin%2A>プロパティのメンバーである、<xref:System.Drawing.Drawing2D.LineJoin>列挙します。</span><span class="sxs-lookup"><span data-stu-id="33acf-112">In the following code, the value <xref:System.Drawing.Drawing2D.LineJoin.Bevel> assigned to the <xref:System.Drawing.Pen.LineJoin%2A> property is a member of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration.</span></span> <span data-ttu-id="33acf-113">他のメンバー、<xref:System.Drawing.Drawing2D.LineJoin>列挙体は<xref:System.Drawing.Drawing2D.LineJoin.Miter>と<xref:System.Drawing.Drawing2D.LineJoin.Round>です。</span><span class="sxs-lookup"><span data-stu-id="33acf-113">The other members of the <xref:System.Drawing.Drawing2D.LineJoin> enumeration are <xref:System.Drawing.Drawing2D.LineJoin.Miter> and <xref:System.Drawing.Drawing2D.LineJoin.Round>.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="33acf-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="33acf-114">Compiling the Code</span></span>  
 <span data-ttu-id="33acf-115">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="33acf-115">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33acf-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="33acf-116">See Also</span></span>  
 [<span data-ttu-id="33acf-117">ペンを使用した直線と図形の描画</span><span class="sxs-lookup"><span data-stu-id="33acf-117">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
