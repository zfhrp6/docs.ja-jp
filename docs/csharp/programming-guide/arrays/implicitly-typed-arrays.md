---
title: "暗黙的に型指定される配列 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#], implicity-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
caps.latest.revision: 13
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
ms.openlocfilehash: 5a042bdebd07062debe70cbea0a9661fbd425804
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="implicitly-typed-arrays-c-programming-guide"></a><span data-ttu-id="4db18-102">暗黙的に型指定される配列 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="4db18-102">Implicitly Typed Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="4db18-103">配列インスタンスの型が、配列初期化子で指定された要素から推論される暗黙的に型指定された配列を作成できます。</span><span class="sxs-lookup"><span data-stu-id="4db18-103">You can create an implicitly-typed array in which the type of the array instance is inferred from the elements specified in the array initializer.</span></span> <span data-ttu-id="4db18-104">暗黙的に型指定された変数の規則は、暗黙的に型指定された配列にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="4db18-104">The rules for any implicitly-typed variable also apply to implicitly-typed arrays.</span></span> <span data-ttu-id="4db18-105">詳細については、「[暗黙的に型指定されたローカル変数](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4db18-105">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
 <span data-ttu-id="4db18-106">暗黙的に型指定された配列は通常、匿名型、オブジェクト、コレクション初期化子と共にクエリ式で使用されます。</span><span class="sxs-lookup"><span data-stu-id="4db18-106">Implicitly-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.</span></span>  
  
 <span data-ttu-id="4db18-107">次の例では、暗黙的に型指定された配列を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4db18-107">The following examples show how to create an implicitly-typed array:</span></span>  
  
 <span data-ttu-id="4db18-108">[!code-cs[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4db18-108">[!code-cs[csProgGuideLINQ#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_1.cs)]</span></span>  
  
 <span data-ttu-id="4db18-109">前の例で、暗黙的に型指定された配列では、初期化ステートメントの左側では角かっこが使用されていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4db18-109">In the previous example, notice that with implicitly-typed arrays, no square brackets are used on the left side of the initialization statement.</span></span> <span data-ttu-id="4db18-110">また、ジャグ配列は、1 次元の配列と同じように `new []` を使用して初期化されます。</span><span class="sxs-lookup"><span data-stu-id="4db18-110">Note also that jagged arrays are initialized by using `new []` just like single-dimension arrays.</span></span>  
  
## <a name="implicitly-typed-arrays-in-object-initializers"></a><span data-ttu-id="4db18-111">オブジェクト初期化子で暗黙的に型指定された配列</span><span class="sxs-lookup"><span data-stu-id="4db18-111">Implicitly-typed Arrays in Object Initializers</span></span>  
 <span data-ttu-id="4db18-112">配列を含む匿名型を作成するときには、型のオブジェクトの初期化子で配列を暗黙的に型指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4db18-112">When you create an anonymous type that contains an array, the array must be implicitly typed in the type's object initializer.</span></span> <span data-ttu-id="4db18-113">次の例では、`contacts` は、匿名型の暗黙的に型指定された配列で、それぞれが `PhoneNumbers` という名前の配列を含んでいます。</span><span class="sxs-lookup"><span data-stu-id="4db18-113">In the following example, `contacts` is an implicitly-typed array of anonymous types, each of which contains an array named `PhoneNumbers`.</span></span> <span data-ttu-id="4db18-114">`var` キーワードは、オブジェクト初期化子内で使用されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4db18-114">Note that the `var` keyword is not used inside the object initializers.</span></span>  
  
 <span data-ttu-id="4db18-115">[!code-cs[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4db18-115">[!code-cs[csProgGuideLINQ#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-arrays_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db18-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4db18-116">See Also</span></span>  
 <span data-ttu-id="4db18-117">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4db18-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4db18-118">[暗黙的に型指定されるローカル変数](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) </span><span class="sxs-lookup"><span data-stu-id="4db18-118">[Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) </span></span>  
 <span data-ttu-id="4db18-119">[配列](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="4db18-119">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="4db18-120">[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="4db18-120">[Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md) </span></span>  
 <span data-ttu-id="4db18-121">[オブジェクト初期化子とコレクション初期化子](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) </span><span class="sxs-lookup"><span data-stu-id="4db18-121">[Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) </span></span>  
 <span data-ttu-id="4db18-122">[var](../../../csharp/language-reference/keywords/var.md) </span><span class="sxs-lookup"><span data-stu-id="4db18-122">[var](../../../csharp/language-reference/keywords/var.md) </span></span>  
 [<span data-ttu-id="4db18-123">LINQ クエリ式</span><span class="sxs-lookup"><span data-stu-id="4db18-123">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)

