---
title: "方法: オブザーバーを実装する"
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
- observers [.NET Framework], observer design pattern
- observer design pattern [.NET Framework], implementing observers
ms.assetid: 8ecfa9f5-b500-473d-bcf0-5652ffb1e53d
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a964bd031f6f8a7fc029b2b209b9693b72e688af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-an-observer"></a><span data-ttu-id="451f8-102">方法: オブザーバーを実装する</span><span class="sxs-lookup"><span data-stu-id="451f8-102">How to: Implement an Observer</span></span>
<span data-ttu-id="451f8-103">オブサーバー デザイン パターンでは、通知を登録すると、監視者、およびデータを監視し、1 つまたは複数のオブザーバーに通知を送信する、プロバイダーの分割が必要です。</span><span class="sxs-lookup"><span data-stu-id="451f8-103">The observer design pattern requires a division between an observer, which registers for notifications, and a provider, which monitors data and sends notifications to one or more observers.</span></span> <span data-ttu-id="451f8-104">このトピックでは、オブザーバーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="451f8-104">This topic discusses how to create an observer.</span></span> <span data-ttu-id="451f8-105">関連するトピック[する方法: プロバイダーを実装する](../../../docs/standard/events/how-to-implement-a-provider.md)プロバイダーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="451f8-105">A related topic, [How to: Implement a Provider](../../../docs/standard/events/how-to-implement-a-provider.md), discusses how to create an provider.</span></span>  
  
### <a name="to-create-an-observer"></a><span data-ttu-id="451f8-106">オブザーバーを作成するには</span><span class="sxs-lookup"><span data-stu-id="451f8-106">To create an observer</span></span>  
  
1.  <span data-ttu-id="451f8-107">実装する型であると、オブザーバーを定義、<xref:System.IObserver%601?displayProperty=nameWithType>インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="451f8-107">Define the observer, which is a type that implements the <xref:System.IObserver%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="451f8-108">たとえば、次のコードがという名前の型を定義`TemperatureReporter`が構築された<xref:System.IObserver%601?displayProperty=nameWithType>のジェネリック型引数で実装`Temperature`です。</span><span class="sxs-lookup"><span data-stu-id="451f8-108">For example, the following code defines a type named `TemperatureReporter` that is a constructed <xref:System.IObserver%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#8)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#8)]  
  
2.  <span data-ttu-id="451f8-109">オブザーバーがプロバイダーの呼び出し前に、の通知の受信を停止することができる場合、<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>実装を保持するプライベート変数を定義する、 <xref:System.IDisposable> 、プロバイダーによって返される実装<xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="451f8-109">If the observer can stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, define a private variable that will hold the <xref:System.IDisposable> implementation returned by the provider's <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="451f8-110">呼び出す、プロバイダーのサブスクリプション メソッドを定義することも必要があります。<xref:System.IObservable%601.Subscribe%2A>メソッドと、返されたストア<xref:System.IDisposable>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="451f8-110">You should also define a subscription method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and stores the returned <xref:System.IDisposable> object.</span></span> <span data-ttu-id="451f8-111">たとえば、次のコードがという名前のプライベート変数を定義`unsubscriber`を定義し、`Subscribe`メソッドは、プロバイダーの呼び出しを<xref:System.IObservable%601.Subscribe%2A>メソッドに返されるオブジェクトを代入し、`unsubscriber`変数。</span><span class="sxs-lookup"><span data-stu-id="451f8-111">For example, the following code defines a private variable named `unsubscriber` and defines a `Subscribe` method that calls the provider's <xref:System.IObservable%601.Subscribe%2A> method and assigns the returned object to the `unsubscriber` variable.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#9)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#9)]  
  
3.  <span data-ttu-id="451f8-112">プロバイダーの呼び出し前に、の通知の受信を停止するオブザーバーをできるようにするメソッドを定義するその<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>実装では、この機能が必要な場合です。</span><span class="sxs-lookup"><span data-stu-id="451f8-112">Define a method that enables the observer to stop receiving notifications before the provider calls its <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementation, if this feature is required.</span></span> <span data-ttu-id="451f8-113">次の例では定義、`Unsubscribe`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="451f8-113">The following example defines an `Unsubscribe` method.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#10)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#10)]  
  
4.  <span data-ttu-id="451f8-114">によって定義された 3 つのメソッドの実装を提供する、<xref:System.IObserver%601>インターフェイス: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>、 <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>、および<xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="451f8-114">Provide implementations of the three methods defined by the <xref:System.IObserver%601> interface: <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="451f8-115">プロバイダーと、アプリケーションのニーズに応じて、<xref:System.IObserver%601.OnError%2A>と<xref:System.IObserver%601.OnCompleted%2A>メソッドがスタブ実装を指定できます。</span><span class="sxs-lookup"><span data-stu-id="451f8-115">Depending on the provider and the needs of the application, the <xref:System.IObserver%601.OnError%2A> and <xref:System.IObserver%601.OnCompleted%2A> methods can be stub implementations.</span></span> <span data-ttu-id="451f8-116">注意してください、<xref:System.IObserver%601.OnError%2A>メソッドを渡された処理しないでください<xref:System.Exception>オブジェクト、例外として、<xref:System.IObserver%601.OnCompleted%2A>メソッドは、プロバイダーの呼び出しに無料<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>実装します。</span><span class="sxs-lookup"><span data-stu-id="451f8-116">Note that the <xref:System.IObserver%601.OnError%2A> method should not handle the passed <xref:System.Exception> object as an exception, and the <xref:System.IObserver%601.OnCompleted%2A> method is free to call the provider's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="451f8-117">次の例は、<xref:System.IObserver%601>の実装、`TemperatureReporter`クラスです。</span><span class="sxs-lookup"><span data-stu-id="451f8-117">The following example shows the <xref:System.IObserver%601> implementation of the `TemperatureReporter` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#11)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="451f8-118">例</span><span class="sxs-lookup"><span data-stu-id="451f8-118">Example</span></span>  
 <span data-ttu-id="451f8-119">次の例には完全なソース コードが含まれています、`TemperatureReporter`を提供するクラス、<xref:System.IObserver%601>温度監視アプリケーションの実装です。</span><span class="sxs-lookup"><span data-stu-id="451f8-119">The following example contains the complete source code for the `TemperatureReporter` class, which provides the <xref:System.IObserver%601> implementation for a temperature monitoring application.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/observer.cs#12)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/observer.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="451f8-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="451f8-120">See Also</span></span>  
 <xref:System.IObserver%601>  
 [<span data-ttu-id="451f8-121">オブサーバー デザイン パターン</span><span class="sxs-lookup"><span data-stu-id="451f8-121">Observer Design Pattern</span></span>](../../../docs/standard/events/observer-design-pattern.md)  
 [<span data-ttu-id="451f8-122">方法: プロバイダーを実装する</span><span class="sxs-lookup"><span data-stu-id="451f8-122">How to: Implement a Provider</span></span>](../../../docs/standard/events/how-to-implement-a-provider.md)  
 [<span data-ttu-id="451f8-123">オブザーバー デザイン パターンのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="451f8-123">Observer Design Pattern Best Practices</span></span>](../../../docs/standard/events/observer-design-pattern-best-practices.md)
