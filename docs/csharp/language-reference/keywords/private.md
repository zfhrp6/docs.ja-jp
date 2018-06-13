---
title: private (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 89bc23e91bf693f0a95b75dffe2399cb7e865b50
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171864"
---
# <a name="private-c-reference"></a><span data-ttu-id="a953b-102">private (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="a953b-102">private (C# Reference)</span></span>
<span data-ttu-id="a953b-103">`private` キーワードはメンバー アクセス修飾子です。</span><span class="sxs-lookup"><span data-stu-id="a953b-103">The `private` keyword is a member access modifier.</span></span> 
   
 > <span data-ttu-id="a953b-104">このページでは、`private` アクセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a953b-104">This page covers `private` access.</span></span> <span data-ttu-id="a953b-105">`private` キーワードも [`private protected`](./private-protected.md) アクセス修飾子に含まれます。</span><span class="sxs-lookup"><span data-stu-id="a953b-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>
  
<span data-ttu-id="a953b-106">プライベート アクセスは、最も制限の多いアクセス レベルです。</span><span class="sxs-lookup"><span data-stu-id="a953b-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="a953b-107">次の例に示すように、プライベート メンバーは、宣言されているクラスまたは構造体の本体内でのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a953b-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>  
  
```csharp  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 <span data-ttu-id="a953b-108">同じ本体にある入れ子にされた型も、プライベート メンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a953b-108">Nested types in the same body can also access those private members.</span></span>  
  
 <span data-ttu-id="a953b-109">プライベート メンバーへの参照を、クラスの外側やメンバーが宣言されているクラスの外側から行った場合は、コンパイル時のエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a953b-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>  
  
 <span data-ttu-id="a953b-110">`private` とその他のアクセス修飾子の比較については、「[アクセシビリティ レベル](../../../csharp/language-reference/keywords/accessibility-levels.md)」と「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a953b-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a953b-111">例</span><span class="sxs-lookup"><span data-stu-id="a953b-111">Example</span></span>  
 <span data-ttu-id="a953b-112">この例では、`Employee` クラスに `name` と `salary` という 2 つのプライベート データ メンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a953b-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="a953b-113">これらのメンバーは、プライベート メンバーであり、メンバー メソッド以外からはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="a953b-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="a953b-114">`GetName` と `Salary` というパブリック メソッドが追加されており、プライベート メンバーへの制御されたアクセスが許可されています。</span><span class="sxs-lookup"><span data-stu-id="a953b-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="a953b-115">`name` メンバーはパブリック メソッドを通してアクセスされ、`salary` メンバーはパブリックな読み取り専用プロパティを通してアクセスされます</span><span class="sxs-lookup"><span data-stu-id="a953b-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="a953b-116">(詳細については、「[プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="a953b-116">(See [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) for more information.)</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a953b-117">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="a953b-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a953b-118">参照</span><span class="sxs-lookup"><span data-stu-id="a953b-118">See Also</span></span>  
 [<span data-ttu-id="a953b-119">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="a953b-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a953b-120">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="a953b-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a953b-121">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="a953b-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a953b-122">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="a953b-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="a953b-123">アクセシビリティ レベル</span><span class="sxs-lookup"><span data-stu-id="a953b-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="a953b-124">修飾子</span><span class="sxs-lookup"><span data-stu-id="a953b-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="a953b-125">public</span><span class="sxs-lookup"><span data-stu-id="a953b-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="a953b-126">protected</span><span class="sxs-lookup"><span data-stu-id="a953b-126">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="a953b-127">internal</span><span class="sxs-lookup"><span data-stu-id="a953b-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
