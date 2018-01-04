---
title: "方法 : バッファリングされたグラフィックスを手動で描画する"
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
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3a5d06da3a398782b0285fb55807df5832cf771
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="c05d3-102">方法 : バッファリングされたグラフィックスを手動で描画する</span><span class="sxs-lookup"><span data-stu-id="c05d3-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="c05d3-103">独自のバッファリングされたグラフィックスを管理している場合は、グラフィックス バッファーを作成して表示できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c05d3-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="c05d3-104"><xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> メソッドを呼び出すことで、画面の描画サーフェイスに関連付けられている <xref:System.Drawing.BufferedGraphics> クラスのインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c05d3-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="c05d3-105">このメソッドは、フォームやコントロールなど、特定の表示サーフェイスに関連付けられている <xref:System.Drawing.BufferedGraphics> インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c05d3-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="c05d3-106"><xref:System.Drawing.BufferedGraphics> インスタンスを作成した後、<xref:System.Drawing.BufferedGraphics.Graphics%2A> プロパティを通じて表すバッファーにグラフィックスを描画することができます。</span><span class="sxs-lookup"><span data-stu-id="c05d3-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="c05d3-107">グラフィックスのすべての操作を実行した後で、<xref:System.Drawing.BufferedGraphics.Render%2A> メソッドを呼び出すことで、バッファーの内容を画面にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="c05d3-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c05d3-108">独自の表示を実行する場合、わずかですがメモリ消費量が増加します。</span><span class="sxs-lookup"><span data-stu-id="c05d3-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="c05d3-109">バッファリングされたグラフィックスを手動で描画するには</span><span class="sxs-lookup"><span data-stu-id="c05d3-109">To manually display buffered graphics</span></span>  
  
1.  <span data-ttu-id="c05d3-110"><xref:System.Drawing.BufferedGraphicsContext> クラスのインスタンスへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="c05d3-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="c05d3-111">詳細については、次を参照してください。[する方法: バッファリングされたグラフィックス管理手動で](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)です。</span><span class="sxs-lookup"><span data-stu-id="c05d3-111">For more information, see [How to: Manually Manage Buffered Graphics](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2.  <span data-ttu-id="c05d3-112">次のコード例に示すように、<xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> メソッドを呼び出して <xref:System.Drawing.BufferedGraphics> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c05d3-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  <span data-ttu-id="c05d3-113"><xref:System.Drawing.BufferedGraphics.Graphics%2A> プロパティを設定することで、グラフィックスのバッファーにグラフィックスを描画します。</span><span class="sxs-lookup"><span data-stu-id="c05d3-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="c05d3-114">例:</span><span class="sxs-lookup"><span data-stu-id="c05d3-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  <span data-ttu-id="c05d3-115">グラフィックス バッファーへのすべての描画操作が完了したら、次のコード例に示すように、<xref:System.Drawing.BufferedGraphics.Render%2A> メソッドを呼び出して、そのバッファーに関連付けられている描画サーフェイス、または指定された描画サーフェイスのいずれかにバッファーを表示します。</span><span class="sxs-lookup"><span data-stu-id="c05d3-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  <span data-ttu-id="c05d3-116">グラフィックのレンダリングが完了した後、<xref:System.Drawing.BufferedGraphics> インスタンスの `Dispose` メソッドを呼び出し、システム リソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="c05d3-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="c05d3-117">参照</span><span class="sxs-lookup"><span data-stu-id="c05d3-117">See Also</span></span>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphics>  
 [<span data-ttu-id="c05d3-118">ダブル バッファリングされたグラフィックス</span><span class="sxs-lookup"><span data-stu-id="c05d3-118">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [<span data-ttu-id="c05d3-119">方法: バッファリングされたグラフィックスを手動で管理する</span><span class="sxs-lookup"><span data-stu-id="c05d3-119">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)
