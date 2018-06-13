---
title: '方法: オブジェクトの遅延初期化を実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d33dcb2b060d1d453ae17a48d2765d489de0038
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394476"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a><span data-ttu-id="a4fbb-102">方法: オブジェクトの遅延初期化を実行する</span><span class="sxs-lookup"><span data-stu-id="a4fbb-102">How to: Perform Lazy Initialization of Objects</span></span>
<span data-ttu-id="a4fbb-103"><xref:System.Lazy%601?displayProperty=nameWithType> クラスは、オブジェクトの遅延初期化とインスタンス化を実行する操作を簡略化します。</span><span class="sxs-lookup"><span data-stu-id="a4fbb-103">The <xref:System.Lazy%601?displayProperty=nameWithType> class simplifies the work of performing lazy initialization and instantiation of objects.</span></span> <span data-ttu-id="a4fbb-104">オブジェクトを限定的に初期化すれば、不要なオブジェクトを作成する必要がなくなります。また、オブジェクトに初めてアクセスするときまで、そのオブジェクトの初期化を延期できます。</span><span class="sxs-lookup"><span data-stu-id="a4fbb-104">By initializing objects in a lazy manner, you can avoid having to create them at all if they are never needed, or you can postpone their initialization until they are first accessed.</span></span> <span data-ttu-id="a4fbb-105">詳細については、「[限定的な初期化](../../../docs/framework/performance/lazy-initialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4fbb-105">For more information, see [Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4fbb-106">例</span><span class="sxs-lookup"><span data-stu-id="a4fbb-106">Example</span></span>  
 <span data-ttu-id="a4fbb-107">次の例では、<xref:System.Lazy%601> で値を初期化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a4fbb-107">The following example shows how to initialize a value with <xref:System.Lazy%601>.</span></span> <span data-ttu-id="a4fbb-108">`someCondition` 変数を true または false に設定する他の一部のコードでは、遅延変数は必要ないものとします。</span><span class="sxs-lookup"><span data-stu-id="a4fbb-108">Assume that the lazy variable might not be needed, depending on some other code that sets the `someCondition` variable to true or false.</span></span>  
  
```vb  
Dim someCondition As Boolean = False  
  
Sub Main()  
    'Initializing a value with a big computation, computed in parallel  
    Dim _data As Lazy(Of Integer) = New Lazy(Of Integer)(Function()  
                                                             Dim result =  
                                                                 ParallelEnumerable.Range(0, 1000).  
                                                                 Aggregate(Function(x, y)  
                                                                               Return x + y  
                                                                           End Function)  
                                                             Return result  
                                                         End Function)  
  
    '  do work that may or may not set someCondition to True  
    ' ...  
    '  Initialize the data only if needed  
    If someCondition = True Then  
  
        If (_data.Value > 100) Then  
  
            Console.WriteLine("Good data")  
        End If  
    End If  
End Sub  
```  
  
```csharp  
  static bool someCondition = false;    
  //Initializing a value with a big computation, computed in parallel  
  Lazy<int> _data = new Lazy<int>(delegate  
  {  
      return ParallelEnumerable.Range(0, 1000).  
          Select(i => Compute(i)).Aggregate((x,y) => x + y);  
  }, LazyExecutionMode.EnsureSingleThreadSafeExecution);  
  
  // Do some work that may or may not set someCondition to true.  
  //  ...  
  // Initialize the data only if necessary  
  if (someCondition)  
{  
    if (_data.Value > 100)  
      {  
          Console.WriteLine("Good data");  
      }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="a4fbb-109">例</span><span class="sxs-lookup"><span data-stu-id="a4fbb-109">Example</span></span>  
 <span data-ttu-id="a4fbb-110">次の例では、<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> クラスを使用して、現在のスレッド上の現在のオブジェクト インスタンスでのみ表示される型を初期化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a4fbb-110">The following example shows how to use the <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> class to initialize a type that is visible only to the current object instance on the current thread.</span></span>  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="a4fbb-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4fbb-111">See Also</span></span>  
 <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>  
 [<span data-ttu-id="a4fbb-112">遅延初期化</span><span class="sxs-lookup"><span data-stu-id="a4fbb-112">Lazy Initialization</span></span>](../../../docs/framework/performance/lazy-initialization.md)
