---
title: '方法: CodeDOM を使用して XML ドキュメント ファイルを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CodeDOM, generating XML documentation
- XML documentation, creating using CodeDOM
- Code Document Object Model, generating XML documentation
ms.assetid: e3b80484-36b9-41dd-9d21-a2f9a36381dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81d09188ade29b0cac8985da218494f5373980cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397154"
---
# <a name="how-to-create-an-xml-documentation-file-using-codedom"></a><span data-ttu-id="97a56-102">方法: CodeDOM を使用して XML ドキュメント ファイルを作成する</span><span class="sxs-lookup"><span data-stu-id="97a56-102">How to: Create an XML Documentation File Using CodeDOM</span></span>
<span data-ttu-id="97a56-103">CodeDOM を利用し、XML ドキュメントを生成するコードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="97a56-103">CodeDOM can be used to create code that generates XML documentation.</span></span> <span data-ttu-id="97a56-104">XML ドキュメント コメントを含む CodeDOM グラフを作成する、コードを生成する、XML 文書出力を作成するコンパイラ オプションでその生成されたコードをコンパイルするというプロセスが行われます。</span><span class="sxs-lookup"><span data-stu-id="97a56-104">The process involves creating the CodeDOM graph that contains the XML documentation comments, generating the code, and compiling the generated code with the compiler option that creates the XML documentation output.</span></span>  
  
### <a name="to-create-a-codedom-graph-that-contains-xml-documentation-comments"></a><span data-ttu-id="97a56-105">XML ドキュメント コメントを含む CodeDOM グラフを作成するには</span><span class="sxs-lookup"><span data-stu-id="97a56-105">To create a CodeDOM graph that contains XML documentation comments</span></span>  
  
1.  <span data-ttu-id="97a56-106">サンプル アプリケーションの CodeDOM グラフを含む <xref:System.CodeDom.CodeCompileUnit> を作成します。</span><span class="sxs-lookup"><span data-stu-id="97a56-106">Create a <xref:System.CodeDom.CodeCompileUnit> containing the CodeDOM graph for the sample application.</span></span>  
  
2.  <span data-ttu-id="97a56-107"><xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> コンストラクターを使用します。このとき、`docComment` パラメーターを `true` に設定し、XML ドキュメント コメントの要素とテキストを作成します。</span><span class="sxs-lookup"><span data-stu-id="97a56-107">Use the <xref:System.CodeDom.CodeCommentStatement.%23ctor%2A> constructor with the `docComment` parameter set to `true` to create the XML documentation comment elements and text.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#4)]
     [!code-vb[CodeDomHelloWorldSample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#4)]  
  
### <a name="to-generate-the-code-from-the-codecompileunit"></a><span data-ttu-id="97a56-108">CodeCompileUnit からコードを生成するには</span><span class="sxs-lookup"><span data-stu-id="97a56-108">To generate the code from the CodeCompileUnit</span></span>  
  
1.  <span data-ttu-id="97a56-109"><xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> メソッドを使用し、コードを生成し、コンパイルするソース ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="97a56-109">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code and create a source file to be compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#5)]
     [!code-vb[CodeDomHelloWorldSample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#5)]  
  
### <a name="to-compile-the-code-and-generate-the-documentation-file"></a><span data-ttu-id="97a56-110">コードをコンパイルし、ドキュメント ファイルを生成するには</span><span class="sxs-lookup"><span data-stu-id="97a56-110">To compile the code and generate the documentation file</span></span>  
  
1.  <span data-ttu-id="97a56-111"><xref:System.CodeDom.Compiler.CompilerParameters> オブジェクトの <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> プロパティに **/doc** コンパイラ オプションを追加し、オブジェクトを <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> メソッドに渡し、コードのコンパイル時に XML ドキュメント ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="97a56-111">Add the **/doc** compiler option to the <xref:System.CodeDom.Compiler.CompilerParameters.CompilerOptions%2A> property of a <xref:System.CodeDom.Compiler.CompilerParameters> object and pass the object to the <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A> method to create the XML documentation file when the code is compiled.</span></span>  
  
     [!code-csharp[CodeDomHelloWorldSample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#6)]
     [!code-vb[CodeDomHelloWorldSample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="97a56-112">例</span><span class="sxs-lookup"><span data-stu-id="97a56-112">Example</span></span>  
 <span data-ttu-id="97a56-113">次のコード例では、ドキュメント コメントのある CodeDOM グラフを作成し、グラフからコード ファイルを生成し、ファイルをコンパイルし、関連 XML ドキュメント ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="97a56-113">The following code example creates a CodeDOM graph with documentation comments, generates a code file from the graph, and compiles the file and creates an associated XML documentation file.</span></span>  
  
 [!code-csharp[CodeDomHelloWorldSample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDomHelloWorldSample/cs/program.cs#1)]
 [!code-vb[CodeDomHelloWorldSample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDomHelloWorldSample/vb/program.vb#1)]  
  
 <span data-ttu-id="97a56-114">このコード例では、HelloWorldDoc.xml ファイルで次の XML ドキュメントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="97a56-114">The code example creates the following XML documentation in the HelloWorldDoc.xml file.</span></span>  
  
```xml  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="97a56-115">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="97a56-115">Compiling the Code</span></span>  
  
-   <span data-ttu-id="97a56-116">このコード サンプルを正しく実行するには、`FullTrust` アクセス許可を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97a56-116">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97a56-117">参照</span><span class="sxs-lookup"><span data-stu-id="97a56-117">See Also</span></span>  
 [<span data-ttu-id="97a56-118">XML の使用によるコードのドキュメントの作成</span><span class="sxs-lookup"><span data-stu-id="97a56-118">Documenting Your Code with XML</span></span>](~/docs/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [<span data-ttu-id="97a56-119">XML ドキュメント コメント</span><span class="sxs-lookup"><span data-stu-id="97a56-119">XML Documentation Comments</span></span>](~/docs/csharp/programming-guide/xmldoc/xml-documentation-comments.md)  
 [<span data-ttu-id="97a56-120">XML に関するドキュメント</span><span class="sxs-lookup"><span data-stu-id="97a56-120">XML Documentation</span></span>](/cpp/ide/xml-documentation-visual-cpp)
