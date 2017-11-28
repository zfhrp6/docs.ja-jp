---
title: "方法: as 演算子と is 演算子を使用して安全にキャストする (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 733b67408997feb0e518db327e3eedd42f286a99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-by-using-as-and-is-operators-c-programming-guide"></a><span data-ttu-id="5018c-102">方法: as 演算子と is 演算子を使用して安全にキャストする (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5018c-102">How to: Safely Cast by Using as and is Operators (C# Programming Guide)</span></span>
<span data-ttu-id="5018c-103">オブジェクトはポリモーフィックであるため、基本クラス型の変数で派生型を保持できます。</span><span class="sxs-lookup"><span data-stu-id="5018c-103">Because objects are polymorphic, it is possible for a variable of a base class type to hold a derived type.</span></span> <span data-ttu-id="5018c-104">派生型のメソッドにアクセスするには、値をキャストして派生型に戻す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5018c-104">To access the derived type's method, it is necessary to cast the value back to the derived type.</span></span> <span data-ttu-id="5018c-105">このような場合に単純にキャストを実行すると、<xref:System.InvalidCastException> がスローされるリスクが生じます。</span><span class="sxs-lookup"><span data-stu-id="5018c-105">However, to attempt a simple cast in these cases creates the risk of throwing an <xref:System.InvalidCastException>.</span></span> <span data-ttu-id="5018c-106">このため、C# には、[is](../../../csharp/language-reference/keywords/is.md) 演算子と [as](../../../csharp/language-reference/keywords/as.md) 演算子が用意されています。</span><span class="sxs-lookup"><span data-stu-id="5018c-106">That is why C# provides the [is](../../../csharp/language-reference/keywords/is.md) and [as](../../../csharp/language-reference/keywords/as.md) operators.</span></span> <span data-ttu-id="5018c-107">これらの演算子を使用すると、例外がスローされることなくキャストが成功するかどうかをテストできます。</span><span class="sxs-lookup"><span data-stu-id="5018c-107">You can use these operators to test whether a cast will succeed without causing an exception to be thrown.</span></span> <span data-ttu-id="5018c-108">通常は、`as` 演算子の方が、キャストが正しく実行できる場合はキャスト値を実際に返すため、より効率的です。</span><span class="sxs-lookup"><span data-stu-id="5018c-108">In general, the `as` operator is more efficient because it actually returns the cast value if the cast can be made successfully.</span></span> <span data-ttu-id="5018c-109">`is` 演算子はブール値のみを返します。</span><span class="sxs-lookup"><span data-stu-id="5018c-109">The `is` operator returns only a Boolean value.</span></span> <span data-ttu-id="5018c-110">したがって、オブジェクトの型の確認のみ行い、キャストは行う必要がない場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="5018c-110">It can therefore be used when you just want to determine an object's type but do not have to actually cast it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5018c-111">例</span><span class="sxs-lookup"><span data-stu-id="5018c-111">Example</span></span>  
 <span data-ttu-id="5018c-112">`is` 演算子と `as` 演算子を使用して、例外がスローされるリスクを回避しながら、参照型を別の参照型にキャストする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="5018c-112">The following examples show how to use the `is` and `as` operators to cast from one reference type to another without the risk of throwing an exception.</span></span> <span data-ttu-id="5018c-113">この例では、null 許容値型で `as` 演算子を使用する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="5018c-113">The example also shows how to use the `as` operator with nullable value types.</span></span>  
  
 [!code-csharp[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5018c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5018c-114">See Also</span></span>  
 [<span data-ttu-id="5018c-115">型</span><span class="sxs-lookup"><span data-stu-id="5018c-115">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="5018c-116">キャストと型変換</span><span class="sxs-lookup"><span data-stu-id="5018c-116">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="5018c-117">Null 許容型</span><span class="sxs-lookup"><span data-stu-id="5018c-117">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)
