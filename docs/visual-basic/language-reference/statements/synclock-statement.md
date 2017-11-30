---
title: "SyncLock ステートメント"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c826e1ba592dfc4f2899a26102466d2e7df54f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="synclock-statement"></a><span data-ttu-id="1bd95-102">SyncLock ステートメント</span><span class="sxs-lookup"><span data-stu-id="1bd95-102">SyncLock Statement</span></span>
<span data-ttu-id="1bd95-103">ブロックを実行する前にステートメント ブロックの排他ロックを取得します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd95-104">構文</span><span class="sxs-lookup"><span data-stu-id="1bd95-104">Syntax</span></span>  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="1bd95-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="1bd95-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="1bd95-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="1bd95-106">Required.</span></span> <span data-ttu-id="1bd95-107">オブジェクト参照に評価される式。</span><span class="sxs-lookup"><span data-stu-id="1bd95-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="1bd95-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1bd95-108">Optional.</span></span> <span data-ttu-id="1bd95-109">ロックが取得されたときに実行されるステートメントのブロックです。</span><span class="sxs-lookup"><span data-stu-id="1bd95-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="1bd95-110">終了、`SyncLock`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="1bd95-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bd95-111">コメント</span><span class="sxs-lookup"><span data-stu-id="1bd95-111">Remarks</span></span>  
 <span data-ttu-id="1bd95-112">`SyncLock`ステートメントが複数のスレッドを実行しない、ステートメント ブロック、同時にことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="1bd95-113">`SyncLock`各スレッドが実行している他のスレッドがなくなるまで、ブロックを入力するを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="1bd95-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="1bd95-114">最も一般的な使用`SyncLock`から複数のスレッドで同時に更新されているデータを保護することです。</span><span class="sxs-lookup"><span data-stu-id="1bd95-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="1bd95-115">場合は、データを操作するステートメントは、中断することがなく完了に移動する必要があります、その内部配置、`SyncLock`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="1bd95-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="1bd95-116">排他ロックによって保護されているステートメント ブロックが呼び出される場合があります、*クリティカル セクション*です。</span><span class="sxs-lookup"><span data-stu-id="1bd95-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="1bd95-117">ルール</span><span class="sxs-lookup"><span data-stu-id="1bd95-117">Rules</span></span>  
  
-   <span data-ttu-id="1bd95-118">分岐します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-118">Branching.</span></span> <span data-ttu-id="1bd95-119">内に分岐することはできません、`SyncLock`ブロックの外側からブロックされます。</span><span class="sxs-lookup"><span data-stu-id="1bd95-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
-   <span data-ttu-id="1bd95-120">ロック オブジェクト値です。</span><span class="sxs-lookup"><span data-stu-id="1bd95-120">Lock Object Value.</span></span> <span data-ttu-id="1bd95-121">値`lockobject`することはできません`Nothing`です。</span><span class="sxs-lookup"><span data-stu-id="1bd95-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="1bd95-122">使用する前に、ロック オブジェクトを作成する必要があります、`SyncLock`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1bd95-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="1bd95-123">値を変更することはできません`lockobject`の実行中に、`SyncLock`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="1bd95-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="1bd95-124">このメカニズムでは、ロック オブジェクトが変化が必要です。</span><span class="sxs-lookup"><span data-stu-id="1bd95-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
-   <span data-ttu-id="1bd95-125">使用することはできません、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)の演算子、`SyncLock`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="1bd95-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="1bd95-126">動作</span><span class="sxs-lookup"><span data-stu-id="1bd95-126">Behavior</span></span>  
  
-   <span data-ttu-id="1bd95-127">メカニズムです。</span><span class="sxs-lookup"><span data-stu-id="1bd95-127">Mechanism.</span></span> <span data-ttu-id="1bd95-128">スレッドに達したとき、`SyncLock`ステートメントでは、評価、`lockobject`式、式によって返されるオブジェクトの排他ロックを取得するまで実行を中断します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="1bd95-129">別のスレッドに達したとき、`SyncLock`ステートメントでは、これはロックを取得、最初のスレッドが実行されるまで、`End SyncLock`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="1bd95-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
-   <span data-ttu-id="1bd95-130">保護されるデータ。</span><span class="sxs-lookup"><span data-stu-id="1bd95-130">Protected Data.</span></span> <span data-ttu-id="1bd95-131">場合`lockobject`は、`Shared`変数、排他ロック クラスの任意のインスタンス内のスレッドが実行されないように、`SyncLock`他のスレッドを実行している場合にブロックします。</span><span class="sxs-lookup"><span data-stu-id="1bd95-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="1bd95-132">これは、すべてのインスタンス間で共有されているデータを保護します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="1bd95-133">場合`lockobject`インスタンス変数は、(いない`Shared`)、ロックにより、スレッドの実行から現在のインスタンスで実行できなくなります、`SyncLock`で、同じインスタンス内の別のスレッドと同時にブロックします。</span><span class="sxs-lookup"><span data-stu-id="1bd95-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="1bd95-134">これは、個別のインスタンスで保持されているデータを保護します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-134">This protects data maintained by the individual instance.</span></span>  
  
