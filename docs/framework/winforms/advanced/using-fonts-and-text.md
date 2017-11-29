---
title: "フォントとテキストの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing in Windows Forms
- examples [Windows Forms], fonts and text
- fonts [Windows Forms], using in Windows Forms
- strings [Windows Forms], drawing in Windows Forms
ms.assetid: d43640f3-da94-4df2-a29d-a9d021a1c069
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c18dde7265a07eb45e0211a882b19acc6342e924
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="using-fonts-and-text"></a><span data-ttu-id="b1bf3-102">フォントとテキストの使用</span><span class="sxs-lookup"><span data-stu-id="b1bf3-102">Using Fonts and Text</span></span>
<span data-ttu-id="b1bf3-103">によって提供されるいくつかのクラスがある[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]と[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]Windows フォームでテキストを描画するためです。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-103">There are several classes offered by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text on Windows Forms.</span></span> <span data-ttu-id="b1bf3-104">[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics>クラスにはいくつか<xref:System.Drawing.Graphics.DrawString%2A>テキスト、位置、外接する四角形、フォント、および形式などのさまざまな機能を指定できるようにするメソッド。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-104">The [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <xref:System.Drawing.Graphics> class has several <xref:System.Drawing.Graphics.DrawString%2A> methods that allow you to specify various features of text, such as location, bounding rectangle, font, and format.</span></span> <span data-ttu-id="b1bf3-105">さらに、描画し、メジャーを含むテキスト[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]静的<xref:System.Windows.Forms.TextRenderer.DrawText%2A>と<xref:System.Windows.Forms.TextRenderer.MeasureText%2A>によって提供されるメソッド、`TextRenderer`クラスです。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-105">In addition, you can draw and measure text with [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] using the static <xref:System.Windows.Forms.TextRenderer.DrawText%2A> and <xref:System.Windows.Forms.TextRenderer.MeasureText%2A> methods offered by the `TextRenderer` class.</span></span> <span data-ttu-id="b1bf3-106">[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]メソッドの場所、フォント、および形式を指定することも可能です。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-106">The [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] methods also allow you to specify location, font, and format.</span></span> <span data-ttu-id="b1bf3-107">いずれかを選択することができます[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]または[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]テキスト レンダリングされます。 ただし、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]通常をより的確にパフォーマンスとより正確なテキストを測定します。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-107">You can choose either [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] or [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] for text rendering; however, [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] generally offers better performance and more accurate text measuring.</span></span> <span data-ttu-id="b1bf3-108">テキスト レンダリングに影響するその他のクラスに含まれる`FontFamily`、 `Font`、 <xref:System.Drawing.StringFormat>、および`TextFormatFlags`です。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-108">Other classes that contribute to text rendering include `FontFamily`, `Font`, <xref:System.Drawing.StringFormat>, and `TextFormatFlags`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1bf3-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b1bf3-109">In This Section</span></span>  
 [<span data-ttu-id="b1bf3-110">方法: フォント ファミリとフォントを作成する</span><span class="sxs-lookup"><span data-stu-id="b1bf3-110">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 <span data-ttu-id="b1bf3-111">作成する方法を示します`Font`と`FontFamily`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-111">Shows how to create `Font` and `FontFamily` objects.</span></span>  
  
 [<span data-ttu-id="b1bf3-112">方法: テキストを指定の位置に描画する</span><span class="sxs-lookup"><span data-stu-id="b1bf3-112">How to: Draw Text at a Specified Location</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)  
 <span data-ttu-id="b1bf3-113">特定の場所を使用して、テキストを描画する方法について説明[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]と[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-113">Describes how to draw text in a certain location using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="b1bf3-114">方法: 四角形内にテキストを折り返して描画する</span><span class="sxs-lookup"><span data-stu-id="b1bf3-114">How to: Draw Wrapped Text in a Rectangle</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)  
 <span data-ttu-id="b1bf3-115">使用して、四角形内のテキストを描画する方法について説明します[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]と[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-115">Explains how to draw text in a rectangle using [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 [<span data-ttu-id="b1bf3-116">方法: GDI を使用してテキストを描画する</span><span class="sxs-lookup"><span data-stu-id="b1bf3-116">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 <span data-ttu-id="b1bf3-117">使用する方法を示します[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]テキストを描画するためです。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-117">Demonstrates how to use [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] for drawing text.</span></span>  
  
 [<span data-ttu-id="b1bf3-118">方法: 描画テキストを配置する</span><span class="sxs-lookup"><span data-stu-id="b1bf3-118">How to: Align Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-align-drawn-text.md)  
 <span data-ttu-id="b1bf3-119">書式設定する方法を示しています。[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]と[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]テキスト。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-119">Shows how to format [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] text.</span></span>  
  
 [<span data-ttu-id="b1bf3-120">方法: 垂直方向のテキストを作成する</span><span class="sxs-lookup"><span data-stu-id="b1bf3-120">How to: Create Vertical Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-vertical-text.md)  
 <span data-ttu-id="b1bf3-121">垂直方向に配置されたテキストを描画する方法について説明[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-121">Describes how to draw vertically aligned text with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="b1bf3-122">方法: 描画されたテキストにタブ ストップを設定する</span><span class="sxs-lookup"><span data-stu-id="b1bf3-122">How to: Set Tab Stops in Drawn Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-tab-stops-in-drawn-text.md)  
 <span data-ttu-id="b1bf3-123">表示方法でタブ位置でテキストの描画[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-123">Shows how draw text with tab stops with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="b1bf3-124">方法: インストールされているフォントを列挙する</span><span class="sxs-lookup"><span data-stu-id="b1bf3-124">How to: Enumerate Installed Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-enumerate-installed-fonts.md)  
 <span data-ttu-id="b1bf3-125">インストールされているフォントの名前を一覧表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-125">Explains how to list the names of installed fonts.</span></span>  
  
 [<span data-ttu-id="b1bf3-126">方法: プライベート フォント コレクションを作成する</span><span class="sxs-lookup"><span data-stu-id="b1bf3-126">How to: Create a Private Font Collection</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-private-font-collection.md)  
 <span data-ttu-id="b1bf3-127">作成する方法について説明します、<xref:System.Drawing.Text.PrivateFontCollection>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-127">Describes how to create a <xref:System.Drawing.Text.PrivateFontCollection> object.</span></span>  
  
 [<span data-ttu-id="b1bf3-128">方法: フォント メトリックを取得する</span><span class="sxs-lookup"><span data-stu-id="b1bf3-128">How to: Obtain Font Metrics</span></span>](../../../../docs/framework/winforms/advanced/how-to-obtain-font-metrics.md)  
 <span data-ttu-id="b1bf3-129">セル アセント降下などのフォント メトリックを取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-129">Shows how to obtain font metrics such as cell ascent and descent.</span></span>  
  
 [<span data-ttu-id="b1bf3-130">方法: テキストでのアンチエイリアシングの使用</span><span class="sxs-lookup"><span data-stu-id="b1bf3-130">How to: Use Antialiasing with Text</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-antialiasing-with-text.md)  
 <span data-ttu-id="b1bf3-131">テキストを描画するときに、アンチ エイリアスを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-131">Explains how to use antialiasing when drawing text.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b1bf3-132">参照</span><span class="sxs-lookup"><span data-stu-id="b1bf3-132">Reference</span></span>  
 <xref:System.Drawing.Font>  
 <span data-ttu-id="b1bf3-133">このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-133">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.FontFamily>  
 <span data-ttu-id="b1bf3-134">このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-134">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 <span data-ttu-id="b1bf3-135">このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-135">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextRenderer>  
 <span data-ttu-id="b1bf3-136">このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-136">Describes this class and contains links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <span data-ttu-id="b1bf3-137">このクラスについて説明し、そのすべてのメンバーへのリンクが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b1bf3-137">Describes this class and contains links to all of its members.</span></span>
