---
title: "ダブル バッファリングの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b5ad51e27c3d31ece1d11831c953023bedba3a97
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="using-double-buffering"></a><span data-ttu-id="1cff7-102">ダブル バッファリングの使用</span><span class="sxs-lookup"><span data-stu-id="1cff7-102">Using Double Buffering</span></span>
<span data-ttu-id="1cff7-103">ダブル バッファリングされたグラフィックスを使用して、複雑な描画操作を必要とするアプリケーションでちらつきを軽減することができます。</span><span class="sxs-lookup"><span data-stu-id="1cff7-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="1cff7-104">.NET Framework には、ダブル バッファリングの組み込みサポートが含まれています。 または、管理し、手動でグラフィックスをレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="1cff7-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1cff7-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1cff7-105">In This Section</span></span>  
 [<span data-ttu-id="1cff7-106">ダブル バッファリングされたグラフィックス</span><span class="sxs-lookup"><span data-stu-id="1cff7-106">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 <span data-ttu-id="1cff7-107">ダブル バッファリングの概念とアウトライン .NET Framework のサポートが導入されています。</span><span class="sxs-lookup"><span data-stu-id="1cff7-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="1cff7-108">方法: フォームとコントロールのダブル バッファリングを行うことによってグラフィックスのちらつきを軽減する</span><span class="sxs-lookup"><span data-stu-id="1cff7-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="1cff7-109">ダブル バッファリングを .NET Framework のサポート、既定値を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1cff7-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="1cff7-110">方法: バッファリングされたグラフィックスを手動で管理する</span><span class="sxs-lookup"><span data-stu-id="1cff7-110">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="1cff7-111">アプリケーションのダブル バッファリングを管理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1cff7-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="1cff7-112">方法: バッファリングされたグラフィックスを手動で描画する</span><span class="sxs-lookup"><span data-stu-id="1cff7-112">How to: Manually Render Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="1cff7-113">ダブル バッファリングされたグラフィックスをレンダリングする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1cff7-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1cff7-114">参照</span><span class="sxs-lookup"><span data-stu-id="1cff7-114">Reference</span></span>  
 <span data-ttu-id="1cff7-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span><span class="sxs-lookup"><span data-stu-id="1cff7-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span></span>  
 <span data-ttu-id="1cff7-116">ダブル バッファリングできるようにするメソッドを制御します。</span><span class="sxs-lookup"><span data-stu-id="1cff7-116">Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="1cff7-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span><span class="sxs-lookup"><span data-stu-id="1cff7-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span></span>  
 <span data-ttu-id="1cff7-118">グラフィックス バッファーを作成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="1cff7-118">Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="1cff7-119">アプリケーション ドメインのバッファリングされたグラフィックス コンテキストへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="1cff7-119">Provides access to the buffered graphics context for a application domain.</span></span>