-   <span data-ttu-id="1bd95-135">取得と解放します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-135">Acquisition and Release.</span></span> <span data-ttu-id="1bd95-136">A`SyncLock`ブロックの動作と同様に、`Try...Finally`を構築、`Try`ブロックに排他ロックを取得する`lockobject`と`Finally`ブロックを解放します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="1bd95-137">このため、`SyncLock`ブロック、ブロックを終了する方法に関係なく、ロックの解放を保証します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="1bd95-138">これは、未処理の例外場合でも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="1bd95-138">This is true even in the case of an unhandled exception.</span></span>  
  
-   <span data-ttu-id="1bd95-139">フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="1bd95-139">Framework Calls.</span></span> <span data-ttu-id="1bd95-140">`SyncLock`ブロックを取得し、呼び出すことによって、排他ロックを解放、`Enter`と`Exit`のメソッド、`Monitor`クラス内で、<xref:System.Threading>名前空間。</span><span class="sxs-lookup"><span data-stu-id="1bd95-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="1bd95-141">プログラミング手法</span><span class="sxs-lookup"><span data-stu-id="1bd95-141">Programming Practices</span></span>  
 <span data-ttu-id="1bd95-142">`lockobject`式は常をクラスにのみ属しているオブジェクトを評価する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1bd95-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="1bd95-143">宣言する必要があります、`Private`オブジェクト変数を現在のインスタンスに属するデータを保護または`Private Shared`オブジェクト変数をすべてのインスタンスに共通のデータを保護します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="1bd95-144">使用しないで、`Me`オブジェクトのインスタンスのデータのキーワードをロックを指定します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="1bd95-145">ロック オブジェクトとしてその参照を使用、クラスの外部のコードに、クラスのインスタンスへの参照がある場合、`SyncLock`ブロック、自分のものとはまったく異なる別のデータを保護します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="1bd95-146">この方法で、クラスとその他のクラスでした互いにブロックの実行、関連付けられていない`SyncLock`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="1bd95-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="1bd95-147">同様に、文字列をロックが問題となる、同じ文字列を使用して、プロセス内の他のすべてのコードは、同じロックを共有するためです。</span><span class="sxs-lookup"><span data-stu-id="1bd95-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="1bd95-148">使用しないでも、`Me.GetType`ロック オブジェクトを提供するメソッドがデータを共有します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="1bd95-149">これは、ため`GetType`常に同じを返します`Type`オブジェクトの特定のクラス名。</span><span class="sxs-lookup"><span data-stu-id="1bd95-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="1bd95-150">外部コードを呼び出すことが`GetType`クラスを使用している同じロック オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="1bd95-151">これは、結果から互いをブロックして 2 つのクラスとして、`SyncLock`ブロックします。</span><span class="sxs-lookup"><span data-stu-id="1bd95-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="1bd95-152">例</span><span class="sxs-lookup"><span data-stu-id="1bd95-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="1bd95-153">説明</span><span class="sxs-lookup"><span data-stu-id="1bd95-153">Description</span></span>  
 <span data-ttu-id="1bd95-154">次の例では、メッセージの単純なリストを保持するクラスを示します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="1bd95-155">配列内のメッセージを保持し、最後は、変数にその配列の要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="1bd95-156">`addAnotherMessage`プロシージャが最後の要素をインクリメントし、新しいメッセージを格納します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="1bd95-157">これら 2 つの操作で保護されている、`SyncLock`と`End SyncLock`ステートメント、他のスレッドでは、最後の要素をもう一度インクリメント前に、新しいメッセージを格納する必要が最後の要素をインクリメントすると後であるためです。</span><span class="sxs-lookup"><span data-stu-id="1bd95-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="1bd95-158">場合、`simpleMessageList`クラスはすべて、そのインスタンスの変数間のメッセージの 1 つのリストを共有`messagesList`と`messagesLast`として宣言することは`Shared`します。</span><span class="sxs-lookup"><span data-stu-id="1bd95-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="1bd95-159">この場合、変数`messagesLock`すべき`Shared`、すべてのインスタンスによって使用される 1 つのロック オブジェクトがあるようにします。</span><span class="sxs-lookup"><span data-stu-id="1bd95-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1bd95-160">コード</span><span class="sxs-lookup"><span data-stu-id="1bd95-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a><span data-ttu-id="1bd95-161">説明</span><span class="sxs-lookup"><span data-stu-id="1bd95-161">Description</span></span>  
 <span data-ttu-id="1bd95-162">次の例は、スレッドを使用し、`SyncLock`です。</span><span class="sxs-lookup"><span data-stu-id="1bd95-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="1bd95-163">限り、`SyncLock`ステートメント、ステートメント ブロックは、クリティカル セクションと`balance`ことはありませんが、負の数になります。</span><span class="sxs-lookup"><span data-stu-id="1bd95-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="1bd95-164">コメント アウトすることができます、`SyncLock`と`End SyncLock`が除外の影響を確認するステートメント、`SyncLock`キーワード。</span><span class="sxs-lookup"><span data-stu-id="1bd95-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1bd95-165">コード</span><span class="sxs-lookup"><span data-stu-id="1bd95-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="1bd95-166">コメント</span><span class="sxs-lookup"><span data-stu-id="1bd95-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd95-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bd95-167">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="1bd95-168">スレッドの同期</span><span class="sxs-lookup"><span data-stu-id="1bd95-168">Thread Synchronization</span></span>](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)  
 [<span data-ttu-id="1bd95-169">スレッド化</span><span class="sxs-lookup"><span data-stu-id="1bd95-169">Threading</span></span>](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)
