---
title: "Windows フォーム コントロールのイベント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [Windows Forms], custom controls (using code)
- custom controls [Windows Forms], events overview (using code)
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e568dd7fadea8af399a63aa95347f368b4e13a54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="events-in-windows-forms-controls"></a><span data-ttu-id="dd9bb-102">Windows フォーム コントロールのイベント</span><span class="sxs-lookup"><span data-stu-id="dd9bb-102">Events in Windows Forms Controls</span></span>
<span data-ttu-id="dd9bb-103">Windows フォーム コントロールから 60 以上のイベントを継承する<xref:System.Windows.Forms.Control?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="dd9bb-103">A Windows Forms control inherits more than sixty events from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dd9bb-104">ように、<xref:System.Windows.Forms.Control.Paint>イベントは、これにより、コントロールを描画するなど、ウィンドウの表示に関連するイベント、<xref:System.Windows.Forms.Control.Resize>と<xref:System.Windows.Forms.Control.Layout>イベント、および低レベルのマウスとキーボード イベント。</span><span class="sxs-lookup"><span data-stu-id="dd9bb-104">These include the <xref:System.Windows.Forms.Control.Paint> event, which causes a control to be drawn, events related to displaying a window, such as the <xref:System.Windows.Forms.Control.Resize> and <xref:System.Windows.Forms.Control.Layout> events, and low-level mouse and keyboard events.</span></span> <span data-ttu-id="dd9bb-105">一部の低レベルのイベントは、合成<xref:System.Windows.Forms.Control>ようセマンティックなイベントに<xref:System.Windows.Forms.Control.Click>と<xref:System.Windows.Forms.Control.DoubleClick>です。</span><span class="sxs-lookup"><span data-stu-id="dd9bb-105">Some low-level events are synthesized by <xref:System.Windows.Forms.Control> into semantic events such as <xref:System.Windows.Forms.Control.Click> and <xref:System.Windows.Forms.Control.DoubleClick>.</span></span> <span data-ttu-id="dd9bb-106">継承されたイベントに関する詳細については、「<xref:System.Windows.Forms.Control>です。</span><span class="sxs-lookup"><span data-stu-id="dd9bb-106">For details about inherited events, see <xref:System.Windows.Forms.Control>.</span></span>  
  
 <span data-ttu-id="dd9bb-107">継承されたイベントの機能をカスタム コントロールでオーバーライドする必要がある場合、デリゲートを結び付けるのではなく、継承された `On`*EventName* メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="dd9bb-107">If your custom control needs to override inherited event functionality, override the inherited `On`*EventName* method instead of attaching a delegate.</span></span> <span data-ttu-id="dd9bb-108">.NET Framework でのイベント モデルに詳しくない場合は、「[コンポーネントからのイベントの生成](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd9bb-108">If you are not familiar with the event model in the .NET Framework, see [Raising Events from a Component](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd9bb-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd9bb-109">See Also</span></span>  
 [<span data-ttu-id="dd9bb-110">OnPaint メソッドのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="dd9bb-110">Overriding the OnPaint Method</span></span>](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)  
 [<span data-ttu-id="dd9bb-111">ユーザーの入力の処理</span><span class="sxs-lookup"><span data-stu-id="dd9bb-111">Handling User Input</span></span>](../../../../docs/framework/winforms/controls/handling-user-input.md)  
 [<span data-ttu-id="dd9bb-112">イベントの定義</span><span class="sxs-lookup"><span data-stu-id="dd9bb-112">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [<span data-ttu-id="dd9bb-113">イベント</span><span class="sxs-lookup"><span data-stu-id="dd9bb-113">Events</span></span>](../../../../docs/standard/events/index.md)
