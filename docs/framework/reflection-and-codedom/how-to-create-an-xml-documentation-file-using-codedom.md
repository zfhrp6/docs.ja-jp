---
title: "方法: CodeDOM を使用して XML ドキュメント ファイルを作成する | Microsoft Docs"
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
  - "Code Document Object Model, 生成 (XML ドキュメントを)"
  - "CodeDOM, 生成 (XML ドキュメントを)"
  - "XML ドキュメント, 作成 (CodeDOM を使用して)"
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法: CodeDOM を使用して XML ドキュメント ファイルを作成する
CodeDOM を使用して、XML ドキュメントを生成するコードを作成できます。  このプロセスには、XML ドキュメント コメントを含む CodeDOM グラフの作成、コードの生成、および生成されたコードのコンパイル \(XML ドキュメント出力を作成するコンパイラ オプションを使用\) が含まれます。  
  
### XML ドキュメント コメントを含む CodeDOM グラフを作成するには  
  
1.  サンプル アプリケーション用の CodeDOM グラフを含む <xref:System.CodeDom.CodeCompileUnit> を作成します。  
  
2.  `docComment` パラメーターを `true` に設定して <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> コンストラクターを使用し、XML ドキュメント コメントの要素およびテキストを作成します。  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### CodeCompileUnit からコードを生成するには  
  
1.  <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> メソッドを使用してコードを生成し、コンパイルするソース ファイルを作成します。  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### コードをコンパイルし、ドキュメント ファイルを生成するには  
  
1.  <xref:System.CodeDom.Compiler.CompilerParameters> オブジェクトの <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> プロパティに **\/doc** コンパイラ オプションを追加し、そのオブジェクトを <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> メソッドに渡して、コードがコンパイルされるときに XML ドキュメント ファイルを作成します。  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## 使用例  
 次のコード例では、ドキュメント コメントのある CodeDOM グラフを作成し、そのグラフからコード ファイルを生成し、そのファイルをコンパイルし、関連付けられた XML ドキュメント ファイルを作成します。  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 このコード例では、HelloWorldDoc.xml ファイルとして次の XML ドキュメントを作成します。  
  
```  
<?xml version="1.0" ?>   
<doc>  
  <assembly>  
    <name>HelloWorld</name>   
  </assembly>  
  <members>  
    <member name="T:Samples.Class1">  
      <summary>  
        Create a Hello World application.   
        <seealso cref="M:Samples.Class1.Main" />   
      </summary>  
    </member>  
    <member name="M:Samples.Class1.Main">  
      <summary>  
        Main method for HelloWorld application.   
        <para>Add a new paragraph to the description.</para>   
      </summary>  
    </member>  
  </members>  
</doc>  
```  
  
## コードのコンパイル  
  
-   このコード例を正常に実行するには、`FullTrust` アクセス許可セットが必要です。  
  
## 参照  
 [Documenting Your Code with XML](../Topic/Documenting%20Your%20Code%20with%20XML%20\(Visual%20Basic\).md)   
 [XML ドキュメント コメント](../Topic/XML%20Documentation%20Comments%20\(C%23%20Programming%20Guide\).md)   
 [XML に関するドキュメント](../Topic/XML%20Documentation%20\(Visual%20C++\).md)