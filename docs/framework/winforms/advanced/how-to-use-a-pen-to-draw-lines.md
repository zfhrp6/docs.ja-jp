---
title: "方法 : ペンを使用して線を描画する"
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
- lines [Windows Forms], drawing
- pens [Windows Forms], drawing lines
ms.assetid: 0828c331-a438-4bdd-a4d6-3ef1e59e8795
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 156d7acbbf3f863e89ae2a5c303b2cf4140b3592
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-pen-to-draw-lines"></a><span data-ttu-id="9d20b-102">方法 : ペンを使用して線を描画する</span><span class="sxs-lookup"><span data-stu-id="9d20b-102">How to: Use a Pen to Draw Lines</span></span>
<span data-ttu-id="9d20b-103">線を描画する必要があります、<xref:System.Drawing.Graphics>オブジェクトおよび<xref:System.Drawing.Pen>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="9d20b-103">To draw lines, you need a <xref:System.Drawing.Graphics> object and a <xref:System.Drawing.Pen> object.</span></span> <span data-ttu-id="9d20b-104"><xref:System.Drawing.Graphics>オブジェクトは、提供、<xref:System.Drawing.Graphics.DrawLine%2A>メソッド、および<xref:System.Drawing.Pen>オブジェクトは、線、色、太さなどの機能を格納します。</span><span class="sxs-lookup"><span data-stu-id="9d20b-104">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawLine%2A> method, and the <xref:System.Drawing.Pen> object stores features of the line, such as color and width.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d20b-105">例</span><span class="sxs-lookup"><span data-stu-id="9d20b-105">Example</span></span>  
 <span data-ttu-id="9d20b-106">次の例から行を描画する (20, 10) に (300, 100)。</span><span class="sxs-lookup"><span data-stu-id="9d20b-106">The following example draws a line from (20, 10) to (300, 100).</span></span> <span data-ttu-id="9d20b-107">最初のステートメントを使用して、<xref:System.Drawing.Pen.%23ctor%2A>黒のペンを作成するクラスのコンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="9d20b-107">The first statement uses the <xref:System.Drawing.Pen.%23ctor%2A> class constructor to create a black pen.</span></span> <span data-ttu-id="9d20b-108">渡される 1 つの引数、<xref:System.Drawing.Pen.%23ctor%2A>コンス トラクターは、<xref:System.Drawing.Color>で作成されたオブジェクト、<xref:System.Drawing.Color.FromArgb%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9d20b-108">The one argument passed to the <xref:System.Drawing.Pen.%23ctor%2A> constructor is a <xref:System.Drawing.Color> object created with the <xref:System.Drawing.Color.FromArgb%2A> method.</span></span> <span data-ttu-id="9d20b-109">作成に使用される値、<xref:System.Drawing.Color>オブジェクト — (255, 0、0, 0): 色のアルファ、赤、緑、および青のコンポーネントに対応します。</span><span class="sxs-lookup"><span data-stu-id="9d20b-109">The values used to create the <xref:System.Drawing.Color> object — (255, 0, 0, 0) — correspond to the alpha, red, green, and blue components of the color.</span></span> <span data-ttu-id="9d20b-110">これらの値は、不透明な黒のペンを定義します。</span><span class="sxs-lookup"><span data-stu-id="9d20b-110">These values define an opaque black pen.</span></span>  
  
 [!code-csharp[System.Drawing.UsingAPen#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.UsingAPen#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d20b-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="9d20b-111">Compiling the Code</span></span>  
 <span data-ttu-id="9d20b-112">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventArgs> イベント ハンドラーのパラメーターである `e`<xref:System.Windows.Forms.Control.Paint> を必要とします。</span><span class="sxs-lookup"><span data-stu-id="9d20b-112">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d20b-113">参照</span><span class="sxs-lookup"><span data-stu-id="9d20b-113">See Also</span></span>  
 <xref:System.Drawing.Pen>  
 [<span data-ttu-id="9d20b-114">ペンを使用した直線と図形の描画</span><span class="sxs-lookup"><span data-stu-id="9d20b-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="9d20b-115">GDI+ でのペン、直線、および四角形</span><span class="sxs-lookup"><span data-stu-id="9d20b-115">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
