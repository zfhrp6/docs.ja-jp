---
title: .NET のジェネリック
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ba9149da420b7b7bdad01e1376793c64adaf1c8d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="generics-in-net"></a><span data-ttu-id="5a913-102">.NET のジェネリック</span><span class="sxs-lookup"><span data-stu-id="5a913-102">Generics in .NET</span></span>

<a name="top"></a> <span data-ttu-id="5a913-103">ジェネリックを使用すると、操作対象のデータ型に厳密に合わせてメソッド、クラス、構造体、またはインターフェイスを調整できます。</span><span class="sxs-lookup"><span data-stu-id="5a913-103">Generics let you tailor a method, class, structure, or interface to the precise data type it acts upon.</span></span> <span data-ttu-id="5a913-104">たとえば、任意の型のキーと値が許可される <xref:System.Collections.Hashtable> クラスを使用する代わりに、 <xref:System.Collections.Generic.Dictionary%602> ジェネリック クラスを使用して、キーに使用できる型と、値に使用できる型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5a913-104">For example, instead of using the <xref:System.Collections.Hashtable> class, which allows keys and values to be of any type, you can use the <xref:System.Collections.Generic.Dictionary%602> generic class and specify the type allowed for the key and the type allowed for the value.</span></span> <span data-ttu-id="5a913-105">ジェネリックの利点として、コードの再利用性やタイプ セーフの向上などを挙げることができます。</span><span class="sxs-lookup"><span data-stu-id="5a913-105">Among the benefits of generics are increased code reusability and type safety.</span></span>  
  
 <span data-ttu-id="5a913-106">このトピックでは、.NET におけるジェネリックの概要と、ジェネリック型またはジェネリック メソッドの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a913-106">This topic provides an overview of generics in .NET and a summary of generic types or methods.</span></span> <span data-ttu-id="5a913-107">このチュートリアルは、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="5a913-107">It contains the following sections:</span></span>  
  
