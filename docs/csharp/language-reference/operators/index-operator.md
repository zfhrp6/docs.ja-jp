---
title: "[] 演算子 (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '[]_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: 20
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
ms.openlocfilehash: b49d41af0dd4dc34b1b74c62ce8779aa31d69f77
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="4b07e-102">[] 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="4b07e-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="4b07e-103">角かっこ (`[]`) は、配列、インデクサー、属性に使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b07e-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="4b07e-104">また、ポインターと共に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="4b07e-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b07e-105">コメント</span><span class="sxs-lookup"><span data-stu-id="4b07e-105">Remarks</span></span>  
 <span data-ttu-id="4b07e-106">配列型は、型の後に `[]` が続きます。</span><span class="sxs-lookup"><span data-stu-id="4b07e-106">An array type is a type followed by `[]`:</span></span>  
  
 <span data-ttu-id="4b07e-107">[!code-cs[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="4b07e-107">[!code-cs[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]</span></span>  
  
 <span data-ttu-id="4b07e-108">配列の要素にアクセスするには、次のように、目的の要素のインデックスを角かっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="4b07e-108">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 <span data-ttu-id="4b07e-109">[!code-cs[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="4b07e-109">[!code-cs[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]</span></span>  
  
 <span data-ttu-id="4b07e-110">配列のインデックスが範囲外の場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="4b07e-110">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="4b07e-111">配列インデックス演算子は、オーバーロードできません。ただし、型はインデクサーと、1 つ以上のパラメーターを受け取るプロパティを定義できます。</span><span class="sxs-lookup"><span data-stu-id="4b07e-111">The array indexing operator cannot be overloaded; however, types can define indexers, and properties that take one or more parameters.</span></span> <span data-ttu-id="4b07e-112">インデクサーのパラメーターは配列のインデックスと同じように角かっこで囲みますが、整数でなければならない配列のインデックスとは異なり、インデクサーのパラメーターは任意の型として宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="4b07e-112">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="4b07e-113">たとえば、.NET Framework では、任意の型のキーと値を関連付ける `Hashtable` 型を定義しています。</span><span class="sxs-lookup"><span data-stu-id="4b07e-113">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 <span data-ttu-id="4b07e-114">[!code-cs[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="4b07e-114">[!code-cs[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]</span></span>  
  
 <span data-ttu-id="4b07e-115">角かっこは、[属性](../../../csharp/programming-guide/concepts/attributes/index.md)を指定するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="4b07e-115">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 <span data-ttu-id="4b07e-116">[!code-cs[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="4b07e-116">[!code-cs[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]</span></span>  
  
 <span data-ttu-id="4b07e-117">角かっこを使用して、ポインターにインデックスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="4b07e-117">You can use square brackets to index off a pointer:</span></span>  
  
 <span data-ttu-id="4b07e-118">[!code-cs[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="4b07e-118">[!code-cs[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]</span></span>  
  
 <span data-ttu-id="4b07e-119">境界のチェックは行われません。</span><span class="sxs-lookup"><span data-stu-id="4b07e-119">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="4b07e-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="4b07e-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4b07e-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b07e-121">See Also</span></span>  
 <span data-ttu-id="4b07e-122">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="4b07e-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="4b07e-123">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="4b07e-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="4b07e-124">[C# 演算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="4b07e-124">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="4b07e-125">[配列](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="4b07e-125">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 <span data-ttu-id="4b07e-126">[インデクサー](../../../csharp/programming-guide/indexers/index.md) </span><span class="sxs-lookup"><span data-stu-id="4b07e-126">[Indexers](../../../csharp/programming-guide/indexers/index.md) </span></span>  
 <span data-ttu-id="4b07e-127">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="4b07e-127">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 [<span data-ttu-id="4b07e-128">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="4b07e-128">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)

