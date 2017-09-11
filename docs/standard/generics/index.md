---
title: ".NET Framework におけるジェネリック | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- generic methods, type inference
- generics [.NET Framework], collections
- generic interfaces [.NET Framework]
- constructed generic types
- nested generic types
- generic type definitions
- generic classes [.NET Framework]
- generics [.NET Framework], interfaces
- generics [.NET Framework], about
- generics [.NET Framework]
- generic collections [.NET Framework]
- generic delegates [.NET Framework]
- generic type arguments
- generics [.NET Framework], delegates
- generics [.NET Framework], features
- constraints [.NET Framework]
- generic types
- generic type parameters
ms.assetid: 2994d786-c5c7-4666-ab23-4c83129fe39c
caps.latest.revision: 23
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9e352489bb22b691d9024a651f3864d2604a90cd
ms.contentlocale: ja-jp
ms.lasthandoff: 05/02/2017

---
# <a name="generics-in-the-net-framework"></a><span data-ttu-id="39151-102">.NET Framework におけるジェネリック</span><span class="sxs-lookup"><span data-stu-id="39151-102">Generics in the .NET Framework</span></span>
<span data-ttu-id="39151-103"><a name="top"></a> ジェネリックを使用すると、操作対象のデータ型に厳密に合わせてメソッド、クラス、構造体、またはインターフェイスを調整できます。</span><span class="sxs-lookup"><span data-stu-id="39151-103"><a name="top"></a> Generics let you tailor a method, class, structure, or interface to the precise data type it acts upon.</span></span> <span data-ttu-id="39151-104">たとえば、任意の型のキーと値が許可される <xref:System.Collections.Hashtable> クラスを使用する代わりに、<xref:System.Collections.Generic.Dictionary%602> ジェネリック クラスを使用して、キーに使用できる型と、値に使用できる型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="39151-104">For example, instead of using the <xref:System.Collections.Hashtable> class, which allows keys and values to be of any type, you can use the <xref:System.Collections.Generic.Dictionary%602> generic class and specify the type allowed for the key and the type allowed for the value.</span></span> <span data-ttu-id="39151-105">ジェネリックの利点として、コードの再利用性やタイプ セーフの向上などを挙げることができます。</span><span class="sxs-lookup"><span data-stu-id="39151-105">Among the benefits of generics are increased code reusability and type safety.</span></span>  
  
 <span data-ttu-id="39151-106">このトピックでは、.NET Framework におけるジェネリックの概要と、ジェネリック型またはジェネリック メソッドの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="39151-106">This topic provides an overview of generics in the .NET Framework and a summary of generic types or methods.</span></span> <span data-ttu-id="39151-107">このチュートリアルは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="39151-107">It contains the following sections:</span></span>  
  
