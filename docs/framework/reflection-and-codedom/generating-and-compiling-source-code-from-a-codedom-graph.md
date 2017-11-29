---
title: "CodeDOM グラフからのソース コードの生成およびコンパイル"
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
- CodeDOM, generating source code
- Code Document Object Model, graphs
- templated code generation
- source code, generating
- dynamically representing source code
- generating CodeDOM graphs
- Code Document Object Model, generating source code
- translating language to language
- compiling assemblies
- generating source code in multiple languages
- graphing with CodeDOM
- dynamic compilation
- assemblies [.NET Framework], CodeDOM
- source code generation
- outputting source code by CodeDOM
- code generators
- compiling source code, multiple languages
- CodeDOM, graphs
ms.assetid: 6c864c8e-6dd3-4a65-ace0-36879d9a9c42
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 55ba7c1b9dd7e8c912903fb9827e0073a8329abb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="generating-and-compiling-source-code-from-a-codedom-graph"></a><span data-ttu-id="c2623-102">CodeDOM グラフからのソース コードの生成およびコンパイル</span><span class="sxs-lookup"><span data-stu-id="c2623-102">Generating and Compiling Source Code from a CodeDOM Graph</span></span>
<span data-ttu-id="c2623-103"><xref:System.CodeDom.Compiler> 名前空間は、CodeDOM オブジェクト グラフからソース コードを生成し、サポートされているコンパイラでコンパイルを管理するためのインターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="c2623-103">The <xref:System.CodeDom.Compiler> namespace provides interfaces for generating source code from CodeDOM object graphs and for managing compilation with supported compilers.</span></span> <span data-ttu-id="c2623-104">コード プロバイダーは、CodeDOM グラフに基づいて、特定のプログラミング言語でソース コードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="c2623-104">A code provider can produce source code in a particular programming language according to a CodeDOM graph.</span></span> <span data-ttu-id="c2623-105"><xref:System.CodeDom.Compiler.CodeDomProvider> から派生したクラスは、通常、プロバイダーが対応している言語のコードを生成し、コンパイルするためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c2623-105">A class that derives from <xref:System.CodeDom.Compiler.CodeDomProvider> can typically provide methods for generating and compiling code for the language the provider supports.</span></span>  
  
