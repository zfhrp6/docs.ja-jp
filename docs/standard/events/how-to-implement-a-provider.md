---
title: "方法: プロバイダーを実装する"
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
- observer design pattern [.NET Framework], implementing providers
- providers [.NET Framework], in observer design pattern
- observables [.NET Framework], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b9d8f96de8cb3d13568e755f1d5e885e0474d891
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-provider"></a><span data-ttu-id="59d45-102">方法: プロバイダーを実装する</span><span class="sxs-lookup"><span data-stu-id="59d45-102">How to: Implement a Provider</span></span>
<span data-ttu-id="59d45-103">オブサーバー デザイン パターンでは、データを監視し、通知を送信する、プロバイダー、およびプロバイダーから通知 (コールバック) を受け取る 1 つまたは複数のオブザーバーの分割が必要です。</span><span class="sxs-lookup"><span data-stu-id="59d45-103">The observer design pattern requires a division between a provider, which monitors data and sends notifications, and one or more observers, which receive notifications (callbacks) from the provider.</span></span> <span data-ttu-id="59d45-104">このトピックでは、プロバイダーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="59d45-104">This topic discusses how to create a provider.</span></span> <span data-ttu-id="59d45-105">関連するトピック[する方法: オブザーバーを実装する](../../../docs/standard/events/how-to-implement-an-observer.md)オブザーバーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="59d45-105">A related topic, [How to: Implement an Observer](../../../docs/standard/events/how-to-implement-an-observer.md), discusses how to create an observer.</span></span>  
  
### <a name="to-create-a-provider"></a><span data-ttu-id="59d45-106">プロバイダーを作成するには</span><span class="sxs-lookup"><span data-stu-id="59d45-106">To create a provider</span></span>  
  
