---
title: "ボックス化とボックス化解除 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.boxing
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
caps.latest.revision: 34
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c783ac60735ba25db2736bd9469063c0897be22f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="9e29b-102">ボックス化とボックス化解除 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="9e29b-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="9e29b-103">ボックス化とは、[値型](../../../csharp/language-reference/keywords/value-types.md)から `object` 型、またはその値型によって実装されている任意のインターフェイス型へ変換するプロセスのことです。</span><span class="sxs-lookup"><span data-stu-id="9e29b-103">Boxing is the process of converting a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="9e29b-104">CLR により値型がボックス化されるとき、値は System.Object 内部にラップされ、マネージ ヒープに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9e29b-104">When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap.</span></span> <span data-ttu-id="9e29b-105">ボックス化解除すると、値型がオブジェクトから抽出されます。</span><span class="sxs-lookup"><span data-stu-id="9e29b-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="9e29b-106">ボックス化は暗黙的に行われ、ボックス化解除すると明示的になります。</span><span class="sxs-lookup"><span data-stu-id="9e29b-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="9e29b-107">ボックス化とボックス化解除の概念は、任意の型の値をオブジェクトとして扱うという C# の型システムの統一されたビューに基づいています。</span><span class="sxs-lookup"><span data-stu-id="9e29b-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="9e29b-108">次の例では、整数の変数 `i` を "*ボックス化*" し、オブジェクト `o` に代入しています。</span><span class="sxs-lookup"><span data-stu-id="9e29b-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 <span data-ttu-id="9e29b-109">[!code-cs[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9e29b-109">[!code-cs[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]</span></span>  
  
 <span data-ttu-id="9e29b-110">次に、オブジェクト `o` は、次のようにボックス化解除し、整数の変数 `i` に代入できます。</span><span class="sxs-lookup"><span data-stu-id="9e29b-110">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 <span data-ttu-id="9e29b-111">[!code-cs[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="9e29b-111">[!code-cs[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]</span></span>  
  
 <span data-ttu-id="9e29b-112">次のコードは、C# でのボックス化の使用例です。</span><span class="sxs-lookup"><span data-stu-id="9e29b-112">The following examples illustrate how boxing is used in C#.</span></span>  
  
 <span data-ttu-id="9e29b-113">[!code-cs[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="9e29b-113">[!code-cs[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]</span></span>  
  
## <a name="performance"></a><span data-ttu-id="9e29b-114">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="9e29b-114">Performance</span></span>  
 <span data-ttu-id="9e29b-115">簡単な代入と比べて、ボックス化およびボックス化解除は負荷の大きいプロセスです。</span><span class="sxs-lookup"><span data-stu-id="9e29b-115">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="9e29b-116">値型をボックス化するときは、新しいオブジェクトを割り当てて構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e29b-116">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="9e29b-117">ボックス化ほどではありませんが、ボックス化解除に必要なキャストも大きな負荷がかかります。</span><span class="sxs-lookup"><span data-stu-id="9e29b-117">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="9e29b-118">詳しくは、「[パフォーマンス](https://msdn.microsoft.com/library/ms173196(VS.110).aspx)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9e29b-118">For more information, see [Performance](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="9e29b-119">ボックス化</span><span class="sxs-lookup"><span data-stu-id="9e29b-119">Boxing</span></span>  
 <span data-ttu-id="9e29b-120">ボックス化は、値型をガベージ コレクション ヒープに格納するために使用します。</span><span class="sxs-lookup"><span data-stu-id="9e29b-120">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="9e29b-121">ボックス化とは、[値型](../../../csharp/language-reference/keywords/value-types.md)から `object` 型、またはその値型によって実装されている任意のインターフェイス型への暗黙の変換のことです。</span><span class="sxs-lookup"><span data-stu-id="9e29b-121">Boxing is an implicit conversion of a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="9e29b-122">値型をボックス化すると、オブジェクト インスタンスがヒープに割り当てられ、値が新しいオブジェクトにコピーされます。</span><span class="sxs-lookup"><span data-stu-id="9e29b-122">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="9e29b-123">値型の変数の宣言例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9e29b-123">Consider the following declaration of a value-type variable:</span></span>  
  
 <span data-ttu-id="9e29b-124">[!code-cs[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="9e29b-124">[!code-cs[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]</span></span>  
  
 <span data-ttu-id="9e29b-125">次のステートメントは、変数 `i` にボックス化を暗黙的に適用します。</span><span class="sxs-lookup"><span data-stu-id="9e29b-125">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 <span data-ttu-id="9e29b-126">[!code-cs[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="9e29b-126">[!code-cs[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]</span></span>  
  
 <span data-ttu-id="9e29b-127">このステートメントによって、ヒープ上にある `o` 型の値を参照するオブジェクト参照 `int` がスタック上に作成されます。</span><span class="sxs-lookup"><span data-stu-id="9e29b-127">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="9e29b-128">この値は、変数 `i` に割り当てられた値型の値のコピーです。</span><span class="sxs-lookup"><span data-stu-id="9e29b-128">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="9e29b-129">2 つの変数 `i` と `o` の違いを次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="9e29b-129">The difference between the two variables, `i` and `o`, is illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="9e29b-130">![BoxingConversion グラフィック](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="9e29b-130">![BoxingConversion graphic](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span></span>  
<span data-ttu-id="9e29b-131">ボックス化</span><span class="sxs-lookup"><span data-stu-id="9e29b-131">Boxing Conversion</span></span>  
  
 <span data-ttu-id="9e29b-132">次の例に示すように、明示的にボックス化を実行することもできますが、明示的なボックス化は不要です。</span><span class="sxs-lookup"><span data-stu-id="9e29b-132">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 <span data-ttu-id="9e29b-133">[!code-cs[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="9e29b-133">[!code-cs[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]</span></span>  
  
## <a name="description"></a><span data-ttu-id="9e29b-134">説明</span><span class="sxs-lookup"><span data-stu-id="9e29b-134">Description</span></span>  
 <span data-ttu-id="9e29b-135">ここでは、ボックス化を使用して整数の変数 `i` をオブジェクト `o` に変換する例を示します。</span><span class="sxs-lookup"><span data-stu-id="9e29b-135">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="9e29b-136">変換後に、変数 `i` の値を `123` から `456` に変更します。</span><span class="sxs-lookup"><span data-stu-id="9e29b-136">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="9e29b-137">この例は、元の値型とボックス化されたオブジェクトが別個のメモリ位置を使用するため、それぞれ別々の値を格納できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="9e29b-137">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e29b-138">例</span><span class="sxs-lookup"><span data-stu-id="9e29b-138">Example</span></span>  
 <span data-ttu-id="9e29b-139">[!code-cs[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="9e29b-139">[!code-cs[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]</span></span>  
  
## <a name="unboxing"></a><span data-ttu-id="9e29b-140">ボックス化解除</span><span class="sxs-lookup"><span data-stu-id="9e29b-140">Unboxing</span></span>  
 <span data-ttu-id="9e29b-141">ボックス化解除とは、`object` 型から[値型](../../../csharp/language-reference/keywords/value-types.md)へ、またはインターフェイス型からそのインターフェイスを実装している値型への明示的な変換のことです。</span><span class="sxs-lookup"><span data-stu-id="9e29b-141">Unboxing is an explicit conversion from the type `object` to a [value type](../../../csharp/language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="9e29b-142">ボックス化解除では、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="9e29b-142">An unboxing operation consists of:</span></span>  
  
-   <span data-ttu-id="9e29b-143">オブジェクト インスタンスが、指定された値型のボックス化された値であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9e29b-143">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
-   <span data-ttu-id="9e29b-144">インスタンスの値を値型の変数にコピーします。</span><span class="sxs-lookup"><span data-stu-id="9e29b-144">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="9e29b-145">次のステートメントに、ボックス化およびボックス化解除の両方を示します。</span><span class="sxs-lookup"><span data-stu-id="9e29b-145">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 <span data-ttu-id="9e29b-146">[!code-cs[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="9e29b-146">[!code-cs[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]</span></span>  
  
 <span data-ttu-id="9e29b-147">前のステートメントの結果は、次の図に示すとおりです。</span><span class="sxs-lookup"><span data-stu-id="9e29b-147">The following figure demonstrates the result of the previous statements.</span></span>  
  
 <span data-ttu-id="9e29b-148">![ボックス化解除変換グラフィック](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="9e29b-148">![UnBoxing Conversion graphic](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span></span>  
<span data-ttu-id="9e29b-149">ボックス化解除</span><span class="sxs-lookup"><span data-stu-id="9e29b-149">Unboxing Conversion</span></span>  
  
 <span data-ttu-id="9e29b-150">実行時に値型のボックス化解除を成功させるには、ボックス化解除の対象項目が、同じ値型のインスタンスのボックス化によって既に作成済みのオブジェクトへの参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e29b-150">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="9e29b-151">`null` をボックス化解除しようとすると <xref:System.NullReferenceException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="9e29b-151">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="9e29b-152">互換性のない値型への参照をボックス化解除しようとすると、<xref:System.InvalidCastException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="9e29b-152">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e29b-153">例</span><span class="sxs-lookup"><span data-stu-id="9e29b-153">Example</span></span>  
 <span data-ttu-id="9e29b-154">次の例は、無効なボックス化解除の結果、`InvalidCastException` が発生する場合を示しています。</span><span class="sxs-lookup"><span data-stu-id="9e29b-154">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="9e29b-155">`try` と `catch` を使用すると、エラーの発生時にエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9e29b-155">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 <span data-ttu-id="9e29b-156">[!code-cs[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="9e29b-156">[!code-cs[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]</span></span>  
  
 <span data-ttu-id="9e29b-157">このプログラムの出力を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9e29b-157">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="9e29b-158">エラーを修正するには、次のステートメントを変更します。</span><span class="sxs-lookup"><span data-stu-id="9e29b-158">If you change the statement:</span></span>  
  
```  
int j = (short) o;  
```  
  
 <span data-ttu-id="9e29b-159">この行を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="9e29b-159">to:</span></span>  
  
```  
int j = (int) o;  
```  
  
 <span data-ttu-id="9e29b-160">ステートメントを変更すると、変換が実行されて次の出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="9e29b-160">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="9e29b-161">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="9e29b-161">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="9e29b-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e29b-162">Related Sections</span></span>  
 <span data-ttu-id="9e29b-163">詳細情報</span><span class="sxs-lookup"><span data-stu-id="9e29b-163">For more information:</span></span>  
  
-   [<span data-ttu-id="9e29b-164">参照型</span><span class="sxs-lookup"><span data-stu-id="9e29b-164">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="9e29b-165">値型</span><span class="sxs-lookup"><span data-stu-id="9e29b-165">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="9e29b-166">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="9e29b-166">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e29b-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e29b-167">See Also</span></span>  
 [<span data-ttu-id="9e29b-168">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="9e29b-168">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