## <a name="using-a-codedom-code-provider-to-generate-source-code"></a><span data-ttu-id="c2623-106">CodeDOM コード プロバイダーを使用してソース コードを生成する</span><span class="sxs-lookup"><span data-stu-id="c2623-106">Using a CodeDOM code provider to generate source code</span></span>  
 <span data-ttu-id="c2623-107">特定の言語でソース コードを生成するには、生成するソース コードの構造を表す CodeDOM グラフが必要です。</span><span class="sxs-lookup"><span data-stu-id="c2623-107">To generate source code in a particular language, you need a CodeDOM graph that represents the structure of the source code to generate.</span></span>  
  
 <span data-ttu-id="c2623-108"><xref:Microsoft.CSharp.CSharpCodeProvider> のインスタンスを作成する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c2623-108">The following example demonstrate how to create an instance of a <xref:Microsoft.CSharp.CSharpCodeProvider>:</span></span>  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 <span data-ttu-id="c2623-109">コード生成のグラフは通常、<xref:System.CodeDom.CodeCompileUnit> に含まれます。</span><span class="sxs-lookup"><span data-stu-id="c2623-109">The graph for code generation is typically contained in a <xref:System.CodeDom.CodeCompileUnit>.</span></span> <span data-ttu-id="c2623-110">CodeDOM グラフが含まれる **CodeCompileUnit** のコードを生成するには、コード プロバイダーの <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c2623-110">To generate code for a **CodeCompileUnit** that contains a CodeDOM graph, call the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method of the code provider.</span></span> <span data-ttu-id="c2623-111">このメソッドには <xref:System.IO.TextWriter> のパラメーターがあり、それがソース コードの生成に利用されます。そのため、場合により、書き込みに使用する **TextWriter** を最初に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2623-111">This method has a parameter for a <xref:System.IO.TextWriter> that it uses to generate the source code, so it is sometimes necessary to first create a **TextWriter** that can be written to.</span></span> <span data-ttu-id="c2623-112">次の例では、**CodeCompileUnit** からコードを生成し、生成したソース コードを HelloWorld.cs という名前のファイルに書き込んでいます。</span><span class="sxs-lookup"><span data-stu-id="c2623-112">The following example demonstrates generating code from a **CodeCompileUnit** and writing the generated source code to a file named HelloWorld.cs.</span></span>  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## <a name="using-a-codedom-code-provider-to-compile-assemblies"></a><span data-ttu-id="c2623-113">CodeDOM コード プロバイダーを使用してアセンブリをコンパイルする</span><span class="sxs-lookup"><span data-stu-id="c2623-113">Using a CodeDOM code provider to compile assemblies</span></span>  
 <span data-ttu-id="c2623-114">**コンパイルを呼び出す**</span><span class="sxs-lookup"><span data-stu-id="c2623-114">**Invoking compilation**</span></span>  
  
 <span data-ttu-id="c2623-115">CodeDom プロバイダーを利用してアセンブリをコンパイルするには、コンパイラが理解できる言語でコンパイルするソース コードか、コンパイルするソース コードの生成元になる CodeDOM グラフを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2623-115">To compile an assembly using a CodeDom provider, you must have either source code to compile in a language for which you have a compiler, or a CodeDOM graph that source code to compile can be generated from.</span></span>  
  
 <span data-ttu-id="c2623-116">CodeDOM グラフからコンパイルする場合、コード プロバイダーの <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> メソッドにグラフを含む <xref:System.CodeDom.CodeCompileUnit> を渡します。</span><span class="sxs-lookup"><span data-stu-id="c2623-116">If you are compiling from a CodeDOM graph, pass the <xref:System.CodeDom.CodeCompileUnit> containing the graph to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> method of the code provider.</span></span> <span data-ttu-id="c2623-117">コンパイラが理解できる言語のソース コード ファイルがある場合、CodeDOM プロバイダーの <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> メソッドにソース コードを含むファイルの名前を渡します。</span><span class="sxs-lookup"><span data-stu-id="c2623-117">If you have a source code file in a language that the compiler understands, pass the name of the file containing the source code to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method of the CodeDom provider.</span></span> <span data-ttu-id="c2623-118">コンパイラが理解できる言語のソース コードを含む文字列を CodeDOM プロバイダーの <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> メソッドに渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="c2623-118">You can also pass a string containing source code in a language that the compiler understands to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> method of the CodeDom provider.</span></span>  
  
 <span data-ttu-id="c2623-119">**コンパイル パラメーターの構成**</span><span class="sxs-lookup"><span data-stu-id="c2623-119">**Configuring compilation parameters**</span></span>  
  
 <span data-ttu-id="c2623-120">CodeDOM プロバイダーの標準的なコンパイル呼び出しメソッドにはすべて、型 <xref:System.CodeDom.Compiler.CompilerParameters> のパラメーターがあります。これはコンパイルに使用するオプションを示します。</span><span class="sxs-lookup"><span data-stu-id="c2623-120">All of the standard compilation-invoking methods of a CodeDom provider have a parameter of type <xref:System.CodeDom.Compiler.CompilerParameters> that indicates the options to use for compilation.</span></span>  
  
 <span data-ttu-id="c2623-121">**CompilerParameters** の <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> プロパティに出力アセンブリのファイル名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c2623-121">You can specify a file name for the output assembly in the <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> property of the **CompilerParameters**.</span></span> <span data-ttu-id="c2623-122">指定しない場合、既定の出力ファイル名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c2623-122">Otherwise, a default output file name will be used.</span></span>  
  
 <span data-ttu-id="c2623-123">既定では、新規の **CompilerParameters** は、<xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> プロパティを **false** に設定して初期化されます。</span><span class="sxs-lookup"><span data-stu-id="c2623-123">By default, a new **CompilerParameters** is initialized with its <xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> property set to **false**.</span></span> <span data-ttu-id="c2623-124">実行可能ファイル プログラムをコンパイルする場合、**GenerateExecutable** プロパティを **true** に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2623-124">If you are compiling an executable program, you must set the **GenerateExecutable** property to **true**.</span></span> <span data-ttu-id="c2623-125">**GenerateExecutable** を **false** に設定すると、コンパイラはクラス ライブラリを生成します。</span><span class="sxs-lookup"><span data-stu-id="c2623-125">When the **GenerateExecutable** is set to **false**, the compiler will generate a class library.</span></span>  
  
 <span data-ttu-id="c2623-126">CodeDOM グラフから実行可能ファイルをコンパイルする場合、グラフに <xref:System.CodeDom.CodeEntryPointMethod> を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2623-126">If you are compiling an executable from a CodeDOM graph, a <xref:System.CodeDom.CodeEntryPointMethod> must be defined in the graph.</span></span> <span data-ttu-id="c2623-127">コードのエントリ ポイントが複数存在するとき、場合によっては、使用するエントリ ポイントを定義するクラスの名前に **CompilerParameters** の <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> プロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2623-127">If there are multiple code entry points, it may be necessary to set the <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> property of the **CompilerParameters** to the name of the class that defines the entry point to use.</span></span>  
  
 <span data-ttu-id="c2623-128">生成された実行可能ファイルにデバッグ情報を追加するには、<xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> プロパティを **true** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c2623-128">To include debug information in a generated executable, set the <xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="c2623-129">プロジェクトがアセンブリを参照する場合、コンパイルを呼び出すときに使用する **CompilerParameters** の <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> プロパティとして、<xref:System.Collections.Specialized.StringCollection> の項目としてのアセンブリ名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2623-129">If your project references any assemblies, you must specify the assembly names as items in a <xref:System.Collections.Specialized.StringCollection> as the <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> property of the **CompilerParameters** you use when invoking compilation.</span></span>  
  
 <span data-ttu-id="c2623-130"><xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> プロパティを **true** に設定することで、ディスクではなくメモリに書き込まれるアセンブリをコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="c2623-130">You can compile an assembly that is written to memory rather than disk by setting the <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> property to **true**.</span></span> <span data-ttu-id="c2623-131">アセンブリをメモリに生成すると、<xref:System.CodeDom.Compiler.CompilerResults> の <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> プロパティから生成されたアセンブリの参照がコードに与えられることがあります。</span><span class="sxs-lookup"><span data-stu-id="c2623-131">When an assembly is generated in memory, your code can obtain a reference to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> property of a <xref:System.CodeDom.Compiler.CompilerResults>.</span></span> <span data-ttu-id="c2623-132">アセンブリをディスクに書き込む場合、**CompilerResults** の <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> プロパティから生成されたアセンブリのパスを取得できます。</span><span class="sxs-lookup"><span data-stu-id="c2623-132">If an assembly is written to disk, you can obtain the path to the generated assembly from the <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> property of a **CompilerResults**.</span></span>  
  
 <span data-ttu-id="c2623-133">コンパイル プロセスを呼び出すときに使用するカスタムのコマンドライン引数を指定するには、<xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> プロパティに文字列を設定します。</span><span class="sxs-lookup"><span data-stu-id="c2623-133">To specify a custom command-line arguments string to use when invoking the compilation process, set the string in the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property.</span></span>  
  
 <span data-ttu-id="c2623-134">コンパイラ プロセスの呼び出しに Win32 セキュリティ トークンが必要な場合、<xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> プロパティにトークンを指定します。</span><span class="sxs-lookup"><span data-stu-id="c2623-134">If a Win32 security token is required to invoke the compiler process, specify the token in the <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> property.</span></span>  
  
 <span data-ttu-id="c2623-135">コンパイルされたアセンブリに Win32 リソース ファイルをリンクするには、<xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> プロパティに Win32 リソース ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2623-135">To link a Win32 resource file into the compiled assembly, specify the name of the Win32 resource file in the <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> property.</span></span>  
  
 <span data-ttu-id="c2623-136">コンパイルを中止する警告レベルを指定するには、コンパイルを中止する警告レベルを表す整数に <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="c2623-136">To specify a warning level at which to halt compilation, set the <xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> property to an integer that represents the warning level at which to halt compilation.</span></span> <span data-ttu-id="c2623-137"><xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> プロパティを **true** に設定すると、警告が出た場合にコンパイルを中止するようにコンパイラを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="c2623-137">You can also configure the compiler to halt compilation if warnings are encountered by setting the <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> property to **true**.</span></span>  
  
 <span data-ttu-id="c2623-138">次のコード サンプルでは、<xref:System.CodeDom.Compiler.CodeDomProvider> クラスから派生した CodeDOM プロバイダーを利用し、ソース ファイルをコンパイルしています。</span><span class="sxs-lookup"><span data-stu-id="c2623-138">The following code example demonstrates compiling a source file using a CodeDom provider derived from the <xref:System.CodeDom.Compiler.CodeDomProvider> class.</span></span>  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## <a name="languages-with-initial-support"></a><span data-ttu-id="c2623-139">初期サポートの言語</span><span class="sxs-lookup"><span data-stu-id="c2623-139">Languages with Initial Support</span></span>  
 <span data-ttu-id="c2623-140">.NET Framework は、C#、Visual Basic、C++、および JScript のコード コンパイラとコード ジェネレーターを提供します。</span><span class="sxs-lookup"><span data-stu-id="c2623-140">The .NET Framework provides code compilers and code generators for the following languages: C#, Visual Basic, C++, and JScript.</span></span> <span data-ttu-id="c2623-141">CodeDOM のサポートは、言語固有のコード ジェネレーターとコード コンパイラを実装することで、他の言語に拡張できます。</span><span class="sxs-lookup"><span data-stu-id="c2623-141">CodeDOM support can be extended to other languages by implementing language-specific code generators and code compilers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2623-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2623-142">See Also</span></span>  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 [<span data-ttu-id="c2623-143">動的なソース コードの生成とコンパイル</span><span class="sxs-lookup"><span data-stu-id="c2623-143">Dynamic Source Code Generation and Compilation</span></span>](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)  
 [<span data-ttu-id="c2623-144">CodeDOM クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="c2623-144">CodeDOM Quick Reference</span></span>](http://msdn.microsoft.com/en-us/c77b8bfd-0a32-4e36-b59a-4f687f32c524)