-   [<span data-ttu-id="39151-108">ジェネリックの定義と使用</span><span class="sxs-lookup"><span data-stu-id="39151-108">Defining and Using Generics</span></span>](#defining_and_using_generics)  
  
-   [<span data-ttu-id="39151-109">ジェネリックの用語</span><span class="sxs-lookup"><span data-stu-id="39151-109">Generics Terminology</span></span>](#generics_terminology)  
  
-   [<span data-ttu-id="39151-110">クラス ライブラリと言語サポート</span><span class="sxs-lookup"><span data-stu-id="39151-110">Class Library and Language Support</span></span>](#class_library_and_language_support)  
  
-   [<span data-ttu-id="39151-111">入れ子にされた型とジェネリック</span><span class="sxs-lookup"><span data-stu-id="39151-111">Nested Types and Generics</span></span>](#nested_types_and_generics)  
  
-   [<span data-ttu-id="39151-112">関連トピック</span><span class="sxs-lookup"><span data-stu-id="39151-112">Related Topics</span></span>](#related_topics)  
  
-   [<span data-ttu-id="39151-113">参照</span><span class="sxs-lookup"><span data-stu-id="39151-113">Reference</span></span>](#reference)  
  
<a name="defining_and_using_generics"></a>   
## <a name="defining-and-using-generics"></a><span data-ttu-id="39151-114">ジェネリックの定義と使用</span><span class="sxs-lookup"><span data-stu-id="39151-114">Defining and Using Generics</span></span>  
 <span data-ttu-id="39151-115">ジェネリックは、格納または使用される 1 つ以上の型のプレースホルダー (型パラメーター) を持つクラス、構造体、インターフェイス、およびメソッドです。</span><span class="sxs-lookup"><span data-stu-id="39151-115">Generics are classes, structures, interfaces, and methods that have placeholders (type parameters) for one or more of the types that they store or use.</span></span> <span data-ttu-id="39151-116">ジェネリック コレクション クラスでは、格納するオブジェクトの型のプレースホルダーとして、型パラメーターを使用することがあります。型パラメーターは、そのフィールドの型やそのメソッドのパラメーター型として出現します。</span><span class="sxs-lookup"><span data-stu-id="39151-116">A generic collection class might use a type parameter as a placeholder for the type of objects that it stores; the type parameters appear as the types of its fields and the parameter types of its methods.</span></span> <span data-ttu-id="39151-117">ジェネリック メソッドでは、その戻り値の型として、またはいずれかの仮パラメーターの型として、型パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="39151-117">A generic method might use its type parameter as the type of its return value or as the type of one of its formal parameters.</span></span> <span data-ttu-id="39151-118">単純なジェネリック クラスの定義を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="39151-118">The following code illustrates a simple generic class definition.</span></span>  
  
 <span data-ttu-id="39151-119">[!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="39151-119">[!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]</span></span>  
  
 <span data-ttu-id="39151-120">ジェネリック クラスのインスタンスを作成する場合は、型パラメーターを置き換える実際の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="39151-120">When you create an instance of a generic class, you specify the actual types to substitute for the type parameters.</span></span> <span data-ttu-id="39151-121">これで、構築されたジェネリック クラスと呼ばれる新しいジェネリック クラスが確立され、この中では、型パラメーターが、出現するすべての場所で、選択した型に置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="39151-121">This establishes a new generic class, referred to as a constructed generic class, with your chosen types substituted everywhere that the type parameters appear.</span></span> <span data-ttu-id="39151-122">次のコードに示すように、結果は選択した型に合わせたタイプ セーフなクラスになります。</span><span class="sxs-lookup"><span data-stu-id="39151-122">The result is a type-safe class that is tailored to your choice of types, as the following code illustrates.</span></span>  
  
 <span data-ttu-id="39151-123">[!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="39151-123">[!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]</span></span>  
  
<a name="generics_terminology"></a>   
### <a name="generics-terminology"></a><span data-ttu-id="39151-124">ジェネリックの用語</span><span class="sxs-lookup"><span data-stu-id="39151-124">Generics terminology</span></span>  
 <span data-ttu-id="39151-125">.NET Framework におけるジェネリックの説明では、次の用語が使用されます。</span><span class="sxs-lookup"><span data-stu-id="39151-125">The following terms are used to discuss generics in the .NET Framework:</span></span>  
  
-   <span data-ttu-id="39151-126">*ジェネリック型定義* は、テンプレートとして機能するクラス、構造体、またはインターフェイスの宣言で、格納または使用できる型のプレースホルダーを含みます。</span><span class="sxs-lookup"><span data-stu-id="39151-126">A *generic type definition* is a class, structure, or interface declaration that functions as a template, with placeholders for the types that it can contain or use.</span></span> <span data-ttu-id="39151-127">たとえば、<xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> クラスには、キーと値の 2 つの型を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="39151-127">For example, the <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> class can contain two types: keys and values.</span></span> <span data-ttu-id="39151-128">ジェネリック型定義は単なるテンプレートであるため、ジェネリック型定義のクラス、構造体、またはインターフェイスのインスタンスを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="39151-128">Because a generic type definition is only a template, you cannot create instances of a class, structure, or interface that is a generic type definition.</span></span>  
  
-   <span data-ttu-id="39151-129">*ジェネリック型パラメーター*(または *型パラメーター*) は、ジェネリック型定義またはジェネリック メソッド定義のプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="39151-129">*Generic type parameters*, or *type parameters*, are the placeholders in a generic type or method definition.</span></span> <span data-ttu-id="39151-130"><xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> ジェネリック型には、そのキーと値の型を表す 2 つの型パラメーター `TKey` と `TValue` があります。</span><span class="sxs-lookup"><span data-stu-id="39151-130">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> generic type has two type parameters, `TKey` and `TValue`, that represent the types of its keys and values.</span></span>  
  
-   <span data-ttu-id="39151-131">*構築ジェネリック型*(または *構築型*) は、ジェネリック型定義のジェネリック型パラメーターに型を指定することによって得られる結果です。</span><span class="sxs-lookup"><span data-stu-id="39151-131">A *constructed generic type*, or *constructed type*, is the result of specifying types for the generic type parameters of a generic type definition.</span></span>  
  
-   <span data-ttu-id="39151-132">*ジェネリック型引数* は、ジェネリック型パラメーターを置き換える任意の型です。</span><span class="sxs-lookup"><span data-stu-id="39151-132">A *generic type argument* is any type that is substituted for a generic type parameter.</span></span>  
  
-   <span data-ttu-id="39151-133">一般的な用語である *ジェネリック型* には、構築型とジェネリック型定義の両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="39151-133">The general term *generic type* includes both constructed types and generic type definitions.</span></span>  
  
-   <span data-ttu-id="39151-134">ジェネリック型パラメーターの*共変性*と*反変性*を使用すると、型引数がターゲットの構築型よりも強い派生型 (共変性) または弱い派生型 (反変性) である構築ジェネリック型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="39151-134">*Covariance* and *contravariance* of generic type parameters enable you to use constructed generic types whose type arguments are more derived (covariance) or less derived (contravariance) than a target constructed type.</span></span> <span data-ttu-id="39151-135">共変性と反変性は、"*分散*" と総称されます。</span><span class="sxs-lookup"><span data-stu-id="39151-135">Covariance and contravariance are collectively referred to as *variance*.</span></span> <span data-ttu-id="39151-136">詳細については、「[共変性と反変性](../../../docs/standard/generics/covariance-and-contravariance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39151-136">For more information, see [Covariance and Contravariance](../../../docs/standard/generics/covariance-and-contravariance.md).</span></span>  
  
-   <span data-ttu-id="39151-137">*制約* は、ジェネリック型パラメーターに適用される制限です。</span><span class="sxs-lookup"><span data-stu-id="39151-137">*Constraints* are limits placed on generic type parameters.</span></span> <span data-ttu-id="39151-138">たとえば、型パラメーターを、<xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> ジェネリック インターフェイスを実装する型に制限すると、型のインスタンスを並べ替えることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="39151-138">For example, you might limit a type parameter to types that implement the <xref:System.Collections.Generic.IComparer%601?displayProperty=fullName> generic interface, to ensure that instances of the type can be ordered.</span></span> <span data-ttu-id="39151-139">また、型パラメーターを、特定の基本クラスや既定のコンストラクターを持つ型、または参照型や値型に制約できます。</span><span class="sxs-lookup"><span data-stu-id="39151-139">You can also constrain type parameters to types that have a particular base class, that have a default constructor, or that are reference types or value types.</span></span> <span data-ttu-id="39151-140">ジェネリック型のユーザーは、制約を満たさない型引数に置き換えることはできません。</span><span class="sxs-lookup"><span data-stu-id="39151-140">Users of the generic type cannot substitute type arguments that do not satisfy the constraints.</span></span>  
  
-   <span data-ttu-id="39151-141">*ジェネリック メソッド定義* は、ジェネリック型パラメーターのリストと仮パラメーターのリストの 2 つのパラメーター リストを持つメソッドです。</span><span class="sxs-lookup"><span data-stu-id="39151-141">A *generic method definition* is a method with two parameter lists: a list of generic type parameters and a list of formal parameters.</span></span> <span data-ttu-id="39151-142">次のコードに示すように、型パラメーターは、戻り値の型または仮パラメーターの型として指定できます。</span><span class="sxs-lookup"><span data-stu-id="39151-142">Type parameters can appear as the return type or as the types of the formal parameters, as the following code shows.</span></span>  
  
 <span data-ttu-id="39151-143">[!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]</span><span class="sxs-lookup"><span data-stu-id="39151-143">[!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
[!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]</span></span>  
  
 <span data-ttu-id="39151-144">ジェネリック メソッドはジェネリック型または非ジェネリック型で指定できます。</span><span class="sxs-lookup"><span data-stu-id="39151-144">Generic methods can appear on generic or nongeneric types.</span></span> <span data-ttu-id="39151-145">メソッドがジェネリック型に属している、またはメソッドに仮パラメーターがあり、その型が外側の型のジェネリック パラメーターであるという理由だけでは、そのメソッドがジェネリックであるとは言えないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="39151-145">It is important to note that a method is not generic just because it belongs to a generic type, or even because it has formal parameters whose types are the generic parameters of the enclosing type.</span></span> <span data-ttu-id="39151-146">メソッドは、独自の型パラメーター リストを持つ場合にのみジェネリックとなります。</span><span class="sxs-lookup"><span data-stu-id="39151-146">A method is generic only if it has its own list of type parameters.</span></span> <span data-ttu-id="39151-147">次のコードでは、`G` メソッドのみがジェネリックです。</span><span class="sxs-lookup"><span data-stu-id="39151-147">In the following code, only method `G` is generic.</span></span>  
  
 <span data-ttu-id="39151-148">[!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]</span><span class="sxs-lookup"><span data-stu-id="39151-148">[!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
[!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]</span></span>  
  
 [<span data-ttu-id="39151-149">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="39151-149">Back to top</span></span>](#top)  
  
<a name="advantages_limitations"></a>   
## <a name="advantages-and-disadvantages-of-generics"></a><span data-ttu-id="39151-150">ジェネリックの利点と欠点</span><span class="sxs-lookup"><span data-stu-id="39151-150">Advantages and disadvantages of generics</span></span>  
 <span data-ttu-id="39151-151">ジェネリック コレクションやジェネリック デリゲートを使用することには多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="39151-151">There are many advantages to using generic collections and delegates:</span></span>  
  
-   <span data-ttu-id="39151-152">インライン関数はタイプ セーフです。</span><span class="sxs-lookup"><span data-stu-id="39151-152">Type safety.</span></span> <span data-ttu-id="39151-153">ジェネリックによって、タイプ セーフの負担がユーザーからコンパイラに移ります。</span><span class="sxs-lookup"><span data-stu-id="39151-153">Generics shift the burden of type safety from you to the compiler.</span></span> <span data-ttu-id="39151-154">コンパイル時に正しいデータ型が適用されるため、これをテストするためのコードを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="39151-154">There is no need to write code to test for the correct data type because it is enforced at compile time.</span></span> <span data-ttu-id="39151-155">型キャストの必要性や、ランタイム エラーが発生する可能性が減少します。</span><span class="sxs-lookup"><span data-stu-id="39151-155">The need for type casting and the possibility of run-time errors are reduced.</span></span>  
  
-   <span data-ttu-id="39151-156">コードは少なければ少ないほど再利用が容易になります。</span><span class="sxs-lookup"><span data-stu-id="39151-156">Less code and code is more easily reused.</span></span> <span data-ttu-id="39151-157">基本型から継承してメンバーをオーバーライドする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="39151-157">There is no need to inherit from a base type and override members.</span></span> <span data-ttu-id="39151-158">たとえば、<xref:System.Collections.Generic.LinkedList%601> はすぐ使える状態になっています。</span><span class="sxs-lookup"><span data-stu-id="39151-158">For example, the <xref:System.Collections.Generic.LinkedList%601> is ready for immediate use.</span></span> <span data-ttu-id="39151-159">たとえば、次の変数宣言で文字列のリンク リストを作成できます。</span><span class="sxs-lookup"><span data-stu-id="39151-159">For example, you can create a linked list of strings with the following variable declaration:</span></span>  
  
     <span data-ttu-id="39151-160">[!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]</span><span class="sxs-lookup"><span data-stu-id="39151-160">[!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
 [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
 [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]</span></span>  
  
-   <span data-ttu-id="39151-161">パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="39151-161">Better performance.</span></span> <span data-ttu-id="39151-162">通常、ジェネリック コレクション型では、値型をボックス化する必要がないため、値型の格納と操作のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="39151-162">Generic collection types generally perform better for storing and manipulating value types because there is no need to box the value types.</span></span>  
  
-   <span data-ttu-id="39151-163">汎用デリゲートによって、複数のデリゲート クラスを作成せずにタイプ セーフなコールバックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="39151-163">Generic delegates enable type-safe callbacks without the need to create multiple delegate classes.</span></span> <span data-ttu-id="39151-164">たとえば、<xref:System.Predicate%601> 汎用デリゲートを使用すると、特定の型を対象とした独自の検索条件を実装するメソッドを作成し、<xref:System.Array.Find%2A>、<xref:System.Array.FindLast%2A>、<xref:System.Array.FindAll%2A> などの <xref:System.Array> 型のメソッドと共に自分のメソッドを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="39151-164">For example, the <xref:System.Predicate%601> generic delegate allows you to create a method that implements your own search criteria for a particular type and to use your method with methods of the <xref:System.Array> type such as <xref:System.Array.Find%2A>, <xref:System.Array.FindLast%2A>, and <xref:System.Array.FindAll%2A>.</span></span>  
  
-   <span data-ttu-id="39151-165">ジェネリックによって、動的に生成されるコードが簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="39151-165">Generics streamline dynamically generated code.</span></span> <span data-ttu-id="39151-166">動的に生成されるコードでジェネリックを使用する場合、型を生成する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="39151-166">When you use generics with dynamically generated code you do not need to generate the type.</span></span> <span data-ttu-id="39151-167">これにより、アセンブリ全体を生成する代わりに軽量の動的メソッドを使用できるシナリオの数が増えます。</span><span class="sxs-lookup"><span data-stu-id="39151-167">This increases the number of scenarios in which you can use lightweight dynamic methods instead of generating entire assemblies.</span></span> <span data-ttu-id="39151-168">詳細については、「方法: 動的メソッドを定義および実行する」および DynamicMethod を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39151-168">For more information, see How to: Define and Execute Dynamic Methods and DynamicMethod.</span></span>  
  
 <span data-ttu-id="39151-169">ジェネリックの制限事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="39151-169">The following are some limitations of generics:</span></span>  
  
-   <span data-ttu-id="39151-170">ジェネリック型は、<xref:System.MarshalByRefObject> などのほとんどの基本クラスから派生できます (制約を使用して、ジェネリック型パラメーターが <xref:System.MarshalByRefObject> のような基本クラスから派生することを要求できます)。</span><span class="sxs-lookup"><span data-stu-id="39151-170">Generic types can be derived from most base classes, such as <xref:System.MarshalByRefObject> (and constraints can be used to require that generic type parameters derive from base classes like <xref:System.MarshalByRefObject>).</span></span> <span data-ttu-id="39151-171">ただし、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、コンテキスト バインドのジェネリック型はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="39151-171">However, the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] does not support context-bound generic types.</span></span> <span data-ttu-id="39151-172">ジェネリック型は、<xref:System.ContextBoundObject> から派生できますが、その型のインスタンスを作成しようとすると、<xref:System.TypeLoadException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="39151-172">A generic type can be derived from <xref:System.ContextBoundObject>, but trying to create an instance of that type causes a <xref:System.TypeLoadException>.</span></span>  
  
-   <span data-ttu-id="39151-173">列挙型にジェネリック型パラメーターを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="39151-173">Enumerations cannot have generic type parameters.</span></span> <span data-ttu-id="39151-174">列挙型が、単なる偶然によってジェネリックのみになる可能性はあります (たとえば、Visual Basic、C#、または C++ を使用して定義されたジェネリック型に入れ子にされているため)。</span><span class="sxs-lookup"><span data-stu-id="39151-174">An enumeration can be generic only incidentally (for example, because it is nested in a generic type that is defined using Visual Basic, C#, or C++).</span></span> <span data-ttu-id="39151-175">詳細については、[「Common Type System」](../../../docs/standard/base-types/common-type-system.md) の「列挙型」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39151-175">For more information, see "Enumerations" in [Common Type System](../../../docs/standard/base-types/common-type-system.md).</span></span>  
  
-   <span data-ttu-id="39151-176">軽量の動的メソッドをジェネリックにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="39151-176">Lightweight dynamic methods cannot be generic.</span></span>  
  
-   <span data-ttu-id="39151-177">Visual Basic、C#、および C++ で、ジェネリック型に囲まれている入れ子にされた型は、外側のすべての型の型パラメーターに型が割り当てられていない限り、インスタンス化できません。</span><span class="sxs-lookup"><span data-stu-id="39151-177">In Visual Basic, C#, and C++, a nested type that is enclosed in a generic type cannot be instantiated unless types have been assigned to the type parameters of all enclosing types.</span></span> <span data-ttu-id="39151-178">言い換えると、リフレクションでは、これらの言語を使用して定義されている入れ子にされた型には、その外側のすべての型の型パラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="39151-178">Another way of saying this is that in reflection, a nested type that is defined using these languages includes the type parameters of all its enclosing types.</span></span> <span data-ttu-id="39151-179">これによって、外側の型の型パラメーターを、入れ子にされた型のメンバー定義で使用できます。</span><span class="sxs-lookup"><span data-stu-id="39151-179">This allows the type parameters of enclosing types to be used in the member definitions of a nested type.</span></span> <span data-ttu-id="39151-180">詳細については、「<xref:System.Type.MakeGenericType%2A>」の「入れ子にされた型」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39151-180">For more information, see "Nested Types" in <xref:System.Type.MakeGenericType%2A>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="39151-181">動的アセンブリでコードを出力するか [Ilasm.exe (IL アセンブラー)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) を使用して定義されている入れ子にされた型に、外側の型の型パラメーターを含める必要はありません。ただし、これらを含んでいない場合、型パラメーターは入れ子にされたクラスのスコープから外れます。</span><span class="sxs-lookup"><span data-stu-id="39151-181">A nested type that is defined by emitting code in a dynamic assembly or by using the [Ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) is not required to include the type parameters of its enclosing types; however, if it does not include them, the type parameters are not in scope in the nested class.</span></span>  
  
     <span data-ttu-id="39151-182">詳細については、「<xref:System.Type.MakeGenericType%2A>」の「入れ子にされた型」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39151-182">For more information, see "Nested Types" in <xref:System.Type.MakeGenericType%2A>.</span></span>  
  
 [<span data-ttu-id="39151-183">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="39151-183">Back to top</span></span>](#top)  
  
<a name="class_library_and_language_support"></a>   
## <a name="class-library-and-language-support"></a><span data-ttu-id="39151-184">クラス ライブラリと言語サポート</span><span class="sxs-lookup"><span data-stu-id="39151-184">Class Library and Language Support</span></span>  
 <span data-ttu-id="39151-185">.NET Framework では、次の名前空間に多数のジェネリック コレクション クラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="39151-185">The .NET Framework provides a number of generic collection classes in the following namespaces:</span></span>  
  
-   <span data-ttu-id="39151-186"><xref:System.Collections.Generic> 名前空間には、<xref:System.Collections.Generic.List%601> ジェネリック クラスや <xref:System.Collections.Generic.Dictionary%602> ジェネリック クラスなど、.NET Framework で用意されているほとんどのジェネリック コレクション型がカタログされています。</span><span class="sxs-lookup"><span data-stu-id="39151-186">The <xref:System.Collections.Generic> namespace catalogs most of the generic collection types provided by the .NET Framework, such as the <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602> generic classes.</span></span>  
  
-   <span data-ttu-id="39151-187"><xref:System.Collections.ObjectModel> 名前空間には、<xref:System.Collections.ObjectModel.ReadOnlyCollection%601> ジェネリック クラスなど、クラスのユーザーにオブジェクト モデルを公開するために役立つ追加のジェネリック コレクション型がカタログされています。</span><span class="sxs-lookup"><span data-stu-id="39151-187">The <xref:System.Collections.ObjectModel> namespace catalogs additional generic collection types, such as the <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> generic class, that are useful for exposing object models to users of your classes.</span></span>  
  
 <span data-ttu-id="39151-188">並べ替えと等価比較を実装するためのジェネリック インターフェイスは、イベント ハンドラー、変換、および検索述語の汎用デリゲート型と共に、<xref:System> 名前空間に用意されています。</span><span class="sxs-lookup"><span data-stu-id="39151-188">Generic interfaces for implementing sort and equality comparisons are provided in the <xref:System> namespace, along with generic delegate types for event handlers, conversions, and search predicates.</span></span>  
  
 <span data-ttu-id="39151-189">ジェネリックのサポートは、ジェネリック型とジェネリック メソッドを調べるために <xref:System.Reflection> 名前空間に追加され、ジェネリック型とジェネリック メソッドを含む動的アセンブリを出力するために <xref:System.Reflection.Emit> に追加され、さらにジェネリックを含むソース グラフを生成するために <xref:System.CodeDom> に追加されています。</span><span class="sxs-lookup"><span data-stu-id="39151-189">Support for generics has been added to the <xref:System.Reflection> namespace for examining generic types and generic methods, to <xref:System.Reflection.Emit> for emitting dynamic assemblies that contain generic types and methods, and to <xref:System.CodeDom> for generating source graphs that include generics.</span></span>  
  
 <span data-ttu-id="39151-190">共通言語ランタイムでは、Microsoft Intermediate Language (MSIL) のジェネリック型をサポートするために、新しいオペコードとプレフィックスを提供しています (<xref:System.Reflection.Emit.OpCodes.Stelem>、<xref:System.Reflection.Emit.OpCodes.Ldelem>、<xref:System.Reflection.Emit.OpCodes.Unbox_Any>、<xref:System.Reflection.Emit.OpCodes.Constrained>、<xref:System.Reflection.Emit.OpCodes.Readonly> など)。</span><span class="sxs-lookup"><span data-stu-id="39151-190">The common language runtime provides new opcodes and prefixes to support generic types in Microsoft intermediate language (MSIL), including <xref:System.Reflection.Emit.OpCodes.Stelem>, <xref:System.Reflection.Emit.OpCodes.Ldelem>, <xref:System.Reflection.Emit.OpCodes.Unbox_Any>, <xref:System.Reflection.Emit.OpCodes.Constrained>, and <xref:System.Reflection.Emit.OpCodes.Readonly>.</span></span>  
  
 <span data-ttu-id="39151-191">Visual C++、C#、および Visual Basic のすべてで、ジェネリックの定義と使用が完全にサポートされています。</span><span class="sxs-lookup"><span data-stu-id="39151-191">Visual C++, C#, and Visual Basic all provide full support for defining and using generics.</span></span> <span data-ttu-id="39151-192">言語サポートの詳細については、「[Visual Basic におけるジェネリック型](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md)」、「[ジェネリックの概要](~/docs/csharp/programming-guide/generics/introduction-to-generics.md)」、および「[Overview of Generics in Visual C++](http://msdn.microsoft.com/library/21f10637-0fce-4916-b925-6c86a126d3aa)」 (Visual C++ のジェネリックの概要) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39151-192">For more information about language support, see [Generic Types in Visual Basic](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md), [Introduction to Generics](~/docs/csharp/programming-guide/generics/introduction-to-generics.md), and [Overview of Generics in Visual C++](http://msdn.microsoft.com/library/21f10637-0fce-4916-b925-6c86a126d3aa).</span></span>  
  
 [<span data-ttu-id="39151-193">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="39151-193">Back to top</span></span>](#top)  
  
<a name="nested_types_and_generics"></a>   
## <a name="nested-types-and-generics"></a><span data-ttu-id="39151-194">入れ子にされた型とジェネリック</span><span class="sxs-lookup"><span data-stu-id="39151-194">Nested Types and Generics</span></span>  
 <span data-ttu-id="39151-195">ジェネリック型に入れ子にされている型は、外側のジェネリック型の型パラメーターに依存している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="39151-195">A type that is nested in a generic type can depend on the type parameters of the enclosing generic type.</span></span> <span data-ttu-id="39151-196">共通言語ランタイムでは、独自のジェネリック型パラメーターがない場合でも、入れ子にされた型をジェネリックと見なします。</span><span class="sxs-lookup"><span data-stu-id="39151-196">The common language runtime considers nested types to be generic, even if they do not have generic type parameters of their own.</span></span> <span data-ttu-id="39151-197">入れ子にされた型のインスタンスを作成するときに、外側のすべてのジェネリック型の型引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39151-197">When you create an instance of a nested type, you must specify type arguments for all enclosing generic types.</span></span>  
  
 [<span data-ttu-id="39151-198">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="39151-198">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="39151-199">関連トピック</span><span class="sxs-lookup"><span data-stu-id="39151-199">Related Topics</span></span>  
  
|<span data-ttu-id="39151-200">タイトル</span><span class="sxs-lookup"><span data-stu-id="39151-200">Title</span></span>|<span data-ttu-id="39151-201">説明</span><span class="sxs-lookup"><span data-stu-id="39151-201">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="39151-202">.NET Framework のジェネリック コレクション</span><span class="sxs-lookup"><span data-stu-id="39151-202">Generic Collections in the .NET Framework</span></span>](../../../docs/standard/generics/collections.md)|<span data-ttu-id="39151-203">.NET Framework のジェネリック コレクション クラスとその他のジェネリック型について説明します。</span><span class="sxs-lookup"><span data-stu-id="39151-203">Describes generic collection classes and other generic types in the .NET Framework.</span></span>|  
|[<span data-ttu-id="39151-204">配列とリストの操作に使用する汎用デリゲート</span><span class="sxs-lookup"><span data-stu-id="39151-204">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|<span data-ttu-id="39151-205">配列またはコレクションの要素に対して実行される変換、検索述語、およびアクションの汎用デリゲートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="39151-205">Describes generic delegates for conversions, search predicates, and actions to be taken on elements of an array or collection.</span></span>|  
|[<span data-ttu-id="39151-206">ジェネリック インターフェイス</span><span class="sxs-lookup"><span data-stu-id="39151-206">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)|<span data-ttu-id="39151-207">ジェネリック型のファミリ間に共通する機能を提供するジェネリック インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="39151-207">Describes generic interfaces that provide common functionality across families of generic types.</span></span>|  
|[<span data-ttu-id="39151-208">共変性と反変性</span><span class="sxs-lookup"><span data-stu-id="39151-208">Covariance and Contravariance</span></span>](../../../docs/standard/generics/covariance-and-contravariance.md)|<span data-ttu-id="39151-209">ジェネリック型パラメーターの共変性と反変性について説明します。</span><span class="sxs-lookup"><span data-stu-id="39151-209">Describes covariance and contravariance in generic type parameters.</span></span>|  
|[<span data-ttu-id="39151-210"> 一般的に使用されるコレクション型</span><span class="sxs-lookup"><span data-stu-id="39151-210">Commonly Used Collection Types</span></span>](../../../docs/standard/collections/commonly-used-collection-types.md)|<span data-ttu-id="39151-211">ジェネリック型など、.NET Framework のコレクション型の特性と使用シナリオの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="39151-211">Provides summary information about the characteristics and usage scenarios of the collection types in the .NET Framework, including generic types.</span></span>|  
|[<span data-ttu-id="39151-212">ジェネリック コレクションを使用する状況</span><span class="sxs-lookup"><span data-stu-id="39151-212">When to Use Generic Collections</span></span>](../../../docs/standard/collections/when-to-use-generic-collections.md)|<span data-ttu-id="39151-213">ジェネリック コレクション型を使用するケースを決定するための一般的な規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="39151-213">Describes general rules for determining when to use generic collection types.</span></span>|  
|[<span data-ttu-id="39151-214">方法: リフレクション出力を使用してジェネリック型を定義する</span><span class="sxs-lookup"><span data-stu-id="39151-214">How to: Define a Generic Type with Reflection Emit</span></span>](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|<span data-ttu-id="39151-215">ジェネリック型とジェネリック メソッドを含む動的アセンブリの生成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="39151-215">Explains how to generate dynamic assemblies that include generic types and methods.</span></span>|  
|[<span data-ttu-id="39151-216">Visual Basic におけるジェネリック型</span><span class="sxs-lookup"><span data-stu-id="39151-216">Generic Types in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md)|<span data-ttu-id="39151-217">ジェネリック型の使用方法や定義方法に関するトピックなど、Visual Basic ユーザー向けにジェネリック機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="39151-217">Describes the generics feature for Visual Basic users, including how-to topics for using and defining generic types.</span></span>|  
|[<span data-ttu-id="39151-218">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="39151-218">Introduction to Generics</span></span>](~/docs/csharp/programming-guide/generics/introduction-to-generics.md)|<span data-ttu-id="39151-219">C# ユーザー向けにジェネリック型の定義方法や使用方法の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="39151-219">Provides an overview of defining and using generic types for C# users.</span></span>|  
|[<span data-ttu-id="39151-220">Visual C++ のジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="39151-220">Overview of Generics in Visual C++</span></span>](http://msdn.microsoft.com/library/21f10637-0fce-4916-b925-6c86a126d3aa)|<span data-ttu-id="39151-221">ジェネリックとテンプレートの違いなど、C++ ユーザー向けにジェネリック機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="39151-221">Describes the generics feature for C++ users, including the differences between generics and templates.</span></span>|  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="39151-222">参照</span><span class="sxs-lookup"><span data-stu-id="39151-222">Reference</span></span>  
 <span data-ttu-id="39151-223"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="39151-223"><xref:System.Collections.Generic></span></span>  
  
 <span data-ttu-id="39151-224"><xref:System.Collections.ObjectModel></span><span class="sxs-lookup"><span data-stu-id="39151-224"><xref:System.Collections.ObjectModel></span></span>  
  
 <span data-ttu-id="39151-225"><xref:System.Reflection.Emit.OpCodes?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="39151-225"><xref:System.Reflection.Emit.OpCodes?displayProperty=fullName></span></span>  
  
 [<span data-ttu-id="39151-226">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="39151-226">Back to top</span></span>](#top)
