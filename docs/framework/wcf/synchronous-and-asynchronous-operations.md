---
title: 同期操作と非同期操作
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
caps.latest.revision: 24
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c626699dc5291f4d4f6d432e89708661b233f16d
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="synchronous-and-asynchronous-operations"></a><span data-ttu-id="4963b-102">同期操作と非同期操作</span><span class="sxs-lookup"><span data-stu-id="4963b-102">Synchronous and Asynchronous Operations</span></span>
<span data-ttu-id="4963b-103">ここでは、非同期サービス操作の実装と呼び出しについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4963b-103">This topic discusses implementing and calling asynchronous service operations.</span></span>  
  
 <span data-ttu-id="4963b-104">多くのアプリケーションは、メソッド呼び出しの実行中に有用な処理を続行できるように、メソッドを非同期的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4963b-104">Many applications call methods asynchronously because it enables the application to continue doing useful work while the method call runs.</span></span> [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="4963b-105"> のサービスとクライアントは、アプリケーションの異なる 2 つのレベルで操作の非同期呼び出しに参加できます。これにより、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションの柔軟性がさらに高まり、対話機能とのバランスの取れたスループットを最大限に高めることができます。</span><span class="sxs-lookup"><span data-stu-id="4963b-105"> services and clients can participate in asynchronous operation calls at two distinct levels of the application, which provide [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications even more flexibility to maximize throughput balanced against interactivity.</span></span>  
  
## <a name="types-of-asynchronous-operations"></a><span data-ttu-id="4963b-106">非同期操作の種類</span><span class="sxs-lookup"><span data-stu-id="4963b-106">Types of Asynchronous Operations</span></span>  
 <span data-ttu-id="4963b-107">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のすべてのサービス コントラクトでは、パラメーターの型と戻り値に関係なく、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] の属性を使用して、クライアントとサービス間の特定のメッセージ交換パターンを指定します。</span><span class="sxs-lookup"><span data-stu-id="4963b-107">All service contracts in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], no matter the parameters types and return values, use [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] attributes to specify a particular message exchange pattern between client and service.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="4963b-108"> は、適切なサービス操作または実行元のクライアント コードに送受信メッセージを自動的にルーティングします。</span><span class="sxs-lookup"><span data-stu-id="4963b-108"> automatically routes inbound and outbound messages to the appropriate service operation or running client code.</span></span>  
  
 <span data-ttu-id="4963b-109">クライアントが所有するのは、特定操作のメッセージ交換パターンが指定されたサービス コントラクトのみです。</span><span class="sxs-lookup"><span data-stu-id="4963b-109">The client possesses only the service contract, which specifies the message exchange pattern for a particular operation.</span></span> <span data-ttu-id="4963b-110">基盤となるメッセージ交換パターンに従っている限り、クライアントは選択する任意のプログラミング モデルを開発者に提供できます。</span><span class="sxs-lookup"><span data-stu-id="4963b-110">Clients can offer the developer any programming model they choose, so long as the underlying message exchange pattern is observed.</span></span> <span data-ttu-id="4963b-111">同様に、サービスも、指定されたメッセージ パターンに従っている限り、任意の方法で操作を実装できます。</span><span class="sxs-lookup"><span data-stu-id="4963b-111">So, too, can services implement operations in any manner, so long as the specified message pattern is observed.</span></span>  
  
 <span data-ttu-id="4963b-112">サービス コントラクトがサービスとクライアントの両方の実装から独立していることで、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションでは次の形式の非同期実行が可能になります。</span><span class="sxs-lookup"><span data-stu-id="4963b-112">The independence of the service contract from either the service or client implementation enables the following forms of asynchronous execution in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications:</span></span>  
  
