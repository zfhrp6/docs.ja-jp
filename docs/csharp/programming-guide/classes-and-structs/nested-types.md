---
title: "入れ子にされた型 (C# プログラミング ガイド)"
ms.date: 2017-07-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 853ec746d9be01ed63d7a229ca86e99d9f192374
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="nested-types-c-programming-guide"></a><span data-ttu-id="c251d-102">入れ子にされた型 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="c251d-102">Nested Types (C# Programming Guide)</span></span>
<span data-ttu-id="c251d-103">[クラス](../../../csharp/language-reference/keywords/class.md)や[構造体](../../../csharp/language-reference/keywords/struct.md)の中で定義された型は、入れ子にされた型と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="c251d-103">A type defined within a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is called a nested type.</span></span> <span data-ttu-id="c251d-104">例:</span><span class="sxs-lookup"><span data-stu-id="c251d-104">For example:</span></span>  
  
<span data-ttu-id="c251d-105">[!code-cs[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c251d-105">[!code-cs[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]</span></span>  
  
<span data-ttu-id="c251d-106">外側の型がクラスまたは構造体のいずれであっても、入れ子にされた型は既定で [private](../../../csharp/language-reference/keywords/private.md) になります。これらにはその包含する型からのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c251d-106">Regardless of whether the outer type is a class or a struct, nested types default to [private](../../../csharp/language-reference/keywords/private.md); they are accessible only from their containing type.</span></span> <span data-ttu-id="c251d-107">前の例では、`Nested` クラスは外部の型にアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="c251d-107">In the previous example, the `Nested` class is inaccessible to external types.</span></span> 

<span data-ttu-id="c251d-108">次のように、[アクセス修飾子](../../language-reference/keywords/access-modifiers.md)を指定して、入れ子にされた型のアクセシビリティを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="c251d-108">You can also specify an [access modifier](../../language-reference/keywords/access-modifiers.md) to define the accessibility of a nested type, as follows:</span></span>

- <span data-ttu-id="c251d-109">**クラス**の入れ子にされた型は、[public](../../../csharp/language-reference/keywords/public.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、`protected internal`、または [private](../../../csharp/language-reference/keywords/private.md) のいずれかが可能です。</span><span class="sxs-lookup"><span data-stu-id="c251d-109">Nested types of a **class** can be [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), `protected internal`, or [private](../../../csharp/language-reference/keywords/private.md).</span></span> 

   <span data-ttu-id="c251d-110">ただし、[シール クラス](../../language-reference/keywords/sealed.md)内で `protected` または `protected internal` の入れ子にされたクラスを定義すると、コンパイラの警告 [CS0628](../../misc/cs0628.md)、"新規のプロテクト メンバーがシール クラスで宣言されました" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c251d-110">However, defining a `protected` or `protected internal` nested class inside a [sealed class](../../language-reference/keywords/sealed.md) generates compiler warning [CS0628](../../misc/cs0628.md), "new protected member declared in sealed class."</span></span>
  
- <span data-ttu-id="c251d-111">**構造体**の入れ子にされた型は、は、[public](../../../csharp/language-reference/keywords/public.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、または [private](../../../csharp/language-reference/keywords/private.md) のいずれかが可能です。</span><span class="sxs-lookup"><span data-stu-id="c251d-111">Nested types of a **struct** can be [public](../../../csharp/language-reference/keywords/public.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md).</span></span>
  
<span data-ttu-id="c251d-112">次の例では、`Nested` クラスを public にします。</span><span class="sxs-lookup"><span data-stu-id="c251d-112">The following example makes the `Nested` class public:</span></span>
  
<span data-ttu-id="c251d-113">[!code-cs[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c251d-113">[!code-cs[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]</span></span>  
  
 <span data-ttu-id="c251d-114">入れ子にされた型 (内側の型) は、包含する型 (外側の型) にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c251d-114">The nested, or inner, type can access the containing, or outer, type.</span></span> <span data-ttu-id="c251d-115">包含する型にアクセスするには、その型を引数として入れ子にされた型のコンストラクターに渡します。</span><span class="sxs-lookup"><span data-stu-id="c251d-115">To access the containing type, pass it as an argument to the constructor of the nested type.</span></span> <span data-ttu-id="c251d-116">例:</span><span class="sxs-lookup"><span data-stu-id="c251d-116">For example:</span></span>  
  
 <span data-ttu-id="c251d-117">[!code-cs[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="c251d-117">[!code-cs[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]</span></span>  
  
 <span data-ttu-id="c251d-118">入れ子にされた型は、包含する型にアクセス可能なすべてのメンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c251d-118">A nested type has access to all of the members that are accessible to its containing type.</span></span> <span data-ttu-id="c251d-119">入れ子にされた型は、継承されたプロテクト メンバーを含む、包含する型のプライベート メンバーとプロテクト メンバーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c251d-119">It can access private and protected members of the containing type, including any inherited protected members.</span></span>  
  
 <span data-ttu-id="c251d-120">上記の宣言では、クラス `Nested` の完全名は `Container.Nested` です。</span><span class="sxs-lookup"><span data-stu-id="c251d-120">In the previous declaration, the full name of class `Nested` is `Container.Nested`.</span></span> <span data-ttu-id="c251d-121">これは、次のように入れ子になったクラスの新しいインスタンスを作成するときに使用される名前です。</span><span class="sxs-lookup"><span data-stu-id="c251d-121">This is the name used to create a new instance of the nested class, as follows:</span></span>  
  
 <span data-ttu-id="c251d-122">[!code-cs[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="c251d-122">[!code-cs[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c251d-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c251d-123">See Also</span></span>  
 <span data-ttu-id="c251d-124">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c251d-124">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="c251d-125">[クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="c251d-125">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="c251d-126">[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="c251d-126">[Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) </span></span>  
 [<span data-ttu-id="c251d-127">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="c251d-127">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)

