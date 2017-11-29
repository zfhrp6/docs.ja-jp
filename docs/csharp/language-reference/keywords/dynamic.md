---
title: "dynamic (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e3bf51ab62e195f7a5d1f0641f62380977c731ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="dynamic-c-reference"></a><span data-ttu-id="41ab4-102">dynamic (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="41ab4-102">dynamic (C# Reference)</span></span>
<span data-ttu-id="41ab4-103">`dynamic` 型を使用すると、コンパイル時の型チェックをバイパスする処理が可能になります。</span><span class="sxs-lookup"><span data-stu-id="41ab4-103">The `dynamic` type enables the operations in which it occurs to bypass compile-time type checking.</span></span> <span data-ttu-id="41ab4-104">代わりに、演算は実行時に解決されます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-104">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="41ab4-105">`dynamic` 型により、Office オートメーション API などの COM API、IronPython ライブラリなどの動的 API、および HTML ドキュメント オブジェクト モデル (DOM: Document Object Model) へのアクセスが容易になります。</span><span class="sxs-lookup"><span data-stu-id="41ab4-105">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, and also to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="41ab4-106">ほとんどの環境で、`dynamic` 型は `object` 型のように動作します。</span><span class="sxs-lookup"><span data-stu-id="41ab4-106">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="41ab4-107">ただし、`dynamic` 型の式を含む演算はコンパイラによって解決または型チェックされません。</span><span class="sxs-lookup"><span data-stu-id="41ab4-107">However, operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="41ab4-108">コンパイラは演算に関する情報をまとめてパッケージ化します。その情報が後で実行時に演算を評価するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-108">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="41ab4-109">このプロセスの過程で、`dynamic` 型の変数は `object` 型の変数にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-109">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="41ab4-110">そのため、`dynamic` 型はコンパイル時にのみ存在し、実行時には存在しません。</span><span class="sxs-lookup"><span data-stu-id="41ab4-110">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>  
  
 <span data-ttu-id="41ab4-111">`dynamic` 型の変数と `object` 型の変数の違いを次に示します。</span><span class="sxs-lookup"><span data-stu-id="41ab4-111">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="41ab4-112">コンパイル時に各変数の型を確認するには、`WriteLine` ステートメントの `dyn` または `obj` にマウス ポインターを置きます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-112">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="41ab4-113">IntelliSense 機能によって、`dyn` には **dynamic**、`obj` には **object** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-113">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]  
  
 <span data-ttu-id="41ab4-114">`WriteLine` ステートメントは `dyn` および `obj` の実行時の型を表示します。</span><span class="sxs-lookup"><span data-stu-id="41ab4-114">The `WriteLine` statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="41ab4-115">その時点では、両方が同じ整数型を持ちます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-115">At that point, both have the same type, integer.</span></span> <span data-ttu-id="41ab4-116">次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-116">The following output is produced:</span></span>  
  
 `System.Int32`  
  
 `System.Int32`  
  
 <span data-ttu-id="41ab4-117">コンパイル時の `dyn` と `obj` の違いを確認するには、前の例の宣言と `WriteLine` ステートメントの間に次の 2 行を追加します。</span><span class="sxs-lookup"><span data-stu-id="41ab4-117">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>  
  
```csharp  
dyn = dyn + 3;  
obj = obj + 3;  
```  
  
 <span data-ttu-id="41ab4-118">式 `obj + 3` に整数およびオブジェクトを追加しようとしたことに対してコンパイル エラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-118">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="41ab4-119">ただし、`dyn + 3` に関するエラーは報告されません。</span><span class="sxs-lookup"><span data-stu-id="41ab4-119">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="41ab4-120">`dyn` を含む式はコンパイル時にはチェックされません。これは、`dyn` の型が `dynamic` であるためです。</span><span class="sxs-lookup"><span data-stu-id="41ab4-120">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>  
  
## <a name="context"></a><span data-ttu-id="41ab4-121">コンテキスト</span><span class="sxs-lookup"><span data-stu-id="41ab4-121">Context</span></span>  
 <span data-ttu-id="41ab4-122">次の状況では、`dynamic` キーワードを直接記述するか、構築型のコンポーネントとして記述できます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-122">The `dynamic` keyword can appear directly or as a component of a constructed type in the following situations:</span></span>  
  
-   <span data-ttu-id="41ab4-123">宣言では、プロパティ、フィールド、インデクサー、パラメーター、戻り値、ローカル変数、または型制約として記述できます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-123">In declarations, as the type of a property, field, indexer, parameter, return value, local variable, or type constraint.</span></span> <span data-ttu-id="41ab4-124">次のクラス定義はさまざまな宣言で `dynamic` を使用します。</span><span class="sxs-lookup"><span data-stu-id="41ab4-124">The following class definition uses `dynamic` in several different declarations.</span></span>  
  
     [!code-csharp[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]  
  
-   <span data-ttu-id="41ab4-125">明示的な型変換で、変換先の型として記述できます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-125">In explicit type conversions, as the target type of a conversion.</span></span>  
  
     [!code-csharp[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]  
  
-   <span data-ttu-id="41ab4-126">`is` 演算子または `as` 演算子の右側、`typeof` への引数など、型が値として機能するコンテキストでは構築型の一部として記述できます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-126">In any context where types serve as values, such as on the right side of an `is` operator or an `as` operator, or as the argument to `typeof` as part of a constructed type.</span></span> <span data-ttu-id="41ab4-127">たとえば、次の式では `dynamic` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-127">For example, `dynamic` can be used in the following expressions.</span></span>  
  
     [!code-csharp[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="41ab4-128">例</span><span class="sxs-lookup"><span data-stu-id="41ab4-128">Example</span></span>  
 <span data-ttu-id="41ab4-129">さまざまな宣言で `dynamic` を使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="41ab4-129">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="41ab4-130">また、`Main` メソッドで、コンパイル時の型チェックと実行時の型チェックの違いを確認できます。</span><span class="sxs-lookup"><span data-stu-id="41ab4-130">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]  
  
 <span data-ttu-id="41ab4-131">使用例を含む詳細については、「[dynamic 型の使用](../../../csharp/programming-guide/types/using-type-dynamic.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41ab4-131">For more information and examples, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ab4-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="41ab4-132">See Also</span></span>  
 <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>  
 <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
 [<span data-ttu-id="41ab4-133">dynamic 型の使用</span><span class="sxs-lookup"><span data-stu-id="41ab4-133">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [<span data-ttu-id="41ab4-134">object</span><span class="sxs-lookup"><span data-stu-id="41ab4-134">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
 [<span data-ttu-id="41ab4-135">is</span><span class="sxs-lookup"><span data-stu-id="41ab4-135">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="41ab4-136">as</span><span class="sxs-lookup"><span data-stu-id="41ab4-136">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
 [<span data-ttu-id="41ab4-137">typeof</span><span class="sxs-lookup"><span data-stu-id="41ab4-137">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 [<span data-ttu-id="41ab4-138">方法: as 演算子と is 演算子を使用して安全にキャストする</span><span class="sxs-lookup"><span data-stu-id="41ab4-138">How to: Safely Cast by Using as and is Operators</span></span>](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)  
 [<span data-ttu-id="41ab4-139">チュートリアル: 動的オブジェクトの作成と使用</span><span class="sxs-lookup"><span data-stu-id="41ab4-139">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
