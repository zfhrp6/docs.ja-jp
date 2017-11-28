---
title: "ジェネリックと属性 (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5535334514afb0b9891dfce2e0cc0a0e95526069
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="09e3e-102">ジェネリックと属性 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="09e3e-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="09e3e-103">属性は、非ジェネリック型の場合と同様に、ジェネリック型に適用できます。</span><span class="sxs-lookup"><span data-stu-id="09e3e-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="09e3e-104">属性の適用については、「[属性](../../../csharp/programming-guide/concepts/attributes/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09e3e-104">For more information on applying attributes, see [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="09e3e-105">カスタム属性は、型引数が与えられないオープン ジェネリック型と、すべての型パラメーターに引数が与えられる、構築クローズ ジェネリック型のみ参照が許可されます。</span><span class="sxs-lookup"><span data-stu-id="09e3e-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="09e3e-106">次の例では、このカスタム属性が使用されています。</span><span class="sxs-lookup"><span data-stu-id="09e3e-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 <span data-ttu-id="09e3e-107">属性は、オープン ジェネリック型を参照できます。</span><span class="sxs-lookup"><span data-stu-id="09e3e-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 <span data-ttu-id="09e3e-108">適切な数のコンマを利用し、複数の型パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="09e3e-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="09e3e-109">この例では、`GenericClass2` には 2 つの型パラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="09e3e-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 <span data-ttu-id="09e3e-110">属性は、構築クローズ ジェネリック型を参照できます。</span><span class="sxs-lookup"><span data-stu-id="09e3e-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 <span data-ttu-id="09e3e-111">ジェネリック型パラメーターを参照する属性は、コンパイル時エラーを引き起こします。</span><span class="sxs-lookup"><span data-stu-id="09e3e-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 <span data-ttu-id="09e3e-112">ジェネリック型は <xref:System.Attribute> から継承できません。</span><span class="sxs-lookup"><span data-stu-id="09e3e-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 <span data-ttu-id="09e3e-113">実行時にジェネリック型または型パラメーターに関する情報を取得するには、<xref:System.Reflection> のメソッドを利用できます。</span><span class="sxs-lookup"><span data-stu-id="09e3e-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="09e3e-114">詳細については、「[ジェネリックとリフレクション](../../../csharp/programming-guide/generics/generics-and-reflection.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09e3e-114">For more information, see [Generics and Reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e3e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="09e3e-115">See Also</span></span>  
 [<span data-ttu-id="09e3e-116">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="09e3e-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="09e3e-117">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="09e3e-117">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="09e3e-118">属性</span><span class="sxs-lookup"><span data-stu-id="09e3e-118">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)
