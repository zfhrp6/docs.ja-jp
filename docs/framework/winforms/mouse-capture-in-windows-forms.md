---
title: Windows フォームにおけるマウスのキャプチャ
ms.date: 03/30/2017
helpviewer_keywords:
- mouse [Windows Forms], capture
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
ms.openlocfilehash: dfe983b9e407eddb9bed3bcc1a767cdeff38f2ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538409"
---
# <a name="mouse-capture-in-windows-forms"></a><span data-ttu-id="a5f41-102">Windows フォームにおけるマウスのキャプチャ</span><span class="sxs-lookup"><span data-stu-id="a5f41-102">Mouse Capture in Windows Forms</span></span>
<span data-ttu-id="a5f41-103">*マウスのキャプチャ*コントロールは、すべてのマウス入力のコマンドを実行する場合を参照します。</span><span class="sxs-lookup"><span data-stu-id="a5f41-103">*Mouse capture* refers to when a control takes command of all mouse input.</span></span> <span data-ttu-id="a5f41-104">コントロールがマウスをキャプチャしていた場合は、ポインターが境界内にあるかどうかを示す、マウス入力を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a5f41-104">When a control has captured the mouse, it receives mouse input whether or not the pointer is within its borders.</span></span>  
  
## <a name="setting-mouse-capture"></a><span data-ttu-id="a5f41-105">マウスのキャプチャの設定</span><span class="sxs-lookup"><span data-stu-id="a5f41-105">Setting Mouse Capture</span></span>  
 <span data-ttu-id="a5f41-106">Windows フォームでは、ユーザーがコントロールでマウス ボタンを押すし、ユーザーがマウス ボタンを離すと、マウスがコントロールによってリリースされたときに、マウスがコントロールによってキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="a5f41-106">In Windows Forms the mouse is captured by the control when the user presses a mouse button on a control, and the mouse is released by the control when the user releases the mouse button.</span></span>  
  
 <span data-ttu-id="a5f41-107"><xref:System.Windows.Forms.Control.Capture%2A>のプロパティ、<xref:System.Windows.Forms.Control>クラスは、コントロールがマウスをキャプチャしたかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a5f41-107">The <xref:System.Windows.Forms.Control.Capture%2A> property of the <xref:System.Windows.Forms.Control> class specifies whether a control has captured the mouse.</span></span> <span data-ttu-id="a5f41-108">調べるには、コントロールがマウス キャプチャを失ったときに、処理、<xref:System.Windows.Forms.Control.MouseCaptureChanged>イベント。</span><span class="sxs-lookup"><span data-stu-id="a5f41-108">To determine when a control loses mouse capture, handle the <xref:System.Windows.Forms.Control.MouseCaptureChanged> event.</span></span>  
  
 <span data-ttu-id="a5f41-109">前面のウィンドウのみでは、マウスをキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="a5f41-109">Only the foreground window can capture the mouse.</span></span> <span data-ttu-id="a5f41-110">バック グラウンド ウィンドウがマウスをキャプチャしようとすると、ウィンドウは、ウィンドウの表示部分内でマウス ポインターがあるときに発生するマウス イベントのメッセージだけを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a5f41-110">When a background window attempts to capture the mouse, the window receives messages only for mouse events that occur when the mouse pointer is within the visible portion of the window.</span></span> <span data-ttu-id="a5f41-111">また、場合でも、前面のウィンドウは、マウスをキャプチャして、ユーザーでもはクリックして別のウィンドウが前面に取り込みます。</span><span class="sxs-lookup"><span data-stu-id="a5f41-111">Also, even if the foreground window has captured the mouse, the user can still click another window, bringing it to the foreground.</span></span> <span data-ttu-id="a5f41-112">マウスがキャプチャされると、ショートカット キーは機能しません。</span><span class="sxs-lookup"><span data-stu-id="a5f41-112">When the mouse is captured, shortcut keys do not work.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5f41-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5f41-113">See Also</span></span>  
 [<span data-ttu-id="a5f41-114">Windows フォーム アプリケーションにおけるマウス入力</span><span class="sxs-lookup"><span data-stu-id="a5f41-114">Mouse Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
