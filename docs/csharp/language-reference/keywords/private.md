---
title: "private (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- private_CSharpKeyword
- private
dev_langs:
- CSharp
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: 17
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
ms.openlocfilehash: c18fd87b12bf3f7f1a1d1ef0dfded8643308169c
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="private-c-reference"></a><span data-ttu-id="23c63-102">private (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="23c63-102">private (C# Reference)</span></span>
<span data-ttu-id="23c63-103">`private` キーワードはメンバー アクセス修飾子です。</span><span class="sxs-lookup"><span data-stu-id="23c63-103">The `private` keyword is a member access modifier.</span></span> <span data-ttu-id="23c63-104">プライベート アクセスは、最も制限の多いアクセス レベルです。</span><span class="sxs-lookup"><span data-stu-id="23c63-104">Private access is the least permissive access level.</span></span> <span data-ttu-id="23c63-105">次の例に示すように、プライベート メンバーは、宣言されているクラスまたは構造体の本体内でのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="23c63-105">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  
  
 <span data-ttu-id="23c63-106">同じ本体にある入れ子にされた型も、プライベート メンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="23c63-106">Nested types in the same body can also access those private members.</span></span>  
  
 <span data-ttu-id="23c63-107">プライベート メンバーへの参照を、クラスの外側やメンバーが宣言されているクラスの外側から行った場合は、コンパイル時のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="23c63-107">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>  
  
 <span data-ttu-id="23c63-108">`private` とその他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」と「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23c63-108">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23c63-109">例</span><span class="sxs-lookup"><span data-stu-id="23c63-109">Example</span></span>  
 <span data-ttu-id="23c63-110">この例では、`Employee` クラスに `name` と `salary` という 2 つのプライベート データ メンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="23c63-110">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="23c63-111">これらのメンバーは、プライベート メンバーであり、メンバー メソッド以外からはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="23c63-111">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="23c63-112">`GetName` と `Salary` というパブリック メソッドが追加されており、プライベート メンバーへの制御されたアクセスが許可されています。</span><span class="sxs-lookup"><span data-stu-id="23c63-112">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="23c63-113">`name` メンバーはパブリック メソッドを通してアクセスされ、`salary` メンバーはパブリックな読み取り専用プロパティを通してアクセスされます</span><span class="sxs-lookup"><span data-stu-id="23c63-113">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="23c63-114">(詳細については、「[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="23c63-114">(See [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) for more information.)</span></span>  
  
 <span data-ttu-id="23c63-115">[!code-cs[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="23c63-115">[!code-cs[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="23c63-116">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="23c63-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="23c63-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="23c63-117">See Also</span></span>  
 <span data-ttu-id="23c63-118">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="23c63-118">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="23c63-119">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="23c63-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="23c63-120">[C# のキーワード](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="23c63-120">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="23c63-121">[アクセス修飾子](../../../csharp/language-reference/keywords/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="23c63-121">[Access Modifiers](../../../csharp/language-reference/keywords/access-modifiers.md) </span></span>  
 <span data-ttu-id="23c63-122">[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md) </span><span class="sxs-lookup"><span data-stu-id="23c63-122">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) </span></span>  
 <span data-ttu-id="23c63-123">[修飾子](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="23c63-123">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 <span data-ttu-id="23c63-124">[public](../../../csharp/language-reference/keywords/public.md) </span><span class="sxs-lookup"><span data-stu-id="23c63-124">[public](../../../csharp/language-reference/keywords/public.md) </span></span>  
 <span data-ttu-id="23c63-125">[protected](../../../csharp/language-reference/keywords/protected.md) </span><span class="sxs-lookup"><span data-stu-id="23c63-125">[protected](../../../csharp/language-reference/keywords/protected.md) </span></span>  
 [<span data-ttu-id="23c63-126">internal</span><span class="sxs-lookup"><span data-stu-id="23c63-126">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)

