---
title: "CodeDOM グラフからのソース コードの生成およびコンパイル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アセンブリ [.NET Framework], CodeDOM"
  - "コード コンパイラ"
  - "Code Document Object Model, 生成 (ソース コードの)"
  - "Code Document Object Model, グラフ"
  - "コード ジェネレーター"
  - "CodeDOM, 生成 (ソース コードの)"
  - "CodeDOM, グラフ"
  - "コンパイル (アセンブリの)"
  - "コンパイル (ソース コードを), 複数言語"
  - "動的コンパイル"
  - "動的表現 (ソース コードの)"
  - "生成 (CodeDOM グラフの)"
  - "生成 (複数言語でのソース コードの)"
  - "グラフ化 (CodeDOM による)"
  - "出力 (CodeDOM によるソース コードの)"
  - "ソース コードの生成"
  - "ソース コード, 生成"
  - "テンプレートを使ったコード生成"
  - "翻訳 (言語から言語への)"
ms.assetid: 6c864c8e-6dd3-4a65-ace0-36879d9a9c42
caps.latest.revision: 20
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# CodeDOM グラフからのソース コードの生成およびコンパイル
<xref:System.CodeDom.Compiler> 名前空間には、CodeDOM オブジェクト グラフからソース コードを生成するためのインターフェイスや、サポートされているコンパイラでコンパイルを管理するためのインターフェイスが用意されています。  コード プロバイダーでは、CodeDOM グラフに基づいて、特定のプログラミング言語でソース コードを生成できます。  <xref:System.CodeDom.Compiler.CodeDomProvider> から派生したクラスは、一般にプロバイダーがサポートする言語でコードを生成してコンパイルするためのメソッドを提供します。  
  
