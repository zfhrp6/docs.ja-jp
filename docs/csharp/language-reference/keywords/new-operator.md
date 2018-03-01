---
title: "new 演算子 (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3c2b484b9872a54ce42520de77a723b9edb441a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="336d5-102">new 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="336d5-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="336d5-103">オブジェクトを作成し、コンストラクターを呼び出すために使用します。</span><span class="sxs-lookup"><span data-stu-id="336d5-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="336d5-104">例:</span><span class="sxs-lookup"><span data-stu-id="336d5-104">For example:</span></span>  
  
```  
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="336d5-105">匿名型のインスタンスの作成にも使用します。</span><span class="sxs-lookup"><span data-stu-id="336d5-105">It is also used to create instances of anonymous types:</span></span>  
  
```  
var query = from cust in customers  
            select new {Name = cust.Name, Address = cust.PrimaryAddress};  
```  
  
 <span data-ttu-id="336d5-106">`new` 演算子は値型の既定コンストラクターの呼び出しにも使用します。</span><span class="sxs-lookup"><span data-stu-id="336d5-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="336d5-107">例:</span><span class="sxs-lookup"><span data-stu-id="336d5-107">For example:</span></span>  
  
```  
int i = new int();  
```  
  
 <span data-ttu-id="336d5-108">上記のステートメントでは、`i` は `int` 型の既定値 `0` に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="336d5-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="336d5-109">このステートメントは次のステートメントと同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="336d5-109">The statement has the same effect as the following:</span></span>  
  
```  
int i = 0;  
```  
  
 <span data-ttu-id="336d5-110">既定値の一覧については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="336d5-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="336d5-111">すべての値型には暗黙的に既定のパブリック コンストラクターがあるため、[構造体](../../../csharp/language-reference/keywords/struct.md) に対して既定のコンストラクターを宣言するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="336d5-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="336d5-112">パラメーター付きのコンストラクターを構造体型で宣言し、その初期値を設定することは可能ですが、これが必要になるのは、既定値以外の値が必要な場合のみです。</span><span class="sxs-lookup"><span data-stu-id="336d5-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="336d5-113">構造体などの値型オブジェクトはスタック領域に作成され、クラスなどの参照型オブジェクトはヒープ領域に作成されます。</span><span class="sxs-lookup"><span data-stu-id="336d5-113">Value-type objects such as structs are created on the stack, while reference-type objects such as classes are created on the heap.</span></span> <span data-ttu-id="336d5-114">どちらの型のオブジェクトも自動的に破棄されますが、値型に基づくオブジェクトがスコープの適用外になると破棄されるのに対し、参照型に基づくオブジェクトは、そのオブジェクトへの最後の参照が削除されたあと、随時破棄されます。</span><span class="sxs-lookup"><span data-stu-id="336d5-114">Both types of objects are destroyed automatically, but objects based on value types are destroyed when they go out of scope, whereas objects based on reference types are destroyed at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="336d5-115">大量のメモリ、ファイル ハンドル、ネットワーク接続などの固定のリソースを消費する参照型の場合、確定的な最終処理を行い、オブジェクトが破棄されたことをできるだけ早く確認することが望ましい場合があります。</span><span class="sxs-lookup"><span data-stu-id="336d5-115">For reference types that consume fixed resources such as large amounts of memory, file handles, or network connections, it is sometimes desirable to employ deterministic finalization to ensure that the object is destroyed as soon as possible.</span></span> <span data-ttu-id="336d5-116">詳細については、「[using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="336d5-116">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="336d5-117">`new` 演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="336d5-117">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="336d5-118">`new` 演算子によるメモリの割り当てが失敗した場合、<xref:System.OutOfMemoryException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="336d5-118">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="336d5-119">例</span><span class="sxs-lookup"><span data-stu-id="336d5-119">Example</span></span>  
 <span data-ttu-id="336d5-120">次の例では、`struct` オブジェクトおよびクラス オブジェクトは、`new` 演算子を使用して作成、初期化され、そのあと値が代入されます。</span><span class="sxs-lookup"><span data-stu-id="336d5-120">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="336d5-121">既定値と代入値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="336d5-121">The default and the assigned values are displayed.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-operator_1.cs)]  
  
 <span data-ttu-id="336d5-122">この例では、文字列の既定値は `null` です。</span><span class="sxs-lookup"><span data-stu-id="336d5-122">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="336d5-123">このため、文字列の既定値は表示されません。</span><span class="sxs-lookup"><span data-stu-id="336d5-123">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="336d5-124">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="336d5-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="336d5-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="336d5-125">See Also</span></span>  
 [<span data-ttu-id="336d5-126">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="336d5-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="336d5-127">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="336d5-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="336d5-128">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="336d5-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="336d5-129">演算子のキーワード</span><span class="sxs-lookup"><span data-stu-id="336d5-129">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="336d5-130">new</span><span class="sxs-lookup"><span data-stu-id="336d5-130">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="336d5-131">匿名型</span><span class="sxs-lookup"><span data-stu-id="336d5-131">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
