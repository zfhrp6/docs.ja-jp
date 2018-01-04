---
title: "方法 : ペンを作成する"
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
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating pens
- pens [Windows Forms], creating
- Pen object
ms.assetid: 7fbea8b7-7ac1-4413-9c17-733a850381e3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 95954960db8534844820d14869273de1c44a51e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-pen"></a><span data-ttu-id="baa16-102">方法 : ペンを作成する</span><span class="sxs-lookup"><span data-stu-id="baa16-102">How to: Create a Pen</span></span>
<span data-ttu-id="baa16-103">この例で作成、<xref:System.Drawing.Pen>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="baa16-103">This example creates a <xref:System.Drawing.Pen> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baa16-104">例</span><span class="sxs-lookup"><span data-stu-id="baa16-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#3)]
 [!code-csharp[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#3)]
 [!code-vb[System.Drawing.ConceptualHowTos#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="baa16-105">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="baa16-105">Robust Programming</span></span>  
 <span data-ttu-id="baa16-106">などのシステム リソースを消費しているオブジェクトを使用して完了したら<xref:System.Drawing.Pen>オブジェクトを呼び出す必要があります<xref:System.Drawing.Pen.Dispose%2A>にします。</span><span class="sxs-lookup"><span data-stu-id="baa16-106">After you have finished using objects that consume system resources, such as <xref:System.Drawing.Pen> objects, you should call <xref:System.Drawing.Pen.Dispose%2A> on them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baa16-107">参照</span><span class="sxs-lookup"><span data-stu-id="baa16-107">See Also</span></span>  
 <xref:System.Drawing.Pen>  
 [<span data-ttu-id="baa16-108">グラフィックス プログラミングについて</span><span class="sxs-lookup"><span data-stu-id="baa16-108">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="baa16-109">GDI+ でのペン、直線、および四角形</span><span class="sxs-lookup"><span data-stu-id="baa16-109">Pens, Lines, and Rectangles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)
