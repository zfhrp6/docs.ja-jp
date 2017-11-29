---
title: "Null 許容型のボックス化 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- boxing [C#], nullable types
- unboxing [C#], nullable types
- nullable types [C#], boxing and unboxing
ms.assetid: bdb5b626-abc0-405d-8f64-0f0a0bf883a4
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 29fccba56f6758fdfd407fa1879baa9260b69187
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="boxing-nullable-types-c-programming-guide"></a><span data-ttu-id="8d02b-102">Null 許容型のボックス化 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="8d02b-102">Boxing Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="8d02b-103">Null 許容型に基づくオブジェクトは、オブジェクトが Null 以外の場合にのみボックス化されます。</span><span class="sxs-lookup"><span data-stu-id="8d02b-103">Objects based on nullable types are only boxed if the object is non-null.</span></span> <span data-ttu-id="8d02b-104"><xref:System.Nullable%601.HasValue%2A> が `false` の場合、オブジェクト参照はボックス化ではなく `null` に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="8d02b-104">If <xref:System.Nullable%601.HasValue%2A> is `false`, the object reference is assigned to `null` instead of boxing.</span></span> <span data-ttu-id="8d02b-105">例:</span><span class="sxs-lookup"><span data-stu-id="8d02b-105">For example:</span></span>  
  
```csharp  
bool? b = null;  
object o = b;  
// Now o is null.  
```  
  
 <span data-ttu-id="8d02b-106">オブジェクトが Null 以外の場合 (<xref:System.Nullable%601.HasValue%2A> が `true` の場合)、ボックス化が発生しますが、Null 許容型オブジェクトの基礎になっている基本型のみがボックス化されます。</span><span class="sxs-lookup"><span data-stu-id="8d02b-106">If the object is non-null -- if <xref:System.Nullable%601.HasValue%2A> is `true` -- then boxing occurs, but only the underlying type that the nullable object is based on is boxed.</span></span> <span data-ttu-id="8d02b-107">Null 以外の Null 許容値型をボックス化すると、値の型をラップする <xref:System.Nullable%601?displayProperty=nameWithType> ではなく、値の型自体がボックス化されます。</span><span class="sxs-lookup"><span data-stu-id="8d02b-107">Boxing a non-null nullable value type boxes the value type itself, not the <xref:System.Nullable%601?displayProperty=nameWithType> that wraps the value type.</span></span> <span data-ttu-id="8d02b-108">例:</span><span class="sxs-lookup"><span data-stu-id="8d02b-108">For example:</span></span>  
  
```csharp  
bool? b = false;  
int? i = 44;  
object bBoxed = b; // bBoxed contains a boxed bool.  
object iBoxed = i; // iBoxed contains a boxed int.  
```  
  
 <span data-ttu-id="8d02b-109">ボックス化された 2 つのオブジェクトは、Null 非許容の型のボックス化で作成されたオブジェクトと同じになります。</span><span class="sxs-lookup"><span data-stu-id="8d02b-109">The two boxed objects are identical to those created by boxing non-nullable types.</span></span> <span data-ttu-id="8d02b-110">また、Null 非許容のボックス化された型と同様に、次の例のように、Null 許容型にボックス化を解除できます。</span><span class="sxs-lookup"><span data-stu-id="8d02b-110">And, just like non-nullable boxed types, they can be unboxed into nullable types, as in the following example:</span></span>  
  
```csharp  
bool? b2 = (bool?)bBoxed;  
int? i2 = (int?)iBoxed;  
```  
  
## <a name="remarks"></a><span data-ttu-id="8d02b-111">コメント</span><span class="sxs-lookup"><span data-stu-id="8d02b-111">Remarks</span></span>  
 <span data-ttu-id="8d02b-112">ボックス化されるとき、Null 許容型の動作には 2 つの利点があります。</span><span class="sxs-lookup"><span data-stu-id="8d02b-112">The behavior of nullable types when boxed provides two advantages:</span></span>  
  
1.  <span data-ttu-id="8d02b-113">Null 許容型オブジェクトとそれがボックス化されたものは null かどうかをテストできます。</span><span class="sxs-lookup"><span data-stu-id="8d02b-113">Nullable objects and their boxed counterpart can be tested for null:</span></span>  
  
    ```csharp  
    bool? b = null;  
    object boxedB = b;  
    if (b == null)  
    {  
      // True.  
    }  
    if (boxedB == null)  
    {  
      // Also true.  
    }  
    ```  
  
2.  <span data-ttu-id="8d02b-114">ボックス化された Null 許容型はその基礎型の機能を完全サポートします。</span><span class="sxs-lookup"><span data-stu-id="8d02b-114">Boxed nullable types fully support the functionality of the underlying type:</span></span>  
  
    ```csharp  
    double? d = 44.4;  
    object iBoxed = d;  
    // Access IConvertible interface implemented by double.  
    IConvertible ic = (IConvertible)iBoxed;  
    int i = ic.ToInt32(null);  
    string str = ic.ToString();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8d02b-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d02b-115">See Also</span></span>  
 [<span data-ttu-id="8d02b-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="8d02b-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8d02b-117">Null 許容型</span><span class="sxs-lookup"><span data-stu-id="8d02b-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="8d02b-118">方法: Null 許容型を識別する</span><span class="sxs-lookup"><span data-stu-id="8d02b-118">How to: Identify a Nullable Type</span></span>](../../../csharp/programming-guide/nullable-types/how-to-identify-a-nullable-type.md)
