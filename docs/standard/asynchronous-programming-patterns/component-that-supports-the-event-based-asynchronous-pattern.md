---
title: "チュートリアル : イベントベースの非同期パターンをサポートするコンポーネントの実装"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 61f676b5-936f-40f6-83ce-f22805ec9c2f
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 150e4b27cc149774895574ddd196de5f9bc2acd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-a-component-that-supports-the-event-based-asynchronous-pattern"></a><span data-ttu-id="4738a-102">チュートリアル : イベントベースの非同期パターンをサポートするコンポーネントの実装</span><span class="sxs-lookup"><span data-stu-id="4738a-102">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="4738a-103">著しい遅延が発生する可能性がありますをいくつかの操作のクラスを作成している場合は、実装することによって、非同期機能を付けることを検討して、[イベント ベースの非同期パターン概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="4738a-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing the [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="4738a-104">このチュートリアルでは、イベント ベースの非同期パターンを実装するコンポーネントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4738a-104">This walkthrough illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="4738a-105">ヘルパー クラスを使用して実装されている、<xref:System.ComponentModel?displayProperty=nameWithType>コンポーネントが正しく動作する任意のアプリケーション モデルで実行できるようにするには、名前空間を含む[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]、コンソール アプリケーションと Windows フォーム アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="4738a-105">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model, including [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Console applications and Windows Forms applications.</span></span> <span data-ttu-id="4738a-106">また、このコンポーネントは、<xref:System.Windows.Forms.PropertyGrid>コントロールや、独自のカスタム デザイナーです。</span><span class="sxs-lookup"><span data-stu-id="4738a-106">This component is also designable with a <xref:System.Windows.Forms.PropertyGrid> control and your own custom designers.</span></span>  
  
 <span data-ttu-id="4738a-107">ときに非同期的に含まれる素数を計算するアプリケーションがあります。</span><span class="sxs-lookup"><span data-stu-id="4738a-107">When you are through, you will have an application that computes prime numbers asynchronously.</span></span> <span data-ttu-id="4738a-108">アプリケーションは、主要なユーザー インターフェイス (UI) スレッドと各素数計算のためのスレッドがあります。</span><span class="sxs-lookup"><span data-stu-id="4738a-108">Your application will have a main user interface (UI) thread and a thread for each prime number calculation.</span></span> <span data-ttu-id="4738a-109">多数あるかどうかをテスト素数かなりの時間がかかることができます、この遅延によって、メイン UI スレッドは中断されませんやフォームが応答性の高い計算中にします。</span><span class="sxs-lookup"><span data-stu-id="4738a-109">Although testing whether a large number is prime can take a noticeable amount of time, the main UI thread will not be interrupted by this delay, and the form will be responsive during the calculations.</span></span> <span data-ttu-id="4738a-110">多数の計算は自由に同時に、選択的に取り消しと保留中の計算を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="4738a-110">You will be able to run as many calculations as you like concurrently and selectively cancel pending calculations.</span></span>  
  
 <span data-ttu-id="4738a-111">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="4738a-111">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="4738a-112">コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="4738a-112">Creating the Component</span></span>  
  
-   <span data-ttu-id="4738a-113">パブリックの非同期イベントおよびデリゲートを定義します。</span><span class="sxs-lookup"><span data-stu-id="4738a-113">Defining Public Asynchronous Events and Delegates</span></span>  
  
-   <span data-ttu-id="4738a-114">プライベート デリゲートの定義</span><span class="sxs-lookup"><span data-stu-id="4738a-114">Defining Private Delegates</span></span>  
  
-   <span data-ttu-id="4738a-115">パブリック イベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="4738a-115">Implementing Public Events</span></span>  
  
-   <span data-ttu-id="4738a-116">完了メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="4738a-116">Implementing the Completion Method</span></span>  
  
-   <span data-ttu-id="4738a-117">ワーカー メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="4738a-117">Implementing the Worker Methods</span></span>  
  
-   <span data-ttu-id="4738a-118">開始とキャンセル メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="4738a-118">Implementing Start and Cancel Methods</span></span>  
  
 <span data-ttu-id="4738a-119">このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: イベント ベースの非同期パターンをサポートするコンポーネントを実装する](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)です。</span><span class="sxs-lookup"><span data-stu-id="4738a-119">To copy the code in this topic as a single listing, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="creating-the-component"></a><span data-ttu-id="4738a-120">コンポーネントの作成</span><span class="sxs-lookup"><span data-stu-id="4738a-120">Creating the Component</span></span>  
 <span data-ttu-id="4738a-121">最初の手順では、イベント ベースの非同期パターンを実装するコンポーネントを作成します。</span><span class="sxs-lookup"><span data-stu-id="4738a-121">The first step is to create the component that will implement the Event-based Asynchronous Pattern.</span></span>  
  
#### <a name="to-create-the-component"></a><span data-ttu-id="4738a-122">コンポーネントを作成するには</span><span class="sxs-lookup"><span data-stu-id="4738a-122">To create the component</span></span>  
  
-   <span data-ttu-id="4738a-123">呼ばれるクラスを作成する`PrimeNumberCalculator`から継承する<xref:System.ComponentModel.Component>です。</span><span class="sxs-lookup"><span data-stu-id="4738a-123">Create a class called `PrimeNumberCalculator` that inherits from <xref:System.ComponentModel.Component>.</span></span>  
  
