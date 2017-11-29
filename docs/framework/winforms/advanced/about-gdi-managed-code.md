---
title: "GDI+ マネージ コードについて"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI+, about GDI+
- GDI+
- graphics [Windows Forms], GDI+
ms.assetid: a98a76ab-e455-49c9-891c-0491ac932f2c
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 711d25c600c2144ad4b134984501f641be24ced2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="about-gdi-managed-code"></a><span data-ttu-id="ff66f-102">GDI+ マネージ コードについて</span><span class="sxs-lookup"><span data-stu-id="ff66f-102">About GDI+ Managed Code</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="ff66f-103"> は、2 次元ベクター グラフィックス、イメージング、および文字体裁を提供する Windows オペレーティング システムの部分です。</span><span class="sxs-lookup"><span data-stu-id="ff66f-103"> is the portion of the Windows operating system that provides two-dimensional vector graphics, imaging, and typography.</span></span> [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="ff66f-104"> は新機能を追加し、既存の機能を最適化することで、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] (以前のバージョンの Windows に含まれているグラフィックス デバイス インターフェイス) を強化しています。</span><span class="sxs-lookup"><span data-stu-id="ff66f-104"> improves on [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] (the Graphics Device Interface included with earlier versions of Windows) by adding new features and by optimizing existing features.</span></span>  
  
 <span data-ttu-id="ff66f-105">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] マネージ クラスのインターフェイス (ラッパーのセット) は、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 一部である XML Web サービスとその他のアプリケーションの構築、配置、および実行のための環境です。</span><span class="sxs-lookup"><span data-stu-id="ff66f-105">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] managed class interface (a set of wrappers) is part of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], an environment for building, deploying, and running XML Web services and other applications.</span></span>  
  
 <span data-ttu-id="ff66f-106">このセクションは、マネージ コードを使用するプログラマのための [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API に関する情報を示しています。</span><span class="sxs-lookup"><span data-stu-id="ff66f-106">This section provides information about the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API for programmers using managed code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff66f-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ff66f-107">In This Section</span></span>  
 [<span data-ttu-id="ff66f-108">直線、曲線、および図形</span><span class="sxs-lookup"><span data-stu-id="ff66f-108">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 <span data-ttu-id="ff66f-109">ベクター グラフィックスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ff66f-109">Discusses vector graphics.</span></span>  
  
 [<span data-ttu-id="ff66f-110">イメージ、ビットマップ、メタファイル</span><span class="sxs-lookup"><span data-stu-id="ff66f-110">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="ff66f-111">使用可能なイメージの種類とそれらを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ff66f-111">Discusses the type of images available and how to work with them.</span></span>  
  
 [<span data-ttu-id="ff66f-112">座標系と変換</span><span class="sxs-lookup"><span data-stu-id="ff66f-112">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 <span data-ttu-id="ff66f-113">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] を使用してグラフィックスを変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ff66f-113">Discusses how to transform graphics with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ff66f-114">参照</span><span class="sxs-lookup"><span data-stu-id="ff66f-114">Reference</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <span data-ttu-id="ff66f-115">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ff66f-115">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Drawing.Image?displayProperty=nameWithType>  
 <span data-ttu-id="ff66f-116">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ff66f-116">Describes this class and has links to all its members.</span></span>  
  
 <span data-ttu-id="ff66f-117"><xref:System.Drawing.Bitmap?displayProperty=nameWithType>、</span><span class="sxs-lookup"><span data-stu-id="ff66f-117"><xref:System.Drawing.Bitmap?displayProperty=nameWithType>,</span></span>  
 <span data-ttu-id="ff66f-118">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ff66f-118">Describes this class and has links to all its members.</span></span>  
  
 <span data-ttu-id="ff66f-119"><xref:System.Drawing.Imaging.Metafile?displayProperty=nameWithType>、</span><span class="sxs-lookup"><span data-stu-id="ff66f-119"><xref:System.Drawing.Imaging.Metafile?displayProperty=nameWithType>,</span></span>  
 <span data-ttu-id="ff66f-120">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ff66f-120">Describes this class and has links to all its members.</span></span>  
  
 <span data-ttu-id="ff66f-121"><xref:System.Drawing.Font?displayProperty=nameWithType>、</span><span class="sxs-lookup"><span data-stu-id="ff66f-121"><xref:System.Drawing.Font?displayProperty=nameWithType>,</span></span>  
 <span data-ttu-id="ff66f-122">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ff66f-122">Describes this class and has links to all its members.</span></span>  
  
 <span data-ttu-id="ff66f-123"><xref:System.Drawing.Brush?displayProperty=nameWithType>、</span><span class="sxs-lookup"><span data-stu-id="ff66f-123"><xref:System.Drawing.Brush?displayProperty=nameWithType>,</span></span>  
 <span data-ttu-id="ff66f-124">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ff66f-124">Describes this class and has links to all its members.</span></span>  
  
 <span data-ttu-id="ff66f-125"><xref:System.Drawing.Color?displayProperty=nameWithType>、</span><span class="sxs-lookup"><span data-stu-id="ff66f-125"><xref:System.Drawing.Color?displayProperty=nameWithType>,</span></span>  
 <span data-ttu-id="ff66f-126">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ff66f-126">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Drawing.Drawing2D.Matrix?displayProperty=nameWithType>  
 <span data-ttu-id="ff66f-127">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ff66f-127">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType>  
 <span data-ttu-id="ff66f-128">このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ff66f-128">Describes this class and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ff66f-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="ff66f-129">Related Sections</span></span>  
 <span data-ttu-id="ff66f-130">[マネージ グラフィックス クラスを使用して](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)です。</span><span class="sxs-lookup"><span data-stu-id="ff66f-130">[Using Managed Graphics Classes](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md).</span></span>  
 <span data-ttu-id="ff66f-131">`Graphics` プログラミング インターフェイスを使用する方法を説明するトピックへのリンクが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ff66f-131">Contains links to topics that demonstrate how to use the `Graphics` programming interface.</span></span>