-   [<span data-ttu-id="5a913-108">ジェネリックの定義と使用</span><span class="sxs-lookup"><span data-stu-id="5a913-108">Defining and Using Generics</span></span>](#defining_and_using_generics)  
  
-   [<span data-ttu-id="5a913-109">ジェネリックの用語</span><span class="sxs-lookup"><span data-stu-id="5a913-109">Generics Terminology</span></span>](#generics_terminology)  
  
-   [<span data-ttu-id="5a913-110">クラス ライブラリと言語サポート</span><span class="sxs-lookup"><span data-stu-id="5a913-110">Class Library and Language Support</span></span>](#class_library_and_language_support)  
  
-   [<span data-ttu-id="5a913-111">入れ子にされた型とジェネリック</span><span class="sxs-lookup"><span data-stu-id="5a913-111">Nested Types and Generics</span></span>](#nested_types_and_generics)  
  
-   [<span data-ttu-id="5a913-112">関連トピック</span><span class="sxs-lookup"><span data-stu-id="5a913-112">Related Topics</span></span>](#related_topics)  
  
-   [<span data-ttu-id="5a913-113">参照</span><span class="sxs-lookup"><span data-stu-id="5a913-113">Reference</span></span>](#reference)  
  
<a name="defining_and_using_generics"></a>   
## <a name="defining-and-using-generics"></a><span data-ttu-id="5a913-114">ジェネリックの定義と使用</span><span class="sxs-lookup"><span data-stu-id="5a913-114">Defining and Using Generics</span></span>  
 <span data-ttu-id="5a913-115">ジェネリックは、格納または使用される 1 つ以上の型のプレースホルダー (型パラメーター) を持つクラス、構造体、インターフェイス、およびメソッドです。</span><span class="sxs-lookup"><span data-stu-id="5a913-115">Generics are classes, structures, interfaces, and methods that have placeholders (type parameters) for one or more of the types that they store or use.</span></span> <span data-ttu-id="5a913-116">ジェネリック コレクション クラスでは、格納するオブジェクトの型のプレースホルダーとして、型パラメーターを使用することがあります。型パラメーターは、そのフィールドの型やそのメソッドのパラメーター型として出現します。</span><span class="sxs-lookup"><span data-stu-id="5a913-116">A generic collection class might use a type parameter as a placeholder for the type of objects that it stores; the type parameters appear as the types of its fields and the parameter types of its methods.</span></span> <span data-ttu-id="5a913-117">ジェネリック メソッドでは、その戻り値の型として、またはいずれかの仮パラメーターの型として、型パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="5a913-117">A generic method might use its type parameter as the type of its return value or as the type of one of its formal parameters.</span></span> <span data-ttu-id="5a913-118">単純なジェネリック クラスの定義を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="5a913-118">The following code illustrates a simple generic class definition.</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#2)]
 [!code-csharp[Conceptual.Generics.Overview#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#2)]
 [!code-vb[Conceptual.Generics.Overview#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#2)]  
  
 <span data-ttu-id="5a913-119">ジェネリック クラスのインスタンスを作成する場合は、型パラメーターを置き換える実際の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="5a913-119">When you create an instance of a generic class, you specify the actual types to substitute for the type parameters.</span></span> <span data-ttu-id="5a913-120">これで、構築されたジェネリック クラスと呼ばれる新しいジェネリック クラスが確立され、この中では、型パラメーターが、出現するすべての場所で、選択した型に置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="5a913-120">This establishes a new generic class, referred to as a constructed generic class, with your chosen types substituted everywhere that the type parameters appear.</span></span> <span data-ttu-id="5a913-121">次のコードに示すように、結果は選択した型に合わせたタイプ セーフなクラスになります。</span><span class="sxs-lookup"><span data-stu-id="5a913-121">The result is a type-safe class that is tailored to your choice of types, as the following code illustrates.</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#3)]
 [!code-csharp[Conceptual.Generics.Overview#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#3)]
 [!code-vb[Conceptual.Generics.Overview#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#3)]  
  
<a name="generics_terminology"></a>   
### <a name="generics-terminology"></a><span data-ttu-id="5a913-122">ジェネリックの用語</span><span class="sxs-lookup"><span data-stu-id="5a913-122">Generics terminology</span></span>  
 <span data-ttu-id="5a913-123">.NET におけるジェネリックの説明では、次の用語が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5a913-123">The following terms are used to discuss generics in .NET:</span></span>  
  
-   <span data-ttu-id="5a913-124">*ジェネリック型定義* は、テンプレートとして機能するクラス、構造体、またはインターフェイスの宣言で、格納または使用できる型のプレースホルダーを含みます。</span><span class="sxs-lookup"><span data-stu-id="5a913-124">A *generic type definition* is a class, structure, or interface declaration that functions as a template, with placeholders for the types that it can contain or use.</span></span> <span data-ttu-id="5a913-125">たとえば、<xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> クラスには、キーと値の 2 つの型を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="5a913-125">For example, the <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> class can contain two types: keys and values.</span></span> <span data-ttu-id="5a913-126">ジェネリック型定義は単なるテンプレートであるため、ジェネリック型定義のクラス、構造体、またはインターフェイスのインスタンスを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="5a913-126">Because a generic type definition is only a template, you cannot create instances of a class, structure, or interface that is a generic type definition.</span></span>  
  
-   <span data-ttu-id="5a913-127">*ジェネリック型パラメーター*(または *型パラメーター*) は、ジェネリック型定義またはジェネリック メソッド定義のプレースホルダーです。</span><span class="sxs-lookup"><span data-stu-id="5a913-127">*Generic type parameters*, or *type parameters*, are the placeholders in a generic type or method definition.</span></span> <span data-ttu-id="5a913-128"><xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> ジェネリック型には、そのキーと値の型を表す 2 つの型パラメーター `TKey` と `TValue` があります。</span><span class="sxs-lookup"><span data-stu-id="5a913-128">The <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> generic type has two type parameters, `TKey` and `TValue`, that represent the types of its keys and values.</span></span>  
  
-   <span data-ttu-id="5a913-129">*構築ジェネリック型*(または *構築型*) は、ジェネリック型定義のジェネリック型パラメーターに型を指定することによって得られる結果です。</span><span class="sxs-lookup"><span data-stu-id="5a913-129">A *constructed generic type*, or *constructed type*, is the result of specifying types for the generic type parameters of a generic type definition.</span></span>  
  
-   <span data-ttu-id="5a913-130">*ジェネリック型引数* は、ジェネリック型パラメーターを置き換える任意の型です。</span><span class="sxs-lookup"><span data-stu-id="5a913-130">A *generic type argument* is any type that is substituted for a generic type parameter.</span></span>  
  
-   <span data-ttu-id="5a913-131">一般的な用語である *ジェネリック型* には、構築型とジェネリック型定義の両方が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5a913-131">The general term *generic type* includes both constructed types and generic type definitions.</span></span>  
  
-   <span data-ttu-id="5a913-132">ジェネリック型パラメーターの*共変性* と *反変性* of generic type parameters enable you to use constructed generic types whose type arguments are more derived (covariance) or less derived (反変性) than a target constructed type.</span><span class="sxs-lookup"><span data-stu-id="5a913-132">*Covariance* and *contravariance* of generic type parameters enable you to use constructed generic types whose type arguments are more derived (covariance) or less derived (contravariance) than a target constructed type.</span></span> <span data-ttu-id="5a913-133">共変性と反変性は、*"分散"* と総称されます。</span><span class="sxs-lookup"><span data-stu-id="5a913-133">Covariance and contravariance are collectively referred to as *variance*.</span></span> <span data-ttu-id="5a913-134">詳細については、「[共変性と反変性](../../../docs/standard/generics/covariance-and-contravariance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a913-134">For more information, see [Covariance and Contravariance](../../../docs/standard/generics/covariance-and-contravariance.md).</span></span>  
  
-   <span data-ttu-id="5a913-135">*制約* は、ジェネリック型パラメーターに適用される制限です。</span><span class="sxs-lookup"><span data-stu-id="5a913-135">*Constraints* are limits placed on generic type parameters.</span></span> <span data-ttu-id="5a913-136">たとえば、型パラメーターを、<xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> ジェネリック インターフェイスを実装する型に制限して、型のインスタンスを並べ替えることができるようにできます。</span><span class="sxs-lookup"><span data-stu-id="5a913-136">For example, you might limit a type parameter to types that implement the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> generic interface, to ensure that instances of the type can be ordered.</span></span> <span data-ttu-id="5a913-137">また、型パラメーターを、特定の基本クラスや既定のコンストラクターを持つ型、または参照型や値型に制約できます。</span><span class="sxs-lookup"><span data-stu-id="5a913-137">You can also constrain type parameters to types that have a particular base class, that have a default constructor, or that are reference types or value types.</span></span> <span data-ttu-id="5a913-138">ジェネリック型のユーザーは、制約を満たさない型引数に置き換えることはできません。</span><span class="sxs-lookup"><span data-stu-id="5a913-138">Users of the generic type cannot substitute type arguments that do not satisfy the constraints.</span></span>  
  
-   <span data-ttu-id="5a913-139">*ジェネリック メソッド定義* は、ジェネリック型パラメーターのリストと仮パラメーターのリストの 2 つのパラメーター リストを持つメソッドです。</span><span class="sxs-lookup"><span data-stu-id="5a913-139">A *generic method definition* is a method with two parameter lists: a list of generic type parameters and a list of formal parameters.</span></span> <span data-ttu-id="5a913-140">次のコードに示すように、型パラメーターは、戻り値の型または仮パラメーターの型として指定できます。</span><span class="sxs-lookup"><span data-stu-id="5a913-140">Type parameters can appear as the return type or as the types of the formal parameters, as the following code shows.</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#4)]
 [!code-csharp[Conceptual.Generics.Overview#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#4)]
 [!code-vb[Conceptual.Generics.Overview#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#4)]  
  
 <span data-ttu-id="5a913-141">ジェネリック メソッドはジェネリック型または非ジェネリック型で指定できます。</span><span class="sxs-lookup"><span data-stu-id="5a913-141">Generic methods can appear on generic or nongeneric types.</span></span> <span data-ttu-id="5a913-142">メソッドがジェネリック型に属している、またはメソッドに仮パラメーターがあり、その型が外側の型のジェネリック パラメーターであるという理由だけでは、そのメソッドがジェネリックであるとは言えないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5a913-142">It is important to note that a method is not generic just because it belongs to a generic type, or even because it has formal parameters whose types are the generic parameters of the enclosing type.</span></span> <span data-ttu-id="5a913-143">メソッドは、独自の型パラメーター リストを持つ場合にのみジェネリックとなります。</span><span class="sxs-lookup"><span data-stu-id="5a913-143">A method is generic only if it has its own list of type parameters.</span></span> <span data-ttu-id="5a913-144">次のコードでは、 `G` メソッドのみがジェネリックです。</span><span class="sxs-lookup"><span data-stu-id="5a913-144">In the following code, only method `G` is generic.</span></span>  
  
 [!code-cpp[Conceptual.Generics.Overview#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source.cpp#5)]
 [!code-csharp[Conceptual.Generics.Overview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source.cs#5)]
 [!code-vb[Conceptual.Generics.Overview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source.vb#5)]  
  
 [<span data-ttu-id="5a913-145">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="5a913-145">Back to top</span></span>](#top)  
  
<a name="advantages_limitations"></a>   
## <a name="advantages-and-disadvantages-of-generics"></a><span data-ttu-id="5a913-146">ジェネリックの利点と欠点</span><span class="sxs-lookup"><span data-stu-id="5a913-146">Advantages and disadvantages of generics</span></span>  
 <span data-ttu-id="5a913-147">ジェネリック コレクションやジェネリック デリゲートを使用することには多くの利点があります。</span><span class="sxs-lookup"><span data-stu-id="5a913-147">There are many advantages to using generic collections and delegates:</span></span>  
  
-   <span data-ttu-id="5a913-148">インライン関数はタイプ セーフです。</span><span class="sxs-lookup"><span data-stu-id="5a913-148">Type safety.</span></span> <span data-ttu-id="5a913-149">ジェネリックによって、タイプ セーフの負担がユーザーからコンパイラに移ります。</span><span class="sxs-lookup"><span data-stu-id="5a913-149">Generics shift the burden of type safety from you to the compiler.</span></span> <span data-ttu-id="5a913-150">コンパイル時に正しいデータ型が適用されるため、これをテストするためのコードを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5a913-150">There is no need to write code to test for the correct data type because it is enforced at compile time.</span></span> <span data-ttu-id="5a913-151">型キャストの必要性や、ランタイム エラーが発生する可能性が減少します。</span><span class="sxs-lookup"><span data-stu-id="5a913-151">The need for type casting and the possibility of run-time errors are reduced.</span></span>  
  
-   <span data-ttu-id="5a913-152">コードは少なければ少ないほど再利用が容易になります。</span><span class="sxs-lookup"><span data-stu-id="5a913-152">Less code and code is more easily reused.</span></span> <span data-ttu-id="5a913-153">基本型から継承してメンバーをオーバーライドする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5a913-153">There is no need to inherit from a base type and override members.</span></span> <span data-ttu-id="5a913-154">たとえば、 <xref:System.Collections.Generic.LinkedList%601> はすぐに使える状態になっています。</span><span class="sxs-lookup"><span data-stu-id="5a913-154">For example, the <xref:System.Collections.Generic.LinkedList%601> is ready for immediate use.</span></span> <span data-ttu-id="5a913-155">たとえば、次の変数宣言で文字列のリンク リストを作成できます。</span><span class="sxs-lookup"><span data-stu-id="5a913-155">For example, you can create a linked list of strings with the following variable declaration:</span></span>  
  
     [!code-cpp[HowToGeneric#24](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/source2.cpp#24)]
     [!code-csharp[HowToGeneric#24](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/source2.cs#24)]
     [!code-vb[HowToGeneric#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/source2.vb#24)]  
  
-   <span data-ttu-id="5a913-156">パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="5a913-156">Better performance.</span></span> <span data-ttu-id="5a913-157">通常、ジェネリック コレクション型では、値型をボックス化する必要がないため、値型の格納と操作のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="5a913-157">Generic collection types generally perform better for storing and manipulating value types because there is no need to box the value types.</span></span>  
  
-   <span data-ttu-id="5a913-158">汎用デリゲートによって、複数のデリゲート クラスを作成せずにタイプ セーフなコールバックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a913-158">Generic delegates enable type-safe callbacks without the need to create multiple delegate classes.</span></span> <span data-ttu-id="5a913-159">たとえば、 <xref:System.Predicate%601> 汎用デリゲートを使用すると、特定の型を対象とした独自の検索条件を実装するメソッドを作成し、 <xref:System.Array> 、 <xref:System.Array.Find%2A>、 <xref:System.Array.FindLast%2A>などの <xref:System.Array.FindAll%2A>型のメソッドと共に自分のメソッドを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="5a913-159">For example, the <xref:System.Predicate%601> generic delegate allows you to create a method that implements your own search criteria for a particular type and to use your method with methods of the <xref:System.Array> type such as <xref:System.Array.Find%2A>, <xref:System.Array.FindLast%2A>, and <xref:System.Array.FindAll%2A>.</span></span>  
  
-   <span data-ttu-id="5a913-160">ジェネリックによって、動的に生成されるコードが簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="5a913-160">Generics streamline dynamically generated code.</span></span> <span data-ttu-id="5a913-161">動的に生成されるコードでジェネリックを使用する場合、型を生成する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="5a913-161">When you use generics with dynamically generated code you do not need to generate the type.</span></span> <span data-ttu-id="5a913-162">これにより、アセンブリ全体を生成する代わりに軽量の動的メソッドを使用できるシナリオの数が増えます。</span><span class="sxs-lookup"><span data-stu-id="5a913-162">This increases the number of scenarios in which you can use lightweight dynamic methods instead of generating entire assemblies.</span></span> <span data-ttu-id="5a913-163">詳細については、「方法: 動的メソッドを定義および実行する」および DynamicMethod を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a913-163">For more information, see How to: Define and Execute Dynamic Methods and DynamicMethod.</span></span>  
  
 <span data-ttu-id="5a913-164">ジェネリックの制限事項を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5a913-164">The following are some limitations of generics:</span></span>  
  
-   <span data-ttu-id="5a913-165">ジェネリック型は、 <xref:System.MarshalByRefObject> などのほとんどの基本クラスから派生できます (制約を使用して、ジェネリック型パラメーターが <xref:System.MarshalByRefObject>のような基本クラスから派生することを要求できます)。</span><span class="sxs-lookup"><span data-stu-id="5a913-165">Generic types can be derived from most base classes, such as <xref:System.MarshalByRefObject> (and constraints can be used to require that generic type parameters derive from base classes like <xref:System.MarshalByRefObject>).</span></span> <span data-ttu-id="5a913-166">ただし、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、コンテキスト バインドのジェネリック型はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="5a913-166">However, the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] does not support context-bound generic types.</span></span> <span data-ttu-id="5a913-167">ジェネリック型は、 <xref:System.ContextBoundObject>から派生できますが、その型のインスタンスを作成しようとすると、 <xref:System.TypeLoadException>が発生します。</span><span class="sxs-lookup"><span data-stu-id="5a913-167">A generic type can be derived from <xref:System.ContextBoundObject>, but trying to create an instance of that type causes a <xref:System.TypeLoadException>.</span></span>  
  
-   <span data-ttu-id="5a913-168">列挙型にジェネリック型パラメーターを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="5a913-168">Enumerations cannot have generic type parameters.</span></span> <span data-ttu-id="5a913-169">列挙型が、単なる偶然によってジェネリックのみになる可能性はあります (たとえば、Visual Basic、C#、または C++ を使用して定義されたジェネリック型に入れ子にされているため)。</span><span class="sxs-lookup"><span data-stu-id="5a913-169">An enumeration can be generic only incidentally (for example, because it is nested in a generic type that is defined using Visual Basic, C#, or C++).</span></span> <span data-ttu-id="5a913-170">詳細については、「 [Common Type System](../../../docs/standard/base-types/common-type-system.md)」の「列挙型」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a913-170">For more information, see "Enumerations" in [Common Type System](../../../docs/standard/base-types/common-type-system.md).</span></span>  
  
-   <span data-ttu-id="5a913-171">軽量の動的メソッドをジェネリックにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5a913-171">Lightweight dynamic methods cannot be generic.</span></span>  
  
-   <span data-ttu-id="5a913-172">Visual Basic、C#、および C++ で、ジェネリック型に囲まれている入れ子にされた型は、外側のすべての型の型パラメーターに型が割り当てられていない限り、インスタンス化できません。</span><span class="sxs-lookup"><span data-stu-id="5a913-172">In Visual Basic, C#, and C++, a nested type that is enclosed in a generic type cannot be instantiated unless types have been assigned to the type parameters of all enclosing types.</span></span> <span data-ttu-id="5a913-173">言い換えると、リフレクションでは、これらの言語を使用して定義されている入れ子にされた型には、その外側のすべての型の型パラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5a913-173">Another way of saying this is that in reflection, a nested type that is defined using these languages includes the type parameters of all its enclosing types.</span></span> <span data-ttu-id="5a913-174">これによって、外側の型の型パラメーターを、入れ子にされた型のメンバー定義で使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a913-174">This allows the type parameters of enclosing types to be used in the member definitions of a nested type.</span></span> <span data-ttu-id="5a913-175">詳細については、「 <xref:System.Type.MakeGenericType%2A>」の「入れ子にされた型」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a913-175">For more information, see "Nested Types" in <xref:System.Type.MakeGenericType%2A>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5a913-176">動的アセンブリでコードを出力するか [Ilasm.exe (IL アセンブラー)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) を使用して定義されている入れ子にされた型に、外側の型の型パラメーターを含める必要はありません。ただし、これらを含んでいない場合、型パラメーターは入れ子にされたクラスのスコープから外れます。</span><span class="sxs-lookup"><span data-stu-id="5a913-176">A nested type that is defined by emitting code in a dynamic assembly or by using the [Ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md) is not required to include the type parameters of its enclosing types; however, if it does not include them, the type parameters are not in scope in the nested class.</span></span>  
  
     <span data-ttu-id="5a913-177">詳細については、「 <xref:System.Type.MakeGenericType%2A>」の「入れ子にされた型」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a913-177">For more information, see "Nested Types" in <xref:System.Type.MakeGenericType%2A>.</span></span>  
  
 [<span data-ttu-id="5a913-178">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="5a913-178">Back to top</span></span>](#top)  
  
<a name="class_library_and_language_support"></a>   
## <a name="class-library-and-language-support"></a><span data-ttu-id="5a913-179">クラス ライブラリと言語サポート</span><span class="sxs-lookup"><span data-stu-id="5a913-179">Class Library and Language Support</span></span>  
 <span data-ttu-id="5a913-180">.NET では、次の名前空間に多数のジェネリック コレクション クラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="5a913-180">.NET provides a number of generic collection classes in the following namespaces:</span></span>  
  
-   <span data-ttu-id="5a913-181"><xref:System.Collections.Generic> 名前空間には、<xref:System.Collections.Generic.List%601> ジェネリック クラスや <xref:System.Collections.Generic.Dictionary%602> ジェネリック クラスなど、.NET で用意されているほとんどのジェネリック コレクション型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5a913-181">The <xref:System.Collections.Generic> namespace contains most of the generic collection types provided by .NET, such as the <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602> generic classes.</span></span>  
  
-   <span data-ttu-id="5a913-182"><xref:System.Collections.ObjectModel> 名前空間には、<xref:System.Collections.ObjectModel.ReadOnlyCollection%601> ジェネリック クラスなど、クラスのユーザーにオブジェクト モデルを公開するために役立つ追加のジェネリック コレクション型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5a913-182">The <xref:System.Collections.ObjectModel> namespace contains additional generic collection types, such as the <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> generic class, that are useful for exposing object models to users of your classes.</span></span>  
  
 <span data-ttu-id="5a913-183">並べ替えと等価比較を実装するためのジェネリック インターフェイスは、イベント ハンドラー、変換、および検索述語の汎用デリゲート型と共に、 <xref:System> 名前空間に用意されています。</span><span class="sxs-lookup"><span data-stu-id="5a913-183">Generic interfaces for implementing sort and equality comparisons are provided in the <xref:System> namespace, along with generic delegate types for event handlers, conversions, and search predicates.</span></span>  
  
 <span data-ttu-id="5a913-184">ジェネリックのサポートは、ジェネリック型とジェネリック メソッドを調べるために <xref:System.Reflection> 名前空間に追加され、ジェネリック型とジェネリック メソッドを含む動的アセンブリを出力するために <xref:System.Reflection.Emit> に追加され、さらにジェネリックを含むソース グラフを生成するために <xref:System.CodeDom> に追加されています。</span><span class="sxs-lookup"><span data-stu-id="5a913-184">Support for generics has been added to the <xref:System.Reflection> namespace for examining generic types and generic methods, to <xref:System.Reflection.Emit> for emitting dynamic assemblies that contain generic types and methods, and to <xref:System.CodeDom> for generating source graphs that include generics.</span></span>  
  
 <span data-ttu-id="5a913-185">共通言語ランタイムでは、Microsoft Intermediate Language (MSIL) のジェネリック型をサポートするために、新しいオペコードとプレフィックスを提供しています ( <xref:System.Reflection.Emit.OpCodes.Stelem>、 <xref:System.Reflection.Emit.OpCodes.Ldelem>、 <xref:System.Reflection.Emit.OpCodes.Unbox_Any>、 <xref:System.Reflection.Emit.OpCodes.Constrained>、 <xref:System.Reflection.Emit.OpCodes.Readonly>など)。</span><span class="sxs-lookup"><span data-stu-id="5a913-185">The common language runtime provides new opcodes and prefixes to support generic types in Microsoft intermediate language (MSIL), including <xref:System.Reflection.Emit.OpCodes.Stelem>, <xref:System.Reflection.Emit.OpCodes.Ldelem>, <xref:System.Reflection.Emit.OpCodes.Unbox_Any>, <xref:System.Reflection.Emit.OpCodes.Constrained>, and <xref:System.Reflection.Emit.OpCodes.Readonly>.</span></span>  
  
 <span data-ttu-id="5a913-186">Visual C++、C#、および Visual Basic のすべてで、ジェネリックの定義と使用が完全にサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5a913-186">Visual C++, C#, and Visual Basic all provide full support for defining and using generics.</span></span> <span data-ttu-id="5a913-187">言語サポートの詳細については、「[Visual Basic におけるジェネリック型](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md)」、「[ジェネリックの概要](~/docs/csharp/programming-guide/generics/introduction-to-generics.md)」、および「[Overview of Generics in Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp)」 (Visual C++ のジェネリックの概要) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a913-187">For more information about language support, see [Generic Types in Visual Basic](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md), [Introduction to Generics](~/docs/csharp/programming-guide/generics/introduction-to-generics.md), and [Overview of Generics in Visual C++](/cpp/windows/overview-of-generics-in-visual-cpp).</span></span>  
  
 [<span data-ttu-id="5a913-188">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="5a913-188">Back to top</span></span>](#top)  
  
<a name="nested_types_and_generics"></a>   
## <a name="nested-types-and-generics"></a><span data-ttu-id="5a913-189">入れ子にされた型とジェネリック</span><span class="sxs-lookup"><span data-stu-id="5a913-189">Nested Types and Generics</span></span>  
 <span data-ttu-id="5a913-190">ジェネリック型に入れ子にされている型は、外側のジェネリック型の型パラメーターに依存している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5a913-190">A type that is nested in a generic type can depend on the type parameters of the enclosing generic type.</span></span> <span data-ttu-id="5a913-191">共通言語ランタイムでは、独自のジェネリック型パラメーターがない場合でも、入れ子にされた型をジェネリックと見なします。</span><span class="sxs-lookup"><span data-stu-id="5a913-191">The common language runtime considers nested types to be generic, even if they do not have generic type parameters of their own.</span></span> <span data-ttu-id="5a913-192">入れ子にされた型のインスタンスを作成するときに、外側のすべてのジェネリック型の型引数を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5a913-192">When you create an instance of a nested type, you must specify type arguments for all enclosing generic types.</span></span>  
  
 [<span data-ttu-id="5a913-193">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="5a913-193">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="5a913-194">関連トピック</span><span class="sxs-lookup"><span data-stu-id="5a913-194">Related Topics</span></span>  
  
|<span data-ttu-id="5a913-195">Title</span><span class="sxs-lookup"><span data-stu-id="5a913-195">Title</span></span>|<span data-ttu-id="5a913-196">説明</span><span class="sxs-lookup"><span data-stu-id="5a913-196">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5a913-197"> .NET の汎用コレクション</span><span class="sxs-lookup"><span data-stu-id="5a913-197">Generic Collections in .NET</span></span>](../../../docs/standard/generics/collections.md)|<span data-ttu-id="5a913-198">.NET のジェネリック コレクション クラスとその他のジェネリック型について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a913-198">Describes generic collection classes and other generic types in .NET.</span></span>|  
|[<span data-ttu-id="5a913-199">配列とリストの操作に使用する汎用デリゲート</span><span class="sxs-lookup"><span data-stu-id="5a913-199">Generic Delegates for Manipulating Arrays and Lists</span></span>](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)|<span data-ttu-id="5a913-200">配列またはコレクションの要素に対して実行される変換、検索述語、およびアクションの汎用デリゲートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5a913-200">Describes generic delegates for conversions, search predicates, and actions to be taken on elements of an array or collection.</span></span>|  
|[<span data-ttu-id="5a913-201">ジェネリック インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a913-201">Generic Interfaces</span></span>](../../../docs/standard/generics/interfaces.md)|<span data-ttu-id="5a913-202">ジェネリック型のファミリ間に共通する機能を提供するジェネリック インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="5a913-202">Describes generic interfaces that provide common functionality across families of generic types.</span></span>|  
|[<span data-ttu-id="5a913-203">共変性と反変性</span><span class="sxs-lookup"><span data-stu-id="5a913-203">Covariance and Contravariance</span></span>](../../../docs/standard/generics/covariance-and-contravariance.md)|<span data-ttu-id="5a913-204">ジェネリック型パラメーターの共変性と反変性について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a913-204">Describes covariance and contravariance in generic type parameters.</span></span>|  
|[<span data-ttu-id="5a913-205"> 一般的に使用されるコレクション型</span><span class="sxs-lookup"><span data-stu-id="5a913-205">Commonly Used Collection Types</span></span>](../../../docs/standard/collections/commonly-used-collection-types.md)|<span data-ttu-id="5a913-206">ジェネリック型など、.NET のコレクション型の特性と使用シナリオの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a913-206">Provides summary information about the characteristics and usage scenarios of the collection types in .NET, including generic types.</span></span>|  
|[<span data-ttu-id="5a913-207">ジェネリック コレクションを使用する状況</span><span class="sxs-lookup"><span data-stu-id="5a913-207">When to Use Generic Collections</span></span>](../../../docs/standard/collections/when-to-use-generic-collections.md)|<span data-ttu-id="5a913-208">ジェネリック コレクション型を使用するケースを決定するための一般的な規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a913-208">Describes general rules for determining when to use generic collection types.</span></span>|  
|[<span data-ttu-id="5a913-209">方法: リフレクション出力を使用してジェネリック型を定義する</span><span class="sxs-lookup"><span data-stu-id="5a913-209">How to: Define a Generic Type with Reflection Emit</span></span>](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)|<span data-ttu-id="5a913-210">ジェネリック型とジェネリック メソッドを含む動的アセンブリの生成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a913-210">Explains how to generate dynamic assemblies that include generic types and methods.</span></span>|  
|[<span data-ttu-id="5a913-211">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a913-211">Generic Types in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/data-types/generic-types.md)|<span data-ttu-id="5a913-212">ジェネリック型の使用方法や定義方法に関するトピックなど、Visual Basic ユーザー向けにジェネリック機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a913-212">Describes the generics feature for Visual Basic users, including how-to topics for using and defining generic types.</span></span>|  
|[<span data-ttu-id="5a913-213">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="5a913-213">Introduction to Generics</span></span>](~/docs/csharp/programming-guide/generics/introduction-to-generics.md)|<span data-ttu-id="5a913-214">C# ユーザー向けにジェネリック型の定義方法や使用方法の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a913-214">Provides an overview of defining and using generic types for C# users.</span></span>|  
|[<span data-ttu-id="5a913-215">Visual C++ のジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="5a913-215">Overview of Generics in Visual C++</span></span>](/cpp/windows/overview-of-generics-in-visual-cpp)|<span data-ttu-id="5a913-216">ジェネリックとテンプレートの違いなど、C++ ユーザー向けにジェネリック機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="5a913-216">Describes the generics feature for C++ users, including the differences between generics and templates.</span></span>|  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="5a913-217">参照</span><span class="sxs-lookup"><span data-stu-id="5a913-217">Reference</span></span>  
 <xref:System.Collections.Generic>  
  
 <xref:System.Collections.ObjectModel>  
  
 <xref:System.Reflection.Emit.OpCodes?displayProperty=nameWithType>  
  
 [<span data-ttu-id="5a913-218">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="5a913-218">Back to top</span></span>](#top)