## <a name="defining-public-asynchronous-events-and-delegates"></a><span data-ttu-id="4738a-124">パブリックの非同期イベントおよびデリゲートを定義します。</span><span class="sxs-lookup"><span data-stu-id="4738a-124">Defining Public Asynchronous Events and Delegates</span></span>  
 <span data-ttu-id="4738a-125">コンポーネントは、イベントを使用するクライアントと通信します。</span><span class="sxs-lookup"><span data-stu-id="4738a-125">Your component communicates to clients using events.</span></span> <span data-ttu-id="4738a-126">*MethodName* `Completed` 、非同期タスクの完了をクライアントに警告イベント、および*MethodName* `ProgressChanged`イベントは、非同期タスクの進行状況のクライアントに通知します。</span><span class="sxs-lookup"><span data-stu-id="4738a-126">The *MethodName*`Completed` event alerts clients to the completion of an asynchronous task, and the *MethodName*`ProgressChanged` event informs clients of the progress of an asynchronous task.</span></span>  
  
#### <a name="to-define-asynchronous-events-for-clients-of-your-component"></a><span data-ttu-id="4738a-127">コンポーネントのクライアントの非同期イベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="4738a-127">To define asynchronous events for clients of your component:</span></span>  
  
1.  <span data-ttu-id="4738a-128">インポート、<xref:System.Threading?displayProperty=nameWithType>と<xref:System.Collections.Specialized?displayProperty=nameWithType>ファイルの上部にある名前空間。</span><span class="sxs-lookup"><span data-stu-id="4738a-128">Import the <xref:System.Threading?displayProperty=nameWithType> and <xref:System.Collections.Specialized?displayProperty=nameWithType> namespaces at the top of your file.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#11)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#11](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#11)]  
  
2.  <span data-ttu-id="4738a-129">前に、`PrimeNumberCalculator`クラス定義、進行状況と完了イベントのデリゲートを宣言します。</span><span class="sxs-lookup"><span data-stu-id="4738a-129">Before the `PrimeNumberCalculator` class definition, declare delegates for progress and completion events.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#7)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#7)]  
  
3.  <span data-ttu-id="4738a-130">`PrimeNumberCalculator`クラス定義、レポートの進行状況および完了をクライアントのイベントを宣言します。</span><span class="sxs-lookup"><span data-stu-id="4738a-130">In the `PrimeNumberCalculator` class definition, declare events for reporting progress and completion to clients.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#8)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#8](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#8)]  
  
4.  <span data-ttu-id="4738a-131">後に、`PrimeNumberCalculator`クラス定義、派生、`CalculatePrimeCompletedEventArgs`のクライアントのイベント ハンドラーをそれぞれの計算の結果を報告のクラス、 `CalculatePrimeCompleted`.event です。</span><span class="sxs-lookup"><span data-stu-id="4738a-131">After the `PrimeNumberCalculator` class definition, derive the `CalculatePrimeCompletedEventArgs` class for reporting the outcome of each calculation to the client's event handler for the `CalculatePrimeCompleted`.event.</span></span> <span data-ttu-id="4738a-132">加え、`AsyncCompletedEventArgs`プロパティ、このクラスにより、クライアントは、どの番号がテストされているの主要なであるか、および最初の除数は素がないかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="4738a-132">In addition to the `AsyncCompletedEventArgs` properties, this class enables the client to determine what number was tested, whether it is prime, and what the first divisor is if it is not prime.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#6)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#6)]  
  
## <a name="checkpoint"></a><span data-ttu-id="4738a-133">チェックポイント</span><span class="sxs-lookup"><span data-stu-id="4738a-133">Checkpoint</span></span>  
 <span data-ttu-id="4738a-134">この時点では、コンポーネントをビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="4738a-134">At this point, you can build the component.</span></span>  
  
#### <a name="to-test-your-component"></a><span data-ttu-id="4738a-135">コンポーネントをテストするには</span><span class="sxs-lookup"><span data-stu-id="4738a-135">To test your component</span></span>  
  
-   <span data-ttu-id="4738a-136">コンポーネントをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="4738a-136">Compile the component.</span></span>  
  
     <span data-ttu-id="4738a-137">2 つのコンパイラ警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4738a-137">You will receive two compiler warnings:</span></span>  
  
    ```  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.ProgressChanged' is never used  
    warning CS0067: The event 'AsynchronousPatternExample.PrimeNumberCalculator.CalculatePrimeCompleted' is never used  
    ```  
  
     <span data-ttu-id="4738a-138">次のセクションでは、これらの警告が消去されます。</span><span class="sxs-lookup"><span data-stu-id="4738a-138">These warnings will be cleared in the next section.</span></span>  
  
## <a name="defining-private-delegates"></a><span data-ttu-id="4738a-139">プライベート デリゲートの定義</span><span class="sxs-lookup"><span data-stu-id="4738a-139">Defining Private Delegates</span></span>  
 <span data-ttu-id="4738a-140">非同期の側面、`PrimeNumberCalculator`と呼ばれる特別なデリゲートを使用してコンポーネントを内部的に実装されます、<xref:System.Threading.SendOrPostCallback>です。</span><span class="sxs-lookup"><span data-stu-id="4738a-140">The asynchronous aspects of the `PrimeNumberCalculator` component are implemented internally with a special delegate known as a <xref:System.Threading.SendOrPostCallback>.</span></span> <span data-ttu-id="4738a-141">A<xref:System.Threading.SendOrPostCallback>で実行されるコールバック メソッドを表す、<xref:System.Threading.ThreadPool>スレッドです。</span><span class="sxs-lookup"><span data-stu-id="4738a-141">A <xref:System.Threading.SendOrPostCallback> represents a callback method that executes on a <xref:System.Threading.ThreadPool> thread.</span></span> <span data-ttu-id="4738a-142">コールバック メソッドには、型の 1 つのパラメーターを受け取る署名が必要<xref:System.Object>、することができるはラッパー クラスでデリゲートの間で状態を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4738a-142">The callback method must have a signature that takes a single parameter of type <xref:System.Object>, which means you will need to pass state among delegates in a wrapper class.</span></span> <span data-ttu-id="4738a-143">詳細については、「<xref:System.Threading.SendOrPostCallback>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4738a-143">For more information, see <xref:System.Threading.SendOrPostCallback>.</span></span>  
  
