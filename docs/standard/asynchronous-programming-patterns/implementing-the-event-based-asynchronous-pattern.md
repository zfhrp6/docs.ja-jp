---
title: イベントベースの非同期パターンの実装
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
ms.openlocfilehash: 89de0690c0f9788120f7805b0b63c22ecafa6b9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577360"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="93eb7-102">イベントベースの非同期パターンの実装</span><span class="sxs-lookup"><span data-stu-id="93eb7-102">Implementing the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="93eb7-103">顕著な遅延が発生する可能性がある操作を伴うクラスを作成する場合は、[イベント ベースの非同期パターン](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)を実装することによって、非同期機能を与えることを検討します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-103">If you are writing a class with some operations that may incur noticeable delays, consider giving it asynchronous functionality by implementing [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
 <span data-ttu-id="93eb7-104">イベント ベースの非同期パターンは、非同期機能を持つクラスをパッケージ化するための標準的な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-104">The Event-based Asynchronous Pattern provides a standardized way to package a class that has asynchronous features.</span></span> <span data-ttu-id="93eb7-105"><xref:System.ComponentModel.AsyncOperationManager> などのヘルパー クラスで実装しても、クラスは、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]、コンソール アプリケーション、Windows フォーム アプリケーションを含むすべてのアプリケーション モデルで正常に動作します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-105">If implemented with helper classes like <xref:System.ComponentModel.AsyncOperationManager>, your class will work correctly under any application model, including [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], Console applications, and Windows Forms applications.</span></span>  
  
 <span data-ttu-id="93eb7-106">イベント ベースの非同期パターンを実装する例については、「[方法: イベント ベースの非同期パターンをサポートするコンポーネントの実装](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93eb7-106">For an example that implements the Event-based Asynchronous Pattern, see [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="93eb7-107">単純な非同期操作の場合は、<xref:System.ComponentModel.BackgroundWorker> コンポーネントが適切である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="93eb7-107">For simple asynchronous operations, you may find the <xref:System.ComponentModel.BackgroundWorker> component suitable.</span></span> <span data-ttu-id="93eb7-108"><xref:System.ComponentModel.BackgroundWorker> の詳細については、「[方法: バックグラウンドで操作を実行する](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93eb7-108">For more information about <xref:System.ComponentModel.BackgroundWorker>, see [How to: Run an Operation in the Background](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
 <span data-ttu-id="93eb7-109">次の一覧は、このトピックで説明するイベント ベースの非同期パターンの機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="93eb7-109">The following list describes the features of the Event-based Asynchronous Pattern discussed in this topic.</span></span>  
  
-   <span data-ttu-id="93eb7-110">イベントベースの非同期パターンを実装するチャンス</span><span class="sxs-lookup"><span data-stu-id="93eb7-110">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
  
-   <span data-ttu-id="93eb7-111">非同期メソッドの名前付け</span><span class="sxs-lookup"><span data-stu-id="93eb7-111">Naming Asynchronous Methods</span></span>  
  
-   <span data-ttu-id="93eb7-112">キャンセル処理の任意のサポート</span><span class="sxs-lookup"><span data-stu-id="93eb7-112">Optionally Support Cancellation</span></span>  
  
-   <span data-ttu-id="93eb7-113">IsBusy プロパティの任意のサポート</span><span class="sxs-lookup"><span data-stu-id="93eb7-113">Optionally Support the IsBusy Property</span></span>  
  
-   <span data-ttu-id="93eb7-114">進行状況レポートの任意のサポート</span><span class="sxs-lookup"><span data-stu-id="93eb7-114">Optionally Provide Support for Progress Reporting</span></span>  
  
-   <span data-ttu-id="93eb7-115">増分の結果を返すことの任意のサポート</span><span class="sxs-lookup"><span data-stu-id="93eb7-115">Optionally Provide Support for Returning Incremental Results</span></span>  
  
-   <span data-ttu-id="93eb7-116">メソッドでの Out パラメーターと Ref パラメーターの処理</span><span class="sxs-lookup"><span data-stu-id="93eb7-116">Handling Out and Ref Parameters in Methods</span></span>  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a><span data-ttu-id="93eb7-117">イベントベースの非同期パターンを実装するチャンス</span><span class="sxs-lookup"><span data-stu-id="93eb7-117">Opportunities for Implementing the Event-based Asynchronous Pattern</span></span>  
 <span data-ttu-id="93eb7-118">以下に該当する場合は、イベントベースの非同期パターンの実装を検討します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-118">Consider implementing the Event-based Asynchronous Pattern when:</span></span>  
  
-   <span data-ttu-id="93eb7-119">クラスのクライアントには、非同期操作に使用できる <xref:System.Threading.WaitHandle> と <xref:System.IAsyncResult> オブジェクトは必要ありません。つまり、ポーリング、<xref:System.Threading.WaitHandle.WaitAll%2A> または <xref:System.Threading.WaitHandle.WaitAny%2A> は、クライアントによってビルドされる必要があるということです。</span><span class="sxs-lookup"><span data-stu-id="93eb7-119">Clients of your class do not need <xref:System.Threading.WaitHandle> and <xref:System.IAsyncResult> objects available for asynchronous operations, meaning that polling and <xref:System.Threading.WaitHandle.WaitAll%2A> or <xref:System.Threading.WaitHandle.WaitAny%2A> will need to be built up by the client.</span></span>  
  
-   <span data-ttu-id="93eb7-120">クライアントでの非同期操作を、使い慣れたイベント/デリゲート モデルを使用して管理したい。</span><span class="sxs-lookup"><span data-stu-id="93eb7-120">You want asynchronous operations to be managed by the client with the familiar event/delegate model.</span></span>  
  
 <span data-ttu-id="93eb7-121">どの操作も非同期を実装するための候補になりますが、長い待機時間が予想される操作を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="93eb7-121">Any operation is a candidate for an asynchronous implementation, but those you expect to incur long latencies should be considered.</span></span> <span data-ttu-id="93eb7-122">特に適切なのは、クライアントがメソッドを呼び出し、完了時に通知を受け取ること以外の介入を必要としない操作です。</span><span class="sxs-lookup"><span data-stu-id="93eb7-122">Especially appropriate are operations in which clients call a method and are notified on completion, with no further intervention required.</span></span> <span data-ttu-id="93eb7-123">継続的に実行され、進捗状況、増分結果、または状態の変更をクライアントに定期的に通知する操作も適しています。</span><span class="sxs-lookup"><span data-stu-id="93eb7-123">Also appropriate are operations which run continuously, periodically notifying clients of progress, incremental results, or state changes.</span></span>  
  
 <span data-ttu-id="93eb7-124">イベント ベースの非同期パターンをいつサポートするかを決定することの詳細については、「[Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)」 (イベントベースの非同期パターンをいつ実装するかの決定) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93eb7-124">For more information on deciding when to support the Event-based Asynchronous Pattern, see [Deciding When to Implement the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="naming-asynchronous-methods"></a><span data-ttu-id="93eb7-125">非同期メソッドの名前付け</span><span class="sxs-lookup"><span data-stu-id="93eb7-125">Naming Asynchronous Methods</span></span>  
 <span data-ttu-id="93eb7-126">対応する非同期メソッドを用意する同期メソッド *MethodName* に対して、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="93eb7-126">For each synchronous method *MethodName* for which you want to provide an asynchronous counterpart:</span></span>  
  
 <span data-ttu-id="93eb7-127">以下を実行する *MethodName***Async** メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-127">Define a *MethodName***Async** method that:</span></span>  
  
-   <span data-ttu-id="93eb7-128">`void` を返します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-128">Returns `void`.</span></span>  
  
-   <span data-ttu-id="93eb7-129">*MethodName* メソッドと同じパラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="93eb7-129">Takes the same parameters as the *MethodName* method.</span></span>  
  
-   <span data-ttu-id="93eb7-130">複数の呼び出しを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="93eb7-130">Accepts multiple invocations.</span></span>  
  
 <span data-ttu-id="93eb7-131">必要に応じて、*MethodName***Async** と同一の *MethodName***Async** オーバーロードを定義しますが、`userState` と呼ばれる追加のオブジェクト値パラメーターを使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-131">Optionally define a *MethodName***Async** overload, identical to *MethodName***Async**, but with an additional object-valued parameter called `userState`.</span></span> <span data-ttu-id="93eb7-132">これは、メソッドの複数の同時呼び出しを管理するために実行します。この場合、メソッドの呼び出しを区別するために `userState` 値がすべてのイベント ハンドラーに返されます。</span><span class="sxs-lookup"><span data-stu-id="93eb7-132">Do this if you're prepared to manage multiple concurrent invocations of your method, in which case the `userState` value will be delivered back to all event handlers to distinguish invocations of the method.</span></span> <span data-ttu-id="93eb7-133">単純に後で取得するためにユーザーの状態を格納する場所として実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="93eb7-133">You may also choose to do this simply as a place to store user state for later retrieval.</span></span>  
  
 <span data-ttu-id="93eb7-134">個別の *MethodName***Async** メソッドのシグネチャに対して、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-134">For each separate *MethodName***Async** method signature:</span></span>  
  
1.  <span data-ttu-id="93eb7-135">メソッドと同じクラス内に次のイベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-135">Define the following event in the same class as the method:</span></span>  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  <span data-ttu-id="93eb7-136">次のデリゲートと <xref:System.ComponentModel.AsyncCompletedEventArgs> を定義します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-136">Define the following delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs>.</span></span> <span data-ttu-id="93eb7-137">これらは、クラス自体の外部に定義される可能性がありますが、同じ名前空間に定義されます。</span><span class="sxs-lookup"><span data-stu-id="93eb7-137">These will likely be defined outside of the class itself, but in the same namespace.</span></span>  
  
    ```vb  
    Public Delegate Sub MethodNameCompletedEventHandler( _  
        ByVal sender As Object, _  
        ByVal e As MethodNameCompletedEventArgs)  
  
    Public Class MethodNameCompletedEventArgs  
        Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As MyReturnType  
    End Property  
    ```  
  
    ```csharp  
    public delegate void MethodNameCompletedEventHandler(object sender,   
        MethodNameCompletedEventArgs e);  
  
    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
    {  
        public MyReturnType Result { get; }  
    }  
    ```  
  
    -   <span data-ttu-id="93eb7-138">*MethodName***CompletedEventArgs** クラスで、フィールドではなくメンバーを読み取り専用プロパティとして公開していることを確認します。これは、フィールドはデータ バインドを妨げるためです。</span><span class="sxs-lookup"><span data-stu-id="93eb7-138">Ensure that the *MethodName***CompletedEventArgs** class exposes its members as read-only properties, and not fields, as fields prevent data binding.</span></span>  
  
    -   <span data-ttu-id="93eb7-139">結果を生成しないメソッドに <xref:System.ComponentModel.AsyncCompletedEventArgs> の派生クラスを定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="93eb7-139">Do not define any <xref:System.ComponentModel.AsyncCompletedEventArgs>-derived classes for methods that do not produce results.</span></span> <span data-ttu-id="93eb7-140">単純に <xref:System.ComponentModel.AsyncCompletedEventArgs> のインスタンス自体を使用します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-140">Simply use an instance of <xref:System.ComponentModel.AsyncCompletedEventArgs> itself.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="93eb7-141">実行可能かつ適切な場合、デリゲートと <xref:System.ComponentModel.AsyncCompletedEventArgs> 型を再利用することはまったく問題ありません。</span><span class="sxs-lookup"><span data-stu-id="93eb7-141">It is perfectly acceptable, when feasible and appropriate, to reuse delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> types.</span></span> <span data-ttu-id="93eb7-142">この場合、特定のデリゲートと <xref:System.ComponentModel.AsyncCompletedEventArgs> が 1 つのメソッドに関連付けられることがないため、メソッド名のような名前の一貫性はなくなります。</span><span class="sxs-lookup"><span data-stu-id="93eb7-142">In this case, the naming will not be as consistent with the method name, since a given delegate and <xref:System.ComponentModel.AsyncCompletedEventArgs> won't be tied to a single method.</span></span>  
  
## <a name="optionally-support-cancellation"></a><span data-ttu-id="93eb7-143">キャンセル処理の任意のサポート</span><span class="sxs-lookup"><span data-stu-id="93eb7-143">Optionally Support Cancellation</span></span>  
 <span data-ttu-id="93eb7-144">クラスで非同期操作のキャンセルをサポートする場合は、以下に示すようにキャンセルをクライアントに公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93eb7-144">If your class will support canceling asynchronous operations, cancellation should be exposed to the client as described below.</span></span> <span data-ttu-id="93eb7-145">キャンセルのサポートを定義する前に、以下の 2 点について判断する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="93eb7-145">Note that there are two decision points that need to be reached before defining your cancellation support:</span></span>  
  
-   <span data-ttu-id="93eb7-146">今後の予想される追加機能を含め、クラスには、キャンセルをサポートする非同期操作が 1 つだけあるかどうか。</span><span class="sxs-lookup"><span data-stu-id="93eb7-146">Does your class, including future anticipated additions to it, have only one asynchronous operation that supports cancellation?</span></span>  
  
-   <span data-ttu-id="93eb7-147">キャンセルをサポートする非同期操作が、複数の保留中の操作をサポートできるかどうか。</span><span class="sxs-lookup"><span data-stu-id="93eb7-147">Can the asynchronous operations that support cancellation support multiple pending operations?</span></span> <span data-ttu-id="93eb7-148">これは、*MethodName***Async** メソッドが `userState` パラメーターを受け取り、いずれかの呼び出しが終了するまで待機する前に、複数の呼び出しを許可できるかどうかを意味します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-148">That is, does the *MethodName***Async** method take a `userState` parameter, and does it allow multiple invocations before waiting for any to finish?</span></span>  
  
 <span data-ttu-id="93eb7-149">これら 2 つの質問に対する回答を次の表に当てはめて、キャンセル メソッドで使用するシグネチャを決定します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-149">Use the answers to these two questions in the table below to determine what the signature for your cancellation method should be.</span></span>  
  
### <a name="visual-basic"></a><span data-ttu-id="93eb7-150">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93eb7-150">Visual Basic</span></span>  
  
||<span data-ttu-id="93eb7-151">複数の同時操作をサポート</span><span class="sxs-lookup"><span data-stu-id="93eb7-151">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="93eb7-152">一度に 1 つだけの操作</span><span class="sxs-lookup"><span data-stu-id="93eb7-152">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="93eb7-153">クラス全体で 1 つの非同期操作</span><span class="sxs-lookup"><span data-stu-id="93eb7-153">One Async Operation in entire class</span></span>|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|<span data-ttu-id="93eb7-154">クラスの複数の非同期操作</span><span class="sxs-lookup"><span data-stu-id="93eb7-154">Multiple Async Operations in class</span></span>|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a><span data-ttu-id="93eb7-155">C#</span><span class="sxs-lookup"><span data-stu-id="93eb7-155">C#</span></span>  
  
||<span data-ttu-id="93eb7-156">複数の同時操作をサポート</span><span class="sxs-lookup"><span data-stu-id="93eb7-156">Multiple Simultaneous Operations Supported</span></span>|<span data-ttu-id="93eb7-157">一度に 1 つだけの操作</span><span class="sxs-lookup"><span data-stu-id="93eb7-157">Only One Operation at a Time</span></span>|  
|------|------------------------------------------------|----------------------------------|  
|<span data-ttu-id="93eb7-158">クラス全体で 1 つの非同期操作</span><span class="sxs-lookup"><span data-stu-id="93eb7-158">One Async Operation in entire class</span></span>|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|<span data-ttu-id="93eb7-159">クラスの複数の非同期操作</span><span class="sxs-lookup"><span data-stu-id="93eb7-159">Multiple Async Operations in class</span></span>|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 <span data-ttu-id="93eb7-160">`CancelAsync(object userState)` メソッドを定義する場合、クライアントは、1 つの非同期メソッドのすべての呼び出しの間だけではなく、オブジェクトに対して呼び出されたすべての非同期メソッドの間で区別できるようにする状態値を慎重に選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93eb7-160">If you define the `CancelAsync(object userState)` method, clients must be careful when choosing their state values to make them capable of distinguishing among all asynchronous methods invoked on the object, and not just between all invocations of a single asynchronous method.</span></span>  
  
 <span data-ttu-id="93eb7-161">1 つの非同期操作のバージョンの *MethodName***AsyncCancel** という名前は、Visual Studio の IntelliSense のようなデザイン環境でそのメソッドをより簡単に検出できるようにするために、このように決定されています。</span><span class="sxs-lookup"><span data-stu-id="93eb7-161">The decision to name the single-async-operation version *MethodName***AsyncCancel** is based on being able to more easily discover the method in a design environment like Visual Studio's IntelliSense.</span></span> <span data-ttu-id="93eb7-162">これにより、関連するメンバーがグループ化され、非同期機能とは無関係の他のメンバーとは区別されます。</span><span class="sxs-lookup"><span data-stu-id="93eb7-162">This groups the related members and distinguishes them from other members that have nothing to do with asynchronous functionality.</span></span> <span data-ttu-id="93eb7-163">今後のバージョンで非同期操作を追加する可能性がある場合は、`CancelAsync` を定義することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="93eb7-163">If you expect that there may be additional asynchronous operations added in subsequent versions, it is better to define `CancelAsync`.</span></span>  
  
 <span data-ttu-id="93eb7-164">同じクラスに上の表の複数のメソッドを定義しないでください。</span><span class="sxs-lookup"><span data-stu-id="93eb7-164">Do not define multiple methods from the table above in the same class.</span></span> <span data-ttu-id="93eb7-165">それは意味のない行為であるか、メソッドの増加によってクラス インターフェイスがわかりにくくなります。</span><span class="sxs-lookup"><span data-stu-id="93eb7-165">That will not make sense, or it will clutter the class interface with a proliferation of methods.</span></span>  
  
 <span data-ttu-id="93eb7-166">これらのメソッドは、通常は直ちに結果が戻り、操作が実際にキャンセルされる場合もキャンセルされない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="93eb7-166">These methods typically will return immediately, and the operation may or may not actually cancel.</span></span> <span data-ttu-id="93eb7-167">*MethodName***Completed** イベント用のイベント ハンドラーでは、*MethodName***CompletedEventArgs** オブジェクトに `Cancelled` フィールドが含まれます。クライアントはこれを使用して、キャンセルが発生したかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="93eb7-167">In the event handler for the *MethodName***Completed** event, the *MethodName***CompletedEventArgs** object contains a `Cancelled` field, which clients can use to determine whether the cancellation occurred.</span></span>  
  
 <span data-ttu-id="93eb7-168">「[イベントベースの非同期パターンを実装するための推奨される手順](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)」に説明されているキャンセルのセマンティクスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="93eb7-168">Abide by the cancellation semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-support-the-isbusy-property"></a><span data-ttu-id="93eb7-169">IsBusy プロパティの任意のサポート</span><span class="sxs-lookup"><span data-stu-id="93eb7-169">Optionally Support the IsBusy Property</span></span>  
 <span data-ttu-id="93eb7-170">クラスが複数の同時呼び出しをサポートしない場合は、`IsBusy` プロパティを公開することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="93eb7-170">If your class does not support multiple concurrent invocations, consider exposing an `IsBusy` property.</span></span> <span data-ttu-id="93eb7-171">開発者は、このプロパティによって、*MethodName***Async** メソッドが *MethodName***Async** メソッドからの例外をキャッチせずに実行されているかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="93eb7-171">This allows developers to determine whether a *MethodName***Async** method is running without catching an exception from the *MethodName***Async** method.</span></span>  
  
 <span data-ttu-id="93eb7-172">「[イベントベースの非同期パターンを実装するための推奨される手順](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)」に説明されている `IsBusy` のセマンティクスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="93eb7-172">Abide by the `IsBusy` semantics described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-progress-reporting"></a><span data-ttu-id="93eb7-173">進行状況レポートの任意のサポート</span><span class="sxs-lookup"><span data-stu-id="93eb7-173">Optionally Provide Support for Progress Reporting</span></span>  
 <span data-ttu-id="93eb7-174">非同期操作の操作中に進行状況を報告することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="93eb7-174">It is frequently desirable for an asynchronous operation to report progress during its operation.</span></span> <span data-ttu-id="93eb7-175">イベント ベースの非同期パターンには、これを行うためのガイドラインがあります。</span><span class="sxs-lookup"><span data-stu-id="93eb7-175">The Event-based Asynchronous Pattern provides a guideline for doing so.</span></span>  
  
-   <span data-ttu-id="93eb7-176">必要に応じて、非同期操作によって発生し、適切なスレッドで呼び出されるイベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-176">Optionally define an event to be raised by the asynchronous operation and invoked on the appropriate thread.</span></span> <span data-ttu-id="93eb7-177"><xref:System.ComponentModel.ProgressChangedEventArgs> オブジェクトは、0 ～ 100 の範囲であることが期待されている整数値の進行状況インジケーターを伝達します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-177">The <xref:System.ComponentModel.ProgressChangedEventArgs> object carries an integer-valued progress indicator that is expected to be between 0 and 100.</span></span>  
  
-   <span data-ttu-id="93eb7-178">このイベントには、次のように名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="93eb7-178">Name this event as follows:</span></span>  
  
    -   <span data-ttu-id="93eb7-179">`ProgressChanged`: クラスに複数の非同期操作がある (または将来のバージョンで複数の非同期操作を含めることが予想される) 場合。</span><span class="sxs-lookup"><span data-stu-id="93eb7-179">`ProgressChanged` if the class has multiple asynchronous operations (or is expected to grow to include multiple asynchronous operations in future versions);</span></span>  
  
    -   <span data-ttu-id="93eb7-180">*MethodName***ProgressChanged**: クラスに非同期操作が 1 つだけある場合。</span><span class="sxs-lookup"><span data-stu-id="93eb7-180">*MethodName***ProgressChanged** if the class has a single asynchronous operation.</span></span>  
  
     <span data-ttu-id="93eb7-181">この名前の付け方は、「キャンセルの任意のサポート」セクションで説明した、キャンセル メソッドに対する方法と対応しています。</span><span class="sxs-lookup"><span data-stu-id="93eb7-181">This naming choice parallels that made for the cancellation method, as described in the Optionally Support Cancellation section.</span></span>  
  
 <span data-ttu-id="93eb7-182">このイベントは、<xref:System.ComponentModel.ProgressChangedEventHandler> デリゲート シグネチャと <xref:System.ComponentModel.ProgressChangedEventArgs> クラスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93eb7-182">This event should use the <xref:System.ComponentModel.ProgressChangedEventHandler> delegate signature and the <xref:System.ComponentModel.ProgressChangedEventArgs> class.</span></span> <span data-ttu-id="93eb7-183">別の方法として、ドメイン固有の進行状況インジケーター (読み取られたバイト数やダウンロード操作の合計バイト数など) を提供できる場合は、<xref:System.ComponentModel.ProgressChangedEventArgs> の派生クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-183">Alternatively, if a more domain-specific progress indicator can be provided (for instance, bytes read and total bytes for a download operation), then you should define a derived class of <xref:System.ComponentModel.ProgressChangedEventArgs>.</span></span>  
  
 <span data-ttu-id="93eb7-184">サポートされる非同期メソッドの数にかかわらず、クラスの `ProgressChanged` または *MethodName***ProgressChanged** イベントは 1 つしかないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="93eb7-184">Note that there is only one `ProgressChanged` or *MethodName***ProgressChanged** event for the class, regardless of the number of asynchronous methods it supports.</span></span> <span data-ttu-id="93eb7-185">クライアントは、*MethodName***Async** メソッドに渡される `userState` オブジェクトを使用して、複数の同時操作に対する進行状況の更新を区別することが期待されています。</span><span class="sxs-lookup"><span data-stu-id="93eb7-185">Clients are expected to use the `userState` object that is passed to the *MethodName***Async** methods to distinguish among progress updates on multiple concurrent operations.</span></span>  
  
 <span data-ttu-id="93eb7-186">複数の操作で進行状況がサポートされ、それぞれが異なる進行状況インジケーターを返す状況が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="93eb7-186">There may be situations in which multiple operations support progress and each returns a different indicator for progress.</span></span> <span data-ttu-id="93eb7-187">この場合は、1 つの `ProgressChanged` イベントでは不適切であり、複数の `ProgressChanged` のサポートを検討することができます。</span><span class="sxs-lookup"><span data-stu-id="93eb7-187">In this case, a single `ProgressChanged` event is not appropriate, and you may consider supporting multiple `ProgressChanged` events.</span></span> <span data-ttu-id="93eb7-188">この場合は、各 *MethodName***Async** メソッドに対して、*MethodName***ProgressChanged** の名前付けパターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-188">In this case use a naming pattern of *MethodName***ProgressChanged** for each *MethodName***Async** method.</span></span>  
  
 <span data-ttu-id="93eb7-189">「[イベントベースの非同期パターンを実装するための推奨される手順](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)」に説明されている進行状況報告のセマンティクスに従ってください。</span><span class="sxs-lookup"><span data-stu-id="93eb7-189">Abide by the progress-reporting semantics described [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a><span data-ttu-id="93eb7-190">増分の結果を返すことの任意のサポート</span><span class="sxs-lookup"><span data-stu-id="93eb7-190">Optionally Provide Support for Returning Incremental Results</span></span>  
 <span data-ttu-id="93eb7-191">場合によっては、非同期操作が完了する前に、増分結果が返ることがあります。</span><span class="sxs-lookup"><span data-stu-id="93eb7-191">Sometimes an asynchronous operation can return incremental results prior to completion.</span></span> <span data-ttu-id="93eb7-192">このシナリオをサポートするために使用できるオプションは多数あります。</span><span class="sxs-lookup"><span data-stu-id="93eb7-192">There are a number of options that can be used to support this scenario.</span></span> <span data-ttu-id="93eb7-193">以下に、いくつかの例を示します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-193">Some examples follow.</span></span>  
  
### <a name="single-operation-class"></a><span data-ttu-id="93eb7-194">単一操作クラス</span><span class="sxs-lookup"><span data-stu-id="93eb7-194">Single-operation Class</span></span>  
 <span data-ttu-id="93eb7-195">クラスが 1 つの非同期操作のみをサポートし、その操作が増分結果を返すことができる場合は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="93eb7-195">If your class only supports a single asynchronous operation, and that operation is able to return incremental results, then:</span></span>  
  
-   <span data-ttu-id="93eb7-196"><xref:System.ComponentModel.ProgressChangedEventArgs> 型を増分結果データを伝達するように拡張し、この拡張されたデータを使用する *MethodName***ProgressChanged** イベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-196">Extend the <xref:System.ComponentModel.ProgressChangedEventArgs> type to carry the incremental result data, and define a *MethodName***ProgressChanged** event with this extended data.</span></span>  
  
-   <span data-ttu-id="93eb7-197">報告する増分結果があるときに、この *MethodName***ProgressChanged** イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="93eb7-197">Raise this *MethodName***ProgressChanged** event when there is an incremental result to report.</span></span>  
  
 <span data-ttu-id="93eb7-198">このソリューションは、*MethodName***ProgressChanged** イベントと同じように、同じイベントの発生で "すべての操作" に対して増分結果を返しても何の問題もないため、特に単一非同期操作のクラスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="93eb7-198">This solution applies specifically to a single-async-operation class because there is no problem with the same event occurring to return incremental results on "all operations", as the *MethodName***ProgressChanged** event does.</span></span>  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a><span data-ttu-id="93eb7-199">同じ型の増分結果を持つ複数操作クラス</span><span class="sxs-lookup"><span data-stu-id="93eb7-199">Multiple-operation Class with Homogeneous Incremental Results</span></span>  
 <span data-ttu-id="93eb7-200">この場合、クラスは、それぞれが増分結果を返すことができる複数の非同期メソッドをサポートし、増分結果はすべて同じ型のデータを持っています。</span><span class="sxs-lookup"><span data-stu-id="93eb7-200">In this case, your class supports multiple asynchronous methods, each capable of returning incremental results, and these incremental results all have the same type of data.</span></span>  
  
 <span data-ttu-id="93eb7-201">同じ <xref:System.EventArgs> 構造体がすべての増分結果で機能するため、上記の単一操作クラスで説明したモデルに従います。</span><span class="sxs-lookup"><span data-stu-id="93eb7-201">Follow the model described above for single-operation classes, as the same <xref:System.EventArgs> structure will work for all incremental results.</span></span> <span data-ttu-id="93eb7-202">複数の非同期メソッドに適用するため、*MethodName***ProgressChanged** イベントの代わりに `ProgressChanged` イベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-202">Define a `ProgressChanged` event instead of a *MethodName***ProgressChanged** event, since it applies to multiple asynchronous methods.</span></span>  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a><span data-ttu-id="93eb7-203">異なる型の増分結果を持つ複数操作クラス</span><span class="sxs-lookup"><span data-stu-id="93eb7-203">Multiple-operation Class with Heterogeneous Incremental Results</span></span>  
 <span data-ttu-id="93eb7-204">クラスが複数の非同期メソッドをサポートし、それぞれが異なる型のデータを返す場合は、以下を行います。</span><span class="sxs-lookup"><span data-stu-id="93eb7-204">If your class supports multiple asynchronous methods, each returning a different type of data, you should:</span></span>  
  
-   <span data-ttu-id="93eb7-205">増分結果の報告と進行状況の報告を分離します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-205">Separate your incremental result reporting from your progress reporting.</span></span>  
  
-   <span data-ttu-id="93eb7-206">各非同期メソッドの増分結果データを処理する個別の *MethodName***ProgressChanged** イベントを、適切な <xref:System.EventArgs> で定義します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-206">Define a separate *MethodName***ProgressChanged** event with appropriate <xref:System.EventArgs> for each asynchronous method to handle that method's incremental result data.</span></span>  
  
 <span data-ttu-id="93eb7-207">「[イベントベースの非同期パターンを実装するための推奨される手順](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)」に説明されているように、そのイベント ハンドラーを適切なスレッドで呼び出します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-207">Invoke that event handler on the appropriate thread as described in [Best Practices for Implementing the Event-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a><span data-ttu-id="93eb7-208">メソッドでの Out パラメーターと Ref パラメーターの処理</span><span class="sxs-lookup"><span data-stu-id="93eb7-208">Handling Out and Ref Parameters in Methods</span></span>  
 <span data-ttu-id="93eb7-209">一般に、.NET Framework では、`out` と `ref` の使用は避けることを推奨していますが、それらが存在するときのルールを次に示します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-209">Although the use of `out` and `ref` is, in general, discouraged in the .NET Framework, here are the rules to follow when they are present:</span></span>  
  
 <span data-ttu-id="93eb7-210">非同期メソッド *MethodName* の場合:</span><span class="sxs-lookup"><span data-stu-id="93eb7-210">Given a synchronous method *MethodName*:</span></span>  
  
-   <span data-ttu-id="93eb7-211">*MethodName* に対する `out` パラメーターは、*MethodName***Async** の一部にしないでください。代わりに、*MethodName* での同等のパラメーターと同じ名前の *MethodName***CompletedEventArgs** の一部にする必要があります (より適切な名前がない限り)。</span><span class="sxs-lookup"><span data-stu-id="93eb7-211">`out` parameters to *MethodName* should not be part of *MethodName***Async**. Instead, they should be part of *MethodName***CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
-   <span data-ttu-id="93eb7-212">*MethodName* に対する `ref` パラメーターは、*MethodName***Async** の一部として出現し、*MethodName* での同等のパラメーターと同じ名前の *MethodName***CompletedEventArgs** の一部として出現する必要があります (より適切な名前がない限り)。</span><span class="sxs-lookup"><span data-stu-id="93eb7-212">`ref` parameters to *MethodName* should appear as part of *MethodName***Async**, and as part of *MethodName***CompletedEventArgs** with the same name as its parameter equivalent in *MethodName* (unless there is a more appropriate name).</span></span>  
  
 <span data-ttu-id="93eb7-213">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="93eb7-213">For example, given:</span></span>  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 <span data-ttu-id="93eb7-214">非同期メソッドとその <xref:System.ComponentModel.AsyncCompletedEventArgs> クラスは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="93eb7-214">Your asynchronous method and its <xref:System.ComponentModel.AsyncCompletedEventArgs> class would look like this:</span></span>  
  
```vb  
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)  
  
Public Class MethodNameCompletedEventArgs  
    Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As Integer   
    End Property  
    Public ReadOnly Property Arg2() As String   
    End Property  
    Public ReadOnly Property Arg3() As String   
    End Property  
End Class  
```  
  
```csharp  
public void MethodNameAsync(string arg1, string arg2);  
  
public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
{  
    public int Result { get; };  
    public string Arg2 { get; };  
    public string Arg3 { get; };  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="93eb7-215">参照</span><span class="sxs-lookup"><span data-stu-id="93eb7-215">See Also</span></span>  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [<span data-ttu-id="93eb7-216">方法: イベントベースの非同期パターンをサポートするコンポーネントを実装する</span><span class="sxs-lookup"><span data-stu-id="93eb7-216">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="93eb7-217">方法: バックグラウンドで操作を実行する</span><span class="sxs-lookup"><span data-stu-id="93eb7-217">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="93eb7-218">方法: バックグラウンド操作を使用するフォームを実装する</span><span class="sxs-lookup"><span data-stu-id="93eb7-218">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="93eb7-219">イベントベースの非同期パターンをいつ実装するかの決定</span><span class="sxs-lookup"><span data-stu-id="93eb7-219">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="93eb7-220">イベント ベースの非同期パターンを使用したマルチスレッド プログラミング</span><span class="sxs-lookup"><span data-stu-id="93eb7-220">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [<span data-ttu-id="93eb7-221">イベントベースの非同期パターンを実装するための推奨される手順</span><span class="sxs-lookup"><span data-stu-id="93eb7-221">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
