---
title: "Windows フォームにおけるドラッグ アンド ドロップ機能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drag and drop [Windows Forms], Windows Forms
- Windows Forms, drag and drop
ms.assetid: 65cd2c03-8782-474e-b958-cbe43eeb902c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f86ff2fbb3944ce2ed381cb29e2b3c6df39b62bf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="drag-and-drop-functionality-in-windows-forms"></a><span data-ttu-id="d3b81-102">Windows フォームにおけるドラッグ アンド ドロップ機能</span><span class="sxs-lookup"><span data-stu-id="d3b81-102">Drag-and-Drop Functionality in Windows Forms</span></span>
<span data-ttu-id="d3b81-103">Windows フォームには、ドラッグ アンド ドロップの動作を実装する一連のメソッド、イベント、およびクラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d3b81-103">Windows Forms includes a set of methods, events, and classes that implement drag-and-drop behavior.</span></span> <span data-ttu-id="d3b81-104">このトピックでは、Windows フォームでのドラッグ アンド ドロップのサポートの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3b81-104">This topic provides an overview of the drag-and-drop support in Windows Forms.</span></span>  <span data-ttu-id="d3b81-105">参照してください[ドラッグ アンド ドロップ操作とクリップボードのサポート](http://msdn.microsoft.com/library/fe5ebfwe\(v=vs.110\))です。</span><span class="sxs-lookup"><span data-stu-id="d3b81-105">Also see [Drag-and-Drop Operations and Clipboard Support](http://msdn.microsoft.com/library/fe5ebfwe\(v=vs.110\)).</span></span>  
  
## <a name="performing-drag-and-drop-operations"></a><span data-ttu-id="d3b81-106">ドラッグ アンド ドロップ操作の実行</span><span class="sxs-lookup"><span data-stu-id="d3b81-106">Performing Drag-and-Drop Operations</span></span>  
 <span data-ttu-id="d3b81-107">ドラッグ アンド ドロップ操作を実行するには、<xref:System.Windows.Forms.Control> クラスの <xref:System.Windows.Forms.Control.DoDragDrop%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d3b81-107">To perform a drag-and-drop operation, use the <xref:System.Windows.Forms.Control.DoDragDrop%2A> method of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="d3b81-108">ドラッグ アンド ドロップ操作の実行方法の詳細については、「<xref:System.Windows.Forms.Control.DoDragDrop%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d3b81-108">For more information about how a drag-and-drop operation is performed, see <xref:System.Windows.Forms.Control.DoDragDrop%2A>.</span></span> <span data-ttu-id="d3b81-109">ドラッグ アンド ドロップ操作が開始される前に、マウス ポインターがドラッグされる四角形を取得するには、<xref:System.Windows.Forms.SystemInformation> クラスの <xref:System.Windows.Forms.SystemInformation.DragSize%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="d3b81-109">To get the rectangle that the mouse pointer must be dragged over before a drag-and-drop operation begins, use the <xref:System.Windows.Forms.SystemInformation.DragSize%2A> property of the <xref:System.Windows.Forms.SystemInformation> class.</span></span>  
  
## <a name="events-related-to-drag-and-drop-operations"></a><span data-ttu-id="d3b81-110">ドラッグ アンド ドロップ操作に関連するイベント</span><span class="sxs-lookup"><span data-stu-id="d3b81-110">Events Related to Drag-and-Drop Operations</span></span>  
 <span data-ttu-id="d3b81-111">ドラッグ アンド ドロップ操作のイベントには、ドラッグ アンド ドロップ操作の現在のターゲットで発生するイベントと、ドラッグ アンド ドロップ操作のソースで発生するイベントの 2 つのカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="d3b81-111">There are two categories of events in a drag and drop operation: events that occur on the current target of the drag-and-drop operation, and events that occur on the source of the drag and drop operation.</span></span>  
  
### <a name="events-on-the-current-target"></a><span data-ttu-id="d3b81-112">現在のターゲットでのイベント</span><span class="sxs-lookup"><span data-stu-id="d3b81-112">Events on the Current Target</span></span>  
 <span data-ttu-id="d3b81-113">次の表は、ドラッグ アンド ドロップ操作の現在のターゲットで発生するイベントを示します。</span><span class="sxs-lookup"><span data-stu-id="d3b81-113">The following table shows the events that occur on the current target of a drag-and-drop operation.</span></span>  
  
|<span data-ttu-id="d3b81-114">マウス イベント</span><span class="sxs-lookup"><span data-stu-id="d3b81-114">Mouse Event</span></span>|<span data-ttu-id="d3b81-115">説明</span><span class="sxs-lookup"><span data-stu-id="d3b81-115">Description</span></span>|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.DragEnter>|<span data-ttu-id="d3b81-116">このイベントは、オブジェクトがコントロールの境界内にドラッグされると発生します。</span><span class="sxs-lookup"><span data-stu-id="d3b81-116">This event occurs when an object is dragged into the control's bounds.</span></span> <span data-ttu-id="d3b81-117">このイベントのハンドラーは、型 <xref:System.Windows.Forms.DragEventArgs> の引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d3b81-117">The handler for this event receives an argument of type <xref:System.Windows.Forms.DragEventArgs>.</span></span>|  
|<xref:System.Windows.Forms.Control.DragOver>|<span data-ttu-id="d3b81-118">このイベントは、マウス ポインターがコントロールの境界内にある間にオブジェクトがドラッグされるときに発生します。</span><span class="sxs-lookup"><span data-stu-id="d3b81-118">This event occurs when an object is dragged while the mouse pointer is within the control's bounds.</span></span> <span data-ttu-id="d3b81-119">このイベントのハンドラーは、型 <xref:System.Windows.Forms.DragEventArgs> の引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d3b81-119">The handler for this event receives an argument of type <xref:System.Windows.Forms.DragEventArgs>.</span></span>|  
|<xref:System.Windows.Forms.Control.DragDrop>|<span data-ttu-id="d3b81-120">このイベントは、ドラッグ アンド ドロップ操作が完了したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="d3b81-120">This event occurs when a drag-and-drop operation is completed.</span></span> <span data-ttu-id="d3b81-121">このイベントのハンドラーは、型 <xref:System.Windows.Forms.DragEventArgs> の引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d3b81-121">The handler for this event receives an argument of type <xref:System.Windows.Forms.DragEventArgs>.</span></span>|  
|<xref:System.Windows.Forms.Control.DragLeave>|<span data-ttu-id="d3b81-122">このイベントは、オブジェクトがコントロールの境界外にドラッグされたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="d3b81-122">This event occurs when an object is dragged out of the control's bounds.</span></span> <span data-ttu-id="d3b81-123">このイベントのハンドラーは、型 <xref:System.EventArgs> の引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d3b81-123">The handler for this event receives an argument of type <xref:System.EventArgs>.</span></span>|  
  
 <span data-ttu-id="d3b81-124"><xref:System.Windows.Forms.DragEventArgs> クラスは、マウスのポインターの場所、マウス ボタンとキーボードの修飾子キーの現在の状態、ドラッグされているデータ、およびドラッグ イベントのソースによって許可される操作と操作に対するターゲットのドロップの効果を指定する <xref:System.Windows.Forms.DragDropEffects> の値を提供します。</span><span class="sxs-lookup"><span data-stu-id="d3b81-124">The <xref:System.Windows.Forms.DragEventArgs> class provides the location of the mouse pointer, the current state of the mouse buttons and modifier keys of the keyboard, the data being dragged, and <xref:System.Windows.Forms.DragDropEffects> values that specify the operations allowed by the source of the drag event and the target drop effect for the operation.</span></span>  
  
### <a name="events-on-the-source"></a><span data-ttu-id="d3b81-125">ソースのイベント</span><span class="sxs-lookup"><span data-stu-id="d3b81-125">Events on the Source</span></span>  
 <span data-ttu-id="d3b81-126">次の表は、ドラッグ アンド ドロップ操作のソースで発生するイベントを示します。</span><span class="sxs-lookup"><span data-stu-id="d3b81-126">The following table shows the events that occur on the source of the drag-and-drop operation.</span></span>  
  
|<span data-ttu-id="d3b81-127">マウス イベント</span><span class="sxs-lookup"><span data-stu-id="d3b81-127">Mouse Event</span></span>|<span data-ttu-id="d3b81-128">説明</span><span class="sxs-lookup"><span data-stu-id="d3b81-128">Description</span></span>|  
|-----------------|-----------------|  
|<xref:System.Windows.Forms.Control.GiveFeedback>|<span data-ttu-id="d3b81-129">このイベントは、ドラッグ操作中に発生します。</span><span class="sxs-lookup"><span data-stu-id="d3b81-129">This event occurs during a drag operation.</span></span> <span data-ttu-id="d3b81-130">マウス ポインターを変更するなど、ドラッグ アンド ドロップ操作が実行されていることを示す視覚上の手掛かりをユーザーに示す機会を提供します。</span><span class="sxs-lookup"><span data-stu-id="d3b81-130">It provides an opportunity to give a visual cue to the user that the drag-and-drop operation is occurring, such as changing the mouse pointer.</span></span> <span data-ttu-id="d3b81-131">このイベントのハンドラーは、型 <xref:System.Windows.Forms.GiveFeedbackEventArgs> の引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d3b81-131">The handler for this event receives an argument of type <xref:System.Windows.Forms.GiveFeedbackEventArgs>.</span></span>|  
|<xref:System.Windows.Forms.Control.QueryContinueDrag>|<span data-ttu-id="d3b81-132">このイベントは、ドラッグ アンド ドロップ操作中に発生し、ドラッグ ソースがドラッグ アンド ドロップ操作をキャンセルする必要があるかどうかを決定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d3b81-132">This event is raised during a drag-and-drop operation and enables the drag source to determine whether the drag-and-drop operation should be canceled.</span></span> <span data-ttu-id="d3b81-133">このイベントのハンドラーは、型 <xref:System.Windows.Forms.QueryContinueDragEventArgs> の引数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d3b81-133">The handler for this event receives an argument of type <xref:System.Windows.Forms.QueryContinueDragEventArgs>.</span></span>|  
  
 <span data-ttu-id="d3b81-134"><xref:System.Windows.Forms.QueryContinueDragEventArgs> クラスは、マウス ボタンとキーボードの修飾子キーの現在の状態、ESC キーを押したかどうかを指定する値、およびドラッグ アンド ドロップ操作を続行するかどうかを指定するために設定できる <xref:System.Windows.Forms.DragAction> の値を提供します。</span><span class="sxs-lookup"><span data-stu-id="d3b81-134">The <xref:System.Windows.Forms.QueryContinueDragEventArgs> class provides the current state of the mouse buttons and modifier keys of the keyboard, a value specifying whether the ESC key was pressed, and a <xref:System.Windows.Forms.DragAction> value that can be set to specify whether the drag-and-drop operation should continue.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b81-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3b81-135">See Also</span></span>  
 [<span data-ttu-id="d3b81-136">Windows フォーム アプリケーションにおけるマウス入力</span><span class="sxs-lookup"><span data-stu-id="d3b81-136">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
