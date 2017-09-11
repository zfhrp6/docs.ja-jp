---
title: "ジェネリック (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
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
ms.sourcegitcommit: 1e548df4de2c07934313311a7ffcfae82be76000
ms.openlocfilehash: de81058173b0985577474e8601aa84d4e83336a5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/28/2017

---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="e5d7f-102">ジェネリック (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="e5d7f-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="e5d7f-103">ジェネリックは、バージョン 2.0 の C# 言語と共通言語ランタイム (CLR) に追加されたものです。</span><span class="sxs-lookup"><span data-stu-id="e5d7f-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="e5d7f-104">ジェネリックは、.NET Framework に型パラメーターという概念を導入します。型パラメーターを使用すると、クラスやメソッドがクライアント コードで宣言され、インスタンス化されるまで、1 つ以上の型の指定を遅延させるクラスとメソッドを設計できます。</span><span class="sxs-lookup"><span data-stu-id="e5d7f-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="e5d7f-105">たとえば、ジェネリック型パラメーター T を使用すると、次に示すようにランタイムのキャストやボックス化操作のコストやリスクを負わずに他のクライアント コードで使用できる単一のクラスを記述できます。</span><span class="sxs-lookup"><span data-stu-id="e5d7f-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 <span data-ttu-id="e5d7f-106">[!code-cs[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e5d7f-106">[!code-cs[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]</span></span>  
  
## <a name="generics-overview"></a><span data-ttu-id="e5d7f-107">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="e5d7f-107">Generics Overview</span></span>  
  
-   <span data-ttu-id="e5d7f-108">ジェネリック型は、コードの再利用、タイプ セーフ、およびパフォーマンスを最大化するために使用します。</span><span class="sxs-lookup"><span data-stu-id="e5d7f-108">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="e5d7f-109">ジェネリックの最も一般的な用途は、コレクション クラスの作成です。</span><span class="sxs-lookup"><span data-stu-id="e5d7f-109">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="e5d7f-110">.NET Framework クラス ライブラリには、複数の新しいジェネリック コレクション クラスが <xref:System.Collections.Generic> 名前空間に含まれています。</span><span class="sxs-lookup"><span data-stu-id="e5d7f-110">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="e5d7f-111"><xref:System.Collections> 名前空間の <xref:System.Collections.ArrayList> などのクラスの代わりとして、できる限りこれらを使用してください。</span><span class="sxs-lookup"><span data-stu-id="e5d7f-111">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="e5d7f-112">独自のジェネリック インターフェイス、クラス、メソッド、イベントおよびデリゲートを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="e5d7f-112">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="e5d7f-113">ジェネリック クラスは、特定のデータ型のメソッドへのアクセスを有効にするように制限できます。</span><span class="sxs-lookup"><span data-stu-id="e5d7f-113">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="e5d7f-114">ジェネリック データ型で使用される型に関する情報は、実行時にリフレクションを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="e5d7f-114">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e5d7f-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5d7f-115">Related Sections</span></span>  
 <span data-ttu-id="e5d7f-116">詳細情報</span><span class="sxs-lookup"><span data-stu-id="e5d7f-116">For more information:</span></span>  
  
-   [<span data-ttu-id="e5d7f-117">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="e5d7f-117">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="e5d7f-118">ジェネリックの利点</span><span class="sxs-lookup"><span data-stu-id="e5d7f-118">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="e5d7f-119">ジェネリック型パラメーター</span><span class="sxs-lookup"><span data-stu-id="e5d7f-119">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="e5d7f-120">型パラメーターの制約</span><span class="sxs-lookup"><span data-stu-id="e5d7f-120">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="e5d7f-121">ジェネリック クラス</span><span class="sxs-lookup"><span data-stu-id="e5d7f-121">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="e5d7f-122">ジェネリック インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e5d7f-122">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="e5d7f-123">ジェネリック メソッド</span><span class="sxs-lookup"><span data-stu-id="e5d7f-123">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="e5d7f-124">汎用デリゲート</span><span class="sxs-lookup"><span data-stu-id="e5d7f-124">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="e5d7f-125">C++ テンプレートと C# ジェネリックの違い</span><span class="sxs-lookup"><span data-stu-id="e5d7f-125">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="e5d7f-126">ジェネリックとリフレクション</span><span class="sxs-lookup"><span data-stu-id="e5d7f-126">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="e5d7f-127">ランタイムのジェネリック</span><span class="sxs-lookup"><span data-stu-id="e5d7f-127">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [<span data-ttu-id="e5d7f-128">.NET Framework クラス ライブラリのジェネリック</span><span class="sxs-lookup"><span data-stu-id="e5d7f-128">Generics in the .NET Framework Class Library</span></span>](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="e5d7f-129">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="e5d7f-129">C# Language Specification</span></span>  
 <span data-ttu-id="e5d7f-130">詳細については、「[C# 言語の仕様](../../../csharp/language-reference/language-specification/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5d7f-130">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5d7f-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5d7f-131">See Also</span></span>  
 <span data-ttu-id="e5d7f-132"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="e5d7f-132"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="e5d7f-133">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e5d7f-133">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e5d7f-134">[型](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="e5d7f-134">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 <span data-ttu-id="e5d7f-135">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md) </span><span class="sxs-lookup"><span data-stu-id="e5d7f-135">[\<typeparam>](../../../csharp/programming-guide/xmldoc/typeparam.md) </span></span>  
 [<span data-ttu-id="e5d7f-136">\<typeparamref></span><span class="sxs-lookup"><span data-stu-id="e5d7f-136">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)