-   <span data-ttu-id="4963b-113">クライアントは、同期メッセージ交換を使用して要求/応答操作を非同期に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="4963b-113">Clients can invoke request/response operations asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="4963b-114">サービスは、同期メッセージ交換を使用して要求/応答操作を非同期に実装できます。</span><span class="sxs-lookup"><span data-stu-id="4963b-114">Services can implement a request/response operation asynchronously using a synchronous message exchange.</span></span>  
  
-   <span data-ttu-id="4963b-115">クライアントまたはサービスの実装に関係なく、一方向のメッセージ交換が可能です。</span><span class="sxs-lookup"><span data-stu-id="4963b-115">Message exchanges can be one-way, regardless of the implementation of the client or service.</span></span>  
  
### <a name="suggested-asynchronous-scenarios"></a><span data-ttu-id="4963b-116">推奨される非同期シナリオ</span><span class="sxs-lookup"><span data-stu-id="4963b-116">Suggested Asynchronous Scenarios</span></span>  
 <span data-ttu-id="4963b-117">操作のサービス実装でブロッキング呼び出し (I/O 処理の実行など) を作成する場合は、サービス操作の実装で非同期手法を使用します。</span><span class="sxs-lookup"><span data-stu-id="4963b-117">Use an asynchronous approach in a service operation implementation if the operation service implementation makes a blocking call, such as doing I/O work.</span></span> <span data-ttu-id="4963b-118">非同期操作を実装している場合、非同期の操作とメソッドを呼び出して、できるだけ非同期呼び出しパスを拡張するようにします。</span><span class="sxs-lookup"><span data-stu-id="4963b-118">When you are in an asynchronous operation implementation, try to call asynchronous operations and methods to extend the asynchronous call path as far as possible.</span></span> <span data-ttu-id="4963b-119">たとえば、`BeginOperationTwo()` 内から `BeginOperationOne()` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4963b-119">For example, call a `BeginOperationTwo()` from within `BeginOperationOne()`.</span></span>  
  
-   <span data-ttu-id="4963b-120">次のような場合には、クライアントまたは呼び出し元アプリケーションで非同期手法を使用します。</span><span class="sxs-lookup"><span data-stu-id="4963b-120">Use an asynchronous approach in a client or calling application in the following cases:</span></span>  
  
