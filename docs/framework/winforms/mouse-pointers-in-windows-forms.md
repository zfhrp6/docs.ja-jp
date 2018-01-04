---
title: "Windows フォームにおけるマウス ポインター"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pointers [Windows Forms], setting
- mouse pointers
- mouse cursors
- mouse pointers [Windows Forms], setting
- cursors [Windows Forms], setting
- mouse [Windows Forms], cursors
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aaca18bff265fafbb5bad26adfe2a8c490d85132
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="mouse-pointers-in-windows-forms"></a><span data-ttu-id="8fbb7-102">Windows フォームにおけるマウス ポインター</span><span class="sxs-lookup"><span data-stu-id="8fbb7-102">Mouse Pointers in Windows Forms</span></span>
<span data-ttu-id="8fbb7-103">マウス*ポインター*マウスを使用してユーザー入力を画面のフォーカス ポイントを指定するビットマップは、そのカーソルと呼ばします。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-103">The mouse *pointer*, which is sometimes referred to as the cursor, is a bitmap that specifies a focus point on the screen for user input with the mouse.</span></span> <span data-ttu-id="8fbb7-104">このトピックでは、Windows フォームにおけるマウス ポインターの概要を説明し、変更およびマウス ポインターを制御する方法をいくつかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-104">This topic provides an overview of the mouse pointer in Windows Forms and describes some of the ways to modify and control the mouse pointer.</span></span>  
  
## <a name="accessing-the-mouse-pointer"></a><span data-ttu-id="8fbb7-105">マウス ポインターへのアクセス</span><span class="sxs-lookup"><span data-stu-id="8fbb7-105">Accessing the Mouse Pointer</span></span>  
 <span data-ttu-id="8fbb7-106">マウス ポインターがによって表される、<xref:System.Windows.Forms.Cursor>クラス、および各<xref:System.Windows.Forms.Control>が、<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>そのコントロールのポインターを指定するプロパティです。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-106">The mouse pointer is represented by the <xref:System.Windows.Forms.Cursor> class, and each <xref:System.Windows.Forms.Control> has a <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> property that specifies the pointer for that control.</span></span> <span data-ttu-id="8fbb7-107"><xref:System.Windows.Forms.Cursor>クラスにはなど、ポインターを記述するプロパティが含まれています、<xref:System.Windows.Forms.Cursor.Position%2A>と<xref:System.Windows.Forms.Cursor.HotSpot%2A>プロパティ、およびメソッドなど、ポインターの外観を変更できる、 <xref:System.Windows.Forms.Cursor.Show%2A>、 <xref:System.Windows.Forms.Cursor.Hide%2A>、および<xref:System.Windows.Forms.Cursor.DrawStretched%2A>メソッド。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-107">The <xref:System.Windows.Forms.Cursor> class contains properties that describe the pointer, such as the <xref:System.Windows.Forms.Cursor.Position%2A> and <xref:System.Windows.Forms.Cursor.HotSpot%2A> properties, and methods that can modify the appearance of the pointer, such as the <xref:System.Windows.Forms.Cursor.Show%2A>, <xref:System.Windows.Forms.Cursor.Hide%2A>, and <xref:System.Windows.Forms.Cursor.DrawStretched%2A> methods.</span></span>  
  
## <a name="controlling-the-mouse-pointer"></a><span data-ttu-id="8fbb7-108">マウス ポインターを制御します。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-108">Controlling the Mouse Pointer</span></span>  
 <span data-ttu-id="8fbb7-109">マウス ポインターが使用できるまたはマウスの位置を変更する領域を制限する場合があります。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-109">Sometimes you may want to limit the area in which the mouse pointer can be used or change the position the mouse.</span></span> <span data-ttu-id="8fbb7-110">取得またはマウスを使用して、現在の場所を設定することができます、<xref:System.Windows.Forms.Cursor.Position%2A>のプロパティ、<xref:System.Windows.Forms.Cursor>です。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-110">You can get or set the current location of the mouse using the <xref:System.Windows.Forms.Cursor.Position%2A> property of the <xref:System.Windows.Forms.Cursor>.</span></span> <span data-ttu-id="8fbb7-111">マウス ポインターを使用できる領域を制限するさらに、設定は、<xref:System.Windows.Forms.Cursor.Clip%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-111">In addition, you can limit the area the mouse pointer can be used be setting the <xref:System.Windows.Forms.Cursor.Clip%2A> property.</span></span> <span data-ttu-id="8fbb7-112">クリップ領域で、既定では、画面全体です。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-112">The clip area, by default, is the entire screen.</span></span>  
  
