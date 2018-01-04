---
title: "方法 : 領域でクリッピングを使用する"
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
- regions [Windows Forms], clipping
- regions [Windows Forms], restricting drawing surface
ms.assetid: 43d121b4-e14c-4901-b25c-2d6c25ba4e29
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 281ae701bc3e5cee38952a05474360019f76a665
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-clipping-with-a-region"></a><span data-ttu-id="3ddc3-102">方法 : 領域でクリッピングを使用する</span><span class="sxs-lookup"><span data-stu-id="3ddc3-102">How to: Use Clipping with a Region</span></span>
<span data-ttu-id="3ddc3-103">プロパティの 1 つ、<xref:System.Drawing.Graphics>クラスは、のクリップ領域。</span><span class="sxs-lookup"><span data-stu-id="3ddc3-103">One of the properties of the <xref:System.Drawing.Graphics> class is the clip region.</span></span> <span data-ttu-id="3ddc3-104">すべての描画を行うを指定された<xref:System.Drawing.Graphics>オブジェクトのクリップ領域に制限されて<xref:System.Drawing.Graphics>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="3ddc3-104">All drawing done by a given <xref:System.Drawing.Graphics> object is restricted to the clip region of that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="3ddc3-105">クリップ領域を設定するには、呼び出すことによって、<xref:System.Drawing.Graphics.SetClip%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="3ddc3-105">You can set the clip region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ddc3-106">例</span><span class="sxs-lookup"><span data-stu-id="3ddc3-106">Example</span></span>  
 <span data-ttu-id="3ddc3-107">次の例では、単一の多角形で構成されるパスを構築します。</span><span class="sxs-lookup"><span data-stu-id="3ddc3-107">The following example constructs a path that consists of a single polygon.</span></span> <span data-ttu-id="3ddc3-108">コードは、そのパスに基づく領域を作成します。</span><span class="sxs-lookup"><span data-stu-id="3ddc3-108">Then the code constructs a region, based on that path.</span></span> <span data-ttu-id="3ddc3-109">渡されるが、地域、<xref:System.Drawing.Graphics.SetClip%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクトと、2 つの文字列が描画されます。</span><span class="sxs-lookup"><span data-stu-id="3ddc3-109">The region is passed to the <xref:System.Drawing.Graphics.SetClip%2A> method of a <xref:System.Drawing.Graphics> object, and then two strings are drawn.</span></span>  
  
 <span data-ttu-id="3ddc3-110">次の図は、クリップされた文字列を示します。</span><span class="sxs-lookup"><span data-stu-id="3ddc3-110">The following illustration shows the clipped strings.</span></span>  
  
 <span data-ttu-id="3ddc3-111">![クリップ](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span><span class="sxs-lookup"><span data-stu-id="3ddc3-111">![Clip](../../../../docs/framework/winforms/advanced/media/clip1.png "clip1")</span></span>  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.MiscLegacyTopics#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3ddc3-112">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="3ddc3-112">Compiling the Code</span></span>  
 <span data-ttu-id="3ddc3-113">前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.PaintEventHandler> のパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。</span><span class="sxs-lookup"><span data-stu-id="3ddc3-113">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ddc3-114">参照</span><span class="sxs-lookup"><span data-stu-id="3ddc3-114">See Also</span></span>  
 [<span data-ttu-id="3ddc3-115">GDI+ での領域</span><span class="sxs-lookup"><span data-stu-id="3ddc3-115">Regions in GDI+</span></span>](../../../../docs/framework/winforms/advanced/regions-in-gdi.md)  
 [<span data-ttu-id="3ddc3-116">領域の使用</span><span class="sxs-lookup"><span data-stu-id="3ddc3-116">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