-   <span data-ttu-id="4963b-121">中間層アプリケーションから操作を呼び出す場合 </span><span class="sxs-lookup"><span data-stu-id="4963b-121">If you are invoking operations from a middle-tier application.</span></span> <span data-ttu-id="4963b-122">(このようなシナリオの詳細については、次を参照してください[中間層クライアント アプリケーション](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)。)。</span><span class="sxs-lookup"><span data-stu-id="4963b-122">(For more information about such scenarios, see [Middle-Tier Client Applications](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)</span></span>  
  
-   <span data-ttu-id="4963b-123">ASP.NET ページ内で操作を呼び出す場合、非同期ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="4963b-123">If you are invoking operations within an ASP.NET page, use asynchronous pages.</span></span>  
  
-   <span data-ttu-id="4963b-124">1 つは、任意のアプリケーションから操作を呼び出す場合は、Windows フォームや Windows Presentation Foundation (WPF) などスレッド。</span><span class="sxs-lookup"><span data-stu-id="4963b-124">If you are invoking operations from any application that is single threaded, such as Windows Forms or Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="4963b-125">イベント ベースの非同期呼び出しモデルを使用すると、結果イベントが UI スレッドで発生するので複数のスレッドを独自に処理する必要がなく、アプリケーションの応答性が向上します。</span><span class="sxs-lookup"><span data-stu-id="4963b-125">When using the event-based asynchronous calling model, the result event is raised on the UI thread, adding responsiveness to the application without requiring you to handle multiple threads yourself.</span></span>  
  
-   <span data-ttu-id="4963b-126">一般に、同期呼び出しと非同期呼び出しのいずれかを選択する場合は、非同期呼び出しを選択します。</span><span class="sxs-lookup"><span data-stu-id="4963b-126">In general, if you have a choice between a synchronous and asynchronous call, choose the asynchronous call.</span></span>  
  
### <a name="implementing-an-asynchronous-service-operation"></a><span data-ttu-id="4963b-127">非同期サービス操作の実装</span><span class="sxs-lookup"><span data-stu-id="4963b-127">Implementing an Asynchronous Service Operation</span></span>  
 <span data-ttu-id="4963b-128">非同期操作は、次の 3 つの方法のいずれかを使用して実装できます。</span><span class="sxs-lookup"><span data-stu-id="4963b-128">Asynchronous operations can be implemented by using one of the three following methods:</span></span>  
  
1.  <span data-ttu-id="4963b-129">タスク ベースの非同期パターン</span><span class="sxs-lookup"><span data-stu-id="4963b-129">The task-based asynchronous pattern</span></span>  
  
2.  <span data-ttu-id="4963b-130">イベント ベースの非同期パターン</span><span class="sxs-lookup"><span data-stu-id="4963b-130">The event-based asynchronous pattern</span></span>  
  
3.  <span data-ttu-id="4963b-131">IAsyncResult 非同期パターン</span><span class="sxs-lookup"><span data-stu-id="4963b-131">The IAsyncResult asynchronous pattern</span></span>  
  
#### <a name="task-based-asynchronous-pattern"></a><span data-ttu-id="4963b-132">タスク ベースの非同期パターン</span><span class="sxs-lookup"><span data-stu-id="4963b-132">Task-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="4963b-133">非同期操作を実装する方法としては、最も直接的でわかりやすいタスク ベースの非同期パターンが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="4963b-133">The task-based asynchronous pattern is the preferred way to implement asynchronous operations because it is the easiest and most straight forward.</span></span> <span data-ttu-id="4963b-134">このメソッドを使用してサービス操作を実装し、タスクの戻り値の型を指定するだけ\<T > ここで T は論理操作によって返される型です。</span><span class="sxs-lookup"><span data-stu-id="4963b-134">To use this method simply implement your service operation and specify a return type of Task\<T>, where T is the type returned by the logical operation.</span></span> <span data-ttu-id="4963b-135">例えば:</span><span class="sxs-lookup"><span data-stu-id="4963b-135">For example:</span></span>  
  
```csharp  
public class SampleService:ISampleService   
{   
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)   
   {   
      return Task<string>.Factory.StartNew(() =>   
      {   
         return msg;   
      });   
   }  
   // ...  
}  
```  
  
 <span data-ttu-id="4963b-136">SampleMethodTaskAsync 操作は、タスクを返します\<文字列 > ため、論理操作は、文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="4963b-136">The SampleMethodTaskAsync operation returns Task\<string> because the logical operation returns a string.</span></span> <span data-ttu-id="4963b-137">タスク ベースの非同期パターンの詳細については、次を参照してください。[タスク ベースの非同期パターン](http://go.microsoft.com/fwlink/?LinkId=232504)です。</span><span class="sxs-lookup"><span data-stu-id="4963b-137">For more information about the task-based asynchronous pattern, see [The Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=232504).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="4963b-138">タスク ベースの非同期パターンを使用している場合、操作の完了を待機している間に例外が発生すると T:System.AggregateException がスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="4963b-138">When using the task-based asynchronous pattern, a T:System.AggregateException may be thrown if an exception occurs while waiting on the completion of the operation.</span></span> <span data-ttu-id="4963b-139">この例外は、クライアントまたはサービスで発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="4963b-139">This exception may occur on the client or services</span></span>  
  
#### <a name="event-based-asynchronous-pattern"></a><span data-ttu-id="4963b-140">イベント ベースの非同期パターン</span><span class="sxs-lookup"><span data-stu-id="4963b-140">Event-Based Asynchronous Pattern</span></span>  
 <span data-ttu-id="4963b-141">イベント ベースの非同期パターンをサポートするサービスには、MethodNameAsync という名前の操作が 1 つ以上含まれます。</span><span class="sxs-lookup"><span data-stu-id="4963b-141">A service that supports the Event-based Asynchronous Pattern will have one or more operations named MethodNameAsync.</span></span> <span data-ttu-id="4963b-142">これらのメソッドは、同期バージョンに対応するもので、現在のスレッドで同じ操作を行います。</span><span class="sxs-lookup"><span data-stu-id="4963b-142">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="4963b-143">クラスには、MethodNameCompleted イベントや MethodNameAsyncCancel メソッド (または単に CancelAsync メソッド) が含まれる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4963b-143">The class may also have a MethodNameCompleted event and it may have a MethodNameAsyncCancel (or simply CancelAsync) method.</span></span> <span data-ttu-id="4963b-144">操作の呼び出し元のクライアントは、操作の完了時に呼び出されるイベント ハンドラーを定義します。</span><span class="sxs-lookup"><span data-stu-id="4963b-144">A client wishing to call the operation will define an event handler to be called when the operation completes,</span></span>  
  
 <span data-ttu-id="4963b-145">次のコードは、イベント ベースの非同期パターンを使用して非同期操作を宣言する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4963b-145">The following code snippet illustrates how to declare asynchronous operations using the event-based asynchronous pattern.</span></span>  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 <span data-ttu-id="4963b-146">イベント ベースの非同期パターンの詳細については、次を参照してください。[イベント ベースの非同期パターン](http://go.microsoft.com/fwlink/?LinkId=232515)です。</span><span class="sxs-lookup"><span data-stu-id="4963b-146">For more information about the Event-based Asynchronous Pattern, see [The Event-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=232515).</span></span>  
  
#### <a name="iasyncresult-asynchronous-pattern"></a><span data-ttu-id="4963b-147">IAsyncResult 非同期パターン</span><span class="sxs-lookup"><span data-stu-id="4963b-147">IAsyncResult Asynchronous Pattern</span></span>  
 <span data-ttu-id="4963b-148">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 非同期プログラミング パターンを使用し、`<Begin>` プロパティが <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> に設定されている `true` メソッドを使用することで、サービス操作を非同期に実装できます。</span><span class="sxs-lookup"><span data-stu-id="4963b-148">A service operation can be implemented in an asynchronous fashion using the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] asynchronous programming pattern and marking the `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true`.</span></span> <span data-ttu-id="4963b-149">この場合の非同期操作は、同期操作と同じ形式でメタデータに公開されます。つまり、要求メッセージとそれに関連する応答メッセージを伴う単独操作として公開されます。</span><span class="sxs-lookup"><span data-stu-id="4963b-149">In this case, the asynchronous operation is exposed in metadata in the same form as a synchronous operation: It is exposed as a single operation with a request message and a correlated response message.</span></span> <span data-ttu-id="4963b-150">このとき、クライアント プログラミング モデルは選択が可能です。</span><span class="sxs-lookup"><span data-stu-id="4963b-150">Client programming models then have a choice.</span></span> <span data-ttu-id="4963b-151">サービスが呼び出されたときに要求/応答メッセージ交換が行われていれば、クライアント プログラミング モデルは、このパターンを同期操作または非同期操作として表すことができます。</span><span class="sxs-lookup"><span data-stu-id="4963b-151">They can represent this pattern as a synchronous operation or as an asynchronous one, so long as when the service is invoked a request-response message exchange takes place.</span></span>  
  
 <span data-ttu-id="4963b-152">一般に、システムの非同期の性質を考えると、スレッドへの依存は避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="4963b-152">In general, with the asynchronous nature of the systems, you should not take a dependency on the threads.</span></span>  <span data-ttu-id="4963b-153">操作のディスパッチ処理のさまざまな段階にデータを渡す最も信頼性の高い方法は、拡張機能を使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="4963b-153">The most reliable way of passing data to various stages of operation dispatch processing is to use extensions.</span></span>  
  
 <span data-ttu-id="4963b-154">例については、次を参照してください。[する方法: 非同期サービス操作を実装する](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)です。</span><span class="sxs-lookup"><span data-stu-id="4963b-154">For an example, see [How to: Implement an Asynchronous Service Operation](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span>  
  
 <span data-ttu-id="4963b-155">クライアント アプリケーションでの呼び出し方法に関係なく、非同期に実行するコントラクト操作 `X` を定義するには次の処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="4963b-155">To define a contract operation `X` that is executed asynchronously regardless of how it is called in the client application:</span></span>  
  
-   <span data-ttu-id="4963b-156">パターン `BeginOperation` と `EndOperation` を使用する 2 つのメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="4963b-156">Define two methods using the pattern `BeginOperation` and `EndOperation`.</span></span>  
  
-   <span data-ttu-id="4963b-157">`BeginOperation` メソッドには操作のための `in` パラメーターと `ref` パラメーターがあり、<xref:System.IAsyncResult> 型を返します。</span><span class="sxs-lookup"><span data-stu-id="4963b-157">The `BeginOperation` method includes `in` and `ref` parameters for the operation and returns an <xref:System.IAsyncResult> type.</span></span>  
  
-   <span data-ttu-id="4963b-158">`EndOperation` メソッドには <xref:System.IAsyncResult> パラメーター、`out` パラメーター、および `ref` パラメーターがあり、操作の戻り値の型を返します。</span><span class="sxs-lookup"><span data-stu-id="4963b-158">The `EndOperation` method includes an <xref:System.IAsyncResult> parameter as well as the `out` and `ref` parameters and returns the operations return type.</span></span>  
  
 <span data-ttu-id="4963b-159">たとえば、次のメソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4963b-159">For example, see the following method.</span></span>  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 <span data-ttu-id="4963b-160">非同期操作を作成するには、2 つのメソッドを次のように記述します。</span><span class="sxs-lookup"><span data-stu-id="4963b-160">To create an asynchronous operation, the two methods would be:</span></span>  
  
```csharp  
[OperationContract(AsyncPattern=true)]IAsyncResult BeginDoWork(string data,                           ref string inout,                           AsyncCallback callback,                           object state);int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>  _Function BeginDoWork(ByVal data As String, _                 ByRef inout As String, _                 ByVal callback As AsyncCallback, _                 ByVal state As Object) _As IAsyncResult Function EndDoWork(ByRef inout As String, _        ByRef outonly As String, _        ByVal result As IAsyncResult) _As Integer  
```  
  
> [!NOTE]
>  <span data-ttu-id="4963b-161"><xref:System.ServiceModel.OperationContractAttribute> 属性は、`BeginDoWork` のメソッドにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="4963b-161">The <xref:System.ServiceModel.OperationContractAttribute> attribute is applied only to the `BeginDoWork` method.</span></span> <span data-ttu-id="4963b-162">生成されるコントラクトには、`DoWork` という名前の WSDL 操作が 1 つ含まれます。</span><span class="sxs-lookup"><span data-stu-id="4963b-162">The resulting contract has one WSDL operation named `DoWork`.</span></span>  
  
### <a name="client-side-asynchronous-invocations"></a><span data-ttu-id="4963b-163">クライアント側の非同期呼び出し</span><span class="sxs-lookup"><span data-stu-id="4963b-163">Client-Side Asynchronous Invocations</span></span>  
 <span data-ttu-id="4963b-164">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント アプリケーションでは、既に説明した 3 つの非同期呼び出しモデルをどれでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="4963b-164">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client application can use any of three asynchronous calling models described previously</span></span>  
  
 <span data-ttu-id="4963b-165">タスク ベースのモデルを使用する場合は、次のコードに示すように、await キーワードを使用して操作を呼び出すだけです。</span><span class="sxs-lookup"><span data-stu-id="4963b-165">When using the task-based model, simply call the operation using the await keyword as shown in the following code snippet.</span></span>  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 <span data-ttu-id="4963b-166">イベント ベースの非同期パターンを使用する場合は、応答の通知を受信するイベント ハンドラーを追加するだけで済み、結果イベントはユーザー インターフェイス スレッドで自動的に発生します。</span><span class="sxs-lookup"><span data-stu-id="4963b-166">Using the event-based asynchronous pattern only requires adding an event handler to receive a notification of the response -- and the resulting event is raised on the user interface thread automatically.</span></span> <span data-ttu-id="4963b-167">このアプローチを使用するには、両方を指定、 **/async**と **/tcv:Version35**コマンドとオプション、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)次のように、例です。</span><span class="sxs-lookup"><span data-stu-id="4963b-167">To use this approach, specify both the **/async** and **/tcv:Version35** command options with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 <span data-ttu-id="4963b-168">これらのオプションを指定すると、Svcutil.exe によって、イベント インフラストラクチャを持つ [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント クラスが生成されます。このインフラストラクチャにより、呼び出し元アプリケーションは、応答を受信して適切なアクションを実行するイベント ハンドラーを実装し、割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="4963b-168">When this is done, Svcutil.exe generates a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client class with the event infrastructure that enables the calling application to implement and assign an event handler to receive the response and take the appropriate action.</span></span> <span data-ttu-id="4963b-169">完全な例では、次を参照してください。[する方法: サービスの操作を非同期に呼び出す](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)です。</span><span class="sxs-lookup"><span data-stu-id="4963b-169">For a complete example, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span>  
  
 <span data-ttu-id="4963b-170">イベント ベースの非同期モデルは、[!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)] でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4963b-170">The event-based asynchronous model, however, is only available in [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)].</span></span> <span data-ttu-id="4963b-171">また、[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] を使用して [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント チャネルを作成した場合は、<xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> でもサポートされません。</span><span class="sxs-lookup"><span data-stu-id="4963b-171">In addition, it is not supported even in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] when a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client channel is created by using a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4963b-172">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアント チャネル オブジェクトを使用する場合、<xref:System.IAsyncResult?displayProperty=nameWithType> オブジェクトを使用して操作を非同期に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4963b-172">With [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client channel objects, you must use <xref:System.IAsyncResult?displayProperty=nameWithType> objects to invoke your operations asynchronously.</span></span> <span data-ttu-id="4963b-173">このアプローチを使用するには指定、 **/async**コマンドとオプション、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)次の例のように、します。</span><span class="sxs-lookup"><span data-stu-id="4963b-173">To use this approach, specify the **/async** command option with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), as in the following example.</span></span>  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 <span data-ttu-id="4963b-174">これにより、対応する `<Begin>` メソッドを持ち、<xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> プロパティが `true` に設定された `<End>` メソッドとして各操作がモデル化されたサービス コントラクトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4963b-174">This generates a service contract in which each operation is modeled as a `<Begin>` method with the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property set to `true` and a corresponding `<End>` method.</span></span> <span data-ttu-id="4963b-175">完全な例を使用するため、<xref:System.ServiceModel.ChannelFactory%601>を参照してください[する方法: 呼び出し操作に非同期的を使用して、チャネル ファクトリ](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)です。</span><span class="sxs-lookup"><span data-stu-id="4963b-175">For a complete example using a <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
 <span data-ttu-id="4963b-176">いずれの場合も、サービスが同期的に実装されていても、アプリケーションは操作を非同期に呼び出すことができます。これは、アプリケーションで同じパターンを使用してローカルの同期メソッドを非同期に呼び出す場合と同様です。</span><span class="sxs-lookup"><span data-stu-id="4963b-176">In either case, applications can invoke an operation asynchronously even if the service is implemented synchronously, in the same way that an application can use the same pattern to invoke asynchronously a local synchronous method.</span></span> <span data-ttu-id="4963b-177">クライアントにとって操作がどのように実装されているかは重要ではありません。応答メッセージが到着すると、その内容がクライアントの非同期 <`End`> メソッドにディスパッチされ、クライアントは情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="4963b-177">How the operation is implemented is not significant to the client; when the response message arrives, its content is dispatched to the client's asynchronous <`End`> method and the client retrieves the information.</span></span>  
  
### <a name="one-way-message-exchange-patterns"></a><span data-ttu-id="4963b-178">一方向メッセージ交換パターン</span><span class="sxs-lookup"><span data-stu-id="4963b-178">One-Way Message Exchange Patterns</span></span>  
 <span data-ttu-id="4963b-179">クライアントまたはサービスが単独で一方向操作 (<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> が `true` に設定されている操作には相関する応答がない) を相手側に送信できる、非同期メッセージ交換パターンを作成することもできます </span><span class="sxs-lookup"><span data-stu-id="4963b-179">You can also create an asynchronous message exchange pattern in which one-way operations (operations for which the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> is `true` have no correlated response) can be sent in either direction by the client or service independently of the other side.</span></span> <span data-ttu-id="4963b-180">(双方向メッセージ交換パターンを一方向メッセージで使用します)。この場合、サービス コントラクトは、両側が非同期呼び出しまたは非同期実装として実装できる一方向メッセージ交換を指定します。また、状況によっては指定しません。</span><span class="sxs-lookup"><span data-stu-id="4963b-180">(This uses the duplex message exchange pattern with one-way messages.) In this case, the service contract specifies a one-way message exchange that either side can implement as asynchronous calls or implementations, or not, as appropriate.</span></span> <span data-ttu-id="4963b-181">一般的に、コントラクトが一方向メッセージ交換の場合、メッセージが送信されるとアプリケーションは応答を待機することなく他の作業を継続できるため、多くの場合、実装が非同期になります。</span><span class="sxs-lookup"><span data-stu-id="4963b-181">Generally, when the contract is an exchange of one-way messages, the implementations can largely be asynchronous because once a message is sent the application does not wait for a reply and can continue doing other work.</span></span>  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a><span data-ttu-id="4963b-182">イベント ベースの非同期クライアントとメッセージ コントラクト</span><span class="sxs-lookup"><span data-stu-id="4963b-182">Event-based Asynchronous Clients and Message Contracts</span></span>  
 <span data-ttu-id="4963b-183">イベント ベースの非同期モデルのデザイン ガイドラインには、複数の値を返す場合に、1 つの値を `Result` プロパティとして返し、残りの値を <xref:System.EventArgs> オブジェクトのプロパティとして返すことが記載されています。</span><span class="sxs-lookup"><span data-stu-id="4963b-183">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="4963b-184">この 1 つの結果として、クライアントがイベント ベースの非同期コマンド オプションを使用してメタデータをインポートし、操作から複数の値が返される場合、既定の <xref:System.EventArgs> オブジェクトは 1 つの値を `Result` プロパティとして返し、残りの値は <xref:System.EventArgs> オブジェクトのプロパティになります。</span><span class="sxs-lookup"><span data-stu-id="4963b-184">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="4963b-185">メッセージ オブジェクトを受信する場合、`Result`プロパティように、そのオブジェクトにプロパティを使用して、返される値であると、 **/messageContract**コマンド オプション。</span><span class="sxs-lookup"><span data-stu-id="4963b-185">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the **/messageContract** command option.</span></span> <span data-ttu-id="4963b-186">これにより、`Result` オブジェクトの <xref:System.EventArgs> プロパティとして応答メッセージを返すシグネチャが生成されます。</span><span class="sxs-lookup"><span data-stu-id="4963b-186">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="4963b-187">すべての内部戻り値は、応答メッセージ オブジェクトのプロパティになります。</span><span class="sxs-lookup"><span data-stu-id="4963b-187">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4963b-188">関連項目</span><span class="sxs-lookup"><span data-stu-id="4963b-188">See Also</span></span>  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
