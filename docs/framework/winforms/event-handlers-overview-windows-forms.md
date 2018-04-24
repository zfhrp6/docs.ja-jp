---
title: イベント ハンドラーの概要 (Windows フォーム)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
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
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 44d79fb9d6ca2712c470354999b4795408044166
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="event-handlers-overview-windows-forms"></a><span data-ttu-id="2f1b6-102">イベント ハンドラーの概要 (Windows フォーム)</span><span class="sxs-lookup"><span data-stu-id="2f1b6-102">Event Handlers Overview (Windows Forms)</span></span>
<span data-ttu-id="2f1b6-103">イベント ハンドラーは、イベントにバインドされるメソッドです</span><span class="sxs-lookup"><span data-stu-id="2f1b6-103">An event handler is a method that is bound to an event.</span></span> <span data-ttu-id="2f1b6-104">イベントが発生したとき、そのイベント ハンドラー内のコードが実行されます</span><span class="sxs-lookup"><span data-stu-id="2f1b6-104">When the event is raised, the code within the event handler is executed.</span></span> <span data-ttu-id="2f1b6-105">各イベント ハンドラーは、イベントを正しく処理できるように 2 つのパラメーターを提供しています。</span><span class="sxs-lookup"><span data-stu-id="2f1b6-105">Each event handler provides two parameters that allow you to handle the event properly.</span></span> <span data-ttu-id="2f1b6-106">次の例では、<xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベントのイベント ハンドラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="2f1b6-106">The following example shows an event handler for a <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
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
  
 <span data-ttu-id="2f1b6-107">最初のパラメーター、`sender` はイベントを発生させたオブジェクトへの参照を提供します。</span><span class="sxs-lookup"><span data-stu-id="2f1b6-107">The first parameter,`sender`, provides a reference to the object that raised the event.</span></span> <span data-ttu-id="2f1b6-108">2 番目のパラメーター、 `e`は、上記の例では、処理されたイベントで特有のオブジェクトを渡しています。</span><span class="sxs-lookup"><span data-stu-id="2f1b6-108">The second parameter, `e`, in the example above, passes an object specific to the event that is being handled.</span></span> <span data-ttu-id="2f1b6-109">そのオブジェクトのプロパティ (また、ときには、そのメソッド) を参照することによって、マウス イベントにおけるマウスの位置や、あるいはドラッグ アンド ドロップのイベントで移動したデータのような情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="2f1b6-109">By referencing the object's properties (and, sometimes, its methods), you can obtain information such as the location of the mouse for mouse events or data being transferred in drag-and-drop events.</span></span>  
  
 <span data-ttu-id="2f1b6-110">多くのイベントは、2 番目のパラメーターに異なるイベント オブジェクト型を持つ イベント ハンドラーを有しています。</span><span class="sxs-lookup"><span data-stu-id="2f1b6-110">Typically each event produces an event handler with a different event-object type for the second parameter.</span></span> <span data-ttu-id="2f1b6-111"><xref:System.Windows.Forms.Control.MouseDown> や <xref:System.Windows.Forms.Control.MouseUp> のようないくつかのイベント ハンドラーは 2 番目のパラメーターに同じオブジェクト型を持ちます。</span><span class="sxs-lookup"><span data-stu-id="2f1b6-111">Some event handlers, such as those for the <xref:System.Windows.Forms.Control.MouseDown> and <xref:System.Windows.Forms.Control.MouseUp> events, have the same object type for their second parameter.</span></span> <span data-ttu-id="2f1b6-112">この種のイベントでは、両方のイベントを処理するために同じイベント ハンドラーを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="2f1b6-112">For these types of events, you can use the same event handler to handle both events.</span></span>  
  
 <span data-ttu-id="2f1b6-113">また、異なるコントロールの同じイベントを処理するために同じイベント ハンドラーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="2f1b6-113">You can also use the same event handler to handle the same event for different controls.</span></span> <span data-ttu-id="2f1b6-114">たとえば、フォーム上に <xref:System.Windows.Forms.RadioButton> のコントロールのグループがある場合、<xref:System.Windows.Forms.Control.Click> イベントのイベント ハンドラーを作成し、それぞれのコントロールの <xref:System.Windows.Forms.Control.Click> イベントをその 1 つのイベント ハンドラーにバインドさせることができます。</span><span class="sxs-lookup"><span data-stu-id="2f1b6-114">For example, if you have a group of <xref:System.Windows.Forms.RadioButton> controls on a form, you could create a single event handler for the <xref:System.Windows.Forms.Control.Click> event and have each control's <xref:System.Windows.Forms.Control.Click> event bound to the single event handler.</span></span> <span data-ttu-id="2f1b6-115">詳細については、[Windows フォームの 1 つのイベント ハンドラーに複数のイベントを接続する方法](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md) についての記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f1b6-115">For more information, see [How to: Connect Multiple Events to a Single Event Handler in Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f1b6-116">参照</span><span class="sxs-lookup"><span data-stu-id="2f1b6-116">See Also</span></span>  
 [<span data-ttu-id="2f1b6-117">Windows フォーム内でのイベント ハンドラーの作成</span><span class="sxs-lookup"><span data-stu-id="2f1b6-117">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="2f1b6-118">イベントの概要</span><span class="sxs-lookup"><span data-stu-id="2f1b6-118">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)
