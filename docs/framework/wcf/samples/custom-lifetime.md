---
title: "カスタム有効期間"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52806c07-b91c-48fe-b992-88a41924f51f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2538a9c483b949dfef1c60bd2225f5daf4e01117
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="custom-lifetime"></a><span data-ttu-id="6a682-102">カスタム有効期間</span><span class="sxs-lookup"><span data-stu-id="6a682-102">Custom Lifetime</span></span>
<span data-ttu-id="6a682-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の共有サービス インスタンスにカスタムの有効期間サービスを提供する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 拡張機能の作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6a682-103">This sample demonstrates how to write a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] extension to provide custom lifetime services for shared [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service instances.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a682-104">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a682-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="shared-instancing"></a><span data-ttu-id="6a682-105">共有インスタンス化</span><span class="sxs-lookup"><span data-stu-id="6a682-105">Shared Instancing</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="6a682-106"> では、サービス インスタンス用にいくつかのインスタンス化モードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="6a682-106"> offers several instancing modes for your service instances.</span></span> <span data-ttu-id="6a682-107">このトピックで説明する共有インスタンス化モードでは、サービス インスタンスを複数のチャネルで共有できます。</span><span class="sxs-lookup"><span data-stu-id="6a682-107">The Shared Instancing mode covered in this topic provides a way to share a service instance between multiple channels.</span></span> <span data-ttu-id="6a682-108">クライアントは、インスタンスのエンドポイント アドレスをローカルで解決するか、サービスのファクトリ メソッドと通信して実行中のインスタンスのエンドポイント アドレスを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="6a682-108">Clients can either resolve the instance’s endpoint address locally or contact a factory method in the service to obtain the endpoint address of a running instance.</span></span> <span data-ttu-id="6a682-109">エンドポイント アドレスを取得したら、新しいチャネルを作成して通信を開始することができます。</span><span class="sxs-lookup"><span data-stu-id="6a682-109">Once it has the endpoint address, it can create a new channel and start communication.</span></span> <span data-ttu-id="6a682-110">次のコード例は、クライアント アプリケーションが既存のサービス インスタンスへの新しいチャネルを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6a682-110">The following code snippet shows how a client application creates a new channel to an existing service instance.</span></span>  
  
```  
// Create the first channel.  
IEchoService proxy = channelFactory.CreateChannel();  
  
// Resolve the instance.  
EndpointAddress epa = ((IClientChannel)proxy).ResolveInstance();  
  
// Create new channel factory with the endpoint address resolved by   
// previous statement.  
ChannelFactory<IEchoService> channelFactory2 =  
                new ChannelFactory<IEchoService>("echoservice",  
                epa);  
  
// Create the second channel to the same instance.  
IEchoService proxy2 = channelFactory2.CreateChannel();  
```  
  
 <span data-ttu-id="6a682-111">他のインスタンス化モードとは異なり、共有インスタンス化モードでは、独特の方法でサービス インスタンスを解放します。</span><span class="sxs-lookup"><span data-stu-id="6a682-111">Unlike other instancing modes, the shared instancing mode has a unique way of releasing the service instances.</span></span> <span data-ttu-id="6a682-112">インスタンスのすべてのチャネルが閉じると、サービスの [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ランタイムによってタイマーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-112">When all the channels are closed for an instance, the service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime starts a timer.</span></span> <span data-ttu-id="6a682-113">タイムアウトになるまでに誰も接続しなかった場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] はインスタンスを解放してリソースを要求します。</span><span class="sxs-lookup"><span data-stu-id="6a682-113">If nobody makes a connection before the timeout expires, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] releases the instance and claims the resources.</span></span> <span data-ttu-id="6a682-114">切り離し手順の一環として、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、インスタンスを解放する前にすべての <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 実装の <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="6a682-114">As a part of the teardown procedure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of all <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementations before releasing the instance.</span></span> <span data-ttu-id="6a682-115">そのすべてが `true` を返す場合は、インスタンスが解放されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-115">If all of them return `true` the instance is released.</span></span> <span data-ttu-id="6a682-116">それ以外の場合、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装は、コールバック メソッドを使用してアイドル状態であることを`Dispatcher`に通知します。</span><span class="sxs-lookup"><span data-stu-id="6a682-116">Otherwise the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is responsible for notifying the `Dispatcher` of the idle state by using a callback method.</span></span>  
  
 <span data-ttu-id="6a682-117">既定では、<xref:System.ServiceModel.InstanceContext> のアイドル タイムアウト値は 1 分です。</span><span class="sxs-lookup"><span data-stu-id="6a682-117">By default, the idle timeout value of <xref:System.ServiceModel.InstanceContext> is one minute.</span></span> <span data-ttu-id="6a682-118">ただし、このサンプルでは、カスタム拡張機能を使用してこれを延長する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6a682-118">However this sample demonstrates how you can extend this using a custom extension.</span></span>  
  
## <a name="extending-the-instancecontext"></a><span data-ttu-id="6a682-119">InstanceContext の拡張</span><span class="sxs-lookup"><span data-stu-id="6a682-119">Extending the InstanceContext</span></span>  
 <span data-ttu-id="6a682-120">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の <xref:System.ServiceModel.InstanceContext> は、サービス インスタンスと`Dispatcher`の間のリンクです。</span><span class="sxs-lookup"><span data-stu-id="6a682-120">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.ServiceModel.InstanceContext> is the link between the service instance and the `Dispatcher`.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="6a682-121"> では、拡張可能オブジェクト パターンを使用して新しい状態または動作を追加することで、このランタイム コンポーネントを拡張できます。</span><span class="sxs-lookup"><span data-stu-id="6a682-121"> allows you to extend this runtime component by adding new state or behavior by using its extensible object pattern.</span></span> <span data-ttu-id="6a682-122">拡張可能オブジェクト パターンは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、既存のランタイム クラスに新しい機能を付け加えて拡張するため、またはオブジェクトに新しい状態の機能を追加するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-122">The extensible object pattern is used in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to either extend existing runtime classes with new functionality or to add new state features to an object.</span></span> <span data-ttu-id="6a682-123">拡張可能オブジェクト パターンには、`IExtensibleObject<T>`、`IExtension<T>`、および `IExtensionCollection<T>` の 3 つのインターフェイスがあります。</span><span class="sxs-lookup"><span data-stu-id="6a682-123">There are three interfaces in the extensible object pattern: `IExtensibleObject<T>`, `IExtension<T>`, and `IExtensionCollection<T>`.</span></span>  
  
 <span data-ttu-id="6a682-124">`IExtensibleObject<T>` インターフェイスは、機能をカスタマイズするための拡張が可能なオブジェクトによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-124">The `IExtensibleObject<T>` interface is implemented by objects to allow extensions which customize their functionality.</span></span>  
  
 <span data-ttu-id="6a682-125">`IExtension<T>` インターフェイスは、`T` 型のクラスの拡張が可能なオブジェクトによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-125">The `IExtension<T>` interface is implemented by objects that can be extensions of classes of type `T`.</span></span>  
  
 <span data-ttu-id="6a682-126">最後に、`IExtensionCollection<T>` インターフェイスは `IExtensions` のコレクションで、型ごとに `IExtensions` を取得できます。</span><span class="sxs-lookup"><span data-stu-id="6a682-126">And finally, the `IExtensionCollection<T>` interface is a collection of `IExtensions` that allows for retrieving `IExtensions` by their type.</span></span>  
  
 <span data-ttu-id="6a682-127">したがって、<xref:System.ServiceModel.InstanceContext> を拡張するには、`IExtension` インターフェイスを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a682-127">Therefore in order to extend the <xref:System.ServiceModel.InstanceContext> you must implement the `IExtension` interface.</span></span> <span data-ttu-id="6a682-128">このサンプル プロジェクトでは、`CustomLeaseExtension` クラスにこの実装が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6a682-128">In this sample project the `CustomLeaseExtension` class contains this implementation.</span></span>  
  
```  
class CustomLeaseExtension : IExtension<InstanceContext>  
{  
}  
```  
  
 <span data-ttu-id="6a682-129">`IExtension` インターフェイスには、`Attach` と `Detach` の 2 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6a682-129">The `IExtension` interface has two methods `Attach` and `Detach`.</span></span> <span data-ttu-id="6a682-130">名前が示すように、これらの 2 つのメソッドは、ランタイムが <xref:System.ServiceModel.InstanceContext> クラスのインスタンスに拡張機能を関連付けるときと関連付けを解除するときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-130">As their names imply, these two methods are called when the runtime attaches and detaches the extension to an instance of the <xref:System.ServiceModel.InstanceContext> class.</span></span> <span data-ttu-id="6a682-131">このサンプルでは、`Attach` メソッドを使用して、拡張機能の現在のインスタンスに属する <xref:System.ServiceModel.InstanceContext> オブジェクトを追跡します。</span><span class="sxs-lookup"><span data-stu-id="6a682-131">In this sample, the `Attach` method is used to keep track of the <xref:System.ServiceModel.InstanceContext> object that belongs to the current instance of the extension.</span></span>  
  
```  
InstanceContext owner;  
  
public void Attach(InstanceContext owner)  
{  
  this.owner = owner;   
}  
```  
  
 <span data-ttu-id="6a682-132">また、有効期間の延長をサポートするには、必要な実装を拡張機能に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a682-132">In addition, you must add the necessary implementation to the extension to provide the extended lifetime support.</span></span> <span data-ttu-id="6a682-133">したがって、`ICustomLease` インターフェイスを目的のメソッドで宣言し、`CustomLeaseExtension` クラスに実装します。</span><span class="sxs-lookup"><span data-stu-id="6a682-133">Therefore the `ICustomLease` interface is declared with the desired methods and is implemented in the `CustomLeaseExtension` class.</span></span>  
  
```  
interface ICustomLease  
{  
    bool IsIdle { get; }          
    InstanceContextIdleCallback Callback { get; set; }  
}  
  
class CustomLeaseExtension : IExtension<InstanceContext>, ICustomLease  
{  
}  
```  
  
 <span data-ttu-id="6a682-134">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> 実装で <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> メソッドを呼び出すと、この呼び出しは <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> の `CustomLeaseExtension` メソッドにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="6a682-134">When [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invokes the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method in the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation this call is routed to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method of the `CustomLeaseExtension`.</span></span> <span data-ttu-id="6a682-135">次に、`CustomLeaseExtension` はそのプライベート状態をチェックし、<xref:System.ServiceModel.InstanceContext> がアイドル状態かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="6a682-135">Then the `CustomLeaseExtension` checks its private state to see whether the <xref:System.ServiceModel.InstanceContext> is idle.</span></span> <span data-ttu-id="6a682-136">アイドル状態の場合は、`true` を返します。</span><span class="sxs-lookup"><span data-stu-id="6a682-136">If it is idle it returns `true`.</span></span> <span data-ttu-id="6a682-137">それ以外の場合は、延長された指定の有効期間のタイマーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-137">Otherwise, it starts a timer for a specified amount of extended lifetime.</span></span>  
  
```  
public bool IsIdle  
{  
  get  
  {  
    lock (thisLock)  
    {  
      if (isIdle)  
      {  
        return true;  
      }  
      else  
      {  
        StartTimer();  
        return false;  
      }  
    }  
  }  
}  
```  
  
 <span data-ttu-id="6a682-138">タイマーの `Elapsed` イベントで、別のクリーンアップ サイクルを開始するためにディスパッチャーのコールバック関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-138">In the timer’s `Elapsed` event the callback function in the Dispatcher is called in order to start another clean up cycle.</span></span>  
  
```  
void idleTimer_Elapsed(object sender, ElapsedEventArgs args)  
{  
    idleTimer.Stop();  
    isIdle = true;    
    callback(owner);  
}  
```  
  
 <span data-ttu-id="6a682-139">アイドル状態に移行中のインスタンスに新しいメッセージが届いたときに、実行中のタイマーを更新する方法はありません。</span><span class="sxs-lookup"><span data-stu-id="6a682-139">There is no way to renew the running timer when a new message arrives for the instance being moved to the idle state.</span></span>  
  
 <span data-ttu-id="6a682-140">このサンプルでは、<xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> メソッドの呼び出しを受け取って <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> にルーティングするために `CustomLeaseExtension` を実装します。</span><span class="sxs-lookup"><span data-stu-id="6a682-140">The sample implements <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> to intercept the calls to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method and route them to the `CustomLeaseExtension`.</span></span> <span data-ttu-id="6a682-141"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装は、`CustomLifetimeLease` クラスに含まれています。</span><span class="sxs-lookup"><span data-stu-id="6a682-141">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> implementation is contained in `CustomLifetimeLease` class.</span></span> <span data-ttu-id="6a682-142"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> メソッドは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] がサービス インスタンスを解放するときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-142">The <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method is invoked when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is about to release the service instance.</span></span> <span data-ttu-id="6a682-143">ただし、ServiceBehavior の `ISharedSessionInstance` コレクションに存在する特定の <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> 実装のインスタンスは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="6a682-143">However, there is only one instance of a particular `ISharedSessionInstance` implementation in the ServiceBehavior’s <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> collection.</span></span> <span data-ttu-id="6a682-144">つまり、<xref:System.ServiceModel.InstanceContext> が [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] メソッドをチェックする時点で閉じられている <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> を知る方法はありません。</span><span class="sxs-lookup"><span data-stu-id="6a682-144">This means there is no way of knowing the <xref:System.ServiceModel.InstanceContext> being closed at the time [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] checks the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span> <span data-ttu-id="6a682-145">したがって、このサンプルでは、スレッド ロックを使用して <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> メソッドへの要求をシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="6a682-145">Therefore this sample uses thread locking to serialize requests to the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.IsIdle%2A> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6a682-146">シリアル化はアプリケーションのパフォーマンスに大きな影響を及ぼす可能性があるので、スレッド ロックは使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6a682-146">Using thread locking is not a recommended approach because serialization can severely affect the performance of your application.</span></span>  
  
 <span data-ttu-id="6a682-147">`CustomLeaseExtension` クラスでプライベート メンバー変数を使用して、`IsIdle` の値を追跡します。</span><span class="sxs-lookup"><span data-stu-id="6a682-147">A private member variable is used in the `CustomLeaseExtension` class to track the `IsIdle` value.</span></span> <span data-ttu-id="6a682-148"><xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> の値が取得されるたびに、`IsIdle` プライベート メンバーが返されて `false` にリセットされます。</span><span class="sxs-lookup"><span data-stu-id="6a682-148">Each time the value of <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider> is retrieved the `IsIdle` private member is returned and reset to `false`.</span></span> <span data-ttu-id="6a682-149">ディスパッチャーが `false` メソッドを呼び出すようにするには、この値を <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a682-149">It is essential to set this value to `false` in order to make sure the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceContextProvider.NotifyIdle%2A> method.</span></span>  
  
```  
public bool IsIdle  
{  
    get   
    {  
       lock (thisLock)  
       {  
           bool idleCopy = isIdle;  
           isIdle = false;  
           return idleCopy;  
       }  
    }  
}  
```  
  
 <span data-ttu-id="6a682-150">`ISharedSessionLifetime.IsIdle` プロパティが `false` を返す場合、ディスパッチャーは `NotifyIdle` メソッドを使用してコールバック関数を登録します。</span><span class="sxs-lookup"><span data-stu-id="6a682-150">If the `ISharedSessionLifetime.IsIdle` property returns `false` the Dispatcher registers a callback function by using the `NotifyIdle` method.</span></span> <span data-ttu-id="6a682-151">このメソッドは、解放される <xref:System.ServiceModel.InstanceContext> への参照を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="6a682-151">This method receives a reference to the <xref:System.ServiceModel.InstanceContext> being released.</span></span> <span data-ttu-id="6a682-152">したがって、このサンプル コードでは、`ICustomLease` 型拡張に対してクエリを実行し、拡張状態の `ICustomLease.IsIdle` プロパティをチェックすることができます。</span><span class="sxs-lookup"><span data-stu-id="6a682-152">Therefore the sample code can query the `ICustomLease` type extension and check the `ICustomLease.IsIdle` property in the extended state.</span></span>  
  
```  
public void NotifyIdle(InstanceContextIdleCallback callback,   
            InstanceContext instanceContext)  
{  
    lock (thisLock)  
    {  
       ICustomLease customLease =  
           instanceContext.Extensions.Find<ICustomLease>();  
       customLease.Callback = callback;   
       isIdle = customLease.IsIdle;  
       if (isIdle)  
       {  
             callback(instanceContext);  
       }  
    }   
}  
```  
  
 <span data-ttu-id="6a682-153">`ICustomLease.IsIdle` プロパティをチェックする前に、Callback プロパティを設定する必要があります。これは、アイドル状態になったときに `CustomLeaseExtension` がディスパッチャーに通知するために不可欠です。</span><span class="sxs-lookup"><span data-stu-id="6a682-153">Before the `ICustomLease.IsIdle` property is checked the Callback property needs to be set as this is essential for `CustomLeaseExtension` to notify the Dispatcher when it becomes idle.</span></span> <span data-ttu-id="6a682-154">`ICustomLease.IsIdle` が `true` を返す場合は、`isIdle` プライベート メンバーが `CustomLifetimeLease` で単に `true` に設定され、コールバック メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-154">If `ICustomLease.IsIdle` returns `true`, the `isIdle` private member is simply set in `CustomLifetimeLease` to `true` and calls the callback method.</span></span> <span data-ttu-id="6a682-155">このコードではロックが使用されているので、他のスレッドではこのプライベート メンバーの値を変更できません。</span><span class="sxs-lookup"><span data-stu-id="6a682-155">Because the code holds a lock, other threads cannot change the value of this private member.</span></span> <span data-ttu-id="6a682-156">次にディスパッチャーが `ISharedSessionLifetime.IsIdle` をチェックするときに `true` が返されて、ディスパッチャーがインスタンスを解放できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6a682-156">And the next time Dispatcher checks the `ISharedSessionLifetime.IsIdle`, it returns `true` and lets Dispatcher release the instance.</span></span>  
  
 <span data-ttu-id="6a682-157">これでカスタム拡張機能の基礎が完成したので、この拡張機能をサービス モデルにフックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a682-157">Now that the groundwork for the custom extension is completed, it has to be hooked up to the service model.</span></span> <span data-ttu-id="6a682-158">`CustomLeaseExtension` 実装を <xref:System.ServiceModel.InstanceContext> にフックするために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> のブートストラップを実行する <xref:System.ServiceModel.InstanceContext> インターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="6a682-158">To hook up the `CustomLeaseExtension` implementation to the <xref:System.ServiceModel.InstanceContext>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides the <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> interface to perform the bootstrapping of <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="6a682-159">このサンプルでは、`CustomLeaseInitializer` クラスでこのインターフェイスを実装し、`CustomLeaseExtension` のインスタンスを唯一のメソッドの初期化から得られる <xref:System.ServiceModel.InstanceContext.Extensions%2A> コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="6a682-159">In the sample, the `CustomLeaseInitializer` class implements this interface and adds an instance of `CustomLeaseExtension` to the <xref:System.ServiceModel.InstanceContext.Extensions%2A> collection from the only method initialization.</span></span> <span data-ttu-id="6a682-160">このメソッドは、<xref:System.ServiceModel.InstanceContext> の初期化中にディスパッチャーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-160">This method is called by Dispatcher while initializing the <xref:System.ServiceModel.InstanceContext>.</span></span>  
  
```  
public void Initialize(InstanceContext instanceContext, Message message)  
{  
  IExtension<InstanceContext> customLeaseExtension =  
    new CustomLeaseExtension(timeout);  
  instanceContext.Extensions.Add(customLeaseExtension);  
}  
```  
  
 <span data-ttu-id="6a682-161">最後に、`System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime`と<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer>は実装が、サービス モデルを使用して最大フック、<xref:System.ServiceModel.Description.IServiceBehavior>実装します。</span><span class="sxs-lookup"><span data-stu-id="6a682-161">Finally the `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` and <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> implementations are is hooked up to the service model by using the <xref:System.ServiceModel.Description.IServiceBehavior> implementation.</span></span> <span data-ttu-id="6a682-162">この実装は、`CustomLeaseTimeAttribute` クラスに配置されています。また、`Attribute` 基本クラスから派生してこの動作を属性として公開します。</span><span class="sxs-lookup"><span data-stu-id="6a682-162">This implementation is placed in the `CustomLeaseTimeAttribute` class and it also derives from the `Attribute` base class to expose this behavior as an attribute.</span></span> <span data-ttu-id="6a682-163">`IServiceBehavior.ApplyBehavior` メソッドで、<xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> 実装と `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` 実装のインスタンスがそれぞれ `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` の <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> コレクションと <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-163">In the `IServiceBehavior.ApplyBehavior` method, instances of <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer> and `System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime` implementations are added to the `System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextLifetimes` and <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceContextInitializers%2A> collections of the <xref:System.ServiceModel.Dispatcher.IShareableInstanceContextLifetime> respectively.</span></span>  
  
```  
public void ApplyBehavior(ServiceDescription description,   
           ServiceHostBase serviceHostBase,   
           Collection<DispatchBehavior> behaviors,  
           Collection<BindingParameterCollection> parameters)  
{  
    CustomLifetimeLease customLease = new CustomLifetimeLease();  
    CustomLeaseInitializer initializer =   
                new CustomLeaseInitializer(timeout);  
  
    foreach (DispatchBehavior dispatchBehavior in behaviors)  
    {  
        dispatchBehavior.InstanceContextLifetimes.Add(customLease);  
        dispatchBehavior.InstanceContextInitializers.Add(initializer);  
    }  
}  
```  
  
 <span data-ttu-id="6a682-164">この動作は、`CustomLeaseTime` 属性を使用して注釈を付けることにより、サンプル サービス クラスに追加できます。</span><span class="sxs-lookup"><span data-stu-id="6a682-164">This behavior can be added to a sample service class by annotating it with the `CustomLeaseTime` attribute.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.Shareable)]  
[CustomLeaseTime(Timeout = 20000)]  
public class EchoService : IEchoService  
{  
  //…  
}  
```  
  
 <span data-ttu-id="6a682-165">このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-165">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="6a682-166">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="6a682-166">Press ENTER in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6a682-167">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="6a682-167">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="6a682-168">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="6a682-168">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="6a682-169">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6a682-169">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="6a682-170">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="6a682-170">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6a682-171">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="6a682-171">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6a682-172">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6a682-172">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6a682-173">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="6a682-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6a682-174">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6a682-174">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Lifetime`  
  
## <a name="see-also"></a><span data-ttu-id="6a682-175">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a682-175">See Also</span></span>
