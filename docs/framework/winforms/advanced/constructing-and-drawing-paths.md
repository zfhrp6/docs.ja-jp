---
title: パスの作成および描画
ms.date: 03/30/2017
helpviewer_keywords:
- paths [Windows Forms], drawing
- drawing paths [Windows Forms]
- graphics paths [Windows Forms], creating
- graphics paths [Windows Forms], drawing
- examples [Windows Forms], drawing paths
ms.assetid: f16ec921-56cf-46d1-9741-d7316ad06b23
ms.openlocfilehash: 120bb3edcf8e35feca37f02dda5148ba4eebd0ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520657"
---
# <a name="constructing-and-drawing-paths"></a><span data-ttu-id="e5429-102">パスの作成および描画</span><span class="sxs-lookup"><span data-stu-id="e5429-102">Constructing and Drawing Paths</span></span>
<span data-ttu-id="e5429-103">パスは、操作および 1 つの単位として描画できるグラフィックス プリミティブ (線、四角形、曲線、テキスト、および、like) のシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="e5429-103">A path is a sequence of graphics primitives (lines, rectangles, curves, text, and the like) that can be manipulated and drawn as a single unit.</span></span> <span data-ttu-id="e5429-104">パスに分けられます*図表*オープンかクローズしています。</span><span class="sxs-lookup"><span data-stu-id="e5429-104">A path can be divided into *figures* that are either open or closed.</span></span> <span data-ttu-id="e5429-105">図では、複数のプリミティブを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e5429-105">A figure can contain several primitives.</span></span>  
  
 <span data-ttu-id="e5429-106">パスの描画呼び出しをすることができます、<xref:System.Drawing.Graphics.DrawPath%2A>のメソッド、<xref:System.Drawing.Graphics>クラス、およびするを呼び出して、パスを読み込むことができます、<xref:System.Drawing.Graphics.FillPath%2A>のメソッド、<xref:System.Drawing.Graphics>クラスです。</span><span class="sxs-lookup"><span data-stu-id="e5429-106">You can draw a path by calling the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class, and you can fill a path by calling the <xref:System.Drawing.Graphics.FillPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5429-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="e5429-107">In This Section</span></span>  
 [<span data-ttu-id="e5429-108">方法: 直線、曲線、および形状から図形を作成する</span><span class="sxs-lookup"><span data-stu-id="e5429-108">How to: Create Figures from Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-figures-from-lines-curves-and-shapes.md)  
 <span data-ttu-id="e5429-109">使用する方法を示します、<xref:System.Drawing.Drawing2D.GraphicsPath>図形を作成します。</span><span class="sxs-lookup"><span data-stu-id="e5429-109">Shows how to use a <xref:System.Drawing.Drawing2D.GraphicsPath> to create figures.</span></span>  
  
 [<span data-ttu-id="e5429-110">方法: 開いている図形を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="e5429-110">How to: Fill Open Figures</span></span>](../../../../docs/framework/winforms/advanced/how-to-fill-open-figures.md)  
 <span data-ttu-id="e5429-111">入力する方法について説明します、<xref:System.Drawing.Drawing2D.GraphicsPath>です。</span><span class="sxs-lookup"><span data-stu-id="e5429-111">Explains how to fill a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
 [<span data-ttu-id="e5429-112">方法: 曲線のパスを直線に平坦化する</span><span class="sxs-lookup"><span data-stu-id="e5429-112">How to: Flatten a Curved Path into a Line</span></span>](../../../../docs/framework/winforms/advanced/how-to-flatten-a-curved-path-into-a-line.md)  
 <span data-ttu-id="e5429-113">平坦化する方法を示します、<xref:System.Drawing.Drawing2D.GraphicsPath>です。</span><span class="sxs-lookup"><span data-stu-id="e5429-113">Shows how to flatten a <xref:System.Drawing.Drawing2D.GraphicsPath>.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e5429-114">参照</span><span class="sxs-lookup"><span data-stu-id="e5429-114">Reference</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 <span data-ttu-id="e5429-115">このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e5429-115">Describes this class and contains links to all of its members.</span></span>
