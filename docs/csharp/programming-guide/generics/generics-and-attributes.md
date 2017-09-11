---
title: "ジェネリックと属性 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
caps.latest.revision: 13
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
ms.openlocfilehash: 5136ae928a3a4b6f8ec4d86100d695f958d55858
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="87d6a-102">ジェネリックと属性 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="87d6a-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="87d6a-103">属性は、非ジェネリック型の場合と同様に、ジェネリック型に適用できます。</span><span class="sxs-lookup"><span data-stu-id="87d6a-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="87d6a-104">属性の適用については、「[属性](../../../csharp/programming-guide/concepts/attributes/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87d6a-104">For more information on applying attributes, see [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="87d6a-105">カスタム属性は、型引数が与えられないオープン ジェネリック型と、すべての型パラメーターに引数が与えられる、構築クローズ ジェネリック型のみ参照が許可されます。</span><span class="sxs-lookup"><span data-stu-id="87d6a-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="87d6a-106">次の例では、このカスタム属性が使用されています。</span><span class="sxs-lookup"><span data-stu-id="87d6a-106">The following examples use this custom attribute:</span></span>  
  
 <span data-ttu-id="87d6a-107">[!code-cs[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="87d6a-107">[!code-cs[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]</span></span>  
  
 <span data-ttu-id="87d6a-108">属性は、オープン ジェネリック型を参照できます。</span><span class="sxs-lookup"><span data-stu-id="87d6a-108">An attribute can reference an open generic type:</span></span>  
  
 <span data-ttu-id="87d6a-109">[!code-cs[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="87d6a-109">[!code-cs[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]</span></span>  
  
 <span data-ttu-id="87d6a-110">適切な数のコンマを利用し、複数の型パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="87d6a-110">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="87d6a-111">この例では、`GenericClass2` には 2 つの型パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="87d6a-111">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 <span data-ttu-id="87d6a-112">[!code-cs[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="87d6a-112">[!code-cs[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]</span></span>  
  
 <span data-ttu-id="87d6a-113">属性は、構築クローズ ジェネリック型を参照できます。</span><span class="sxs-lookup"><span data-stu-id="87d6a-113">An attribute can reference a closed constructed generic type:</span></span>  
  
 <span data-ttu-id="87d6a-114">[!code-cs[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="87d6a-114">[!code-cs[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]</span></span>  
  
 <span data-ttu-id="87d6a-115">ジェネリック型パラメーターを参照する属性は、コンパイル時エラーを引き起こします。</span><span class="sxs-lookup"><span data-stu-id="87d6a-115">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 <span data-ttu-id="87d6a-116">[!code-cs[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="87d6a-116">[!code-cs[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]</span></span>  
  
 <span data-ttu-id="87d6a-117">ジェネリック型は <xref:System.Attribute> から継承できません。</span><span class="sxs-lookup"><span data-stu-id="87d6a-117">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 <span data-ttu-id="87d6a-118">[!code-cs[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="87d6a-118">[!code-cs[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]</span></span>  
  
 <span data-ttu-id="87d6a-119">実行時にジェネリック型または型パラメーターに関する情報を取得するには、<xref:System.Reflection> のメソッドを利用できます。</span><span class="sxs-lookup"><span data-stu-id="87d6a-119">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="87d6a-120">詳細については、「[ジェネリックとリフレクション](../../../csharp/programming-guide/generics/generics-and-reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87d6a-120">For more information, see [Generics and Reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87d6a-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="87d6a-121">See Also</span></span>  
 <span data-ttu-id="87d6a-122">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="87d6a-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="87d6a-123">[ジェネリック](../../../csharp/programming-guide/generics/index.md) </span><span class="sxs-lookup"><span data-stu-id="87d6a-123">[Generics](../../../csharp/programming-guide/generics/index.md) </span></span>  
 [<span data-ttu-id="87d6a-124">属性</span><span class="sxs-lookup"><span data-stu-id="87d6a-124">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)

