---
title: "プロパティ変更イベント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7685891e99f1dcb2ca9e515c7dc6d7730ff0b2e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="property-changed-events"></a><span data-ttu-id="13943-102">プロパティ変更イベント</span><span class="sxs-lookup"><span data-stu-id="13943-102">Property-Changed Events</span></span>
<span data-ttu-id="13943-103">いう名前のプロパティの通知を送信する、制御したいかどうか*PropertyName*という名前のイベントを定義する、変更*PropertyName* `Changed`という名前のメソッドと`On` *PropertyName* `Changed`イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="13943-103">If you want your control to send notifications when a property named *PropertyName* changes, define an event named *PropertyName*`Changed` and a method named `On`*PropertyName*`Changed` that raises the event.</span></span> <span data-ttu-id="13943-104">Windows フォームの名前付け規則では、単語を追加*Changed*プロパティの名前にします。</span><span class="sxs-lookup"><span data-stu-id="13943-104">The naming convention in Windows Forms is to append the word *Changed* to the name of the property.</span></span> <span data-ttu-id="13943-105">プロパティ変更イベントに関連付けられているイベントのデリゲート型は<xref:System.EventHandler>、イベントのデータ型は、<xref:System.EventArgs>です。</span><span class="sxs-lookup"><span data-stu-id="13943-105">The associated event delegate type for property-changed events is <xref:System.EventHandler>, and the event data type is <xref:System.EventArgs>.</span></span> <span data-ttu-id="13943-106">基本クラス<xref:System.Windows.Forms.Control>など多数のプロパティ変更イベントを定義<xref:System.Windows.Forms.Control.BackColorChanged>、 <xref:System.Windows.Forms.Control.BackgroundImageChanged>、 <xref:System.Windows.Forms.Control.FontChanged>、 <xref:System.Windows.Forms.Control.LocationChanged>、およびその他。</span><span class="sxs-lookup"><span data-stu-id="13943-106">The base class <xref:System.Windows.Forms.Control> defines many property-changed events, such as <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>, and others.</span></span> <span data-ttu-id="13943-107">イベントに関する背景情報については、次を参照してください。[イベント](../../../../docs/standard/events/index.md)と[Windows フォーム コントロールのイベント](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)です。</span><span class="sxs-lookup"><span data-stu-id="13943-107">For background information about events, see [Events](../../../../docs/standard/events/index.md) and [Events in Windows Forms Controls](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).</span></span>  
  
 <span data-ttu-id="13943-108">プロパティ変更イベントは、コントロールの変更に応答するイベント ハンドラーをアタッチするコンシューマーが追加できるため便利です。</span><span class="sxs-lookup"><span data-stu-id="13943-108">Property-changed events are useful because they allow consumers of a control to attach event handlers that respond to the change.</span></span> <span data-ttu-id="13943-109">コントロールを生成するプロパティ変更イベントに応答する場合は、上書き、対応する`On` *PropertyName* `Changed`メソッド、イベントにデリゲートをアタッチする代わりにします。</span><span class="sxs-lookup"><span data-stu-id="13943-109">If your control needs to respond to a property-changed event that it raises, override the corresponding `On`*PropertyName*`Changed` method instead of attaching a delegate to the event.</span></span> <span data-ttu-id="13943-110">その他のプロパティを更新するかの描画サーフェイスの一部またはすべてを再描画して、コントロールは通常、プロパティ変更イベントに応答します。</span><span class="sxs-lookup"><span data-stu-id="13943-110">A control typically responds to a property-changed event by updating other properties or by redrawing some or all of its drawing surface.</span></span>  
  
 <span data-ttu-id="13943-111">例を次にどのように`FlashTrackBar`に対するいくつかのプロパティ変更イベントから継承するカスタム コントロールの応答<xref:System.Windows.Forms.Control>です。</span><span class="sxs-lookup"><span data-stu-id="13943-111">The following example shows how the `FlashTrackBar` custom control responds to some of the property-changed events that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="13943-112">サンプル全体については、次を参照してください。[する方法: Windows フォーム コントロールを示しています進行状況を作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)です。</span><span class="sxs-lookup"><span data-stu-id="13943-112">For the complete sample, see [How to: Create a Windows Forms Control That Shows Progress](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="13943-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="13943-113">See Also</span></span>  
 [<span data-ttu-id="13943-114">イベント</span><span class="sxs-lookup"><span data-stu-id="13943-114">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="13943-115">Windows フォーム コントロールのイベント</span><span class="sxs-lookup"><span data-stu-id="13943-115">Events in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [<span data-ttu-id="13943-116">Windows フォーム コントロールのプロパティ</span><span class="sxs-lookup"><span data-stu-id="13943-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
