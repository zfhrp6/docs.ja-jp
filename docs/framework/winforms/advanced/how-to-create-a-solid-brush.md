---
title: '方法 : ソリッド ブラシを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- solid color brushes
- brushes [Windows Forms], examples
- brushes [Windows Forms], creating solid
ms.assetid: 85c3fe7d-fb1d-4591-8a9f-d75b556b90af
ms.openlocfilehash: 8dad10fbfb0dfb34fee6a5640b1a49e7fb234479
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520748"
---
# <a name="how-to-create-a-solid-brush"></a><span data-ttu-id="d6c57-102">方法 : ソリッド ブラシを作成する</span><span class="sxs-lookup"><span data-stu-id="d6c57-102">How to: Create a Solid Brush</span></span>
<span data-ttu-id="d6c57-103">この例で作成、<xref:System.Drawing.SolidBrush>で使用できるオブジェクト、<xref:System.Drawing.Graphics>図形を塗りつぶすためのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d6c57-103">This example creates a <xref:System.Drawing.SolidBrush> object that can be used by a <xref:System.Drawing.Graphics> object for filling shapes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6c57-104">例</span><span class="sxs-lookup"><span data-stu-id="d6c57-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d6c57-105">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="d6c57-105">Robust Programming</span></span>  
 <span data-ttu-id="d6c57-106">呼び出す必要がありますが、使用後<xref:System.IDisposable.Dispose%2A>ブラシ オブジェクトなどのシステム リソースを消費しているオブジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="d6c57-106">After you have finished using them, you should call <xref:System.IDisposable.Dispose%2A> on objects that consume system resources, such as brush objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c57-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6c57-107">See Also</span></span>  
 <xref:System.Drawing.SolidBrush>  
 <xref:System.Drawing.Brush>  
 [<span data-ttu-id="d6c57-108">グラフィックス プログラミングについて</span><span class="sxs-lookup"><span data-stu-id="d6c57-108">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="d6c57-109">GDI+ でのブラシと塗りつぶされた図形</span><span class="sxs-lookup"><span data-stu-id="d6c57-109">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)  
 [<span data-ttu-id="d6c57-110">ブラシを使用した図形の塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="d6c57-110">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
