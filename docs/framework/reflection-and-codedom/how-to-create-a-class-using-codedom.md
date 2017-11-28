---
title: "方法 : CodeDOM を使用してクラスを作成する"
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
helpviewer_keywords:
- Code Document Object Model, graphs
- Code Document Object Model, creating classes
- graphing with CodeDOM
- CodeDOM, creating classes
- CodeDOM, graphs
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d92af3e2a04588e3942dd6c8c0625c607e08f123
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="0ba3e-102">方法 : CodeDOM を使用してクラスを作成する</span><span class="sxs-lookup"><span data-stu-id="0ba3e-102">How to: Create a Class Using CodeDOM</span></span>
<span data-ttu-id="0ba3e-103">2 つのフィールド、3 つのプロパティ、1 つのメソッド、1 つのコンストラクター、1 つのエントリ ポイントを含むクラスを生成する CodeDOM グラフを作成し、コンパイルする方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-103">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1.  <span data-ttu-id="0ba3e-104">CodeDOM コードを使用するコンソール アプリケーションを作成し、クラスのソース コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-104">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="0ba3e-105">この例では、生成元のクラスの名前が `Sample` で、生成されるコードが SampleCode という名前のファイルの `CodeDOMCreatedClass` という名前のクラスになります。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-105">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2.  <span data-ttu-id="0ba3e-106">生成元のクラスでは、CodeDOM グラフを初期化し、CodeDOM メソッドを利用して生成されるクラスのメンバー、コンストラクター、エントリ ポイント (`Main` メソッド) を定義します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-106">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="0ba3e-107">この例では、生成されるクラスに 2 つのフィールド、3 つのプロパティ、1 つのコンストラクター、1 つのメソッド、1 つの `Main` メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-107">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3.  <span data-ttu-id="0ba3e-108">生成元のクラスで、言語固有のコード プロバイダーを作成し、その <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> メソッドを呼び出してグラフからコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-108">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4.  <span data-ttu-id="0ba3e-109">アプリケーションをコンパイルして実行し、コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-109">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="0ba3e-110">この例では、生成されたコードが SampleCode という名前のファイルに入っています。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-110">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="0ba3e-111">そのコードをコンパイルして実行し、サンプル出力を確認します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-111">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="0ba3e-112">CodeDOM コードを実行するアプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="0ba3e-112">To create the application that will execute the CodeDOM code</span></span>  
  
-   <span data-ttu-id="0ba3e-113">CodeDOM コードを含むコンソール アプリケーション クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-113">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="0ba3e-114">このクラスでアセンブリ (<xref:System.CodeDom.CodeCompileUnit>) とクラス (<xref:System.CodeDom.CodeTypeDeclaration>) を参照するためのグローバル フィールドを定義し、生成されるソース ファイルの名前を指定し、`Main` メソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-114">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="0ba3e-115">CodeDOM グラフを初期化するには</span><span class="sxs-lookup"><span data-stu-id="0ba3e-115">To initialize the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="0ba3e-116">コンソール アプリケーション クラスのコンストラクターで、アセンブリとクラスを初期化し、適切な宣言を CodeDOM グラフに追加します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-116">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="0ba3e-117">CodeDOM グラフにメンバーを追加するには</span><span class="sxs-lookup"><span data-stu-id="0ba3e-117">To add members to the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="0ba3e-118">クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeMemberField> オブジェクトを追加することで CodeDOM グラフにフィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-118">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
-   <span data-ttu-id="0ba3e-119">クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeMemberProperty> オブジェクトを追加することで CodeDOM グラフにプロパティを追加します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-119">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
-   <span data-ttu-id="0ba3e-120">クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeMemberMethod> オブジェクトを追加することで CodeDOM グラフにメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-120">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
-   <span data-ttu-id="0ba3e-121">クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeConstructor> オブジェクトを追加することで CodeDOM グラフにコンストラクターを追加します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-121">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
-   <span data-ttu-id="0ba3e-122">クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeEntryPointMethod> オブジェクトを追加することで CodeDOM グラフにエントリ ポイントを追加します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-122">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="0ba3e-123">CodeDOM グラフからコードを生成するには</span><span class="sxs-lookup"><span data-stu-id="0ba3e-123">To generate the code from the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="0ba3e-124"><xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> メソッドを呼び出すことで CodeDOM グラフからソース コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-124">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="0ba3e-125">グラフを作成し、コードを生成するには</span><span class="sxs-lookup"><span data-stu-id="0ba3e-125">To create the graph and generate the code</span></span>  
  
1.  <span data-ttu-id="0ba3e-126">前の手順で作成したメソッドを最初の手順で定義した `Main` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-126">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2.  <span data-ttu-id="0ba3e-127">生成元のクラスをコンパイルし、実行します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-127">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ba3e-128">例</span><span class="sxs-lookup"><span data-stu-id="0ba3e-128">Example</span></span>  
 <span data-ttu-id="0ba3e-129">次のコード サンプルは、前の手順のコードです。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-129">The following code example shows the code from the preceding steps.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 <span data-ttu-id="0ba3e-130">前のサンプルをコンパイルし、実行すると、次のソース コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-130">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 <span data-ttu-id="0ba3e-131">生成されたソース コードは、コンパイルされ、実行されると、次の内容を出力します。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-131">The generated source code produces the following output when compiled and executed.</span></span>  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0ba3e-132">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="0ba3e-132">Compiling the Code</span></span>  
  
-   <span data-ttu-id="0ba3e-133">このコード サンプルを正しく実行するには、`FullTrust` アクセス許可を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ba3e-133">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ba3e-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ba3e-134">See Also</span></span>  
 [<span data-ttu-id="0ba3e-135">CodeDOM の使用方法</span><span class="sxs-lookup"><span data-stu-id="0ba3e-135">Using the CodeDOM</span></span>](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)  
 [<span data-ttu-id="0ba3e-136">CodeDOM グラフからのソース コードの生成およびコンパイル</span><span class="sxs-lookup"><span data-stu-id="0ba3e-136">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)