1.  <span data-ttu-id="59d45-107">プロバイダーはオブザーバーに送信するため、データを定義します。</span><span class="sxs-lookup"><span data-stu-id="59d45-107">Define the data that the provider is responsible for sending to observers.</span></span> <span data-ttu-id="59d45-108">プロバイダーとオブザーバーに送信されるデータを指定できますが、1 つの型は通常、さまざまな種類で表されます。</span><span class="sxs-lookup"><span data-stu-id="59d45-108">Although the provider and the data that it sends to observers can be a single type, they are generally represented by different types.</span></span> <span data-ttu-id="59d45-109">など、アプリケーションの監視温度、`Temperature`構造データの定義をプロバイダー (で表される、`TemperatureMonitor`次の手順で定義されたクラス) を監視し、どのオブザーバーをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="59d45-109">For example, in a temperature monitoring application, the `Temperature` structure defines the data that the provider (which is represented by the `TemperatureMonitor` class defined in the next step) monitors and to which observers subscribe.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2.  <span data-ttu-id="59d45-110">実装する型であるデータ プロバイダーを定義、<xref:System.IObservable%601?displayProperty=nameWithType>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="59d45-110">Define the data provider, which is a type that implements the <xref:System.IObservable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="59d45-111">プロバイダーのジェネリック型引数は、プロバイダーがオブザーバーに送信する型です。</span><span class="sxs-lookup"><span data-stu-id="59d45-111">The provider's generic type argument is the type that the provider sends to observers.</span></span> <span data-ttu-id="59d45-112">次の例では定義、`TemperatureMonitor`は構築されたクラス<xref:System.IObservable%601?displayProperty=nameWithType>のジェネリック型引数で実装`Temperature`です。</span><span class="sxs-lookup"><span data-stu-id="59d45-112">The following example defines a `TemperatureMonitor` class, which is a constructed <xref:System.IObservable%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3.  <span data-ttu-id="59d45-113">プロバイダーは格納方法オブザーバーへの参照できるように、適切な場合に、各オブザーバーを通知することができますを決定します。</span><span class="sxs-lookup"><span data-stu-id="59d45-113">Determine how the provider will store references to observers so that each observer can be notified when appropriate.</span></span> <span data-ttu-id="59d45-114">ジェネリック型などのコレクション オブジェクトではほとんどの場合、<xref:System.Collections.Generic.List%601>オブジェクトはこの目的に使用します。</span><span class="sxs-lookup"><span data-stu-id="59d45-114">Most commonly, a collection object such as a generic <xref:System.Collections.Generic.List%601> object is used for this purpose.</span></span> <span data-ttu-id="59d45-115">次の例では、プライベート<xref:System.Collections.Generic.List%601>でインスタンス化されるオブジェクト、`TemperatureMonitor`クラスのコンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="59d45-115">The following example defines a private <xref:System.Collections.Generic.List%601> object that is instantiated in the `TemperatureMonitor` class constructor.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4.  <span data-ttu-id="59d45-116">定義、<xref:System.IDisposable>実装できるように、いつでも通知の受信が停止することをサブスクライバーにプロバイダーを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="59d45-116">Define an <xref:System.IDisposable> implementation that the provider can return to subscribers so that they can stop receiving notifications at any time.</span></span> <span data-ttu-id="59d45-117">次の例は、入れ子になった定義`Unsubscriber`クラスとサブスクライバーのするサブスクライバーのコレクションの参照を渡し、クラスがインスタンス化されるときです。</span><span class="sxs-lookup"><span data-stu-id="59d45-117">The following example defines a nested `Unsubscriber` class that is passed a reference to the subscribers collection and to the subscriber when the class is instantiated.</span></span> <span data-ttu-id="59d45-118">このコードを有効にするオブジェクトのサブスクライバー<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>自体をサブスクライバーのコレクションから削除する実装。</span><span class="sxs-lookup"><span data-stu-id="59d45-118">This code enables the subscriber to call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation to remove itself from the subscribers collection.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5.  <span data-ttu-id="59d45-119"><xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="59d45-119">Implement the <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="59d45-120">メソッドがへの参照を渡し、<xref:System.IObserver%601?displayProperty=nameWithType>インターフェイスし、手順 3. では、その目的で設計されたオブジェクトに格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59d45-120">The method is passed a reference to the <xref:System.IObserver%601?displayProperty=nameWithType> interface and should be stored in the object designed for that purpose in step 3.</span></span> <span data-ttu-id="59d45-121">メソッドが返す必要がありますし、<xref:System.IDisposable>手順 4. で開発された実装。</span><span class="sxs-lookup"><span data-stu-id="59d45-121">The method should then return the <xref:System.IDisposable> implementation developed in step 4.</span></span> <span data-ttu-id="59d45-122">次の例の実装を示しています、<xref:System.IObservable%601.Subscribe%2A>メソッドで、`TemperatureMonitor`クラスです。</span><span class="sxs-lookup"><span data-stu-id="59d45-122">The following example shows the implementation of the <xref:System.IObservable%601.Subscribe%2A> method in the `TemperatureMonitor` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6.  <span data-ttu-id="59d45-123">呼び出すことによって適切なオブザーバーに通知が<xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>、 <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>、および<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>実装します。</span><span class="sxs-lookup"><span data-stu-id="59d45-123">Notify observers as appropriate by calling their <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementations.</span></span> <span data-ttu-id="59d45-124">場合によっては、プロバイダーを呼び出すことがない、<xref:System.IObserver%601.OnError%2A>メソッドはエラーが発生したとします。</span><span class="sxs-lookup"><span data-stu-id="59d45-124">In some cases, a provider may not call the <xref:System.IObserver%601.OnError%2A> method when an error occurs.</span></span> <span data-ttu-id="59d45-125">たとえば、次`GetTemperature`メソッドは、モニターを 5 秒ごとに気温データを読み取り、前の読み取り以降には、少なくとも 1 度によって、温度、変更された場合、オブザーバーに通知をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="59d45-125">For example, the following `GetTemperature` method simulates a monitor that reads temperature data every five seconds and notifies observers if the temperature has changed by at least .1 degree since the previous reading.</span></span> <span data-ttu-id="59d45-126">場合、デバイスが温度を報告していない (つまり、その値が null 場合)、プロバイダーは、転送が完了したことをオブザーバーに通知します。</span><span class="sxs-lookup"><span data-stu-id="59d45-126">If the device does not report a temperature (that is, if its value is null), the provider notifies observers that the transmission is complete.</span></span> <span data-ttu-id="59d45-127">なお、各オブザーバーを呼び出すだけでなく<xref:System.IObserver%601.OnCompleted%2A>、メソッド、`GetTemperature`メソッドをクリア、<xref:System.Collections.Generic.List%601>コレクション。</span><span class="sxs-lookup"><span data-stu-id="59d45-127">Note that, in addition to calling each observer's <xref:System.IObserver%601.OnCompleted%2A> method, the `GetTemperature` method clears the <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="59d45-128">この場合、プロバイダーを行いませんへの呼び出し、<xref:System.IObserver%601.OnError%2A>そのオブザーバーのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="59d45-128">In this case, the provider makes no calls to the <xref:System.IObserver%601.OnError%2A> method of its observers.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="59d45-129">例</span><span class="sxs-lookup"><span data-stu-id="59d45-129">Example</span></span>  
 <span data-ttu-id="59d45-130">次の例には、定義するための完全なソース コードが含まれています、<xref:System.IObservable%601>温度監視アプリケーションの実装です。</span><span class="sxs-lookup"><span data-stu-id="59d45-130">The following example contains the complete source code for defining an <xref:System.IObservable%601> implementation for a temperature monitoring application.</span></span> <span data-ttu-id="59d45-131">含まれている、`Temperature`オブザーバーに送信するデータには、構造および`TemperatureMonitor`はクラス、<xref:System.IObservable%601>実装します。</span><span class="sxs-lookup"><span data-stu-id="59d45-131">It includes the `Temperature` structure, which is the data sent to observers, and the `TemperatureMonitor` class, which is the <xref:System.IObservable%601> implementation.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="59d45-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="59d45-132">See Also</span></span>  
 <xref:System.IObservable%601>  
 [<span data-ttu-id="59d45-133">オブサーバー デザイン パターン</span><span class="sxs-lookup"><span data-stu-id="59d45-133">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)  
 [<span data-ttu-id="59d45-134">方法: オブザーバーを実装する</span><span class="sxs-lookup"><span data-stu-id="59d45-134">How to: Implement an Observer</span></span>](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [<span data-ttu-id="59d45-135">オブザーバー デザイン パターンのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="59d45-135">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)
