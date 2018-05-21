---
title: new 演算子 (C# リファレンス)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 2ba3c574897ae5f1ec66e3810e23f0af74bd8872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="ab1bb-102">new 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="ab1bb-102">new Operator (C# Reference)</span></span>
<span data-ttu-id="ab1bb-103">オブジェクトを作成し、コンストラクターを呼び出すために使用します。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-103">Used to create objects and invoke constructors.</span></span> <span data-ttu-id="ab1bb-104">例:</span><span class="sxs-lookup"><span data-stu-id="ab1bb-104">For example:</span></span>  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 <span data-ttu-id="ab1bb-105">匿名型のインスタンスの作成にも使用します。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-105">It is also used to create instances of anonymous types:</span></span>  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 <span data-ttu-id="ab1bb-106">`new` 演算子は値型の既定コンストラクターの呼び出しにも使用します。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-106">The `new` operator is also used to invoke the default constructor for value types.</span></span> <span data-ttu-id="ab1bb-107">例:</span><span class="sxs-lookup"><span data-stu-id="ab1bb-107">For example:</span></span>  
  
```csharp
int i = new int();  
```  
  
 <span data-ttu-id="ab1bb-108">上記のステートメントでは、`i` は `int` 型の既定値 `0` に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-108">In the preceding statement, `i` is initialized to `0`, which is the default value for the type `int`.</span></span> <span data-ttu-id="ab1bb-109">このステートメントは次のステートメントと同じ効果があります。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-109">The statement has the same effect as the following:</span></span>  
  
```csharp
int i = 0;  
```  
  
 <span data-ttu-id="ab1bb-110">既定値の一覧については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-110">For a complete list of default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="ab1bb-111">すべての値型には暗黙的に既定のパブリック コンストラクターがあるため、[構造体](../../../csharp/language-reference/keywords/struct.md) に対して既定のコンストラクターを宣言するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-111">Remember that it is an error to declare a default constructor for a [struct](../../../csharp/language-reference/keywords/struct.md) because every value type implicitly has a public default constructor.</span></span> <span data-ttu-id="ab1bb-112">パラメーター付きのコンストラクターを構造体型で宣言し、その初期値を設定することは可能ですが、これが必要になるのは、既定値以外の値が必要な場合のみです。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-112">It is possible to declare parameterized constructors on a struct type to set its initial values, but this is only necessary if values other than the default are required.</span></span>  
  
 <span data-ttu-id="ab1bb-113">構造体などの値型オブジェクトと、クラスなどの参照型オブジェクトは両方とも自動的に破棄されますが、値型オブジェクトは含まれているコンテキストが破棄されたときに破棄され、参照型オブジェクトはそれに対する最後の参照が削除された後、ガベージ コレクターによって随時破棄されます。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-113">Both value-type objects such as structs and reference-type objects such as classes are destroyed automatically, but value-type objects are destroyed when their containing context is destroyed, whereas reference-type objects are destroyed by the garbage collector at an unspecified time after the last reference to them is removed.</span></span> <span data-ttu-id="ab1bb-114">ファイル ハンドルなどのリソース、またはネットワーク接続を含む型の場合、格納されているリソースができるだけ早く解放されるように、決定的なクリーンアップを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-114">For types that contain resources such as file handles, or network connections, it is desirable to employ deterministic cleanup to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="ab1bb-115">詳細については、「[using ステートメント](../../../csharp/language-reference/keywords/using-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-115">For more information, see [using Statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span>  
  
 <span data-ttu-id="ab1bb-116">`new` 演算子はオーバーロードできません。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-116">The `new` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="ab1bb-117">`new` 演算子によるメモリの割り当てが失敗した場合、<xref:System.OutOfMemoryException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-117">If the `new` operator fails to allocate memory, it throws the exception, <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab1bb-118">例</span><span class="sxs-lookup"><span data-stu-id="ab1bb-118">Example</span></span>  
 <span data-ttu-id="ab1bb-119">次の例では、`struct` オブジェクトおよびクラス オブジェクトは、`new` 演算子を使用して作成、初期化され、そのあと値が代入されます。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-119">In the following example, a `struct` object and a class object are created and initialized by using the `new` operator and then assigned values.</span></span> <span data-ttu-id="ab1bb-120">既定値と代入値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-120">The default and the assigned values are displayed.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 <span data-ttu-id="ab1bb-121">この例では、文字列の既定値は `null` です。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-121">Notice in the example that the default value of a string is `null`.</span></span> <span data-ttu-id="ab1bb-122">このため、文字列の既定値は表示されません。</span><span class="sxs-lookup"><span data-stu-id="ab1bb-122">Therefore, it is not displayed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ab1bb-123">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="ab1bb-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ab1bb-124">参照</span><span class="sxs-lookup"><span data-stu-id="ab1bb-124">See Also</span></span>  
 [<span data-ttu-id="ab1bb-125">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="ab1bb-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ab1bb-126">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ab1bb-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ab1bb-127">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="ab1bb-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ab1bb-128">演算子のキーワード</span><span class="sxs-lookup"><span data-stu-id="ab1bb-128">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="ab1bb-129">new</span><span class="sxs-lookup"><span data-stu-id="ab1bb-129">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="ab1bb-130">匿名型</span><span class="sxs-lookup"><span data-stu-id="ab1bb-130">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