## CodeDOM コード プロバイダーを使用したソース コードの生成  
 特定の言語でソース コードを生成するには、生成するソース コードの構造を表す CodeDOM グラフが必要です。  
  
 次に示すのは、<xref:Microsoft.CSharp.CSharpCodeProvider> のインスタンスを作成する方法のコード例です。  
  
 [!code-cpp[CodeDomExample#21](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#21)]
 [!code-csharp[CodeDomExample#21](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#21)]
 [!code-vb[CodeDomExample#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#21)]  
  
 コードを生成するためのグラフは、通常、<xref:System.CodeDom.CodeCompileUnit> に格納されます。  CodeDOM グラフを含む **CodeCompileUnit** のコードを生成するには、コード プロバイダーの <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> メソッドを呼び出します。  このメソッドは、ソース コードを生成するために使用する <xref:System.IO.TextWriter> のパラメーターを使用するため、まず、書き込み可能な **TextWriter** を作成することが必要な場合もあります。  **CodeCompileUnit** からコードを生成し、生成したソース コードを HelloWorld.cs という名前のファイルに書き込む例を次に示します。  
  
 [!code-cpp[CodeDomExample#22](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#22)]
 [!code-csharp[CodeDomExample#22](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#22)]
 [!code-vb[CodeDomExample#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#22)]  
  
## CodeDOM コード プロバイダーを使用したアセンブリのコンパイル  
 **コンパイルの実行**  
  
 CodeDom プロバイダーを使用してアセンブリをコンパイルするには、コンパイラが用意されている言語でコンパイルするソース コードか、コンパイルするソース コードを生成できる CodeDOM グラフのいずれかが必要です。  
  
 CodeDOM グラフからコンパイルする場合は、グラフを格納している <xref:System.CodeDom.CodeCompileUnit> をコード プロバイダーの <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A> メソッドに渡します。  コンパイラが認識できる言語のソース コード ファイルがある場合は、ソース コードを含むファイルの名前を、コード プロバイダーの <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> メソッドに渡します。  コンパイラが認識できる言語のソース コードを含む文字列を、CodeDom プロバイダーの <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A> メソッドに渡すこともできます。  
  
 **コンパイル パラメーターの構成**  
  
 CodeDom プロバイダーの標準的なコンパイル実行メソッドはすべて、コンパイルに使用するオプションを示す <xref:System.CodeDom.Compiler.CompilerParameters> 型のパラメーターを使用します。  
  
 **CompilerParameters** の <xref:System.CodeDom.Compiler.CompilerParameters.OutputAssembly%2A> プロパティで、出力アセンブリのファイル名を指定できます。  このファイル名を指定しない場合は、既定の出力ファイル名が使用されます。  
  
 既定では、新しい **CompilerParameters** は、<xref:System.CodeDom.Compiler.CompilerParameters.GenerateExecutable%2A> プロパティが **false** に設定された状態で初期化されます。  実行可能プログラムをコンパイルする場合は、**GenerateExecutable** プロパティを **true** に設定する必要があります。  **GenerateExecutable** が **false** に設定されている場合、コンパイラはクラス ライブラリを生成します。  
  
 CodeDOM グラフから実行可能ファイルをコンパイルする場合は、<xref:System.CodeDom.CodeEntryPointMethod> がグラフで定義されている必要があります。  複数のコード エントリ ポイントがある場合は、**CompilerParameters** の <xref:System.CodeDom.Compiler.CompilerParameters.MainClass%2A> プロパティを、使用するエントリ ポイントを定義するクラスの名前に設定する必要があります。  
  
 生成された実行可能ファイルにデバッグ情報を含めるには、<xref:System.CodeDom.Compiler.CompilerParameters.IncludeDebugInformation%2A> プロパティを **true** に設定します。  
  
 プロジェクトがアセンブリを参照する場合は、<xref:System.Collections.Specialized.StringCollection> 内の項目としてのアセンブリ名を、コンパイル時に使用する **CompilerParameters** の <xref:System.CodeDom.Compiler.CompilerParameters.ReferencedAssemblies%2A> プロパティとして指定する必要があります。  
  
 <xref:System.CodeDom.Compiler.CompilerParameters.GenerateInMemory%2A> プロパティを **true** に設定することで、ディスクではなくメモリに書き込まれるアセンブリをコンパイルできます。  アセンブリをメモリ上に生成すると、コードでは、生成されたアセンブリへの参照を <xref:System.CodeDom.Compiler.CompilerResults> の <xref:System.CodeDom.Compiler.CompilerResults.CompiledAssembly%2A> プロパティから取得できます。  アセンブリがディスクに書き込まれる場合は、生成されたアセンブリへのパスを、**CompilerResults** の <xref:System.CodeDom.Compiler.CompilerResults.PathToAssembly%2A> プロパティから取得できます。  
  
 コンパイル処理を実行するときに使用するカスタム コマンド ライン引数の文字列を指定するには、<xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> プロパティに文字列を設定します。  
  
 コンパイラ プロセスを起動するために Win32 セキュリティ トークンが必要な場合は、そのトークンを <xref:System.CodeDom.Compiler.CompilerParameters.UserToken%2A> プロパティに指定します。  
  
 コンパイルされるアセンブリに Win32 リソース ファイルへのリンクを設定するには、Win32 リソース ファイルの名前を <xref:System.CodeDom.Compiler.CompilerParameters.Win32Resource%2A> プロパティに指定します。  
  
 コンパイルを中断する警告レベルを指定するには、<xref:System.CodeDom.Compiler.CompilerParameters.WarningLevel%2A> プロパティに、コンパイルを中断する警告レベルを表す整数を設定します。  <xref:System.CodeDom.Compiler.CompilerParameters.TreatWarningsAsErrors%2A> プロパティを **true** に設定して、警告が発生した場合にコンパイルを中断するようにコンパイラを構成することもできます。  
  
 <xref:System.CodeDom.Compiler.CodeDomProvider> クラスから派生する CodeDom プロバイダーを使用してソース ファイルをコンパイルする方法のコード例を次に示します。  
  
 [!code-cpp[CodeDomExample#23](../../../samples/snippets/cpp/VS_Snippets_CLR/CodeDomExample/CPP/source3.cpp#23)]
 [!code-csharp[CodeDomExample#23](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomExample/CS/source3.cs#23)]
 [!code-vb[CodeDomExample#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomExample/VB/source3.vb#23)]  
  
## 既定でサポートされる言語  
 .NET Framework には、C\#、Visual Basic、C\+\+、および JScript の各言語に対応したコード コンパイラとコード ジェネレーターが用意されています。  CodeDOM に、言語固有のコード ジェネレーターおよびコード コンパイラを実装することで、これら以外の言語もサポートできます。  
  
## 参照  
 <xref:System.CodeDom>   
 <xref:System.CodeDom.Compiler>   
 [動的なソース コードの生成とコンパイル](../../../docs/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation.md)   
 [CodeDOM Quick Reference](http://msdn.microsoft.com/ja-jp/c77b8bfd-0a32-4e36-b59a-4f687f32c524)