#### <a name="to-implement-your-components-internal-asynchronous-behavior"></a><span data-ttu-id="4738a-144">コンポーネントの内部の非同期動作を実装するには。</span><span class="sxs-lookup"><span data-stu-id="4738a-144">To implement your component's internal asynchronous behavior:</span></span>  
  
1.  <span data-ttu-id="4738a-145">宣言し、作成、<xref:System.Threading.SendOrPostCallback>でデリゲート、`PrimeNumberCalculator`クラスです。</span><span class="sxs-lookup"><span data-stu-id="4738a-145">Declare and create the <xref:System.Threading.SendOrPostCallback> delegates in the `PrimeNumberCalculator` class.</span></span> <span data-ttu-id="4738a-146">作成、<xref:System.Threading.SendOrPostCallback>ユーティリティ メソッド内のオブジェクトと呼ばれる`InitializeDelegates`です。</span><span class="sxs-lookup"><span data-stu-id="4738a-146">Create the <xref:System.Threading.SendOrPostCallback> objects in a utility method called `InitializeDelegates`.</span></span>  
  
     <span data-ttu-id="4738a-147">2 つのデリゲートが必要になります。 クライアントに進行状況をレポート用とクライアントの完了を報告します。</span><span class="sxs-lookup"><span data-stu-id="4738a-147">You will need two delegates: one for reporting progress to the client, and one for reporting completion to the client.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#9)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#9](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#9)]  
    [!code-csharp[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#20)]
    [!code-vb[System.ComponentModel.AsyncOperationManager#20](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#20)]  
  
2.  <span data-ttu-id="4738a-148">呼び出す、`InitializeDelegates`コンポーネントのコンス トラクターのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="4738a-148">Call the `InitializeDelegates` method in your component's constructor.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#21)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#21](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#21)]  
  
3.  <span data-ttu-id="4738a-149">デリゲートを宣言、`PrimeNumberCalculator`を非同期的に実行する実際の作業を処理するクラス。</span><span class="sxs-lookup"><span data-stu-id="4738a-149">Declare a delegate in the `PrimeNumberCalculator` class that handles the actual work to be done asynchronously.</span></span> <span data-ttu-id="4738a-150">このデリゲートは、数値が素数かどうかをテストするワーカー メソッドをラップします。</span><span class="sxs-lookup"><span data-stu-id="4738a-150">This delegate wraps the worker method that tests whether a number is prime.</span></span> <span data-ttu-id="4738a-151">デリゲートは、<xref:System.ComponentModel.AsyncOperation>非同期操作の有効期間を追跡するために使用されるパラメーター。</span><span class="sxs-lookup"><span data-stu-id="4738a-151">The delegate takes an <xref:System.ComponentModel.AsyncOperation> parameter, which will be used to track the lifetime of the asynchronous operation.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#22)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#22](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#22)]  
  
4.  <span data-ttu-id="4738a-152">保留中の非同期操作の有効期間を管理するためのコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="4738a-152">Create a collection for managing lifetimes of pending asynchronous operations.</span></span> <span data-ttu-id="4738a-153">クライアントでは、この追跡を行うクライアントが非同期メソッドの呼び出しを作成するときに、一意のトークン、またはタスク ID を渡すクライアントを必要として、実行、完了すると、操作を追跡する方法が必要です。</span><span class="sxs-lookup"><span data-stu-id="4738a-153">The client needs a way to track operations as they are executed and completed, and this tracking is done by requiring the client to pass a unique token, or task ID, when the client makes the call to the asynchronous method.</span></span> <span data-ttu-id="4738a-154">`PrimeNumberCalculator`コンポーネント必要がありますの追跡の各呼び出しの対応する呼び出しと、タスク ID を関連付けることによってです。</span><span class="sxs-lookup"><span data-stu-id="4738a-154">The `PrimeNumberCalculator` component must keep track of each call by associating the task ID with its corresponding invocation.</span></span> <span data-ttu-id="4738a-155">クライアントがタスク ID が一意でないことに渡す場合、`PrimeNumberCalculator`コンポーネントが例外を発生させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4738a-155">If the client passes a task ID that is not unique, the `PrimeNumberCalculator` component must raise an exception.</span></span>  
  
     <span data-ttu-id="4738a-156">`PrimeNumberCalculator`コンポーネントの追跡タスク ID と呼ばれる特別なコレクション クラスを使用して、<xref:System.Collections.Specialized.HybridDictionary>です。</span><span class="sxs-lookup"><span data-stu-id="4738a-156">The `PrimeNumberCalculator` component keeps track of task ID by using a special collection class called a <xref:System.Collections.Specialized.HybridDictionary>.</span></span> <span data-ttu-id="4738a-157">クラス定義の作成、<xref:System.Collections.Specialized.HybridDictionary>と呼ばれる`userTokenToLifetime`です。</span><span class="sxs-lookup"><span data-stu-id="4738a-157">In the class definition, create a <xref:System.Collections.Specialized.HybridDictionary> called `userTokenToLifetime`.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#23)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#23](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#23)]  
  
## <a name="implementing-public-events"></a><span data-ttu-id="4738a-158">パブリック イベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="4738a-158">Implementing Public Events</span></span>  
 <span data-ttu-id="4738a-159">イベント ベースの非同期パターンを実装するコンポーネントは、イベントを使用してクライアントに通信します。</span><span class="sxs-lookup"><span data-stu-id="4738a-159">Components that implement the Event-based Asynchronous Pattern communicate to clients using events.</span></span> <span data-ttu-id="4738a-160">これらのイベントが利用して適切なスレッドで呼び出される、<xref:System.ComponentModel.AsyncOperation>クラスです。</span><span class="sxs-lookup"><span data-stu-id="4738a-160">These events are invoked on the proper thread with the help of the <xref:System.ComponentModel.AsyncOperation> class.</span></span>  
  
#### <a name="to-raise-events-to-your-components-clients"></a><span data-ttu-id="4738a-161">イベントを発生させるコンポーネントのクライアント。</span><span class="sxs-lookup"><span data-stu-id="4738a-161">To raise events to your component's clients:</span></span>  
  
1.  <span data-ttu-id="4738a-162">クライアントへの報告のパブリック イベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="4738a-162">Implement public events for reporting to clients.</span></span> <span data-ttu-id="4738a-163">イベントは、進行状況と完了をレポートに 1 つのレポートの必要があります。</span><span class="sxs-lookup"><span data-stu-id="4738a-163">You will need an event for reporting progress and one for reporting completion.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#24)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#24](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#24)]  
  
## <a name="implementing-the-completion-method"></a><span data-ttu-id="4738a-164">完了メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="4738a-164">Implementing the Completion Method</span></span>  
 <span data-ttu-id="4738a-165">完了デリゲートは、非同期操作が正常に完了、エラー、またはキャンセルして終了時に、基になる、フリー スレッドの非同期動作で起動される方法です。</span><span class="sxs-lookup"><span data-stu-id="4738a-165">The completion delegate is the method that the underlying, free-threaded asynchronous behavior will invoke when the asynchronous operation ends by successful completion, error, or cancellation.</span></span> <span data-ttu-id="4738a-166">この呼び出しは、任意のスレッドで発生します。</span><span class="sxs-lookup"><span data-stu-id="4738a-166">This invocation happens on an arbitrary thread.</span></span>  
  
 <span data-ttu-id="4738a-167">このメソッドは、クライアントのタスクの ID が一意のクライアントのトークンの内部コレクションから削除する場所です。</span><span class="sxs-lookup"><span data-stu-id="4738a-167">This method is where the client's task ID is removed from the internal collection of unique client tokens.</span></span> <span data-ttu-id="4738a-168">また、このメソッドは呼び出すことによって、特定の非同期操作の有効期間を終了、<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>メソッドを対応する<xref:System.ComponentModel.AsyncOperation>です。</span><span class="sxs-lookup"><span data-stu-id="4738a-168">This method also ends the lifetime of a particular asynchronous operation by calling the <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> method on the corresponding <xref:System.ComponentModel.AsyncOperation>.</span></span> <span data-ttu-id="4738a-169">この呼び出しでは、アプリケーション モデルを適切なスレッドで完了イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="4738a-169">This call raises the completion event on the thread that is appropriate for the application model.</span></span> <span data-ttu-id="4738a-170">後に、<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>メソッドは、このインスタンスの<xref:System.ComponentModel.AsyncOperation>使用できなくでき、それを使用しようとした後は例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="4738a-170">After the <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> method is called, this instance of <xref:System.ComponentModel.AsyncOperation> can no longer be used, and any subsequent attempts to use it will throw an exception.</span></span>  
  
 <span data-ttu-id="4738a-171">`CompletionMethod`署名が保持するすべての状態、非同期操作の結果を記述するために必要です。</span><span class="sxs-lookup"><span data-stu-id="4738a-171">The `CompletionMethod` signature must hold all state necessary to describe the outcome of the asynchronous operation.</span></span> <span data-ttu-id="4738a-172">素数の数値ではない場合、数値が素数と、最初の除数の値かどうかは、この特定の非同期操作によってテストされた数の状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="4738a-172">It holds state for the number that was tested by this particular asynchronous operation, whether the number is prime, and the value of its first divisor if it is not a prime number.</span></span> <span data-ttu-id="4738a-173">状態が発生した任意の例外を記述するも保持し、<xref:System.ComponentModel.AsyncOperation>この特定のタスクに対応します。</span><span class="sxs-lookup"><span data-stu-id="4738a-173">It also holds state describing any exception that occurred, and the <xref:System.ComponentModel.AsyncOperation> corresponding to this particular task.</span></span>  
  
#### <a name="to-complete-an-asynchronous-operation"></a><span data-ttu-id="4738a-174">非同期操作を完了します。</span><span class="sxs-lookup"><span data-stu-id="4738a-174">To complete an asynchronous operation:</span></span>  
  
-   <span data-ttu-id="4738a-175">完了メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="4738a-175">Implement the completion method.</span></span> <span data-ttu-id="4738a-176">設定にそれを使用して、6 つのパラメーター、`CalculatePrimeCompletedEventArgs`を通じて、クライアントのクライアントに返される`CalculatePrimeCompletedEventHandler`です。</span><span class="sxs-lookup"><span data-stu-id="4738a-176">It takes six parameters, which it uses to populate a `CalculatePrimeCompletedEventArgs` that is returned to the client through the client's `CalculatePrimeCompletedEventHandler`.</span></span> <span data-ttu-id="4738a-177">内部のコレクションから、クライアントのタスクの ID トークンを削除しを呼び出して非同期操作の有効期間終了<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>です。</span><span class="sxs-lookup"><span data-stu-id="4738a-177">It removes the client's task ID token from the internal collection, and it ends the asynchronous operation's lifetime with a call to <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>.</span></span> <span data-ttu-id="4738a-178"><xref:System.ComponentModel.AsyncOperation>スレッドまたはコンテキストに適したアプリケーション モデルへの呼び出しをマーシャ リングします。</span><span class="sxs-lookup"><span data-stu-id="4738a-178">The <xref:System.ComponentModel.AsyncOperation> marshals the call to the thread or context that is appropriate for the application model.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#26)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#26](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#26)]  
  
## <a name="checkpoint"></a><span data-ttu-id="4738a-179">チェックポイント</span><span class="sxs-lookup"><span data-stu-id="4738a-179">Checkpoint</span></span>  
 <span data-ttu-id="4738a-180">この時点では、コンポーネントをビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="4738a-180">At this point, you can build the component.</span></span>  
  
#### <a name="to-test-your-component"></a><span data-ttu-id="4738a-181">コンポーネントをテストするには</span><span class="sxs-lookup"><span data-stu-id="4738a-181">To test your component</span></span>  
  
-   <span data-ttu-id="4738a-182">コンポーネントをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="4738a-182">Compile the component.</span></span>  
  
     <span data-ttu-id="4738a-183">コンパイラの警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4738a-183">You will receive one compiler warning:</span></span>  
  
    ```  
    warning CS0169: The private field 'AsynchronousPatternExample.PrimeNumberCalculator.workerDelegate' is never used  
    ```  
  
     <span data-ttu-id="4738a-184">この警告は、次のセクションでは解決されます。</span><span class="sxs-lookup"><span data-stu-id="4738a-184">This warning will be resolved in the next section.</span></span>  
  
## <a name="implementing-the-worker-methods"></a><span data-ttu-id="4738a-185">ワーカー メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="4738a-185">Implementing the Worker Methods</span></span>  
 <span data-ttu-id="4738a-186">これまでのサポート、非同期コードを実装している、`PrimeNumberCalculator`コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="4738a-186">So far, you have implemented the supporting asynchronous code for the `PrimeNumberCalculator` component.</span></span> <span data-ttu-id="4738a-187">実際の処理を行うコードを実装できます。</span><span class="sxs-lookup"><span data-stu-id="4738a-187">Now you can implement the code that does the actual work.</span></span> <span data-ttu-id="4738a-188">次の 3 つの方法を実装する: `CalculateWorker`、 `BuildPrimeNumberList`、および`IsPrime`です。</span><span class="sxs-lookup"><span data-stu-id="4738a-188">You will implement three methods: `CalculateWorker`, `BuildPrimeNumberList`, and `IsPrime`.</span></span> <span data-ttu-id="4738a-189">同時に、`BuildPrimeNumberList`と`IsPrime`篩のエラトステネス、かどうかを数値素数テスト数値の平方根までのすべての素数を検索するいると呼ばれる、よく知られているアルゴリズムを構成します。</span><span class="sxs-lookup"><span data-stu-id="4738a-189">Together, `BuildPrimeNumberList` and `IsPrime` comprise a well-known algorithm called the Sieve of Eratosthenes, which determines if a number is prime by finding all the prime numbers up to the square root of the test number.</span></span> <span data-ttu-id="4738a-190">その時点で除数が見つからない場合、テストの数は、素数です。</span><span class="sxs-lookup"><span data-stu-id="4738a-190">If no divisors are found by that point, the test number is prime.</span></span>  
  
 <span data-ttu-id="4738a-191">このコンポーネントは、効率性を高める用に作成された場合、異なるテスト数値のさまざまな呼び出しによって検出されたすべての素数を記憶します。</span><span class="sxs-lookup"><span data-stu-id="4738a-191">If this component were written for maximum efficiency, it would remember all the prime numbers discovered by various invocations for different test numbers.</span></span> <span data-ttu-id="4738a-192">2、3、5 などの単純な除数もチェックします。</span><span class="sxs-lookup"><span data-stu-id="4738a-192">It would also check for trivial divisors like 2, 3, and 5.</span></span> <span data-ttu-id="4738a-193">どの時間のかかる操作を示すためには、この例の目的は、実行できる非同期で、ただし、ため、これらの最適化は、手順のままにします。</span><span class="sxs-lookup"><span data-stu-id="4738a-193">The intent of this example is to demonstrate how time-consuming operations can be executed asynchronously, however, so these optimizations are left as an exercise for you.</span></span>  
  
 <span data-ttu-id="4738a-194">`CalculateWorker`メソッドは、デリゲートにラップされ、呼び出しを非同期で呼び出される`BeginInvoke`です。</span><span class="sxs-lookup"><span data-stu-id="4738a-194">The `CalculateWorker` method is wrapped in a delegate and is invoked asynchronously with a call to `BeginInvoke`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4738a-195">進行状況レポートでは実装されて、`BuildPrimeNumberList`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="4738a-195">Progress reporting is implemented in the `BuildPrimeNumberList` method.</span></span> <span data-ttu-id="4738a-196">高速なコンピューターは、`ProgressChanged`すばやく連続的にイベントを発生することができます。</span><span class="sxs-lookup"><span data-stu-id="4738a-196">On fast computers, `ProgressChanged` events can be raised in rapid succession.</span></span> <span data-ttu-id="4738a-197">これらのイベントが発生した、クライアントのスレッドは、このような状況を処理できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4738a-197">The client thread, on which these events are raised, must be able to handle this situation.</span></span> <span data-ttu-id="4738a-198">ユーザー インターフェイスのコードのメッセージであふれしてありますに対する遅れ、ハングします。</span><span class="sxs-lookup"><span data-stu-id="4738a-198">User interface code may be flooded with messages and unable to keep up, resulting in hanging behavior.</span></span> <span data-ttu-id="4738a-199">このような状況を処理する例のユーザー インターフェイスを参照してください。[する方法: イベント ベースの非同期パターンのクライアントを実装する](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)です。</span><span class="sxs-lookup"><span data-stu-id="4738a-199">For an example user interface that handles this situation, see [How to: Implement a Client of the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).</span></span>  
  
#### <a name="to-execute-the-prime-number-calculation-asynchronously"></a><span data-ttu-id="4738a-200">素数の計算を非同期的に実行するには。</span><span class="sxs-lookup"><span data-stu-id="4738a-200">To execute the prime number calculation asynchronously:</span></span>  
  
1.  <span data-ttu-id="4738a-201">実装、`TaskCanceled`ユーティリティ メソッドです。</span><span class="sxs-lookup"><span data-stu-id="4738a-201">Implement the `TaskCanceled` utility method.</span></span> <span data-ttu-id="4738a-202">これは、指定したタスクの ID のタスクの有効期間のコレクションをチェックし、返します`true`タスク ID が見つからない場合。</span><span class="sxs-lookup"><span data-stu-id="4738a-202">This checks the task lifetime collection for the given task ID, and returns `true` if the task ID is not found.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#32)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#32](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#32)]  
  
2.  <span data-ttu-id="4738a-203">`CalculateWorker` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="4738a-203">Implement the `CalculateWorker` method.</span></span> <span data-ttu-id="4738a-204">2 つのパラメーター: 数をテストするには、<xref:System.ComponentModel.AsyncOperation>です。</span><span class="sxs-lookup"><span data-stu-id="4738a-204">It takes two parameters: a number to test, and an <xref:System.ComponentModel.AsyncOperation>.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#27)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#27](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#27)]  
  
3.  <span data-ttu-id="4738a-205">`BuildPrimeNumberList` を実装します。</span><span class="sxs-lookup"><span data-stu-id="4738a-205">Implement `BuildPrimeNumberList`.</span></span> <span data-ttu-id="4738a-206">2 つのパラメーター: をテストするには、番号と<xref:System.ComponentModel.AsyncOperation>です。</span><span class="sxs-lookup"><span data-stu-id="4738a-206">It takes two parameters: the number to test, and an <xref:System.ComponentModel.AsyncOperation>.</span></span> <span data-ttu-id="4738a-207">使用して、<xref:System.ComponentModel.AsyncOperation>レポートの進行状況およびインクリメンタル結果をします。</span><span class="sxs-lookup"><span data-stu-id="4738a-207">It uses the <xref:System.ComponentModel.AsyncOperation> to report progress and incremental results.</span></span> <span data-ttu-id="4738a-208">これで、適切なスレッドまたはアプリケーション モデルのコンテキストで、クライアントのイベント ハンドラーを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="4738a-208">This assures that the client's event handlers are called on the proper thread or context for the application model.</span></span> <span data-ttu-id="4738a-209">ときに`BuildPrimeNumberList`素数見つかると、報告この増分の結果としてのクライアントのイベント ハンドラーに、`ProgressChanged`イベント。</span><span class="sxs-lookup"><span data-stu-id="4738a-209">When `BuildPrimeNumberList` finds a prime number, it reports this as an incremental result to the client's event handler for the `ProgressChanged` event.</span></span> <span data-ttu-id="4738a-210">派生したクラスが必要です<xref:System.ComponentModel.ProgressChangedEventArgs>という`CalculatePrimeProgressChangedEventArgs`、これがいずれかの追加と呼ばれるプロパティ`LatestPrimeNumber`です。</span><span class="sxs-lookup"><span data-stu-id="4738a-210">This requires a class derived from <xref:System.ComponentModel.ProgressChangedEventArgs>, called `CalculatePrimeProgressChangedEventArgs`, which has one added property called `LatestPrimeNumber`.</span></span>  
  
     <span data-ttu-id="4738a-211">`BuildPrimeNumberList`メソッドも定期的に呼び出して、`TaskCanceled`メソッドと終了メソッドを返す場合`true`です。</span><span class="sxs-lookup"><span data-stu-id="4738a-211">The `BuildPrimeNumberList` method also periodically calls the `TaskCanceled` method and exits if the method returns `true`.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#5)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#5)]  
  
4.  <span data-ttu-id="4738a-212">`IsPrime` を実装します。</span><span class="sxs-lookup"><span data-stu-id="4738a-212">Implement `IsPrime`.</span></span> <span data-ttu-id="4738a-213">3 つのパラメーター: 既知の素数をテストする数、および最初に見つかった除数の出力パラメーターの一覧です。</span><span class="sxs-lookup"><span data-stu-id="4738a-213">It takes three parameters: a list of known prime numbers, the number to test, and an output parameter for the first divisor found.</span></span> <span data-ttu-id="4738a-214">素数のリストを指定するには、テスト数は素数が決定されます。</span><span class="sxs-lookup"><span data-stu-id="4738a-214">Given the list of prime numbers, it determines if the test number is prime.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#28)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#28](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#28)]  
  
5.  <span data-ttu-id="4738a-215">派生`CalculatePrimeProgressChangedEventArgs`から<xref:System.ComponentModel.ProgressChangedEventArgs>です。</span><span class="sxs-lookup"><span data-stu-id="4738a-215">Derive `CalculatePrimeProgressChangedEventArgs` from <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span> <span data-ttu-id="4738a-216">このクラスは、クライアントのイベント ハンドラーにインクリメンタル結果を報告するために必要な`ProgressChanged`イベント。</span><span class="sxs-lookup"><span data-stu-id="4738a-216">This class is necessary for reporting incremental results to the client's event handler for the `ProgressChanged` event.</span></span> <span data-ttu-id="4738a-217">呼ばれる 1 つの追加プロパティがある`LatestPrimeNumber`です。</span><span class="sxs-lookup"><span data-stu-id="4738a-217">It has one added property called `LatestPrimeNumber`.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#29)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#29](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#29)]  
  
## <a name="checkpoint"></a><span data-ttu-id="4738a-218">チェックポイント</span><span class="sxs-lookup"><span data-stu-id="4738a-218">Checkpoint</span></span>  
 <span data-ttu-id="4738a-219">この時点では、コンポーネントをビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="4738a-219">At this point, you can build the component.</span></span>  
  
#### <a name="to-test-your-component"></a><span data-ttu-id="4738a-220">コンポーネントをテストするには</span><span class="sxs-lookup"><span data-stu-id="4738a-220">To test your component</span></span>  
  
-   <span data-ttu-id="4738a-221">コンポーネントをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="4738a-221">Compile the component.</span></span>  
  
     <span data-ttu-id="4738a-222">書き込まれるは開始して、非同期操作をキャンセルする方法は、すべて`CalculatePrimeAsync`と`CancelAsync`です。</span><span class="sxs-lookup"><span data-stu-id="4738a-222">All that remains to be written are the methods to start and cancel asynchronous operations, `CalculatePrimeAsync` and `CancelAsync`.</span></span>  
  
## <a name="implementing-the-start-and-cancel-methods"></a><span data-ttu-id="4738a-223">開始とキャンセル メソッドの実装</span><span class="sxs-lookup"><span data-stu-id="4738a-223">Implementing the Start and Cancel Methods</span></span>  
 <span data-ttu-id="4738a-224">呼び出すことにより、独自のスレッドで、ワーカー スレッドを開始する`BeginInvoke`でそれをラップするデリゲート。</span><span class="sxs-lookup"><span data-stu-id="4738a-224">You start the worker method on its own thread by calling `BeginInvoke` on the delegate that wraps it.</span></span> <span data-ttu-id="4738a-225">特定の非同期操作の有効期間を管理するを呼び出す、<xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A>メソッドを<xref:System.ComponentModel.AsyncOperationManager>ヘルパー クラス。</span><span class="sxs-lookup"><span data-stu-id="4738a-225">To manage the lifetime of a particular asynchronous operation, you call the <xref:System.ComponentModel.AsyncOperationManager.CreateOperation%2A> method on the <xref:System.ComponentModel.AsyncOperationManager> helper class.</span></span> <span data-ttu-id="4738a-226">これを返します、 <xref:System.ComponentModel.AsyncOperation>、適切なスレッドまたはコンテキストに、クライアントのイベント ハンドラーに呼び出しをマーシャ リングします。</span><span class="sxs-lookup"><span data-stu-id="4738a-226">This returns an <xref:System.ComponentModel.AsyncOperation>, which marshals calls on the client's event handlers to the proper thread or context.</span></span>  
  
 <span data-ttu-id="4738a-227">呼び出して、特定の保留中の操作を取り消す<xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A>それに対応する <xref:System.ComponentModel.AsyncOperation>です。</span><span class="sxs-lookup"><span data-stu-id="4738a-227">You cancel a particular pending operation by calling <xref:System.ComponentModel.AsyncOperation.PostOperationCompleted%2A> on its corresponding <xref:System.ComponentModel.AsyncOperation>.</span></span> <span data-ttu-id="4738a-228">これは、操作を終了する、し、後続の呼び出し、<xref:System.ComponentModel.AsyncOperation>例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="4738a-228">This ends that operation, and any subsequent calls to its <xref:System.ComponentModel.AsyncOperation> will throw an exception.</span></span>  
  
#### <a name="to-implement-start-and-cancel-functionality"></a><span data-ttu-id="4738a-229">開始を実装する機能をキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="4738a-229">To implement Start and Cancel functionality:</span></span>  
  
1.  <span data-ttu-id="4738a-230">`CalculatePrimeAsync` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="4738a-230">Implement the `CalculatePrimeAsync` method.</span></span> <span data-ttu-id="4738a-231">クライアントが指定したトークン (タスク ID) が現在保留中のタスクを表すすべてのトークンで一意であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4738a-231">Make sure the client-supplied token (task ID) is unique with respect to all the tokens representing currently pending tasks.</span></span> <span data-ttu-id="4738a-232">クライアントが非一意のトークンで渡す場合`CalculatePrimeAsync`例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="4738a-232">If the client passes in a non-unique token, `CalculatePrimeAsync` raises an exception.</span></span> <span data-ttu-id="4738a-233">それ以外の場合、トークンは、タスク ID のコレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="4738a-233">Otherwise, the token is added to the task ID collection.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#3)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#3)]  
  
2.  <span data-ttu-id="4738a-234">`CancelAsync` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="4738a-234">Implement the `CancelAsync` method.</span></span> <span data-ttu-id="4738a-235">場合、`taskId`トークンのコレクションにパラメーターが存在し、削除されます。</span><span class="sxs-lookup"><span data-stu-id="4738a-235">If the `taskId` parameter exists in the token collection, it is removed.</span></span> <span data-ttu-id="4738a-236">これは、取り消されたタスクの実行を開始していないことを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="4738a-236">This prevents canceled tasks that have not started from running.</span></span> <span data-ttu-id="4738a-237">タスクが実行されている場合、`BuildPrimeNumberList`メソッドは、タスク ID が有効期間のコレクションから削除されたことを検出した場合に終了します。</span><span class="sxs-lookup"><span data-stu-id="4738a-237">If the task is running, the `BuildPrimeNumberList` method exits when it detects that the task ID has been removed from the lifetime collection.</span></span>  
  
     [!code-csharp[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#4)]
     [!code-vb[System.ComponentModel.AsyncOperationManager#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#4)]  
  
## <a name="checkpoint"></a><span data-ttu-id="4738a-238">チェックポイント</span><span class="sxs-lookup"><span data-stu-id="4738a-238">Checkpoint</span></span>  
 <span data-ttu-id="4738a-239">この時点では、コンポーネントをビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="4738a-239">At this point, you can build the component.</span></span>  
  
#### <a name="to-test-your-component"></a><span data-ttu-id="4738a-240">コンポーネントをテストするには</span><span class="sxs-lookup"><span data-stu-id="4738a-240">To test your component</span></span>  
  
-   <span data-ttu-id="4738a-241">コンポーネントをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="4738a-241">Compile the component.</span></span>  
  
 <span data-ttu-id="4738a-242">`PrimeNumberCalculator`コンポーネントは完全で使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4738a-242">The `PrimeNumberCalculator` component is now complete and ready to use.</span></span>  
  
 <span data-ttu-id="4738a-243">使用する例をクライアントに対して、`PrimeNumberCalculator`コンポーネントを参照してください[する方法: イベント ベースの非同期パターンのクライアントを実装する](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)です。</span><span class="sxs-lookup"><span data-stu-id="4738a-243">For an example client that uses the `PrimeNumberCalculator` component, see [How to: Implement a Client of the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4738a-244">次の手順</span><span class="sxs-lookup"><span data-stu-id="4738a-244">Next Steps</span></span>  
 <span data-ttu-id="4738a-245">この例を記入を記述して`CalculatePrime`、同期に相当`CalculatePrimeAsync`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="4738a-245">You can fill out this example by writing `CalculatePrime`, the synchronous equivalent of `CalculatePrimeAsync` method.</span></span> <span data-ttu-id="4738a-246">これは、操作を行う、`PrimeNumberCalculator`コンポーネント、イベント ベースの非同期パターンに完全に準拠します。</span><span class="sxs-lookup"><span data-stu-id="4738a-246">This will make the `PrimeNumberCalculator` component fully compliant with the Event-based Asynchronous Pattern.</span></span>  
  
 <span data-ttu-id="4738a-247">別のテストの数値のさまざまな呼び出しによって検出されたすべての素数のリストを保持すると、この例を向上できます。</span><span class="sxs-lookup"><span data-stu-id="4738a-247">You can improve this example by retaining the list of all the prime numbers discovered by various invocations for different test numbers.</span></span> <span data-ttu-id="4738a-248">このアプローチを使用して、各タスクは、以前のタスクで行われる作業からメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="4738a-248">Using this approach, each task will benefit from the work done by previous tasks.</span></span> <span data-ttu-id="4738a-249">この一覧を保護するように注意する`lock`領域の場合、別のスレッドでリストへのアクセスがシリアル化されるようにします。</span><span class="sxs-lookup"><span data-stu-id="4738a-249">Be careful to protect this list with `lock` regions, so access to the list by different threads is serialized.</span></span>  
  
 <span data-ttu-id="4738a-250">この例は、2、3、5 などの単純な除数のテストによっても向上できます。</span><span class="sxs-lookup"><span data-stu-id="4738a-250">You can also improve this example by testing for trivial divisors, like 2, 3, and 5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4738a-251">関連項目</span><span class="sxs-lookup"><span data-stu-id="4738a-251">See Also</span></span>  
 [<span data-ttu-id="4738a-252">方法: バックグラウンドで操作を実行する</span><span class="sxs-lookup"><span data-stu-id="4738a-252">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="4738a-253">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="4738a-253">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [<span data-ttu-id="4738a-254">NOT IN BUILD: Visual Basic でのマルチ スレッド</span><span class="sxs-lookup"><span data-stu-id="4738a-254">NOT IN BUILD: Multithreading in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [<span data-ttu-id="4738a-255">方法: イベントベースの非同期パターンをサポートするコンポーネントを実装する</span><span class="sxs-lookup"><span data-stu-id="4738a-255">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="4738a-256">イベント ベースの非同期パターンを使用したマルチスレッド プログラミング</span><span class="sxs-lookup"><span data-stu-id="4738a-256">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
