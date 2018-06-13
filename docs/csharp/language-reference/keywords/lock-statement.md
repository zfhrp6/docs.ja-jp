---
title: lock ステートメント (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2ce870e8caa67d780ce603a6f1dbcc7cd303b842
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274220"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="487e4-102">lock ステートメント (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="487e4-102">lock Statement (C# Reference)</span></span>
<span data-ttu-id="487e4-103">`lock` キーワードは、ステートメント ブロックをクリティカル セクションとして指定します。このためには、特定のオブジェクトの相互排他ロックを取得し、ステートメントを実行して、ロックを解放します。</span><span class="sxs-lookup"><span data-stu-id="487e4-103">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="487e4-104">次の例では、`lock` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="487e4-104">The following example includes a `lock` statement.</span></span>  
  
```csharp  
class Account  
{  
    decimal balance;  
    private Object thisLock = new Object();  
  
    public void Withdraw(decimal amount)  
    {  
        lock (thisLock)  
        {  
            if (amount > balance)  
            {  
                throw new Exception("Insufficient funds");  
            }  
            balance -= amount;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="487e4-105">詳細については、「[スレッドの同期](../../programming-guide/concepts/threading/thread-synchronization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="487e4-105">For more information, see [Thread Synchronization](../../programming-guide/concepts/threading/thread-synchronization.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="487e4-106">コメント</span><span class="sxs-lookup"><span data-stu-id="487e4-106">Remarks</span></span>  
 <span data-ttu-id="487e4-107">`lock` キーワードは、コードのクリティカル セクションに複数のスレッドが同時に進入することを防ぐ働きをします。</span><span class="sxs-lookup"><span data-stu-id="487e4-107">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="487e4-108">これから実行しようとしているコードがロックされている場合、別のスレッドは、そのオブジェクトが解放されるまで待機 (ブロック) 状態になります。</span><span class="sxs-lookup"><span data-stu-id="487e4-108">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>  
  
 <span data-ttu-id="487e4-109">スレッド処理については、「[スレッド処理](../../programming-guide/concepts/threading/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="487e4-109">The section [Threading](../../programming-guide/concepts/threading/index.md) discusses threading.</span></span>  
  
 <span data-ttu-id="487e4-110">`lock` キーワードは、ブロックの先頭で <xref:System.Threading.Monitor.Enter%2A> を呼び出し、ブロックの末尾で <xref:System.Threading.Monitor.Exit%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="487e4-110">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="487e4-111">`lock` ステートメントの実行を待っているスレッドを <xref:System.Threading.Thread.Interrupt%2A> で中断すると、<xref:System.Threading.ThreadInterruptedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="487e4-111">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>  
  
 <span data-ttu-id="487e4-112">一般に、`public` 型 (つまり、コードの制御が及ばないインスタンス) をロックすることは避けてください。</span><span class="sxs-lookup"><span data-stu-id="487e4-112">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="487e4-113">`lock (this)`、`lock (typeof (MyType))`、`lock ("myLock")` は、このガイドラインに違反する代表的なコンストラクトです。</span><span class="sxs-lookup"><span data-stu-id="487e4-113">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>  
  
-   <span data-ttu-id="487e4-114">`lock (this)` は、このインスタンスにパブリックにアクセスできる場合に問題となります。</span><span class="sxs-lookup"><span data-stu-id="487e4-114">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>  
  
-   <span data-ttu-id="487e4-115">`lock (typeof (MyType))` は、`MyType` にパブリックにアクセスできる場合に問題となります。</span><span class="sxs-lookup"><span data-stu-id="487e4-115">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>  
  
-   <span data-ttu-id="487e4-116">`lock("myLock")` が問題となる理由は、同じ文字列を使用するコードがプロセス内に他にも存在した場合、そのコードも同じロックを共有するためです。</span><span class="sxs-lookup"><span data-stu-id="487e4-116">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>  
  
 <span data-ttu-id="487e4-117">`private` オブジェクトを定義してロックの適用対象を限定するか、`private static` オブジェクト変数を定義して、すべてのインスタンスに共通するデータを保護することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="487e4-117">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="487e4-118">`lock` ステートメントの本体で [await](../../../csharp/language-reference/keywords/await.md) キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="487e4-118">You can't use the [await](../../../csharp/language-reference/keywords/await.md) keyword in the body of a `lock` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="487e4-119">例</span><span class="sxs-lookup"><span data-stu-id="487e4-119">Example</span></span>  
 <span data-ttu-id="487e4-120">次のサンプルでは、C# でロックされていないスレッドの簡単な使用例を示しています。</span><span class="sxs-lookup"><span data-stu-id="487e4-120">The following sample shows a simple use of threads without locking in C#.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="487e4-121">例</span><span class="sxs-lookup"><span data-stu-id="487e4-121">Example</span></span>  
 <span data-ttu-id="487e4-122">次のサンプルでは、スレッドと `lock` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="487e4-122">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="487e4-123">`lock` ステートメントが存在する限り、このステートメント ブロックはクリティカル セクションとなり、`balance` が負の数になることはありません。</span><span class="sxs-lookup"><span data-stu-id="487e4-123">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="487e4-124">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="487e4-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="487e4-125">参照</span><span class="sxs-lookup"><span data-stu-id="487e4-125">See Also</span></span>  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [<span data-ttu-id="487e4-126">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="487e4-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="487e4-127">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="487e4-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="487e4-128">スレッド化</span><span class="sxs-lookup"><span data-stu-id="487e4-128">Threading</span></span>](../../programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="487e4-129">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="487e4-129">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="487e4-130">ステートメントのキーワード</span><span class="sxs-lookup"><span data-stu-id="487e4-130">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="487e4-131">インタロックされた操作</span><span class="sxs-lookup"><span data-stu-id="487e4-131">Interlocked Operations</span></span>](../../../standard/threading/interlocked-operations.md)  
 [<span data-ttu-id="487e4-132">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="487e4-132">AutoResetEvent</span></span>](../../../standard/threading/autoresetevent.md)  
 [<span data-ttu-id="487e4-133">スレッドの同期</span><span class="sxs-lookup"><span data-stu-id="487e4-133">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)
