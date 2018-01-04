---
title: "Windows フォーム アプリケーションにおけるマウス入力"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Windows Forms, mouse input
ms.assetid: 743c2f3c-219e-4a52-b6b8-2657096a2da6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56b267222f8e22d9d411d744f67d93cde6ba17a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mouse-input-in-a-windows-forms-application"></a><span data-ttu-id="5f7a2-102">Windows フォーム アプリケーションにおけるマウス入力</span><span class="sxs-lookup"><span data-stu-id="5f7a2-102">Mouse Input in a Windows Forms Application</span></span>
<span data-ttu-id="5f7a2-103">Windows フォームには、さまざまなマウス イベントがあり、カスタマイズされたマウス カーソル、マウスのキャプチャ、ドラッグ アンド ドロップ動作もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5f7a2-103">Windows Forms includes a variety of mouse events and additional support for customized mouse cursors, mouse capture, and drag-and-drop behavior.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5f7a2-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5f7a2-104">In This Section</span></span>  
 [<span data-ttu-id="5f7a2-105">Windows フォームにおけるマウス入力のしくみ</span><span class="sxs-lookup"><span data-stu-id="5f7a2-105">How Mouse Input Works in Windows Forms</span></span>](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md)  
 <span data-ttu-id="5f7a2-106">マウス イベントについて説明し、マウスの現在の情報とシステム設定を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5f7a2-106">Provides information about the mouse events and how to get current information and system settings for the mouse.</span></span>  
  
 [<span data-ttu-id="5f7a2-107">Windows フォームにおけるマウス イベント</span><span class="sxs-lookup"><span data-stu-id="5f7a2-107">Mouse Events in Windows Forms</span></span>](../../../docs/framework/winforms/mouse-events-in-windows-forms.md)  
 <span data-ttu-id="5f7a2-108">マウス イベントが発生する順序と、特定のコントロール内でマウス イベントが発生するしくみについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5f7a2-108">Provides information about the order in which the mouse events occur and how the mouse events are raised within specific controls.</span></span>  
  
 [<span data-ttu-id="5f7a2-109">方法 : クリックとダブルクリックを識別する</span><span class="sxs-lookup"><span data-stu-id="5f7a2-109">How to: Distinguish Between Clicks and Double-Clicks</span></span>](../../../docs/framework/winforms/how-to-distinguish-between-clicks-and-double-clicks.md)  
 <span data-ttu-id="5f7a2-110">シングルクリックとダブルクリックを使用して、互換性のないアクションを開始する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f7a2-110">Demonstrates how to use single and double clicks to initiate incompatible actions.</span></span>  
  
 [<span data-ttu-id="5f7a2-111">Windows フォームにおけるマウス ポインター</span><span class="sxs-lookup"><span data-stu-id="5f7a2-111">Mouse Pointers in Windows Forms</span></span>](../../../docs/framework/winforms/mouse-pointers-in-windows-forms.md)  
 <span data-ttu-id="5f7a2-112">マウス カーソルを変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f7a2-112">Describes how to change the mouse cursor.</span></span>  
  
 [<span data-ttu-id="5f7a2-113">Windows フォームにおけるマウスのキャプチャ</span><span class="sxs-lookup"><span data-stu-id="5f7a2-113">Mouse Capture in Windows Forms</span></span>](../../../docs/framework/winforms/mouse-capture-in-windows-forms.md)  
 <span data-ttu-id="5f7a2-114">コントロールがマウスをキャプチャする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f7a2-114">Describes how a control can capture the mouse.</span></span>  
  
 [<span data-ttu-id="5f7a2-115">Windows フォームにおけるドラッグ アンド ドロップ機能</span><span class="sxs-lookup"><span data-stu-id="5f7a2-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="5f7a2-116">ドラッグ アンド ドロップ動作を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5f7a2-116">Describes how to implement drag-and-drop behavior.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5f7a2-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5f7a2-117">Related Sections</span></span>  
 [<span data-ttu-id="5f7a2-118">マウスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="5f7a2-118">Accessing the Mouse</span></span>](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md)  
 <span data-ttu-id="5f7a2-119">Visual Basic を使用したマウスへのアクセスに関するトピックの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="5f7a2-119">Lists topics for accessing the mouse using Visual Basic.</span></span>
