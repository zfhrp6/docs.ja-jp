---
title: "new 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: 22
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
ms.openlocfilehash: 59e1cc2006548df9a7a10283a34044040e5c2fef
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="new-operator-c-reference"></a><span data-ttu-id="f4b0d-102">new 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f4b0d-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="f4b0d-103">オブジェクトを作成し、コンストラクターを呼び出すために使用します。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="f4b0d-104">例:</span><span class="sxs-lookup"><span data-stu-id="f4b0d-104">For example:</span></span>  
  
```  
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="f4b0d-105">匿名型のインスタンスの作成にも使用します。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-105">It is also used to create instances of anonymous types:</span></span>  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 <span data-ttu-id="f4b0d-106">`new` 演算子は値型の既定コンストラクターの呼び出しにも使用します。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="f4b0d-107">例:</span><span class="sxs-lookup"><span data-stu-id="f4b0d-107">For example:</span></span>  
  
```  
int i = new int();  
```  
  
 <span data-ttu-id="f4b0d-108">上記のステートメントでは、`i` は `int` 型の既定値 `0` に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="f4b0d-109">このステートメントは次のステートメントと同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-109">The statement has the same effect as the following:</span></span>  
  
```  
int i = 0;  
```  
  
 <span data-ttu-id="f4b0d-110">既定値の一覧については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="f4b0d-111">すべての値型には暗黙的に既定のパブリック コンストラクターがあるため、[構造体](../../../csharp/language-reference/keywords/struct.md) に対して既定のコンストラクターを宣言するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="f4b0d-112">パラメーター付きのコンストラクターを構造体型で宣言し、その初期値を設定することは可能ですが、これが必要になるのは、既定値以外の値が必要な場合のみです。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="f4b0d-113">構造体などの値型オブジェクトはスタック領域に作成され、クラスなどの参照型オブジェクトはヒープ領域に作成されます。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-113">Value-type objects such as structs are created on the stack, while reference-type objects such as classes are created on the heap.</span></span> <span data-ttu-id="f4b0d-114">どちらの型のオブジェクトも自動的に破棄されますが、値型に基づくオブジェクトがスコープの適用外になると破棄されるのに対し、参照型に基づくオブジェクトは、そのオブジェクトへの最後の参照が削除されたあと、随時破棄されます。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-114">Both types of objects are destroyed automatically, but objects based on value types are destroyed when they go out of scope, whereas objects based on reference types are destroyed at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="f4b0d-115">大量のメモリ、ファイル ハンドル、ネットワーク接続などの固定のリソースを消費する参照型の場合、確定的な最終処理を行い、オブジェクトが破棄されたことをできるだけ早く確認することが望ましい場合があります。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-115">For reference types that consume fixed resources such as large amounts of memory, file handles, or network connections, it is sometimes desirable to employ deterministic finalization to ensure that the object is destroyed as soon as possible.</span></span> <span data-ttu-id="f4b0d-116">詳細については、「[using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-116">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="f4b0d-117">`new` 演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-117">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="f4b0d-118">`new` 演算子によるメモリの割り当てが失敗した場合、<xref:System.OutOfMemoryException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-118">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4b0d-119">例</span><span class="sxs-lookup"><span data-stu-id="f4b0d-119">Example</span></span>  
 <span data-ttu-id="f4b0d-120">次の例では、`struct` オブジェクトおよびクラス オブジェクトは、`new` 演算子を使用して作成、初期化され、そのあと値が代入されます。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-120">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="f4b0d-121">既定値と代入値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-121">The default and the assigned values are displayed.</span></span>  
  
 <span data-ttu-id="f4b0d-122">[!code-cs[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f4b0d-122">[!code-cs[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="f4b0d-123">この例では、文字列の既定値は `null` です。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-123">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="f4b0d-124">このため、文字列の既定値は表示されません。</span><span class="sxs-lookup"><span data-stu-id="f4b0d-124">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f4b0d-125">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f4b0d-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f4b0d-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4b0d-126">See Also</span></span>  
 <span data-ttu-id="f4b0d-127">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f4b0d-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f4b0d-128">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f4b0d-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f4b0d-129">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="f4b0d-129">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="f4b0d-130">[演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="f4b0d-130">[Operator Keywords](../../../csharp/language-reference/keywords/operator-keywords.md) </span></span>  
 <span data-ttu-id="f4b0d-131">[new](../../../csharp/language-reference/keywords/new.md) </span><span class="sxs-lookup"><span data-stu-id="f4b0d-131">[new](../../../csharp/language-reference/keywords/new.md) </span></span>  
 [<span data-ttu-id="f4b0d-132">匿名型</span><span class="sxs-lookup"><span data-stu-id="f4b0d-132">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)

