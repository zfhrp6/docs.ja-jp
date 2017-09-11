---
title: "ジェネリック型の型パラメーター (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], type parameters
- type parameters [C#]
ms.assetid: a03b0ab2-0606-4b41-b7bf-e64d5bb4d18f
caps.latest.revision: 23
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
ms.openlocfilehash: ce1024215a381afb3a7b42f2127fe5e8c212d378
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="generic-type-parameters-c-programming-guide"></a><span data-ttu-id="12a9d-102">ジェネリック型の型パラメーター (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="12a9d-102">Generic Type Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="12a9d-103">ジェネリック型またはメソッド定義で、型パラメーターは、ジェネリック型の変数をインスタンス化するときにクライアントが指定する特定の型のためのプレースホルダーになります。</span><span class="sxs-lookup"><span data-stu-id="12a9d-103">In a generic type or method definition, a type parameters is a placeholder for a specific type that a client specifies when they instantiate a variable of the generic type.</span></span> <span data-ttu-id="12a9d-104">「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」に記載されている `GenericList<T>` などのジェネリック クラスは、実際は型でないため、そのままでは使用できません。これは型の設計図のようなものです。</span><span class="sxs-lookup"><span data-stu-id="12a9d-104">A generic class, such as `GenericList<T>` listed in [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md), cannot be used as-is because it is not really a type; it is more like a blueprint for a type.</span></span> <span data-ttu-id="12a9d-105">`GenericList<T>` を使用するには、クライアント コードで構築された型を宣言し、インスタンス化する必要があります。山かっこ内に型引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="12a9d-105">To use `GenericList<T>`, client code must declare and instantiate a constructed type by specifying a type argument inside the angle brackets.</span></span> <span data-ttu-id="12a9d-106">この特定のクラスの型引数は、コンパイラで認識されるあらゆる型にすることができます。</span><span class="sxs-lookup"><span data-stu-id="12a9d-106">The type argument for this particular class can be any type recognized by the compiler.</span></span> <span data-ttu-id="12a9d-107">構築された型インスタンスは、次のようにさまざまな型引数を利用し、いくつでも作成できます。</span><span class="sxs-lookup"><span data-stu-id="12a9d-107">Any number of constructed type instances can be created, each one using a different type argument, as follows:</span></span>  
  
 <span data-ttu-id="12a9d-108">[!code-cs[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="12a9d-108">[!code-cs[csProgGuideGenerics#7](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_1.cs)]</span></span>  
  
 <span data-ttu-id="12a9d-109">`GenericList<T>` の各インスタンスでは、クラス内のすべての `T` は実行時に型引数に置換されます。</span><span class="sxs-lookup"><span data-stu-id="12a9d-109">In each of these instances of `GenericList<T>`, every occurrence of `T` in the class will be substituted at run time with the type argument.</span></span> <span data-ttu-id="12a9d-110">この置換を使用し、単一クラス定義を使用してタイプ セーフで効率的なオブジェクトを 3 つ作成しました。</span><span class="sxs-lookup"><span data-stu-id="12a9d-110">By means of this substitution, we have created three separate type-safe and efficient objects using a single class definition.</span></span> <span data-ttu-id="12a9d-111">この置換が CLR で実行されるしくみについては、「[ランタイムのジェネリック](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12a9d-111">For more information on how this substitution is performed by the CLR, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
## <a name="type-parameter-naming-guidelines"></a><span data-ttu-id="12a9d-112">型パラメーターの名前付けガイドライン</span><span class="sxs-lookup"><span data-stu-id="12a9d-112">Type Parameter Naming Guidelines</span></span>  
  
-   <span data-ttu-id="12a9d-113">1 文字の名前でも完全に説明され、説明的な名前を付けることに意味がない場合を除き、ジェネリック型パラメーターには**説明的な名前を付けてください**。</span><span class="sxs-lookup"><span data-stu-id="12a9d-113">**Do** name generic type parameters with descriptive names, unless a single letter name is completely self explanatory and a descriptive name would not add value.</span></span>  
  
     <span data-ttu-id="12a9d-114">[!code-cs[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="12a9d-114">[!code-cs[csProgGuideGenerics#8](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_2.cs)]</span></span>  
  
-   <span data-ttu-id="12a9d-115">1 文字の型パラメーターを持つ型の型パラメーター名として T を利用することを**検討してください**。</span><span class="sxs-lookup"><span data-stu-id="12a9d-115">**Consider** using T as the type parameter name for types with one single letter type parameter.</span></span>  
  
     <span data-ttu-id="12a9d-116">[!code-cs[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="12a9d-116">[!code-cs[csProgGuideGenerics#9](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_3.cs)]</span></span>  
  
-   <span data-ttu-id="12a9d-117">型パラメーターの説明的な名前には "T" という**接頭辞を付けてください**。</span><span class="sxs-lookup"><span data-stu-id="12a9d-117">**Do** prefix descriptive type parameter names with "T".</span></span>  
  
     <span data-ttu-id="12a9d-118">[!code-cs[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="12a9d-118">[!code-cs[csProgGuideGenerics#10](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-type-parameters_4.cs)]</span></span>  
  
-   <span data-ttu-id="12a9d-119">型パラメーターに与えられた制約をパラメーターの名前で示唆することを**検討してください**。</span><span class="sxs-lookup"><span data-stu-id="12a9d-119">**Consider** indicating constraints placed on a type parameter in the name of parameter.</span></span> <span data-ttu-id="12a9d-120">たとえば、`ISession` に制約されているパラメーターの名前を `TSession` にします。</span><span class="sxs-lookup"><span data-stu-id="12a9d-120">For example, a parameter constrained to `ISession` may be called `TSession`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a9d-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="12a9d-121">See Also</span></span>  
 <span data-ttu-id="12a9d-122"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="12a9d-122"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="12a9d-123">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="12a9d-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="12a9d-124">[ジェネリック](../../../csharp/programming-guide/generics/index.md) </span><span class="sxs-lookup"><span data-stu-id="12a9d-124">[Generics](../../../csharp/programming-guide/generics/index.md) </span></span>  
 [<span data-ttu-id="12a9d-125">C++ テンプレートと C# ジェネリックの違い</span><span class="sxs-lookup"><span data-stu-id="12a9d-125">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)

