---
title: '[] 演算子 (C# リファレンス)'
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 65908bb3bcd8912ef81fc094e5958ae8dc4ae1f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286030"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6017d-102">[] 演算子 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6017d-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="6017d-103">角かっこ (`[]`) は、配列、インデクサー、属性に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6017d-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="6017d-104">また、ポインターと共に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="6017d-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6017d-105">コメント</span><span class="sxs-lookup"><span data-stu-id="6017d-105">Remarks</span></span>  
 <span data-ttu-id="6017d-106">配列型は、型の後に `[]` が続きます。</span><span class="sxs-lookup"><span data-stu-id="6017d-106">An array type is a type followed by `[]`:</span></span>  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 <span data-ttu-id="6017d-107">配列の要素にアクセスするには、次のように、目的の要素のインデックスを角かっこで囲みます。</span><span class="sxs-lookup"><span data-stu-id="6017d-107">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 <span data-ttu-id="6017d-108">配列のインデックスが範囲外の場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="6017d-108">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="6017d-109">配列インデックス演算子は、オーバーロードできません。ただし、型はインデクサーと、1 つ以上のパラメーターを受け取るプロパティを定義できます。</span><span class="sxs-lookup"><span data-stu-id="6017d-109">The array indexing operator cannot be overloaded; however, types can define indexers, and properties that take one or more parameters.</span></span> <span data-ttu-id="6017d-110">インデクサーのパラメーターは配列のインデックスと同じように角かっこで囲みますが、整数でなければならない配列のインデックスとは異なり、インデクサーのパラメーターは任意の型として宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="6017d-110">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="6017d-111">たとえば、.NET Framework では、任意の型のキーと値を関連付ける `Hashtable` 型を定義しています。</span><span class="sxs-lookup"><span data-stu-id="6017d-111">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 <span data-ttu-id="6017d-112">角かっこは、[属性](../../../csharp/programming-guide/concepts/attributes/index.md)を指定するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="6017d-112">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 <span data-ttu-id="6017d-113">角かっこを使用して、ポインターにインデックスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="6017d-113">You can use square brackets to index off a pointer:</span></span>  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 <span data-ttu-id="6017d-114">境界のチェックは行われません。</span><span class="sxs-lookup"><span data-stu-id="6017d-114">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6017d-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="6017d-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6017d-116">参照</span><span class="sxs-lookup"><span data-stu-id="6017d-116">See Also</span></span>  
 [<span data-ttu-id="6017d-117">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="6017d-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6017d-118">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="6017d-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6017d-119">C# 演算子</span><span class="sxs-lookup"><span data-stu-id="6017d-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="6017d-120">配列</span><span class="sxs-lookup"><span data-stu-id="6017d-120">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="6017d-121">インデクサー</span><span class="sxs-lookup"><span data-stu-id="6017d-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="6017d-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="6017d-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="6017d-123">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="6017d-123">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
