---
title: "as (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: 24
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
ms.openlocfilehash: 7a55c696ac295eee8d5d35ed56038f3c4a90b215
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="as-c-reference"></a><span data-ttu-id="00c3a-102">as (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="00c3a-102">as (C# Reference)</span></span>
<span data-ttu-id="00c3a-103">`as` 演算子を使用して、互換性のある参照型または [null 許容型](../../../csharp/programming-guide/nullable-types/index.md)間で特定の型変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="00c3a-103">You can use the `as` operator to perform certain types of conversions between compatible reference types or [nullable types](../../../csharp/programming-guide/nullable-types/index.md).</span></span> <span data-ttu-id="00c3a-104">次のコードは一例を示しています。</span><span class="sxs-lookup"><span data-stu-id="00c3a-104">The following code shows an example.</span></span>  
  
 <span data-ttu-id="00c3a-105">[!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="00c3a-105">[!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00c3a-106">コメント</span><span class="sxs-lookup"><span data-stu-id="00c3a-106">Remarks</span></span>  
 <span data-ttu-id="00c3a-107">`as` 演算子はキャスト演算と似ています。</span><span class="sxs-lookup"><span data-stu-id="00c3a-107">The `as` operator is like a cast operation.</span></span> <span data-ttu-id="00c3a-108">ただし、変換が可能でない場合、`as` は例外を発生させる代わりに `null` を返します。</span><span class="sxs-lookup"><span data-stu-id="00c3a-108">However, if the conversion isn't possible, `as` returns `null` instead of raising an exception.</span></span> <span data-ttu-id="00c3a-109">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="00c3a-109">Consider the following example:</span></span>  
  
```  
expression as type  
```  
  
 <span data-ttu-id="00c3a-110">このコードは次の式と同等ですが、`expression` 変数は 1 回しか評価されません。</span><span class="sxs-lookup"><span data-stu-id="00c3a-110">The code is equivalent to the following expression except that the `expression` variable is evaluated only one time.</span></span>  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 <span data-ttu-id="00c3a-111">なお、`as` 演算子は、参照変換、null 許容変換またはボックス変換のみ実行します。</span><span class="sxs-lookup"><span data-stu-id="00c3a-111">Note that the `as` operator performs only reference conversions, nullable conversions, and boxing conversions.</span></span> <span data-ttu-id="00c3a-112">`as` 演算子は、ユーザー定義変換など、他の変換を実行できないため、ユーザー定義変換を実行するには、代わりにキャスト式を使用します。</span><span class="sxs-lookup"><span data-stu-id="00c3a-112">The `as` operator can't perform other conversions, such as user-defined conversions, which should instead be performed by using cast expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00c3a-113">例</span><span class="sxs-lookup"><span data-stu-id="00c3a-113">Example</span></span>  
 <span data-ttu-id="00c3a-114">[!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="00c3a-114">[!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="00c3a-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="00c3a-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="00c3a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="00c3a-116">See Also</span></span>  
 <span data-ttu-id="00c3a-117">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="00c3a-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="00c3a-118">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="00c3a-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="00c3a-119">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="00c3a-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="00c3a-120">[is](../../../csharp/language-reference/keywords/is.md) </span><span class="sxs-lookup"><span data-stu-id="00c3a-120">[is](../../../csharp/language-reference/keywords/is.md) </span></span>  
 <span data-ttu-id="00c3a-121">[?: 演算子](../../../csharp/language-reference/operators/conditional-operator.md) </span><span class="sxs-lookup"><span data-stu-id="00c3a-121">[?: Operator](../../../csharp/language-reference/operators/conditional-operator.md) </span></span>  
 [<span data-ttu-id="00c3a-122">演算子のキーワード</span><span class="sxs-lookup"><span data-stu-id="00c3a-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)

