---
title: as (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
ms.openlocfilehash: 092c30a858df7baeb35bdf28bae53802fb0916d4
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="as-c-reference"></a><span data-ttu-id="95c26-102">as (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="95c26-102">as (C# Reference)</span></span>
<span data-ttu-id="95c26-103">`as` 演算子を使用して、互換性のある参照型または [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)間で特定の型変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="95c26-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="95c26-104">次のコードは一例を示しています。</span><span class="sxs-lookup"><span data-stu-id="95c26-104">The following code shows an example.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="95c26-105">コメント</span><span class="sxs-lookup"><span data-stu-id="95c26-105">Remarks</span></span>  
 <span data-ttu-id="95c26-106">`as` 演算子はキャスト演算と似ています。</span><span class="sxs-lookup"><span data-stu-id="95c26-106">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="95c26-107">ただし、変換が可能でない場合、`as` は例外を発生させる代わりに `null` を返します。</span><span class="sxs-lookup"><span data-stu-id="95c26-107">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="95c26-108">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="95c26-108">Consider the following example:</span></span>  
  
```csharp  
expression as type  
```  
  
 <span data-ttu-id="95c26-109">このコードは次の式と同等ですが、`expression` 変数は 1 回しか評価されません。</span><span class="sxs-lookup"><span data-stu-id="95c26-109">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```csharp  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="95c26-110">なお、`as` 演算子は、参照変換、null 許容変換またはボックス変換のみ実行します。</span><span class="sxs-lookup"><span data-stu-id="95c26-110">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="95c26-111">`as` 演算子は、ユーザー定義変換など、他の変換を実行できないため、ユーザー定義変換を実行するには、代わりにキャスト式を使用します。</span><span class="sxs-lookup"><span data-stu-id="95c26-111">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95c26-112">例</span><span class="sxs-lookup"><span data-stu-id="95c26-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="95c26-113">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="95c26-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="95c26-114">参照</span><span class="sxs-lookup"><span data-stu-id="95c26-114">See Also</span></span>  
 [<span data-ttu-id="95c26-115">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="95c26-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="95c26-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="95c26-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="95c26-117">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="95c26-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="95c26-118">is</span><span class="sxs-lookup"><span data-stu-id="95c26-118">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="95c26-119">?: 演算子</span><span class="sxs-lookup"><span data-stu-id="95c26-119">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
 [<span data-ttu-id="95c26-120">演算子のキーワード</span><span class="sxs-lookup"><span data-stu-id="95c26-120">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
