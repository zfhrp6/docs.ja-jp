---
title: "Windows フォームの座標"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms coordinates
- screen coordinates
- client coordinates
- coordinates [Windows Forms], Windows Forms
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f4b42fd71dacb0071013067dc3c14add96c8aca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-coordinates"></a><span data-ttu-id="efa3b-102">Windows フォームの座標</span><span class="sxs-lookup"><span data-stu-id="efa3b-102">Windows Forms Coordinates</span></span>
<span data-ttu-id="efa3b-103">Windows フォームの座標システムは、デバイスの座標に基づいており、Windows フォームで描画するときに、メジャーの基本単位は、デバイス単位 (通常は、ピクセル)。</span><span class="sxs-lookup"><span data-stu-id="efa3b-103">The coordinate system for a Windows Form is based on device coordinates, and the basic unit of measure when drawing in Windows Forms is the device unit (typically, the pixel).</span></span> <span data-ttu-id="efa3b-104">画面上の点は増加権限、および y 座標が上から下に増加する x 座標を使用して、x 座標と y 座標ペアで説明します。</span><span class="sxs-lookup"><span data-stu-id="efa3b-104">Points on the screen are described by x- and y-coordinate pairs, with the x-coordinates increasing to the right and the y-coordinates increasing from top to bottom.</span></span> <span data-ttu-id="efa3b-105">画面の基準とした、元の場所は、画面、またはクライアント座標を指定するかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="efa3b-105">The location of the origin, relative to the screen, will vary depending on whether you are specifying screen or client coordinates.</span></span>  
  
## <a name="screen-coordinates"></a><span data-ttu-id="efa3b-106">画面座標</span><span class="sxs-lookup"><span data-stu-id="efa3b-106">Screen Coordinates</span></span>  
 <span data-ttu-id="efa3b-107">Windows フォーム アプリケーションでは、画面座標で画面上のウィンドウの位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="efa3b-107">A Windows Forms application specifies the position of a window on the screen in screen coordinates.</span></span> <span data-ttu-id="efa3b-108">画面座標、原点は、画面の左上隅です。</span><span class="sxs-lookup"><span data-stu-id="efa3b-108">For screen coordinates, the origin is the upper-left corner of the screen.</span></span> <span data-ttu-id="efa3b-109">フル ウィンドウの位置がによって定義された多くの場合、<xref:System.Drawing.Rectangle>ウィンドウの左と右下隅の四隅を定義する 2 つのポイントの画面座標を含む構造体。</span><span class="sxs-lookup"><span data-stu-id="efa3b-109">The full position of a window is often described by a <xref:System.Drawing.Rectangle> structure containing the screen coordinates of two points that define the upper-left and lower-right corners of the window.</span></span>  
  
## <a name="client-coordinates"></a><span data-ttu-id="efa3b-110">クライアント座標</span><span class="sxs-lookup"><span data-stu-id="efa3b-110">Client Coordinates</span></span>  
 <span data-ttu-id="efa3b-111">Windows フォーム アプリケーションでは、フォームまたはコントロールのクライアント座標を使用してポイントの位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="efa3b-111">A Windows Forms application specifies the position of points in a form or control using client coordinates.</span></span> <span data-ttu-id="efa3b-112">クライアント座標の原点は、コントロールまたはフォームのクライアント領域の左上隅です。</span><span class="sxs-lookup"><span data-stu-id="efa3b-112">The origin for client coordinates is the upper-left corner of the client area of the control or form.</span></span> <span data-ttu-id="efa3b-113">クライアント座標では、アプリケーションがフォームまたはフォームまたは画面上のコントロールの位置に関係なく、コントロールの描画中に一貫性のある座標値を使用できることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="efa3b-113">Client coordinates ensure that an application can use consistent coordinate values while drawing in a form or control, regardless of the position of the form or control on the screen.</span></span>  
  
 <span data-ttu-id="efa3b-114">クライアント領域の大きさについても説明によって、<xref:System.Drawing.Rectangle>領域のクライアント座標を格納する構造体。</span><span class="sxs-lookup"><span data-stu-id="efa3b-114">The dimensions of the client area are also described by a <xref:System.Drawing.Rectangle> structure that contains client coordinates for the area.</span></span> <span data-ttu-id="efa3b-115">すべてのケースで、右下隅の座標が除外されているときに、クライアント領域に四角形の左上隅の座標が含まれます。</span><span class="sxs-lookup"><span data-stu-id="efa3b-115">In all cases, the upper-left coordinate of the rectangle is included in the client area, while the lower-right coordinate is excluded.</span></span> <span data-ttu-id="efa3b-116">グラフィックス操作は、クライアント領域の右方向と下の端を含めないでください。</span><span class="sxs-lookup"><span data-stu-id="efa3b-116">Graphics operations do not include the right and lower edges of a client area.</span></span> <span data-ttu-id="efa3b-117">たとえば、<xref:System.Drawing.Graphics.FillRectangle%2A>メソッドは、指定した四角形の右方向と下の端にいっぱいになりますが、これらのエッジは含まれません。</span><span class="sxs-lookup"><span data-stu-id="efa3b-117">For example the <xref:System.Drawing.Graphics.FillRectangle%2A> method will fill up to the right and lower edge of the specified rectangle, but will not include these edges.</span></span>  
  
## <a name="mapping-from-one-type-of-coordinate-to-another"></a><span data-ttu-id="efa3b-118">座標の 1 つの型から別のマッピング</span><span class="sxs-lookup"><span data-stu-id="efa3b-118">Mapping From One Type of Coordinate to Another</span></span>  
 <span data-ttu-id="efa3b-119">場合によっては、画面座標からクライアント座標をマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="efa3b-119">Occasionally, you may need to map from screen coordinates to client coordinates.</span></span> <span data-ttu-id="efa3b-120">簡単にこれを行うを使用して、<xref:System.Windows.Forms.Control.PointToClient%2A>と<xref:System.Windows.Forms.Control.PointToScreen%2A>で使用できるメソッド、<xref:System.Windows.Forms.Control>クラスです。</span><span class="sxs-lookup"><span data-stu-id="efa3b-120">You can easily accomplish this by using the <xref:System.Windows.Forms.Control.PointToClient%2A> and <xref:System.Windows.Forms.Control.PointToScreen%2A> methods available in the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="efa3b-121">たとえば、<xref:System.Windows.Forms.Control.MousePosition%2A>プロパティの<xref:System.Windows.Forms.Control>画面座標で報告されるクライアント座標に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="efa3b-121">For example, the <xref:System.Windows.Forms.Control.MousePosition%2A> property of <xref:System.Windows.Forms.Control> is reported in screen coordinates, but you may want to convert these to client coordinates.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efa3b-122">参照</span><span class="sxs-lookup"><span data-stu-id="efa3b-122">See Also</span></span>  
 <xref:System.Windows.Forms.Control.PointToClient%2A>  
 <xref:System.Windows.Forms.Control.PointToScreen%2A>
