---
title: "イベント (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 72563b9e37c26257a2bf5939f63ece050ec003ab
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/24/2018
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="b7a40-102">イベント (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b7a40-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="b7a40-103">[クラス](../../../csharp/language-reference/keywords/class.md) やオブジェクトは、何か重要なことが起こった場合に、イベントを使用して他のクラスまたはオブジェクトに通知を送ります。</span><span class="sxs-lookup"><span data-stu-id="b7a40-103">Events enable a [class](../../../csharp/language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="b7a40-104">イベントを送信する ( *発生させる*) クラスを *パブリッシャー* 、イベントを受信する ( *処理する*) クラスを *サブスクライバー*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="b7a40-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="b7a40-105">一般的な C# Windows フォームまたは Web アプリケーションでは、ボタンやリスト ボックスなどのコントロールによって発生したイベントを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="b7a40-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="b7a40-106">[!INCLUDE[csprcs](~/includes/csprcs-md.md)] 統合開発環境 (IDE) を使用して、コントロールによって発行されるイベントを参照し、処理するイベントを選択できます。</span><span class="sxs-lookup"><span data-stu-id="b7a40-106">You can use the [!INCLUDE[csprcs](~/includes/csprcs-md.md)] integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="b7a40-107">IDE は、空のイベント ハンドラー メソッドとイベントを定期受信するためのコードを自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="b7a40-107">The IDE automatically adds an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="b7a40-108">詳細については、「[方法: イベント サブスクリプションとサブスクリプションの解除](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7a40-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="b7a40-109">イベントの概要</span><span class="sxs-lookup"><span data-stu-id="b7a40-109">Events Overview</span></span>  
 <span data-ttu-id="b7a40-110">イベントには次のようなプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="b7a40-110">Events have the following properties:</span></span>  
  
-   <span data-ttu-id="b7a40-111">パブリッシャーがイベントが発生するタイミングを判断し、サブスクライバーがイベントに対応して実行するアクションを決定します。</span><span class="sxs-lookup"><span data-stu-id="b7a40-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
-   <span data-ttu-id="b7a40-112">イベントには複数のサブスクライバーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b7a40-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="b7a40-113">サブスクライバーは、複数のパブリッシャーからの複数のイベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="b7a40-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
-   <span data-ttu-id="b7a40-114">サブスクライバーがないイベントは発生しません。</span><span class="sxs-lookup"><span data-stu-id="b7a40-114">Events that have no subscribers are never raised.</span></span>  
  
-   <span data-ttu-id="b7a40-115">イベントは一般的に、グラフィカル ユーザー インターフェイスでのボタンのクリックやメニューの選択などのユーザーの操作を知らせるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b7a40-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
-   <span data-ttu-id="b7a40-116">イベントに複数のサブスクライバーがある場合は、イベントが発生したときに複数のイベント ハンドラーが同時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b7a40-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="b7a40-117">イベントを非同期に呼び出すには、「 [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7a40-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
-   <span data-ttu-id="b7a40-118">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] クラス ライブラリ以内で、イベントは、 <xref:System.EventHandler> デリゲートおよび <xref:System.EventArgs> 基底クラスを基にしています。</span><span class="sxs-lookup"><span data-stu-id="b7a40-118">In the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b7a40-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7a40-119">Related Sections</span></span>  
 <span data-ttu-id="b7a40-120">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="b7a40-120">For more information, see:</span></span>  
  
-   [<span data-ttu-id="b7a40-121">方法: イベント サブスクリプションとサブスクリプションの解除</span><span class="sxs-lookup"><span data-stu-id="b7a40-121">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [<span data-ttu-id="b7a40-122">方法: .NET Framework ガイドラインに準拠したイベントを発行する</span><span class="sxs-lookup"><span data-stu-id="b7a40-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [<span data-ttu-id="b7a40-123">方法: 派生クラスから基本クラス イベントを発生させる</span><span class="sxs-lookup"><span data-stu-id="b7a40-123">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [<span data-ttu-id="b7a40-124">方法: インターフェイス イベントを実装する</span><span class="sxs-lookup"><span data-stu-id="b7a40-124">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="b7a40-125">スレッドの同期</span><span class="sxs-lookup"><span data-stu-id="b7a40-125">Thread Synchronization</span></span>](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [<span data-ttu-id="b7a40-126">方法: ディクショナリを使用してイベント インスタンスを格納する</span><span class="sxs-lookup"><span data-stu-id="b7a40-126">How to: Use a Dictionary to Store Event Instances</span></span>](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [<span data-ttu-id="b7a40-127">方法: カスタム イベント アクセサーを実装する</span><span class="sxs-lookup"><span data-stu-id="b7a40-127">How to: Implement Custom Event Accessors</span></span>](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="b7a40-128">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="b7a40-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="b7a40-129">参考書籍の該当する章</span><span class="sxs-lookup"><span data-stu-id="b7a40-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="b7a40-130">『 [Delegates, Events, and Lambda Expressions (デリゲート、イベント、およびラムダ式) (C# 3.0 クックブック (第 3 版): C# 3.0 プログラマ向けの 250 以上のソリューション)](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) 』の「 [Delegates, Events, and Lambda Expressions (デリゲート、イベント、およびラムダ式)](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx) 」</span><span class="sxs-lookup"><span data-stu-id="b7a40-130">[Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span></span>  
  
 <span data-ttu-id="b7a40-131">「[Learn」の「g C# 3.0: Master the Fundamentals of C# 3.0 (C# 3.0 の学習: C# 3.0 の基礎を習得)](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) 」の「 [Learn」の「g C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)」</span><span class="sxs-lookup"><span data-stu-id="b7a40-131">[Delegates and Events](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7a40-132">参照</span><span class="sxs-lookup"><span data-stu-id="b7a40-132">See Also</span></span>  
 <xref:System.EventHandler>  
 [<span data-ttu-id="b7a40-133">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b7a40-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b7a40-134">デリゲート</span><span class="sxs-lookup"><span data-stu-id="b7a40-134">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="b7a40-135">Windows フォーム内でのイベント ハンドラーの作成</span><span class="sxs-lookup"><span data-stu-id="b7a40-135">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="b7a40-136">イベント ベースの非同期パターンを使用したマルチスレッド プログラミング</span><span class="sxs-lookup"><span data-stu-id="b7a40-136">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
