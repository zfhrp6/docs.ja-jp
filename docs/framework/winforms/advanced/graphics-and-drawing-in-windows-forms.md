---
title: "Windows フォームにおけるグラフィックスと描画"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms]
- graphics [Windows Forms], using in Windows Forms
- GDI+, using in managed code
- drawing [Windows Forms]
ms.assetid: 362532c5-1a06-4257-bdc8-723461009ede
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8ae9810b10a7357f7f8d00783335335a391a5211
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-and-drawing-in-windows-forms"></a><span data-ttu-id="404c5-102">Windows フォームにおけるグラフィックスと描画</span><span class="sxs-lookup"><span data-stu-id="404c5-102">Graphics and Drawing in Windows Forms</span></span>
<span data-ttu-id="404c5-103">共通言語ランタイムは、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] と呼ばれる Windows グラフィックス デバイス インターフェイス ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) の高度な実装を使用します。</span><span class="sxs-lookup"><span data-stu-id="404c5-103">The common language runtime uses an advanced implementation of the Windows Graphics Device Interface ([!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]) called [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="404c5-104">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を使用して、グラフィックスの作成、テキストの描画や、グラフィカル イメージをオブジェクトとして操作することができます。</span><span class="sxs-lookup"><span data-stu-id="404c5-104">With [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] you can create graphics, draw text, and manipulate graphical images as objects.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="404c5-105"> はパフォーマンスと使いやすさを提供するよう設計されています。</span><span class="sxs-lookup"><span data-stu-id="404c5-105"> is designed to offer performance and ease of use.</span></span> <span data-ttu-id="404c5-106">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を使用して、Windows フォームとコントロールのグラフィカル イメージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="404c5-106">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render graphical images on Windows Forms and controls.</span></span> <span data-ttu-id="404c5-107">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を Web フォームで直接使用することはできませんが、イメージの Web サーバー コントロールからグラフィカル イメージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="404c5-107">Although you cannot use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] directly on Web Forms, you can display graphical images through the Image Web Server control.</span></span>  
  
 <span data-ttu-id="404c5-108">このセクションでは、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] プログラミングの基礎を紹介するトピックが見つかります。</span><span class="sxs-lookup"><span data-stu-id="404c5-108">In this section, you will find topics that introduce the fundamentals of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] programming.</span></span> <span data-ttu-id="404c5-109">このセクションは、包括的なリファレンスを意図したものではありませんが、<xref:System.Drawing.Graphics>、<xref:System.Drawing.Pen>、<xref:System.Drawing.Brush>、および <xref:System.Drawing.Color> の各オブジェクトに関する情報が含まれ、図形の描画、テキストの描画、イメージの表示などのタスクを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="404c5-109">Although not intended to be a comprehensive reference, this section includes information about the <xref:System.Drawing.Graphics>, <xref:System.Drawing.Pen>, <xref:System.Drawing.Brush>, and <xref:System.Drawing.Color> objects, and explains how to perform such tasks as drawing shapes, drawing text, or displaying images.</span></span> <span data-ttu-id="404c5-110">詳細については、次を参照してください。 [GDI + の参照](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="404c5-110">For more information, see [GDI+ Reference](https://msdn.microsoft.com/library/vs/alm/ms533799.aspx).</span></span>  
  
 <span data-ttu-id="404c5-111">すぐに開始する場合、「[グラフィックス プログラミングについて](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="404c5-111">If you'd like to jump in and get started right away, see [Getting Started with Graphics Programming](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md).</span></span> <span data-ttu-id="404c5-112">Windows フォームで線、図形、テキストなどを描画するためのコードの使用方法に関するトピックがあります。</span><span class="sxs-lookup"><span data-stu-id="404c5-112">It has topics on how to use code to draw lines, shapes, text, and more on Windows forms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="404c5-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="404c5-113">In This Section</span></span>  
 [<span data-ttu-id="404c5-114">グラフィックスの概要</span><span class="sxs-lookup"><span data-stu-id="404c5-114">Graphics Overview</span></span>](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 <span data-ttu-id="404c5-115">グラフィックスに関連するマネージ クラスの概要を提供します。</span><span class="sxs-lookup"><span data-stu-id="404c5-115">Provides an introduction to the graphics-related managed classes.</span></span>  
  
 [<span data-ttu-id="404c5-116">GDI+ マネージ コードについて</span><span class="sxs-lookup"><span data-stu-id="404c5-116">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 <span data-ttu-id="404c5-117">マネージ [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] クラスに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="404c5-117">Provides information about the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes.</span></span>  
  
 [<span data-ttu-id="404c5-118">マネージ グラフィックス クラスの使用</span><span class="sxs-lookup"><span data-stu-id="404c5-118">Using Managed Graphics Classes</span></span>](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)  
 <span data-ttu-id="404c5-119">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] マネージ クラスを使用して、さまざまなタスクを完了する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="404c5-119">Demonstrates how to complete a variety of tasks using the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] managed classes.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="404c5-120">参照</span><span class="sxs-lookup"><span data-stu-id="404c5-120">Reference</span></span>  
 <xref:System.Drawing>  
 <span data-ttu-id="404c5-121">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] の基本的なグラフィックス機能を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="404c5-121">Provides access to [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] basic graphics functionality.</span></span>  
  
 <xref:System.Drawing.Drawing2D>  
 <span data-ttu-id="404c5-122">2 次元グラフィックスおよびベクター グラフィックス機能の詳細を提供します。</span><span class="sxs-lookup"><span data-stu-id="404c5-122">Provides advanced two-dimensional and vector graphics functionality.</span></span>  
  
 <xref:System.Drawing.Imaging>  
 <span data-ttu-id="404c5-123">高度な [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] イメージング機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="404c5-123">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] imaging functionality.</span></span>  
  
 <xref:System.Drawing.Text>  
 <span data-ttu-id="404c5-124">高度な [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] タイポグラフィ機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="404c5-124">Provides advanced [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] typography functionality.</span></span> <span data-ttu-id="404c5-125">この名前空間のクラスを使用して、フォントのコレクションを作成して使用することができます。</span><span class="sxs-lookup"><span data-stu-id="404c5-125">The classes in this namespace can be used to create and use collections of fonts.</span></span>  
  
 <xref:System.Drawing.Printing>  
 <span data-ttu-id="404c5-126">印刷機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="404c5-126">Provides printing functionality.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="404c5-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="404c5-127">Related Sections</span></span>  
 [<span data-ttu-id="404c5-128">コントロールのカスタム描画およびレンダリング</span><span class="sxs-lookup"><span data-stu-id="404c5-128">Custom Control Painting and Rendering</span></span>](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)  
 <span data-ttu-id="404c5-129">描画コントロールのコードを提供する方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="404c5-129">Details how to provide code for painting controls.</span></span>
