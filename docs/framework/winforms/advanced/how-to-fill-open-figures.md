---
title: "方法 : 開いている図形を塗りつぶす"
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
- open figures [Windows Forms], filling
- figures [Windows Forms], filling
ms.assetid: 5a36b0e4-f1f4-46c0-a85a-22ae98491950
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c020e5f7306e73ee97dff0b492b04b5a153059cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-fill-open-figures"></a><span data-ttu-id="99d02-102">方法 : 開いている図形を塗りつぶす</span><span class="sxs-lookup"><span data-stu-id="99d02-102">How to: Fill Open Figures</span></span>
<span data-ttu-id="99d02-103">渡すことによって、パスを入力することができます、<xref:System.Drawing.Drawing2D.GraphicsPath>オブジェクトを<xref:System.Drawing.Graphics.FillPath%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="99d02-103">You can fill a path by passing a <xref:System.Drawing.Drawing2D.GraphicsPath> object to the <xref:System.Drawing.Graphics.FillPath%2A> method.</span></span> <span data-ttu-id="99d02-104"><xref:System.Drawing.Graphics.FillPath%2A>メソッドが塗りつぶしモード (代替またはワインディング) に従って、パスに設定されているパスを入力します。</span><span class="sxs-lookup"><span data-stu-id="99d02-104">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the fill mode (alternate or winding) currently set for the path.</span></span> <span data-ttu-id="99d02-105">パスに任意の開いている図形がある場合、その数値が終了した場合と、パスが塗りつぶされます。</span><span class="sxs-lookup"><span data-stu-id="99d02-105">If the path has any open figures, the path is filled as if those figures were closed.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="99d02-106">終了位置から開始点に直線を描画して、図を閉じます。</span><span class="sxs-lookup"><span data-stu-id="99d02-106"> closes a figure by drawing a straight line from its ending point to its starting point.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99d02-107">例</span><span class="sxs-lookup"><span data-stu-id="99d02-107">Example</span></span>  
 <span data-ttu-id="99d02-108">次の例では、1 つ開いている図 (円弧) と 1 つ閉じた図形 (楕円) を持つパスを作成します。</span><span class="sxs-lookup"><span data-stu-id="99d02-108">The following example creates a path that has one open figure (an arc) and one closed figure (an ellipse).</span></span> <span data-ttu-id="99d02-109"><xref:System.Drawing.Graphics.FillPath%2A>メソッドが、パスは、既定の塗りつぶしモードに従って<xref:System.Drawing.Drawing2D.FillMode.Alternate>です。</span><span class="sxs-lookup"><span data-stu-id="99d02-109">The <xref:System.Drawing.Graphics.FillPath%2A> method fills the path according to the default fill mode, which is <xref:System.Drawing.Drawing2D.FillMode.Alternate>.</span></span>  
  
 <span data-ttu-id="99d02-110">次の図は、コード例の出力を示します。</span><span class="sxs-lookup"><span data-stu-id="99d02-110">The following illustration shows the output of the example code.</span></span> <span data-ttu-id="99d02-111">パスが格納されていることに注意してください (に従って<xref:System.Drawing.Drawing2D.FillMode.Alternate>) 開いている図形が終了して直線の行の終了点を基盤にした場合とします。</span><span class="sxs-lookup"><span data-stu-id="99d02-111">Note that the path is filled (according to <xref:System.Drawing.Drawing2D.FillMode.Alternate>) as if the open figure were closed by a straight line from its ending point to its starting point.</span></span>  
  
 <span data-ttu-id="99d02-112">![ファイルを開くパス](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span><span class="sxs-lookup"><span data-stu-id="99d02-112">![Fill Open Path](../../../../docs/framework/winforms/advanced/media/fillopenpath.png "FillOpenPath")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="99d02-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="99d02-113">Compiling the Code</span></span>  
 <span data-ttu-id="99d02-114">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="99d02-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99d02-115">参照</span><span class="sxs-lookup"><span data-stu-id="99d02-115">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [<span data-ttu-id="99d02-116">GDI+ でのグラフィックス パス</span><span class="sxs-lookup"><span data-stu-id="99d02-116">Graphics Paths in GDI+</span></span>](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md)
