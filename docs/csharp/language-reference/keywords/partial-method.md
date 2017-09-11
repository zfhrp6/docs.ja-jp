---
title: "partial (メソッド) (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- partialmethod_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
caps.latest.revision: 26
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
ms.openlocfilehash: b6f8ecca01ebf681c906b73abefc94e9e45b8700
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="partial-method-c-reference"></a><span data-ttu-id="f15d5-102">partial (メソッド) (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f15d5-102">partial (Method) (C# Reference)</span></span>
<span data-ttu-id="f15d5-103">部分メソッドには、部分型の一部に定義されたシグネチャ、および部分型の別の部分に定義された実装があります。</span><span class="sxs-lookup"><span data-stu-id="f15d5-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="f15d5-104">部分メソッドを使用すると、イベント ハンドラーと同じように、開発者が実装するかどうかを決定できるメソッド フックをクラス デザイナーで提供できます。</span><span class="sxs-lookup"><span data-stu-id="f15d5-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="f15d5-105">開発者が実装を指定しない場合、コンパイラはコンパイル時にシグネチャを削除します。</span><span class="sxs-lookup"><span data-stu-id="f15d5-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="f15d5-106">部分メソッドには次の条件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="f15d5-106">The following conditions apply to partial methods:</span></span>  
  
-   <span data-ttu-id="f15d5-107">部分型の両方の部分のシグネチャが一致する必要がある。</span><span class="sxs-lookup"><span data-stu-id="f15d5-107">Signatures in both parts of the partial type must match.</span></span>  
  
-   <span data-ttu-id="f15d5-108">メソッドが void を返す必要がある。</span><span class="sxs-lookup"><span data-stu-id="f15d5-108">The method must return void.</span></span>  
  
-   <span data-ttu-id="f15d5-109">アクセス修飾子はできない。</span><span class="sxs-lookup"><span data-stu-id="f15d5-109">No access modifiers are allowed.</span></span> <span data-ttu-id="f15d5-110">部分メソッドは暗黙的にプライベート メソッドになる。</span><span class="sxs-lookup"><span data-stu-id="f15d5-110">Partial methods are implicitly private.</span></span>  
  
 <span data-ttu-id="f15d5-111">部分クラスの 2 つの部分に定義された部分メソッドを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="f15d5-111">The following example shows a partial method defined in two parts of a partial class:</span></span>  
  
 <span data-ttu-id="f15d5-112">[!code-cs[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f15d5-112">[!code-cs[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]</span></span>  
  
 <span data-ttu-id="f15d5-113">詳細については、「[部分クラスと部分メソッド](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f15d5-113">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15d5-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f15d5-114">See Also</span></span>  
 <span data-ttu-id="f15d5-115">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f15d5-115">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 [<span data-ttu-id="f15d5-116">partial (型)</span><span class="sxs-lookup"><span data-stu-id="f15d5-116">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)

