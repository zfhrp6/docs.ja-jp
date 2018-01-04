---
title: "方法 : 純色で図形を塗りつぶす"
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
- colors [Windows Forms], adding to shapes
- shapes [Windows Forms], filling
ms.assetid: 06088b31-bac9-4ef3-9ebe-06c2c764d6df
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f016404feeac47c5f77527b8baa68d70742d4763
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-a-shape-with-a-solid-color"></a><span data-ttu-id="6fe78-102">方法 : 純色で図形を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="6fe78-102">How to: Fill a Shape with a Solid Color</span></span>
<span data-ttu-id="6fe78-103">純色で図形を塗りつぶす、作成、<xref:System.Drawing.SolidBrush>オブジェクト、およびをパススルーする<xref:System.Drawing.SolidBrush>オブジェクトへの fill メソッドのいずれかの引数として、<xref:System.Drawing.Graphics>クラスです。</span><span class="sxs-lookup"><span data-stu-id="6fe78-103">To fill a shape with a solid color, create a <xref:System.Drawing.SolidBrush> object, and then pass that <xref:System.Drawing.SolidBrush> object as an argument to one of the fill methods of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="6fe78-104">次の例では、色が赤に楕円を設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6fe78-104">The following example shows how to fill an ellipse with the color red.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fe78-105">例</span><span class="sxs-lookup"><span data-stu-id="6fe78-105">Example</span></span>  
 <span data-ttu-id="6fe78-106">次のコードで、<xref:System.Drawing.SolidBrush.%23ctor%2A>コンス トラクター、<xref:System.Drawing.Color>唯一の引数としてオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="6fe78-106">In the following code, the <xref:System.Drawing.SolidBrush.%23ctor%2A> constructor takes a <xref:System.Drawing.Color> object as its only argument.</span></span> <span data-ttu-id="6fe78-107">によって使用される値、<xref:System.Drawing.Color.FromArgb%2A>メソッドは、色のアルファ、赤、緑、および青の要素を表します。</span><span class="sxs-lookup"><span data-stu-id="6fe78-107">The values used by the <xref:System.Drawing.Color.FromArgb%2A> method represent the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="6fe78-108">これらの各値は、0 ~ 255 の範囲でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="6fe78-108">Each of these values must be in the range 0 through 255.</span></span> <span data-ttu-id="6fe78-109">最初の 255 は、色は完全に不透明で、ある 2 つ目の 255 赤の要素が、最大の輝度を示します。</span><span class="sxs-lookup"><span data-stu-id="6fe78-109">The first 255 indicates that the color is fully opaque, and the second 255 indicates that the red component is at full intensity.</span></span> <span data-ttu-id="6fe78-110">2 つの 0 は、緑、青のコンポーネントは、両方が 0 の輝度を持つことを示すです。</span><span class="sxs-lookup"><span data-stu-id="6fe78-110">The two zeros indicate that the green and blue components both have an intensity of 0.</span></span>  
  
 <span data-ttu-id="6fe78-111">渡される 4 つの数字 (0, 0、100, 60)、<xref:System.Drawing.Graphics.FillEllipse%2A>メソッドは、楕円の外接する四角形のサイズと場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="6fe78-111">The four numbers (0, 0, 100, 60) passed to the <xref:System.Drawing.Graphics.FillEllipse%2A> method specify the location and size of the bounding rectangle for the ellipse.</span></span> <span data-ttu-id="6fe78-112">四角形は、左上隅の (0, 0)、100 の幅と高さが 60 です。</span><span class="sxs-lookup"><span data-stu-id="6fe78-112">The rectangle has an upper-left corner of (0, 0), a width of 100, and a height of 60.</span></span>  
  
 [!code-csharp[System.Drawing.UsingABrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingABrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6fe78-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6fe78-113">Compiling the Code</span></span>  
 <span data-ttu-id="6fe78-114">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="6fe78-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe78-115">参照</span><span class="sxs-lookup"><span data-stu-id="6fe78-115">See Also</span></span>  
 [<span data-ttu-id="6fe78-116">ブラシを使用した図形の塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="6fe78-116">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
