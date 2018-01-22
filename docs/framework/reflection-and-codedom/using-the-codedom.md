---
title: "CodeDOM の使用方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- code compilers
- Code Document Object Model
- Code Document Object Model, graphs
- types, CodeDOM
- namespaces [.NET Framework], CodeDOM
- templated code generation
- dynamically representing source code
- source code models
- CodeDOM
- graphing with CodeDOM
- dynamic compilation
- code generators
- CodeDOM, graphs
ms.assetid: 0444ddf3-c3f6-44ed-a999-f710d9c3e0cf
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2cd2b8e8ecb0e5d451ebf3c6823144e4a90e0d79
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="using-the-codedom"></a><span data-ttu-id="e91b3-102">CodeDOM の使用方法</span><span class="sxs-lookup"><span data-stu-id="e91b3-102">Using the CodeDOM</span></span>
<span data-ttu-id="e91b3-103">CodeDOM には一般的なさまざま種類のソース コード要素を表す型が用意されています。</span><span class="sxs-lookup"><span data-stu-id="e91b3-103">The CodeDOM provides types that represent many common types of source code elements.</span></span> <span data-ttu-id="e91b3-104">オブジェクト グラフをアセンブルする CodeDOM 要素を使用すると、ソース コード モデルを構築するプログラムをデザインできます。</span><span class="sxs-lookup"><span data-stu-id="e91b3-104">You can design a program that builds a source code model using CodeDOM elements to assemble an object graph.</span></span> <span data-ttu-id="e91b3-105">このオブジェクト グラフは、サポートされているプログラミング言語用の CodeDOM コード ジェネレーターを使用して、ソース コードとしてレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="e91b3-105">This object graph can be rendered as source code using a CodeDOM code generator for a supported programming language.</span></span> <span data-ttu-id="e91b3-106">また、CodeDOM を使用して、ソース コードをバイナリ アセンブリにコンパイルすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e91b3-106">The CodeDOM can also be used to compile source code into a binary assembly.</span></span>  
  
 <span data-ttu-id="e91b3-107">CodeDOM の一般的な使用方法の例は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e91b3-107">Some common uses for the CodeDOM include:</span></span>  
  
-   <span data-ttu-id="e91b3-108">テンプレートを使ったコード生成。ASP.NET、XML Web サービス クライアント プロキシ、コード ウィザード、デザイナー、またはその他のコード出力機構のためのコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="e91b3-108">Templated code generation: generating code for ASP.NET, XML Web services client proxies, code wizards, designers, or other code-emitting mechanisms.</span></span>  
  
-   <span data-ttu-id="e91b3-109">動的コンパイル。1 つ以上の言語でのコードのコンパイルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="e91b3-109">Dynamic compilation: supporting code compilation in single or multiple languages.</span></span>  
  
## <a name="building-a-codedom-graph"></a><span data-ttu-id="e91b3-110">CodeDOM グラフの構築</span><span class="sxs-lookup"><span data-stu-id="e91b3-110">Building a CodeDOM Graph</span></span>  
 <span data-ttu-id="e91b3-111"><xref:System.CodeDom> 名前空間には、言語の構文に依存しない、ソース コードの論理構造を表すクラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e91b3-111">The <xref:System.CodeDom> namespace provides classes for representing the logical structure of source code, independent of language syntax.</span></span>  
  
### <a name="the-structure-of-a-codedom-graph"></a><span data-ttu-id="e91b3-112">CodeDOM グラフの構造</span><span class="sxs-lookup"><span data-stu-id="e91b3-112">The Structure of a CodeDOM Graph</span></span>  
 <span data-ttu-id="e91b3-113">CodeDOM グラフの構造はコンテナーのツリーに似ています。</span><span class="sxs-lookup"><span data-stu-id="e91b3-113">The structure of a CodeDOM graph is like a tree of containers.</span></span> <span data-ttu-id="e91b3-114">コンパイル可能な CodeDOM グラフの最上位のコンテナー、つまりルートのコンテナーは <xref:System.CodeDom.CodeCompileUnit> です。</span><span class="sxs-lookup"><span data-stu-id="e91b3-114">The top-most, or root, container of each compilable CodeDOM graph is a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="e91b3-115">ソース コード モデルの各要素は、CodeDOM グラフ内の <xref:System.CodeDom.CodeObject> のプロパティを通じて CodeDOM グラフにリンクされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e91b3-115">Every element of your source code model must be linked into the graph through a property of a <xref:System.CodeDom.CodeObject> in the graph.</span></span>  
  