## <a name="changing-the-mouse-pointer"></a><span data-ttu-id="8fbb7-113">マウス ポインターを変更します。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-113">Changing the Mouse Pointer</span></span>  
 <span data-ttu-id="8fbb7-114">マウス ポインターを変更するは、ユーザーにフィードバックを提供することの重要な方法です。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-114">Changing the mouse pointer is an important way of providing feedback to the user.</span></span> <span data-ttu-id="8fbb7-115">ハンドラーでマウス ポインターを変更するなど、<xref:System.Windows.Forms.Control.MouseEnter>と<xref:System.Windows.Forms.Control.MouseLeave>計算が行われていることをユーザーに伝えるためと、コントロール内のユーザーの操作を制限するイベントです。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-115">For example, the mouse pointer can be modified in the handlers of the <xref:System.Windows.Forms.Control.MouseEnter> and <xref:System.Windows.Forms.Control.MouseLeave> events to tell the user that computations are occurring and to limit user interaction in the control.</span></span> <span data-ttu-id="8fbb7-116">場合によっては、マウス ポインターがドラッグ アンド ドロップ操作で、アプリケーションが関係している場合など、システム イベントによって変更されます。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-116">Sometimes, the mouse pointer will change because of system events, such as when your application is involved in a drag-and-drop operation.</span></span>  
  
 <span data-ttu-id="8fbb7-117">マウス ポインターを変更する主な方法は、設定して、<xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType>または<xref:System.Windows.Forms.Control.DefaultCursor%2A>を新しいコントロールのプロパティの<xref:System.Windows.Forms.Cursor>します。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-117">The primary way to change the mouse pointer is by setting the <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=nameWithType> or <xref:System.Windows.Forms.Control.DefaultCursor%2A> property of a control to a new <xref:System.Windows.Forms.Cursor>.</span></span> <span data-ttu-id="8fbb7-118">マウス ポインターを変更する例のコード例を参照してください、<xref:System.Windows.Forms.Cursor>クラスです。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-118">For examples of changing the mouse pointer, see the code example in the <xref:System.Windows.Forms.Cursor> class.</span></span> <span data-ttu-id="8fbb7-119">さらに、<xref:System.Windows.Forms.Cursors>クラスのセットを公開する<xref:System.Windows.Forms.Cursor>ポインター、手の形のようなポインターなどのさまざまな種類のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-119">In addition, the <xref:System.Windows.Forms.Cursors> class exposes a set of <xref:System.Windows.Forms.Cursor> objects for many different types of pointers, such as a pointer that resembles a hand.</span></span> <span data-ttu-id="8fbb7-120">砂時計が、コントロールにマウス ポインターがあるたびに似ていますが、待機のポインターを表示するには、<xref:System.Windows.Forms.Control.UseWaitCursor%2A>のプロパティ、<xref:System.Windows.Forms.Control>クラスです。</span><span class="sxs-lookup"><span data-stu-id="8fbb7-120">To display the wait pointer, which resembles an hourglass, whenever the mouse pointer is on the control, use the <xref:System.Windows.Forms.Control.UseWaitCursor%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fbb7-121">参照</span><span class="sxs-lookup"><span data-stu-id="8fbb7-121">See Also</span></span>  
 <xref:System.Windows.Forms.Cursor>  
 [<span data-ttu-id="8fbb7-122">Windows フォーム アプリケーションにおけるマウス入力</span><span class="sxs-lookup"><span data-stu-id="8fbb7-122">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="8fbb7-123">Windows フォームにおけるドラッグ アンド ドロップ機能</span><span class="sxs-lookup"><span data-stu-id="8fbb7-123">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)
