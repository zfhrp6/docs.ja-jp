---
title: "イベント ハンドラーの概要 (Windows フォーム)"
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
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7353f3ab4513d8331b1d38cb01ad16c7d3cde165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="12e38-102">イベント ハンドラーの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="12e38-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="12e38-103">イベント ハンドラーは、イベントにバインドされている方法です。</span><span class="sxs-lookup"><span data-stu-id="12e38-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="12e38-104">このイベントは、イベント ハンドラー内のコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="12e38-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="12e38-105">各イベント ハンドラーは、イベントを正しく処理することは 2 つのパラメーターを提供します。</span><span class="sxs-lookup"><span data-stu-id="12e38-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="12e38-106">次の例は、イベント ハンドラーを<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント。</span><span class="sxs-lookup"><span data-stu-id="12e38-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 <span data-ttu-id="12e38-107">最初のパラメーターでは、`sender`イベントを発生させたオブジェクトへの参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="12e38-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="12e38-108">2 番目のパラメーターでは、 `e`、上記の例では、オブジェクトを渡します特定イベントを処理していることにします。</span><span class="sxs-lookup"><span data-stu-id="12e38-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="12e38-109">オブジェクトのプロパティ (および場合によっては、そのメソッド) を参照する、マウス イベントやドラッグ アンド ドロップのイベントで転送されるデータのマウスの位置などの情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="12e38-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="12e38-110">通常の各イベントには、2 番目のパラメーターの異なるイベント オブジェクト型を持つイベント ハンドラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="12e38-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="12e38-111">場合など、いくつかのイベント ハンドラー、<xref:System.Windows.Forms.Control.MouseDown>と<xref:System.Windows.Forms.Control.MouseUp>イベントを同じ型であるオブジェクトが 2 番目のパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="12e38-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="12e38-112">この種のイベントでは、両方のイベントを処理するのに同じイベント ハンドラーを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="12e38-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="12e38-113">同じイベント ハンドラーを使用して、異なるコントロールに同じイベントを処理することができますも。</span><span class="sxs-lookup"><span data-stu-id="12e38-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="12e38-114">グループがある場合など、<xref:System.Windows.Forms.RadioButton>フォーム上のコントロールの 1 つのイベント ハンドラーを作成する可能性があります、<xref:System.Windows.Forms.Control.Click>イベントにある各コントロールの<xref:System.Windows.Forms.Control.Click>イベントが 1 つのイベント ハンドラーにバインドします。</span><span class="sxs-lookup"><span data-stu-id="12e38-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="12e38-115">詳細については、次を参照してください。[する方法: Windows フォームの 1 つのイベント ハンドラーの複数のイベントを接続](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)です。</span><span class="sxs-lookup"><span data-stu-id="12e38-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e38-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="12e38-116">See Also</span></span>  
 [<span data-ttu-id="12e38-117">Windows フォーム内でのイベント ハンドラーの作成</span><span class="sxs-lookup"><span data-stu-id="12e38-117">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="12e38-118">イベントの概要</span><span class="sxs-lookup"><span data-stu-id="12e38-118">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)
