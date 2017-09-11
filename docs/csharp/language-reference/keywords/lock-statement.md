---
title: "lock ステートメント (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- lock_CSharpKeyword
- lock
dev_langs:
- CSharp
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 00dcbb9feec11587265bf61667d91c2c1598065b
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="0c3b8-102">lock ステートメント (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0c3b8-102">lock Statement (C# Reference)</span></span>
<span data-ttu-id="0c3b8-103">`lock` キーワードは、ステートメント ブロックをクリティカル セクションとして指定します。このためには、特定のオブジェクトの相互排他ロックを取得し、ステートメントを実行して、ロックを解放します。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-103">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="0c3b8-104">次の例では、`lock` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-104">The following example includes a `lock` statement.</span></span>  
  
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
  
 <span data-ttu-id="0c3b8-105">詳細については、「[スレッドの同期](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-105">For more information, see [Thread Synchronization](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c3b8-106">コメント</span><span class="sxs-lookup"><span data-stu-id="0c3b8-106">Remarks</span></span>  
 <span data-ttu-id="0c3b8-107">`lock` キーワードは、コードのクリティカル セクションに複数のスレッドが同時に進入することを防ぐ働きをします。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-107">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="0c3b8-108">これから実行しようとしているコードがロックされている場合、別のスレッドは、そのオブジェクトが解放されるまで待機 (ブロック) 状態になります。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-108">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>  
  
 <span data-ttu-id="0c3b8-109">スレッド処理については、「[スレッド処理](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-109">The section [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) discusses threading.</span></span>  
  
 <span data-ttu-id="0c3b8-110">`lock` キーワードは、ブロックの先頭で <xref:System.Threading.Monitor.Enter%2A> を呼び出し、ブロックの末尾で <xref:System.Threading.Monitor.Exit%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-110">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="0c3b8-111">`lock` ステートメントの実行を待っているスレッドを <xref:System.Threading.Thread.Interrupt%2A> で中断すると、<xref:System.Threading.ThreadInterruptedException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-111">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>  
  
 <span data-ttu-id="0c3b8-112">一般に、`public` 型 (つまり、コードの制御が及ばないインスタンス) をロックすることは避けてください。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-112">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="0c3b8-113">`lock (this)`、`lock (typeof (MyType))`、`lock ("myLock")` は、このガイドラインに違反する代表的なコンストラクトです。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-113">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>  
  
-   <span data-ttu-id="0c3b8-114">`lock (this)` は、このインスタンスにパブリックにアクセスできる場合に問題となります。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-114">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>  
  
-   <span data-ttu-id="0c3b8-115">`lock (typeof (MyType))` は、`MyType` にパブリックにアクセスできる場合に問題となります。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-115">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>  
  
-   <span data-ttu-id="0c3b8-116">`lock("myLock")` が問題となる理由は、同じ文字列を使用するコードがプロセス内に他にも存在した場合、そのコードも同じロックを共有するためです。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-116">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>  
  
 <span data-ttu-id="0c3b8-117">`private` オブジェクトを定義してロックの適用対象を限定するか、`private static` オブジェクト変数を定義して、すべてのインスタンスに共通するデータを保護することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-117">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="0c3b8-118">`lock` ステートメントの本体で [await](../../../csharp/language-reference/keywords/await.md) キーワードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-118">You can't use the [await](../../../csharp/language-reference/keywords/await.md) keyword in the body of a `lock` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c3b8-119">例</span><span class="sxs-lookup"><span data-stu-id="0c3b8-119">Example</span></span>  
 <span data-ttu-id="0c3b8-120">次のサンプルでは、C# でロックされていないスレッドの簡単な使用例を示しています。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-120">The following sample shows a simple use of threads without locking in C#.</span></span>  
  
 <span data-ttu-id="0c3b8-121">[!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="0c3b8-121">[!code-cs[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c3b8-122">例</span><span class="sxs-lookup"><span data-stu-id="0c3b8-122">Example</span></span>  
 <span data-ttu-id="0c3b8-123">次のサンプルでは、スレッドと `lock` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-123">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="0c3b8-124">`lock` ステートメントが存在する限り、このステートメント ブロックはクリティカル セクションとなり、`balance` が負の数になることはありません。</span><span class="sxs-lookup"><span data-stu-id="0c3b8-124">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number.</span></span>  
  
 <span data-ttu-id="0c3b8-125">[!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="0c3b8-125">[!code-cs[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0c3b8-126">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="0c3b8-126">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0c3b8-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c3b8-127">See Also</span></span>  
 <span data-ttu-id="0c3b8-128"><xref:System.Reflection.MethodImplAttributes></span><span class="sxs-lookup"><span data-stu-id="0c3b8-128"><xref:System.Reflection.MethodImplAttributes></span></span>   
 <span data-ttu-id="0c3b8-129"><xref:System.Threading.Mutex></span><span class="sxs-lookup"><span data-stu-id="0c3b8-129"><xref:System.Threading.Mutex></span></span>   
 <span data-ttu-id="0c3b8-130">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="0c3b8-130">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="0c3b8-131">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="0c3b8-131">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="0c3b8-132">[スレッド処理](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) </span><span class="sxs-lookup"><span data-stu-id="0c3b8-132">[Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c) </span></span>  
 <span data-ttu-id="0c3b8-133">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="0c3b8-133">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="0c3b8-134">[ステートメントのキーワード](../../../csharp/language-reference/keywords/statement-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="0c3b8-134">[Statement Keywords](../../../csharp/language-reference/keywords/statement-keywords.md) </span></span>  
 <span data-ttu-id="0c3b8-135">@System.Threading.Monitor</span><span class="sxs-lookup"><span data-stu-id="0c3b8-135">@System.Threading.Monitor</span></span>   
 <span data-ttu-id="0c3b8-136">[インタロックされた操作](../../../standard/threading/interlocked-operations.md) </span><span class="sxs-lookup"><span data-stu-id="0c3b8-136">[Interlocked Operations](../../../standard/threading/interlocked-operations.md) </span></span>  
 <span data-ttu-id="0c3b8-137">[AutoResetEvent](../../../standard/threading/autoresetevent.md) </span><span class="sxs-lookup"><span data-stu-id="0c3b8-137">[AutoResetEvent](../../../standard/threading/autoresetevent.md) </span></span>  
 [<span data-ttu-id="0c3b8-138">スレッドの同期</span><span class="sxs-lookup"><span data-stu-id="0c3b8-138">Thread Synchronization</span></span>](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)

