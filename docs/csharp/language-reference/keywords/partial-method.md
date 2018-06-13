---
title: partial (メソッド) (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 29b5d442a1aa33babc24aee987e749c93a5ec727
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269042"
---
# <a name="partial-method-c-reference"></a><span data-ttu-id="8987b-102">partial (メソッド) (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="8987b-102">partial (Method) (C# Reference)</span></span>
<span data-ttu-id="8987b-103">部分メソッドには、部分型の一部に定義されたシグネチャ、および部分型の別の部分に定義された実装があります。</span><span class="sxs-lookup"><span data-stu-id="8987b-103">A partial method has its signature defined in one part of a partial type, and its implementation defined in another part of the type.</span></span> <span data-ttu-id="8987b-104">部分メソッドを使用すると、イベント ハンドラーと同じように、開発者が実装するかどうかを決定できるメソッド フックをクラス デザイナーで提供できます。</span><span class="sxs-lookup"><span data-stu-id="8987b-104">Partial methods enable class designers to provide method hooks, similar to event handlers, that developers may decide to implement or not.</span></span> <span data-ttu-id="8987b-105">開発者が実装を指定しない場合、コンパイラはコンパイル時にシグネチャを削除します。</span><span class="sxs-lookup"><span data-stu-id="8987b-105">If the developer does not supply an implementation, the compiler removes the signature at compile time.</span></span> <span data-ttu-id="8987b-106">部分メソッドには次の条件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="8987b-106">The following conditions apply to partial methods:</span></span>  
  
-   <span data-ttu-id="8987b-107">部分型の両方の部分のシグネチャが一致する必要がある。</span><span class="sxs-lookup"><span data-stu-id="8987b-107">Signatures in both parts of the partial type must match.</span></span>  
  
-   <span data-ttu-id="8987b-108">メソッドが void を返す必要がある。</span><span class="sxs-lookup"><span data-stu-id="8987b-108">The method must return void.</span></span>  
  
-   <span data-ttu-id="8987b-109">アクセス修飾子はできない。</span><span class="sxs-lookup"><span data-stu-id="8987b-109">No access modifiers are allowed.</span></span> <span data-ttu-id="8987b-110">部分メソッドは暗黙的にプライベート メソッドになる。</span><span class="sxs-lookup"><span data-stu-id="8987b-110">Partial methods are implicitly private.</span></span>  
  
 <span data-ttu-id="8987b-111">部分クラスの 2 つの部分に定義された部分メソッドを次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="8987b-111">The following example shows a partial method defined in two parts of a partial class:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/partial-method_1.cs)]  
  
 <span data-ttu-id="8987b-112">詳細については、「[部分クラスと部分メソッド](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8987b-112">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8987b-113">参照</span><span class="sxs-lookup"><span data-stu-id="8987b-113">See Also</span></span>  
 [<span data-ttu-id="8987b-114">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="8987b-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8987b-115">partial (型)</span><span class="sxs-lookup"><span data-stu-id="8987b-115">partial (Type)</span></span>](../../../csharp/language-reference/keywords/partial-type.md)