### <a name="building-a-source-code-model-for-a-sample-hello-world-program"></a><span data-ttu-id="e91b3-116">サンプルの Hello World プログラム用ソース コード モデルの構築</span><span class="sxs-lookup"><span data-stu-id="e91b3-116">Building a Source Code Model for a Sample Hello World Program</span></span>  
 <span data-ttu-id="e91b3-117">単純な Hello World アプリケーションのコードを表す CodeDOM オブジェクト グラフを構築する手順の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e91b3-117">The following walkthrough provides an example of how to build a CodeDOM object graph that represents the code for a simple Hello World application.</span></span> <span data-ttu-id="e91b3-118">このコード サンプルのソース コード例全体については、「<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e91b3-118">For the complete source code for this code example, see the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> topic.</span></span>  
  
#### <a name="creating-a-compile-unit"></a><span data-ttu-id="e91b3-119">コンパイル単位の作成</span><span class="sxs-lookup"><span data-stu-id="e91b3-119">Creating a compile unit</span></span>  
 <span data-ttu-id="e91b3-120">CodeDOM は、<xref:System.CodeDom.CodeCompileUnit> と呼ばれるオブジェクトを定義します。このオブジェクトでは、コンパイルするソース コードをモデル化した CodeDOM オブジェクト グラフを参照できます。</span><span class="sxs-lookup"><span data-stu-id="e91b3-120">The CodeDOM defines an object called a <xref:System.CodeDom.CodeCompileUnit>, which can reference a CodeDOM object graph that models the source code to compile.</span></span> <span data-ttu-id="e91b3-121">**CodeCompileUnit** には、属性、名前空間、およびアセンブリへの参照を格納するためのプロパティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="e91b3-121">A **CodeCompileUnit** has properties for storing references to attributes, namespaces, and assemblies.</span></span>  
  
 <span data-ttu-id="e91b3-122"><xref:System.CodeDom.Compiler.CodeDomProvider> クラスから派生する CodeDom プロバイダーには、**CodeCompileUnit** が参照するオブジェクト グラフを処理するメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e91b3-122">The CodeDom providers that derive from the <xref:System.CodeDom.Compiler.CodeDomProvider> class contain methods that process the object graph referenced by a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="e91b3-123">簡単なアプリケーション用のオブジェクト グラフを作成するには、ソース コード モデルをアセンブルし、生成されたオブジェクト グラフを **CodeCompileUnit** から参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e91b3-123">To create an object graph for a simple application, you must assemble the source code model and reference it from a **CodeCompileUnit**.</span></span>  
  
 <span data-ttu-id="e91b3-124">新しいコンパイル単位を作成するには、次の例に示す構文を使います。</span><span class="sxs-lookup"><span data-stu-id="e91b3-124">You can create a new compile unit with the syntax demonstrated in this example:</span></span>  
  
 [!code-cpp[CodeDomExample#12](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#12)]
 [!code-csharp[CodeDomExample#12](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#12)]
 [!code-vb[CodeDomExample#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#12)]  
  
 <span data-ttu-id="e91b3-125"><xref:System.CodeDom.CodeSnippetCompileUnit> には、既に対象言語で記述されているソース コードのセクションを格納できますが、この単位は別の言語にはレンダリングできません。</span><span class="sxs-lookup"><span data-stu-id="e91b3-125">A <xref:System.CodeDom.CodeSnippetCompileUnit> can contain a section of source code that is already in the target language, but cannot be rendered to another language.</span></span>  
  
#### <a name="defining-a-namespace"></a><span data-ttu-id="e91b3-126">名前空間の定義</span><span class="sxs-lookup"><span data-stu-id="e91b3-126">Defining a namespace</span></span>  
 <span data-ttu-id="e91b3-127">名前空間を定義するには、<xref:System.CodeDom.CodeNamespace> を作成してから、適切なコンストラクターを使用するか **Name** プロパティを設定することにより、定義する名前空間の名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e91b3-127">To define a namespace, create a <xref:System.CodeDom.CodeNamespace> and assign a name for it using the appropriate constructor or by setting its **Name** property.</span></span>  
  
 [!code-cpp[CodeDomExample#13](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#13)]
 [!code-csharp[CodeDomExample#13](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#13)]
 [!code-vb[CodeDomExample#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#13)]  
  
#### <a name="importing-a-namespace"></a><span data-ttu-id="e91b3-128">名前空間のインポート</span><span class="sxs-lookup"><span data-stu-id="e91b3-128">Importing a namespace</span></span>  
 <span data-ttu-id="e91b3-129">名前空間のインポート ディレクティブを名前空間に追加するには、インポートする名前空間を示す <xref:System.CodeDom.CodeNamespaceImport> を **CodeNamespace.Imports** コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="e91b3-129">To add a namespace import directive to the namespace, add a <xref:System.CodeDom.CodeNamespaceImport> that indicates the namespace to import to the **CodeNamespace.Imports** collection.</span></span>  
  
 <span data-ttu-id="e91b3-130">**System** 名前空間のインポートを、`samples` という名前の **CodeNamespace** の **Imports** コレクションに追加するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="e91b3-130">The following code adds an import for the **System** namespace to the **Imports** collection of a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#14](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#14)]
 [!code-csharp[CodeDomExample#14](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#14)]
 [!code-vb[CodeDomExample#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#14)]  
  
#### <a name="linking-code-elements-into-the-object-graph"></a><span data-ttu-id="e91b3-131">コード要素のオブジェクト グラフへのリンク</span><span class="sxs-lookup"><span data-stu-id="e91b3-131">Linking code elements into the object graph</span></span>  
 <span data-ttu-id="e91b3-132">CodeDOM グラフを形成するすべてのコード要素は、CodeDOM グラフのルート オブジェクトのプロパティから直接参照される要素間の一連の参照によって、ツリーのルート要素である <xref:System.CodeDom.CodeCompileUnit> にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e91b3-132">All code elements that form a CodeDOM graph must be linked to the <xref:System.CodeDom.CodeCompileUnit> that is the root element of the tree by a series of references between elements directly referenced from the properties of the root object of the graph.</span></span> <span data-ttu-id="e91b3-133">オブジェクトをコンテナー オブジェクトのプロパティに設定し、コンテナー オブジェクトからの参照を確立します。</span><span class="sxs-lookup"><span data-stu-id="e91b3-133">Set an object to a property of a container object to establish a reference from the container object.</span></span>  
  
 <span data-ttu-id="e91b3-134">`samples` **CodeNamespace** をルートの **CodeCompileUnit** の **Namespaces** コレクション プロパティに追加するステートメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="e91b3-134">The following statement adds the `samples` **CodeNamespace** to the **Namespaces** collection property of the root **CodeCompileUnit**.</span></span>  
  
 [!code-cpp[CodeDomExample#15](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#15)]
 [!code-csharp[CodeDomExample#15](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#15)]
 [!code-vb[CodeDomExample#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#15)]  
  
#### <a name="defining-a-type"></a><span data-ttu-id="e91b3-135">型の定義</span><span class="sxs-lookup"><span data-stu-id="e91b3-135">Defining a type</span></span>  
 <span data-ttu-id="e91b3-136">CodeDOM を使ってクラス、構造体、インターフェイス、または列挙体を宣言するには、新しい <xref:System.CodeDom.CodeTypeDeclaration> を作成し、名前を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e91b3-136">To declare a class, structure, interface, or enumeration using the CodeDOM, create a new <xref:System.CodeDom.CodeTypeDeclaration>, and assign it a name.</span></span> <span data-ttu-id="e91b3-137">このために、**Name** プロパティを設定するコンストラクターのオーバーロードを使用する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e91b3-137">The following example demonstrates this using a constructor overload to set the **Name** property:</span></span>  
  
 [!code-cpp[CodeDomExample#16](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#16)]
 [!code-csharp[CodeDomExample#16](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#16)]
 [!code-vb[CodeDomExample#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#16)]  
  
 <span data-ttu-id="e91b3-138">名前空間に型を追加するには、名前空間に追加する型を表す <xref:System.CodeDom.CodeTypeDeclaration> を、**CodeNamespace** の **Types** コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="e91b3-138">To add a type to a namespace, add a <xref:System.CodeDom.CodeTypeDeclaration> that represents the type to add to the namespace to the **Types** collection of a **CodeNamespace**.</span></span>  
  
 <span data-ttu-id="e91b3-139">`class1` という名前のクラスを `samples` という名前の **CodeNamespace** に追加する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e91b3-139">The following example demonstrates how to add a class named `class1` to a **CodeNamespace** named `samples`:</span></span>  
  
 [!code-cpp[CodeDomExample#17](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#17)]
 [!code-csharp[CodeDomExample#17](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#17)]
 [!code-vb[CodeDomExample#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#17)]  
  
#### <a name="adding-class-members-to-a-class"></a><span data-ttu-id="e91b3-140">クラスへのクラス メンバーの追加</span><span class="sxs-lookup"><span data-stu-id="e91b3-140">Adding class members to a class</span></span>  
 <span data-ttu-id="e91b3-141"><xref:System.CodeDom> 名前空間には、クラス メンバーを表すために使用できるさまざまな要素が用意されています。</span><span class="sxs-lookup"><span data-stu-id="e91b3-141">The <xref:System.CodeDom> namespace provides a variety of elements that can be used to represent class members.</span></span> <span data-ttu-id="e91b3-142">各クラス メンバーは、<xref:System.CodeDom.CodeTypeDeclaration> の **Members** コレクションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="e91b3-142">Each class member can be added to the **Members** collection of a <xref:System.CodeDom.CodeTypeDeclaration>.</span></span>  
  
#### <a name="defining-a-code-entry-point-method-for-an-executable"></a><span data-ttu-id="e91b3-143">実行可能プログラムのコード エントリ ポイント メソッドの定義</span><span class="sxs-lookup"><span data-stu-id="e91b3-143">Defining a code entry point method for an executable</span></span>  
 <span data-ttu-id="e91b3-144">実行可能プログラムのコードを記述する場合は、プログラムの実行を開始するメソッドを表す <xref:System.CodeDom.CodeEntryPointMethod> を作成して、プログラムのエントリ ポイントを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e91b3-144">If you are building code for an executable program, it is necessary to indicate the entry point of a program by creating a <xref:System.CodeDom.CodeEntryPointMethod> to represent the method at which program execution should begin.</span></span>  
  
 <span data-ttu-id="e91b3-145">"Hello World!" と出力するための **System.Console.WriteLine** を呼び出す <xref:System.CodeDom.CodeMethodInvokeExpression> を格納しているエントリ ポイント メソッドを定義する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e91b3-145">The following example demonstrates how to define an entry point method that contains a <xref:System.CodeDom.CodeMethodInvokeExpression> that calls **System.Console.WriteLine** to print "Hello World!":</span></span>  
  
 [!code-cpp[CodeDomExample#18](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#18)]
 [!code-csharp[CodeDomExample#18](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#18)]
 [!code-vb[CodeDomExample#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#18)]  
  
 <span data-ttu-id="e91b3-146">`Start` という名前のエントリ ポイント メソッドを `class1` の **Members** コレクションに追加するステートメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="e91b3-146">The following statement adds the entry point method named `Start` to the **Members** collection of `class1`:</span></span>  
  
 [!code-cpp[CodeDomExample#19](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source2.cpp#19)]
 [!code-csharp[CodeDomExample#19](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source2.cs#19)]
 [!code-vb[CodeDomExample#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source2.vb#19)]  
  
 <span data-ttu-id="e91b3-147">これで、<xref:System.CodeDom.CodeCompileUnit> という名前の `compileUnit` に、簡単な Hello World プログラムの CodeDOM グラフが追加されました。</span><span class="sxs-lookup"><span data-stu-id="e91b3-147">Now the <xref:System.CodeDom.CodeCompileUnit> named `compileUnit` contains the CodeDOM graph for a simple Hello World program.</span></span> <span data-ttu-id="e91b3-148">CodeDOM グラフからのコードの生成およびコンパイルについては、「[CodeDOM グラフからのソース コードの生成およびプログラムのコンパイル](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e91b3-148">For information on generating and compiling code from a CodeDOM graph, see [Generating Source Code and Compiling a Program from a CodeDOM Graph](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md).</span></span>  
  
### <a name="more-information-on-building-a-codedom-graph"></a><span data-ttu-id="e91b3-149">CodeDOM グラフの構築に関する詳細</span><span class="sxs-lookup"><span data-stu-id="e91b3-149">More information on building a CodeDOM graph</span></span>  
 <span data-ttu-id="e91b3-150">CodeDOM では、共通言語ランタイムをサポートするプログラミング言語の一般的なさまざまな種類のコード要素をサポートします。</span><span class="sxs-lookup"><span data-stu-id="e91b3-150">The CodeDOM supports the many common types of code elements found in programming languages that support the common language runtime.</span></span> <span data-ttu-id="e91b3-151">CodeDOM は、プログラミング言語のすべての機能を表す要素を提供するようにはデザインされていません。</span><span class="sxs-lookup"><span data-stu-id="e91b3-151">The CodeDOM was not designed to provide elements to represent all possible programming language features.</span></span> <span data-ttu-id="e91b3-152">CodeDOM 要素で簡単に表すことができないコードは、<xref:System.CodeDom.CodeSnippetExpression>、<xref:System.CodeDom.CodeSnippetStatement>、<xref:System.CodeDom.CodeSnippetTypeMember>、または <xref:System.CodeDom.CodeSnippetCompileUnit> にカプセル化できます。</span><span class="sxs-lookup"><span data-stu-id="e91b3-152">Code that cannot be represented easily with CodeDOM elements can be encapsulated in a <xref:System.CodeDom.CodeSnippetExpression>, a <xref:System.CodeDom.CodeSnippetStatement>, a <xref:System.CodeDom.CodeSnippetTypeMember>, or a <xref:System.CodeDom.CodeSnippetCompileUnit>.</span></span> <span data-ttu-id="e91b3-153">ただし、CodeDOM ではコードを自動的に他の言語に変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="e91b3-153">However, snippets cannot be translated to other languages automatically by the CodeDOM.</span></span>  
  
 <span data-ttu-id="e91b3-154">CodeDOM のそれぞれの型については、<xref:System.CodeDom> 名前空間の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e91b3-154">For documentation for the each of the CodeDOM types, see the reference documentation for the <xref:System.CodeDom> namespace.</span></span>  
  
 <span data-ttu-id="e91b3-155">特定の種類のコード要素を表す CodeDOM 要素を探すための一覧については、「[CodeDOM Quick Reference](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524)」(CodeDOM クイック リファレンス) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e91b3-155">For a quick chart to locate the CodeDOM element that represents a specific type of code element, see the [CodeDOM Quick Reference](http://msdn.microsoft.com/library/c77b8bfd-0a32-4e36-b59a-4f687f32c524).</span></span>
