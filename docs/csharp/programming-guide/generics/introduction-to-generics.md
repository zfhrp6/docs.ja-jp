---
title: ジェネリックの概要 (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], about generics
ms.assetid: a1ad761e-42f7-41dd-a62f-452a2de26b9d
ms.openlocfilehash: 892b6bfe5cf18bde91221bb8b2fa7ca7a2813870
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321247"
---
# <a name="introduction-to-generics-c-programming-guide"></a><span data-ttu-id="f1e6f-102">ジェネリックの概要 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f1e6f-102">Introduction to Generics (C# Programming Guide)</span></span>
<span data-ttu-id="f1e6f-103">ジェネリックのクラスとメソッドは、非ジェネリックでは不可能な方法で、再利用性、タイプ セーフ、効率性を同時に実現しています。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-103">Generic classes and methods combine reusability, type safety and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="f1e6f-104">ジェネリックは、コレクションとそれを操作するメソッドとともに使用されるのが通常です。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-104">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="f1e6f-105">.NET Framework クラス ライブラリのバージョン 2.0 には、いくつかの新しいジェネリック ベースのコレクション クラスを含む新しい名前空間、<xref:System.Collections.Generic> が用意されています。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-105">Version 2.0 of the .NET Framework class library provides a new namespace, <xref:System.Collections.Generic>, which contains several new generic-based collection classes.</span></span> <span data-ttu-id="f1e6f-106">.NET Framework 2.0 以降を対象とするすべてのアプリケーションでは、<xref:System.Collections.ArrayList> などの以前の非ジェネリック コレクション クラスの代わりに、新しいジェネリック コレクション クラスを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-106">It is recommended that all applications that target the .NET Framework 2.0 and later use the new generic collection classes instead of the older non-generic counterparts such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="f1e6f-107">詳細については、「[.NET のジェネリック](../../../standard/generics/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-107">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>  
  
 <span data-ttu-id="f1e6f-108">もちろん、カスタムのジェネリック型やジェネリック メソッドを作成して、タイプ セーフで効率的な独自の汎用ソリューションや設計パターンを実現することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-108">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="f1e6f-109">次のコード例では、デモンストレーション用の簡単なジェネリックのリンク リスト クラスを示します。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-109">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="f1e6f-110">(通常は、独自のクラスを作成するのではなく、.NET Framework クラス ライブラリに用意されている <xref:System.Collections.Generic.List%601> クラスを使用してください。)この例では、通常、具体的な型を使用して、リストに格納する項目の型を示す場面で、型パラメーター `T` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-110">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by the .NET Framework class library instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="f1e6f-111">このパラメーターは、次のように使用されています。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-111">It is used in the following ways:</span></span>  
  
-   <span data-ttu-id="f1e6f-112">`AddHead` メソッドのメソッド パラメーターの型として使用。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-112">As the type of a method parameter in the `AddHead` method.</span></span>  
  
-   <span data-ttu-id="f1e6f-113">入れ子になった `Node` クラスの `Data` プロパティの戻り値の型として使用。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-113">As the return type of the `Data` property in the nested `Node` class.</span></span>  
  
-   <span data-ttu-id="f1e6f-114">入れ子になったクラスのプライベート メンバー `data` の型として使用。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-114">As the type of the private member `data` in the nested class.</span></span>  
  
 <span data-ttu-id="f1e6f-115">T は、入れ子になった `Node` クラスで使用できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-115">Note that T is available to the nested `Node` class.</span></span> <span data-ttu-id="f1e6f-116">`GenericList<T>` が `GenericList<int>` のような具象型でインスタンス化されると、`T` の部分はそれぞれ `int` に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-116">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#2](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_1.cs)]  
  
 <span data-ttu-id="f1e6f-117">次のコード例では、クライアント コードでジェネリックの `GenericList<T>` クラスを使用して、整数のリストを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-117">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="f1e6f-118">このコードの型引数を変更するだけで、文字列やその他の任意のカスタム型のリストを作成するように簡単に修正できます。</span><span class="sxs-lookup"><span data-stu-id="f1e6f-118">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#3](../../../csharp/programming-guide/generics/codesnippet/CSharp/introduction-to-generics_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f1e6f-119">参照</span><span class="sxs-lookup"><span data-stu-id="f1e6f-119">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="f1e6f-120">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f1e6f-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f1e6f-121">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="f1e6f-121">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
