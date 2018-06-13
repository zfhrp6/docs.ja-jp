---
title: '方法 : ルーティング イベントのクラス処理を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
ms.openlocfilehash: 85c3491c9035d807b4c654659a8641121bb5709f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545364"
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a><span data-ttu-id="7ddde-102">方法 : ルーティング イベントのクラス処理を追加する</span><span class="sxs-lookup"><span data-stu-id="7ddde-102">How to: Add Class Handling for a Routed Event</span></span>
<span data-ttu-id="7ddde-103">クラス ハンドラーまたはルート内の特定のノード上のインスタンス ハンドラーによって、ルーティングされたイベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="7ddde-103">Routed events can be handled either by class handlers or instance handlers on any given node in the route.</span></span> <span data-ttu-id="7ddde-104">クラス ハンドラーは、最初に、呼び出され、インスタンス処理からイベントを抑制するか、基本クラスによって所有されているイベントに関するその他のイベント固有の動作を紹介するクラスの実装で使用できます。</span><span class="sxs-lookup"><span data-stu-id="7ddde-104">Class handlers are invoked first, and can be used by class implementations to suppress events from instance handling or introduce other event specific behaviors on events that are owned by base classes.</span></span> <span data-ttu-id="7ddde-105">この例では、クラス ハンドラーを実装するための 2 つの密接に関連する手法を示します。</span><span class="sxs-lookup"><span data-stu-id="7ddde-105">This example illustrates two closely related techniques for implementing class handlers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ddde-106">例</span><span class="sxs-lookup"><span data-stu-id="7ddde-106">Example</span></span>  
 <span data-ttu-id="7ddde-107">この例に基づくカスタム クラスを使用して、<xref:System.Windows.Controls.Canvas>パネルです。</span><span class="sxs-lookup"><span data-stu-id="7ddde-107">This example uses a custom class based on the <xref:System.Windows.Controls.Canvas> panel.</span></span> <span data-ttu-id="7ddde-108">アプリケーションの基本的な前提は、カスタムのクラスがインターセプトし、いずれかのマウスの左ボタンをクリックして、子要素のクラスやそれにインスタンス ハンドラーが呼び出される前に、その処理をマークすることを含め、子要素にビヘイビアーを導入することです。</span><span class="sxs-lookup"><span data-stu-id="7ddde-108">The basic premise of the application is that the custom class introduces behaviors on its child elements, including intercepting any left mouse button clicks and marking them handled, before the child element class or any instance handlers on it will be invoked.</span></span>  
  
 <span data-ttu-id="7ddde-109"><xref:System.Windows.UIElement>クラスをクラスに処理を有効にする仮想メソッドを公開する、<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>単にイベントをオーバーライドして、イベント。</span><span class="sxs-lookup"><span data-stu-id="7ddde-109">The <xref:System.Windows.UIElement> class exposes a virtual method that enables class handling on the <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> event, by simply overriding the event.</span></span> <span data-ttu-id="7ddde-110">これは、このような仮想メソッドがクラスの階層のどこかに利用可能な場合は、クラス処理を実装する最も簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="7ddde-110">This is the simplest way to implement class handling if such a virtual method is available somewhere in your class' hierarchy.</span></span> <span data-ttu-id="7ddde-111">次のコードは、 <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> "MyEditContainer"から派生する実装<xref:System.Windows.Controls.Canvas>です。</span><span class="sxs-lookup"><span data-stu-id="7ddde-111">The following code shows the <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementation in the "MyEditContainer" that is derived from <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="7ddde-112">実装では、イベント引数を処理済みとして示し、基本的な表示の変更を元の要素に与えるコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="7ddde-112">The implementation marks the event as handled in the arguments, and then adds some code to give the source element a basic visible change.</span></span>  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 <span data-ttu-id="7ddde-113">ユーティリティ メソッドを使用して直接クラス処理を追加できる場合はなく仮想基底クラスまたはその特定のメソッドの使用可能な、<xref:System.Windows.EventManager>クラス、<xref:System.Windows.EventManager.RegisterClassHandler%2A>です。</span><span class="sxs-lookup"><span data-stu-id="7ddde-113">If no virtual is available on base classes or for that particular method, class handling can be added directly using a utility method of the <xref:System.Windows.EventManager> class, <xref:System.Windows.EventManager.RegisterClassHandler%2A>.</span></span> <span data-ttu-id="7ddde-114">このメソッドは、クラス処理を追加しているクラスの静的な初期化内でのみ呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ddde-114">This method should only be called within the static initialization of classes that are adding class handling.</span></span> <span data-ttu-id="7ddde-115">この例の別のハンドラーを追加する<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>、ここでは、登録されているクラスは、カスタム クラスとします。</span><span class="sxs-lookup"><span data-stu-id="7ddde-115">This example adds another handler for <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , and in this case the registered class is the custom class.</span></span> <span data-ttu-id="7ddde-116">これに対し、仮想メソッドを使用する場合、登録されているクラスは、実際に、<xref:System.Windows.UIElement>基本クラスです。</span><span class="sxs-lookup"><span data-stu-id="7ddde-116">In contrast, when using the virtuals, the registered class is really the <xref:System.Windows.UIElement> base class.</span></span> <span data-ttu-id="7ddde-117">基底クラスとサブクラスのクラス処理を登録する場所の場合、サブクラス ハンドラーは、最初に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="7ddde-117">In cases where base classes and subclass each register class handling, the subclass handlers are invoked first.</span></span> <span data-ttu-id="7ddde-118">最初、このハンドラーは、メッセージ ボックスを表示すると、仮想メソッドのハンドラーで視覚的変更し、表示される、アプリケーションで動作になります。</span><span class="sxs-lookup"><span data-stu-id="7ddde-118">The behavior in an application would be that first this handler would show its message box and then the visual change in the virtual method's handler would be shown.</span></span>  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a><span data-ttu-id="7ddde-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ddde-119">See Also</span></span>  
 <xref:System.Windows.EventManager>  
 [<span data-ttu-id="7ddde-120">ルーティング イベントの処理済みとしてのマーキング、およびクラス処理</span><span class="sxs-lookup"><span data-stu-id="7ddde-120">Marking Routed Events as Handled, and Class Handling</span></span>](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [<span data-ttu-id="7ddde-121">ルーティング イベントを処理する</span><span class="sxs-lookup"><span data-stu-id="7ddde-121">Handle a Routed Event</span></span>](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)  
 [<span data-ttu-id="7ddde-122">ルーティング イベントの概要</span><span class="sxs-lookup"><span data-stu-id="7ddde-122">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
