---
title: "as (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4f2964f32a4139ffeb6d51b761f1176a57c5be6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="as-c-reference"></a><span data-ttu-id="566bb-102">as (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="566bb-102">as (C# Reference)</span></span>
<span data-ttu-id="566bb-103">`as` 演算子を使用して、互換性のある参照型または [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)間で特定の型変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="566bb-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="566bb-104">次のコードは一例を示しています。</span><span class="sxs-lookup"><span data-stu-id="566bb-104">The following code shows an example.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="566bb-105">コメント</span><span class="sxs-lookup"><span data-stu-id="566bb-105">Remarks</span></span>  
 <span data-ttu-id="566bb-106">`as` 演算子はキャスト演算と似ています。</span><span class="sxs-lookup"><span data-stu-id="566bb-106">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="566bb-107">ただし、変換が可能でない場合、`as` は例外を発生させる代わりに `null` を返します。</span><span class="sxs-lookup"><span data-stu-id="566bb-107">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="566bb-108">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="566bb-108">Consider the following example:</span></span>  
  
```  
expression as type  
```  
  
 <span data-ttu-id="566bb-109">このコードは次の式と同等ですが、`expression` 変数は 1 回しか評価されません。</span><span class="sxs-lookup"><span data-stu-id="566bb-109">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="566bb-110">なお、`as` 演算子は、参照変換、null 許容変換またはボックス変換のみ実行します。</span><span class="sxs-lookup"><span data-stu-id="566bb-110">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="566bb-111">`as` 演算子は、ユーザー定義変換など、他の変換を実行できないため、ユーザー定義変換を実行するには、代わりにキャスト式を使用します。</span><span class="sxs-lookup"><span data-stu-id="566bb-111">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="566bb-112">例</span><span class="sxs-lookup"><span data-stu-id="566bb-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="566bb-113">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="566bb-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="566bb-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="566bb-114">See Also</span></span>  
 [<span data-ttu-id="566bb-115">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="566bb-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="566bb-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="566bb-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="566bb-117">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="566bb-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="566bb-118">is</span><span class="sxs-lookup"><span data-stu-id="566bb-118">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="566bb-119">?: 演算子</span><span class="sxs-lookup"><span data-stu-id="566bb-119">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
 [<span data-ttu-id="566bb-120">演算子のキーワード</span><span class="sxs-lookup"><span data-stu-id="566bb-120">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
