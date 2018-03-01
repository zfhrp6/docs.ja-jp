---
title: "入れ子にされた型 (C# プログラミング ガイド)"
ms.date: 07/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab13c68b638062ab89c90dbfc51b51b8d72d3bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="5d61e-102">入れ子にされた型 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5d61e-102">Nested Types (C# Programming Guide)</span></span>
<span data-ttu-id="5d61e-103">[クラス](../../../csharp/language-reference/keywords/class.md)や[構造体](../../../csharp/language-reference/keywords/struct.md)の中で定義された型は、入れ子にされた型と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="5d61e-103">A type defined within a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is called a nested type.</span></span> <span data-ttu-id="5d61e-104">例:</span><span class="sxs-lookup"><span data-stu-id="5d61e-104">For example:</span></span>  
  
[!code-csharp[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
<span data-ttu-id="5d61e-105">外側の型がクラスまたは構造体のいずれであっても、入れ子にされた型は既定で [private](../../../csharp/language-reference/keywords/private.md) になります。これらにはその包含する型からのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5d61e-105">Regardless of whether the outer type is a class or a struct, nested types default to [private](../../../csharp/language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="5d61e-106">前の例では、`Nested` クラスは外部の型にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="5d61e-106">In the previous example, the `Nested` class is inaccessible to external types.</span></span> 

<span data-ttu-id="5d61e-107">次のように、[アクセス修飾子](../../language-reference/keywords/access-modifiers.md)を指定して、入れ子にされた型のアクセシビリティを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="5d61e-107">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="5d61e-108">入れ子にされた型の**クラス**できます[パブリック](../../../csharp/language-reference/keywords/public.md)、[保護](../../../csharp/language-reference/keywords/protected.md)、[内部](../../../csharp/language-reference/keywords/internal.md)、[内部保護](../../../csharp/language-reference/keywords/protected-internal.md)、[プライベート](../../../csharp/language-reference/keywords/private.md)または[保護されたプライベート](../../../csharp/language-reference/keywords/private-protected.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d61e-108">Nested types of a **class** can be [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md), [private](../../../csharp/language-reference/keywords/private.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> 

   <span data-ttu-id="5d61e-109">ただし、定義、 `protected`、`protected internal`または`private protected`内のクラスを入れ子になった、[クラスをシール](../../language-reference/keywords/sealed.md)コンパイラの警告が生成されます[CS0628](../../misc/cs0628.md)、「新規のプロテクト メンバーはシール クラスで宣言されています」。</span><span class="sxs-lookup"><span data-stu-id="5d61e-109">However, defining a `protected`, `protected internal` or `private protected` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="5d61e-110">**構造体**の入れ子にされた型は、は、[public](../../../csharp/language-reference/keywords/public.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、または [private](../../../csharp/language-reference/keywords/private.md) のいずれかが可能です。</span><span class="sxs-lookup"><span data-stu-id="5d61e-110">Nested types of a **struct** can be [public](../../../csharp/language-reference/keywords/public.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md).</span></span>
  
<span data-ttu-id="5d61e-111">次の例では、`Nested` クラスを public にします。</span><span class="sxs-lookup"><span data-stu-id="5d61e-111">The following example makes the `Nested` class public:</span></span>
  
[!code-csharp[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 <span data-ttu-id="5d61e-112">入れ子にされた型 (内側の型) は、包含する型 (外側の型) にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5d61e-112">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="5d61e-113">包含する型にアクセスするには、その型を引数として入れ子にされた型のコンストラクターに渡します。</span><span class="sxs-lookup"><span data-stu-id="5d61e-113">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="5d61e-114">例:</span><span class="sxs-lookup"><span data-stu-id="5d61e-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 <span data-ttu-id="5d61e-115">入れ子にされた型は、包含する型にアクセス可能なすべてのメンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5d61e-115">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="5d61e-116">入れ子にされた型は、継承されたプロテクト メンバーを含む、包含する型のプライベート メンバーとプロテクト メンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5d61e-116">It can access private and protected members of the containing type, including any inherited protected members.</span></span>  
  
 <span data-ttu-id="5d61e-117">上記の宣言では、クラス `Nested` の完全名は `Container.Nested` です。</span><span class="sxs-lookup"><span data-stu-id="5d61e-117">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="5d61e-118">これは、次のように入れ子になったクラスの新しいインスタンスを作成するときに使用される名前です。</span><span class="sxs-lookup"><span data-stu-id="5d61e-118">This is the name used to create a new instance of the nested class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5d61e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d61e-119">See Also</span></span>  
 [<span data-ttu-id="5d61e-120">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5d61e-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5d61e-121">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="5d61e-121">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="5d61e-122">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="5d61e-122">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="5d61e-123">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="5d61e-123">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
