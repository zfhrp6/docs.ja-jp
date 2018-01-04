---
title: "グラフィックス コンテナーの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 244f8e8a280369798daf12f8a61519826f937a4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-graphics-containers"></a><span data-ttu-id="54f1d-102">グラフィックス コンテナーの使用</span><span class="sxs-lookup"><span data-stu-id="54f1d-102">Using Graphics Containers</span></span>
<span data-ttu-id="54f1d-103">A<xref:System.Drawing.Graphics>オブジェクトなどのメソッドを提供<xref:System.Drawing.Graphics.DrawLine%2A>、 <xref:System.Drawing.Graphics.DrawImage%2A>、および<xref:System.Drawing.Graphics.DrawString%2A>ベクター イメージ、ラスター イメージおよびテキストを表示するためです。</span><span class="sxs-lookup"><span data-stu-id="54f1d-103">A <xref:System.Drawing.Graphics> object provides methods such as <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, and <xref:System.Drawing.Graphics.DrawString%2A> for displaying vector images, raster images, and text.</span></span> <span data-ttu-id="54f1d-104">A<xref:System.Drawing.Graphics>オブジェクトに品質と印刷の向きに描画される項目の影響を与えるいくつかのプロパティもあります。</span><span class="sxs-lookup"><span data-stu-id="54f1d-104">A <xref:System.Drawing.Graphics> object also has several properties that influence the quality and orientation of the items that are drawn.</span></span> <span data-ttu-id="54f1d-105">たとえば、スムージング モード プロパティは、直線と曲線にアンチエイリアシングを適用し、位置と回転に描画される項目のワールド変換プロパティに影響を与えますかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="54f1d-105">For example, the smoothing mode property determines whether antialiasing is applied to lines and curves, and the world transformation property influences the position and rotation of the items that are drawn.</span></span>  
  
 <span data-ttu-id="54f1d-106">A<xref:System.Drawing.Graphics>オブジェクトが特定のディスプレイ デバイスに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="54f1d-106">A <xref:System.Drawing.Graphics> object is associated with a particular display device.</span></span> <span data-ttu-id="54f1d-107">使用する場合、<xref:System.Drawing.Graphics>のウィンドウで描画するオブジェクト、<xref:System.Drawing.Graphics>オブジェクトは、その特定の期間に関連付けられてもいます。</span><span class="sxs-lookup"><span data-stu-id="54f1d-107">When you use a <xref:System.Drawing.Graphics> object to draw in a window, the <xref:System.Drawing.Graphics> object is also associated with that particular window.</span></span>  
  
 <span data-ttu-id="54f1d-108">A<xref:System.Drawing.Graphics>オブジェクトはコンテナーとして描画に影響を与えるプロパティのセットが格納されているためと、デバイスに固有の情報にリンクされています。</span><span class="sxs-lookup"><span data-stu-id="54f1d-108">A <xref:System.Drawing.Graphics> object can be thought of as a container because it holds a set of properties that influence drawing and it is linked to device-specific information.</span></span> <span data-ttu-id="54f1d-109">内で、既存のセカンダリのコンテナーを作成できます<xref:System.Drawing.Graphics>オブジェクトを呼び出して、<xref:System.Drawing.Graphics.BeginContainer%2A>そのメソッド<xref:System.Drawing.Graphics>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="54f1d-109">You can create a secondary container within an existing <xref:System.Drawing.Graphics> object by calling the <xref:System.Drawing.Graphics.BeginContainer%2A> method of that <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="54f1d-110">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="54f1d-110">In This Section</span></span>  
 [<span data-ttu-id="54f1d-111">Graphics オブジェクトの状態の管理</span><span class="sxs-lookup"><span data-stu-id="54f1d-111">Managing the State of a Graphics Object</span></span>](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 <span data-ttu-id="54f1d-112">について説明します、品質の設定、クリッピング領域との変換の管理方法、<xref:System.Drawing.Graphics>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="54f1d-112">Describes how manage the quality settings, clipping area and transformations of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [<span data-ttu-id="54f1d-113">入れ子になっているグラフィックス コンテナーの使用</span><span class="sxs-lookup"><span data-stu-id="54f1d-113">Using Nested Graphics Containers</span></span>](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 <span data-ttu-id="54f1d-114">コンテナーの状態の制御を使用する方法を示します、<xref:System.Drawing.Graphics>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="54f1d-114">Shows how to use containers to control the state of the <xref:System.Drawing.Graphics> object.</span></span>
