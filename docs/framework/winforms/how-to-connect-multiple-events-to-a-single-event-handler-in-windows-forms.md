---
title: '方法 : Windows フォームの 1 つのイベント ハンドラーに複数のイベントを関連付ける'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: 527a76376a4c1d5ad051f4768ca2bd42c3548b3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538581"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a><span data-ttu-id="8a957-102">方法 : Windows フォームの 1 つのイベント ハンドラーに複数のイベントを関連付ける</span><span class="sxs-lookup"><span data-stu-id="8a957-102">How to: Connect Multiple Events to a Single Event Handler in Windows Forms</span></span>
<span data-ttu-id="8a957-103">アプリケーションの設計にする必要がありますを単一のイベント ハンドラーを使用して、複数のイベントまたは同じ手順を実行する複数のイベント。</span><span class="sxs-lookup"><span data-stu-id="8a957-103">In your application design, you may find it necessary to use a single event handler for multiple events or have multiple events perform the same procedure.</span></span> <span data-ttu-id="8a957-104">たとえば、時間を短縮するように、フォーム上のボタンは、同じ機能を公開している場合に、同じイベントを発生させるためのメニュー コマンドでは多くの場合です。</span><span class="sxs-lookup"><span data-stu-id="8a957-104">For example, it is often a powerful time-saver to have a menu command raise the same event as a button on your form does if they expose the same functionality.</span></span> <span data-ttu-id="8a957-105">C# の場合、[プロパティ] ウィンドウのイベント ビューを使用するかを使用してこれを行う、`Handles`キーワードおよび**クラス名**と**メソッド名**ドロップダウン ボックスでは、Visual Basic コード エディター。</span><span class="sxs-lookup"><span data-stu-id="8a957-105">You can do this by using the Events view of the Properties window in C# or using the `Handles` keyword and the **Class Name** and **Method Name** drop-down boxes in the Visual Basic Code Editor.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a><span data-ttu-id="8a957-106">Visual Basic での 1 つのイベント ハンドラーに複数のイベントを接続するには</span><span class="sxs-lookup"><span data-stu-id="8a957-106">To connect multiple events to a single event handler in Visual Basic</span></span>  
  
1.  <span data-ttu-id="8a957-107">フォームを右クリックして選択**コードの表示**です。</span><span class="sxs-lookup"><span data-stu-id="8a957-107">Right-click the form and choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="8a957-108">**クラス名**ドロップダウン ボックスで、イベント ハンドラーが処理するコントロールのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="8a957-108">From the **Class Name** drop-down box, select one of the controls that you want to have the event handler handle.</span></span>  
  
3.  <span data-ttu-id="8a957-109">**メソッド名**ドロップダウン ボックスで、イベント ハンドラーが処理するイベントのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="8a957-109">From the **Method Name** drop-down box, select one of the events that you want the event handler to handle.</span></span>  
  
4.  <span data-ttu-id="8a957-110">コード エディターでは、適切なイベント ハンドラーを挿入し、メソッド内でカーソルを配置します。</span><span class="sxs-lookup"><span data-stu-id="8a957-110">The Code Editor inserts the appropriate event handler and positions the insertion point within the method.</span></span> <span data-ttu-id="8a957-111">次の例では、<xref:System.Windows.Forms.Control.Click>イベントを<xref:System.Windows.Forms.Button>コントロール。</span><span class="sxs-lookup"><span data-stu-id="8a957-111">In the example below, it is the <xref:System.Windows.Forms.Control.Click> event for the <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  <span data-ttu-id="8a957-112">他のイベントが表示する処理を追加、`Handles`句。</span><span class="sxs-lookup"><span data-stu-id="8a957-112">Append the other events you would like handled to the `Handles` clause.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  <span data-ttu-id="8a957-113">イベント ハンドラーに適切なコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="8a957-113">Add the appropriate code to the event handler.</span></span>  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a><span data-ttu-id="8a957-114">C# での 1 つのイベント ハンドラーに複数のイベントを接続するには</span><span class="sxs-lookup"><span data-stu-id="8a957-114">To connect multiple events to a single event handler in C#</span></span>  
  
1.  <span data-ttu-id="8a957-115">イベント ハンドラーを接続するコントロールを選択します。</span><span class="sxs-lookup"><span data-stu-id="8a957-115">Select the control to which you want to connect an event handler.</span></span>  
  
2.  <span data-ttu-id="8a957-116">[プロパティ] ウィンドウ、**イベント**ボタン (![イベント ボタン](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow"))。</span><span class="sxs-lookup"><span data-stu-id="8a957-116">In the Properties window, click the **Events** button (![Events Button](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).</span></span>  
  
3.  <span data-ttu-id="8a957-117">処理するイベントの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a957-117">Click the name of the event that you want to handle.</span></span>  
  
4.  <span data-ttu-id="8a957-118">イベント名の横の [値] セクションでは、処理するイベントのメソッド シグネチャに一致する既存のイベント ハンドラーの一覧を表示するドロップダウン ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="8a957-118">In the value section next to the event name, click the drop-down button to display a list of existing event handlers that match the method signature of the event you want to handle.</span></span>  
  
5.  <span data-ttu-id="8a957-119">一覧から適切なイベント ハンドラーを選択します。</span><span class="sxs-lookup"><span data-stu-id="8a957-119">Select the appropriate event handler from the list.</span></span>  
  
     <span data-ttu-id="8a957-120">コードは、既存のイベント ハンドラーにイベントをバインドするフォームに追加されます。</span><span class="sxs-lookup"><span data-stu-id="8a957-120">Code will be added to the form to bind the event to the existing event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a957-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a957-121">See Also</span></span>  
 [<span data-ttu-id="8a957-122">Windows フォーム内でのイベント ハンドラーの作成</span><span class="sxs-lookup"><span data-stu-id="8a957-122">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="8a957-123">イベント ハンドラーの概要</span><span class="sxs-lookup"><span data-stu-id="8a957-123">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)
