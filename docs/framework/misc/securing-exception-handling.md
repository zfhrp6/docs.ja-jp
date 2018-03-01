---
title: "例外処理の保護"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 548606a0196012fdd21bf5512e8ea7b089c723ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="securing-exception-handling"></a><span data-ttu-id="b8e0b-102">例外処理の保護</span><span class="sxs-lookup"><span data-stu-id="b8e0b-102">Securing Exception Handling</span></span>
<span data-ttu-id="b8e0b-103">Visual C および Visual Basic では、スタックをさらにフィルター式を実行前に、 **finally**ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="b8e0b-104">**キャッチ**に関連付けられているブロックの後にそのフィルターが実行される、**最後に**ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="b8e0b-105">詳細については、次を参照してください。[ユーザー フィルター例外](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-105">For more information, see [Using User-Filtered Exceptions](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="b8e0b-106">このセクションでは、この注文のセキュリティへの影響を調べます。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="b8e0b-107">どのフィルター ステートメント内での順序を示す次の擬似コード例について考えますと**最後に**ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
```cpp  
void Main()   
{  
    try   
    {  
        Sub();  
    }   
    except (Filter())   
    {  
        Console.WriteLine("catch");  
    }  
}  
bool Filter () {  
    Console.WriteLine("filter");  
    return true;  
}  
void Sub()   
{  
    try   
    {  
        Console.WriteLine("throw");  
        throw new Exception();  
    }   
    finally   
    {  
        Console.WriteLine("finally");  
    }  
}                        
```  
  
 <span data-ttu-id="b8e0b-108">このコードは、次を出力します。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-108">This code prints the following.</span></span>  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="b8e0b-109">フィルターを実行する前に、 **finally**ステートメントでは、セキュリティの問題は状態を他のコードの実行が利点かかる場合がありますを変更することによってもたらされるようにします。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="b8e0b-110">例:</span><span class="sxs-lookup"><span data-stu-id="b8e0b-110">For example:</span></span>  
  
```cpp  
try   
{  
    Alter_Security_State();  
    // This means changing anything (state variables,  
    // switching unmanaged context, impersonation, and   
    // so on) that could be exploited if malicious   
    // code ran before state is restored.  
    Do_some_work();  
}   
finally   
{  
    Restore_Security_State();  
    // This simply restores the state change above.  
}  
```  
  
 <span data-ttu-id="b8e0b-111">次の擬似コードは、任意のコードを実行するスタックの上位フィルターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="b8e0b-112">同様の効果を持つ処理の他の例は、いくつかのセキュリティ チェックをバイパスする内部フラグの設定、他の id の一時的な権限の借用またはスレッドに関連付けられているカルチャを変更します。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="b8e0b-113">スレッドの状態を呼び出し元のフィルター ブロックから、コードの変更を分離する例外ハンドラーを導入することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="b8e0b-114">ただし、例外ハンドラーを正しく導入することが重要ですか、この問題は修正されません。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="b8e0b-115">次の例は、UI カルチャを切り替えるが任意の種類のスレッド状態の変更を同様に公開される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
   CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
   try {  
      Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
      // Do something that throws an exception.  
}  
   finally {  
      Thread.CurrentThread.CurrentUICulture = saveCulture;  
   }  
}  
```  
  
```vb  
Public Class UserCode  
   Public Shared Sub Main()  
      Try  
         Dim obj As YourObject = new YourObject  
         obj.YourMethod()  
      Catch e As Exception When FilterFunc  
         Console.WriteLine("An error occurred: '{0}'", e)  
         Console.WriteLine("Current Culture: {0}",   
Thread.CurrentThread.CurrentUICulture)  
      End Try  
   End Sub  
  
   Public Function FilterFunc As Boolean  
      Console.WriteLine("Current Culture: {0}", Thread.CurrentThread.CurrentUICulture)  
      Return True  
   End Sub  
  
End Class  
```  
  
 <span data-ttu-id="b8e0b-116">修正プログラムがここでは、既存をラップする**を再試行してください**/**finally**のブロック、**を再試行してください**/**キャッチ**ブロックです。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="b8e0b-117">簡単に把握、 **catch throw**既存に句**再試行**/**最後に**の次の例に示すように、ブロックで、問題が解決しません。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
  
    try   
    {  
        Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
        // Do something that throws an exception.  
    }  
    catch { throw; }  
    finally   
    {  
        Thread.CurrentThread.CurrentUICulture = saveCulture;  
    }  
}  
```  
  
 <span data-ttu-id="b8e0b-118">問題が解決しない、 **finally**する前にステートメントが実行、`FilterFunc`コントロールを取得します。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="b8e0b-119">次の例では、問題を修正するようにすることで、 **finally**句が呼び出し元の例外フィルター ブロックの例外を提供する前に実行します。</span><span class="sxs-lookup"><span data-stu-id="b8e0b-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
    try    
    {  
        try   
        {  
            Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
            // Do something that throws an exception.  
        }  
        finally   
        {  
            Thread.CurrentThread.CurrentUICulture = saveCulture;  
        }  
    }  
    catch { throw; }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8e0b-120">参照</span><span class="sxs-lookup"><span data-stu-id="b8e0b-120">See Also</span></span>  
 [<span data-ttu-id="b8e0b-121">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b8e0b-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
