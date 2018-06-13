---
title: Windows フォーム内でのイベント ハンドラーの作成
ms.date: 03/30/2017
helpviewer_keywords:
- event handling [Windows Forms]
- Windows Forms controls, event handling
- Windows Forms, event handling
- events [Windows Forms], event handlers
- event handlers [Windows Forms]
ms.assetid: 6514e530-c6b8-489c-a8d2-eda7b7072701
ms.openlocfilehash: 96697fa54b569b6d1ce092ebfc76ef593f2ac66f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539154"
---
# <a name="creating-event-handlers-in-windows-forms"></a><span data-ttu-id="6349a-102">Windows フォーム内でのイベント ハンドラーの作成</span><span class="sxs-lookup"><span data-stu-id="6349a-102">Creating Event Handlers in Windows Forms</span></span>
<span data-ttu-id="6349a-103">イベント ハンドラーは、ユーザーがボタンをクリックする、またはメッセージ キューがメッセージを受信するなどのイベントが発生したときに実行するアクションを決定する、コード内の手順です。</span><span class="sxs-lookup"><span data-stu-id="6349a-103">An event handler is a procedure in your code that determines what actions are performed when an event occurs, such as when the user clicks a button or a message queue receives a message.</span></span> <span data-ttu-id="6349a-104">イベントが発生すると、そのイベントを受信した一つまたは複数のイベント ハンドラーが実行されます。</span><span class="sxs-lookup"><span data-stu-id="6349a-104">When an event is raised, the event handler or handlers that receive the event are executed.</span></span> <span data-ttu-id="6349a-105">イベントは複数のハンドラーに割り当てられ、特定のイベントを処理するメソッドは動的に変更できます。</span><span class="sxs-lookup"><span data-stu-id="6349a-105">Events can be assigned to multiple handlers, and the methods that handle particular events can be changed dynamically.</span></span> <span data-ttu-id="6349a-106">イベント ハンドラーを作成するには、Windows フォーム デザイナーを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="6349a-106">You can also use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6349a-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6349a-107">In This Section</span></span>  
 [<span data-ttu-id="6349a-108">イベントの概要</span><span class="sxs-lookup"><span data-stu-id="6349a-108">Events Overview</span></span>](../../../docs/framework/winforms/events-overview-windows-forms.md)  
 <span data-ttu-id="6349a-109">イベント モデルおよびデリゲートの役割を説明します。</span><span class="sxs-lookup"><span data-stu-id="6349a-109">Explains the event model and the role of delegates.</span></span>  
  
 [<span data-ttu-id="6349a-110">イベント ハンドラーの概要</span><span class="sxs-lookup"><span data-stu-id="6349a-110">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 <span data-ttu-id="6349a-111">イベントを処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6349a-111">Describes how to handle events.</span></span>  
  
 [<span data-ttu-id="6349a-112">方法 : Windows フォームで実行時にイベント ハンドラーを作成する</span><span class="sxs-lookup"><span data-stu-id="6349a-112">How to: Create Event Handlers at Run Time for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md)  
 <span data-ttu-id="6349a-113">システム イベントおよびユーザー イベントへの動的な応答の手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="6349a-113">Gives directions for responding to system or user events dynamically.</span></span>  
  
 [<span data-ttu-id="6349a-114">方法 : Windows フォームの 1 つのイベント ハンドラーに複数のイベントを関連付ける</span><span class="sxs-lookup"><span data-stu-id="6349a-114">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)  
 <span data-ttu-id="6349a-115">イベントを通じて、複数のコントロールに同じ機能を割り当てる手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="6349a-115">Gives directions for assigning the same functionality to multiple controls through events.</span></span>  
  
 [<span data-ttu-id="6349a-116">Windows フォームのイベントの順序</span><span class="sxs-lookup"><span data-stu-id="6349a-116">Order of Events in Windows Forms</span></span>](../../../docs/framework/winforms/order-of-events-in-windows-forms.md)  
 <span data-ttu-id="6349a-117">Windows フォーム コントロールで発生するイベントの順序について説明します。</span><span class="sxs-lookup"><span data-stu-id="6349a-117">Describes the order in which events are raised in Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="6349a-118">方法 : デザイナーを使用してイベント ハンドラーを作成する</span><span class="sxs-lookup"><span data-stu-id="6349a-118">How to: Create Event Handlers Using the Designer</span></span>](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2)  
 <span data-ttu-id="6349a-119">Windows フォーム デザイナーを使用してイベント ハンドラーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6349a-119">Describes how to use the Windows Forms Designer to create event handlers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6349a-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="6349a-120">Related Sections</span></span>  
 [<span data-ttu-id="6349a-121">イベント</span><span class="sxs-lookup"><span data-stu-id="6349a-121">Events</span></span>](../../../docs/standard/events/index.md)  
 <span data-ttu-id="6349a-122">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] を使用したイベントの処理および発生に関するトピックへのリンクを提供します。</span><span class="sxs-lookup"><span data-stu-id="6349a-122">Provides links to topics on handling and raising events using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [<span data-ttu-id="6349a-123">Visual Basic での継承されたイベント ハンドラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6349a-123">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 <span data-ttu-id="6349a-124">継承されたコンポーネントでイベント ハンドラーに生じる一般的な問題を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="6349a-124">Lists common issues that occur with event handlers in inherited components.</span></span>
