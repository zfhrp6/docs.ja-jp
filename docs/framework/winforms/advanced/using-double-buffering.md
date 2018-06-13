---
title: ダブル バッファリングの使用
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: 9b09210eba0ac3a141219a7cdbff15f22c6ed003
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523911"
---
# <a name="using-double-buffering"></a><span data-ttu-id="99aec-102">ダブル バッファリングの使用</span><span class="sxs-lookup"><span data-stu-id="99aec-102">Using Double Buffering</span></span>
<span data-ttu-id="99aec-103">ダブル バッファリングされたグラフィックスを使用して、複雑な描画操作を必要とするアプリケーションでちらつきを軽減することができます。</span><span class="sxs-lookup"><span data-stu-id="99aec-103">You can use double-buffered graphics to reduce flicker in your applications that contain complex painting operations.</span></span> <span data-ttu-id="99aec-104">.NET Framework には、ダブル バッファリングの組み込みサポートが含まれています。 または、管理し、手動でグラフィックスをレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="99aec-104">The .NET Framework contains built-in support for double-buffering or you can manage and render graphics manually.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="99aec-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="99aec-105">In This Section</span></span>  
 [<span data-ttu-id="99aec-106">ダブル バッファリングされたグラフィックス</span><span class="sxs-lookup"><span data-stu-id="99aec-106">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 <span data-ttu-id="99aec-107">ダブル バッファリングの概念とアウトライン .NET Framework のサポートが導入されています。</span><span class="sxs-lookup"><span data-stu-id="99aec-107">Introduces double buffering concept and outlines .NET Framework support.</span></span>  
  
 [<span data-ttu-id="99aec-108">方法: フォームとコントロールのダブル バッファリングを行うことによってグラフィックスのちらつきを軽減する</span><span class="sxs-lookup"><span data-stu-id="99aec-108">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 <span data-ttu-id="99aec-109">ダブル バッファリングを .NET Framework のサポート、既定値を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="99aec-109">Demonstrates how to use the default double buffering support in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="99aec-110">方法: バッファリングされたグラフィックスを手動で管理する</span><span class="sxs-lookup"><span data-stu-id="99aec-110">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 <span data-ttu-id="99aec-111">アプリケーションのダブル バッファリングを管理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="99aec-111">Shows how to manage double buffering in applications.</span></span>  
  
 [<span data-ttu-id="99aec-112">方法: バッファリングされたグラフィックスを手動で描画する</span><span class="sxs-lookup"><span data-stu-id="99aec-112">How to: Manually Render Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 <span data-ttu-id="99aec-113">ダブル バッファリングされたグラフィックスをレンダリングする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="99aec-113">Demonstrates how to render double-buffered graphics.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="99aec-114">参照</span><span class="sxs-lookup"><span data-stu-id="99aec-114">Reference</span></span>  
 <span data-ttu-id="99aec-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span><span class="sxs-lookup"><span data-stu-id="99aec-115"><xref:System.Windows.Forms.Control.SetStyle%2A> ,</span></span>  
 <span data-ttu-id="99aec-116">ダブル バッファリングできるようにするメソッドを制御します。</span><span class="sxs-lookup"><span data-stu-id="99aec-116">Control method that enables double buffering.</span></span>  
  
 <span data-ttu-id="99aec-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span><span class="sxs-lookup"><span data-stu-id="99aec-117"><xref:System.Drawing.BufferedGraphicsContext> ,</span></span>  
 <span data-ttu-id="99aec-118">グラフィックス バッファーを作成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="99aec-118">Provides methods for creating graphics buffers.</span></span>  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 <span data-ttu-id="99aec-119">アプリケーション ドメインのバッファリングされたグラフィックス コンテキストへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="99aec-119">Provides access to the buffered graphics context for a application domain.</span></span>
