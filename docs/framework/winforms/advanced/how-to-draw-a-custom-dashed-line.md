---
title: "方法 : カスタム破線を描画する"
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
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 90fcc99414e8d5c9542d643677c85d4ff670f50f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-draw-a-custom-dashed-line"></a><span data-ttu-id="b32e1-102">方法 : カスタム破線を描画する</span><span class="sxs-lookup"><span data-stu-id="b32e1-102">How to: Draw a Custom Dashed Line</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="b32e1-103">記載されているいくつかの破線スタイルを提供、<xref:System.Drawing.Drawing2D.DashStyle>列挙します。</span><span class="sxs-lookup"><span data-stu-id="b32e1-103"> provides several dash styles that are listed in the <xref:System.Drawing.Drawing2D.DashStyle> enumeration.</span></span> <span data-ttu-id="b32e1-104">これらの標準の破線スタイルがニーズに適合しないいない場合は、カスタムの破線のパターンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b32e1-104">If those standard dash styles do not suit your needs, you can create a custom dash pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b32e1-105">例</span><span class="sxs-lookup"><span data-stu-id="b32e1-105">Example</span></span>  
 <span data-ttu-id="b32e1-106">カスタム破線を描画する、配列にダッシュと空白の長さを格納し、配列の値として割り当てます、<xref:System.Drawing.Pen.DashPattern%2A>のプロパティ、<xref:System.Drawing.Pen>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b32e1-106">To draw a custom dashed line, put the lengths of the dashes and spaces in an array and assign the array as the value of the <xref:System.Drawing.Pen.DashPattern%2A> property of a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="b32e1-107">次の例は、配列に基づくカスタム破線を描画`{5, 2, 15, 4}`です。</span><span class="sxs-lookup"><span data-stu-id="b32e1-107">The following example draws a custom dashed line based on the array `{5, 2, 15, 4}`.</span></span> <span data-ttu-id="b32e1-108">取得する場合は、配列の要素を 5 のペンの幅に乗算する`{25, 10, 75, 20}`です。</span><span class="sxs-lookup"><span data-stu-id="b32e1-108">If you multiply the elements of the array by the pen width of 5, you get `{25, 10, 75, 20}`.</span></span> <span data-ttu-id="b32e1-109">25 と 75 の長さの別の表示ダッシュと長が 10 ~ 20 の空白が交互です。</span><span class="sxs-lookup"><span data-stu-id="b32e1-109">The displayed dashes alternate in length between 25 and 75, and the spaces alternate in length between 10 and 20.</span></span>  
  
 <span data-ttu-id="b32e1-110">次の図は、結果として得られる点線を示します。</span><span class="sxs-lookup"><span data-stu-id="b32e1-110">The following illustration shows the resulting dashed line.</span></span> <span data-ttu-id="b32e1-111">最終的な dash がで行が終了するようにに 25 よりも短くする必要がある注意 (405, 5)。</span><span class="sxs-lookup"><span data-stu-id="b32e1-111">Note that the final dash has to be shorter than 25 units so that the line can end at (405, 5).</span></span>  
  
 <span data-ttu-id="b32e1-112">![ペン](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")</span><span class="sxs-lookup"><span data-stu-id="b32e1-112">![Pens](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b32e1-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b32e1-113">Compiling the Code</span></span>  
 <span data-ttu-id="b32e1-114">Windows フォームを作成し、処理、フォームの<xref:System.Windows.Forms.Control.Paint>イベント。</span><span class="sxs-lookup"><span data-stu-id="b32e1-114">Create a Windows Form and handle the form's <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="b32e1-115">上記のコードを貼り付け、<xref:System.Windows.Forms.Control.Paint>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="b32e1-115">Paste the preceding code into the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b32e1-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="b32e1-116">See Also</span></span>  
 [<span data-ttu-id="b32e1-117">ペンを使用した直線と図形の描画</span><span class="sxs-lookup"><span data-stu-id="b32e1-117">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
