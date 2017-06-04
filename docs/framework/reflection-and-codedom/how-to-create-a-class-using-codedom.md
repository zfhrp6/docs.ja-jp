---
title: "方法 : CodeDOM を使用してクラスを作成する | Microsoft Docs"
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
  - "Code Document Object Model, 作成 (クラスを)"
  - "Code Document Object Model, グラフ"
  - "CodeDOM, 作成 (クラスを)"
  - "CodeDOM, グラフ"
  - "グラフ化 (CodeDOM による)"
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : CodeDOM を使用してクラスを作成する
次の手順は、2 つのフィールド、3 つのプロパティ、1 つのメソッド、1 つのコンストラクター、および 1 つのエントリ ポイントを持つクラスを生成する CodeDOM グラフの作成方法およびコンパイル方法を示しています。  
  
1.  CodeDOM コードを使用してクラス用のソース コードを生成するコンソール アプリケーションを作成します。  
  
     この例では、生成クラスに `Sample` という名前が付けられ、生成されたコードは SampleCode という名前のファイルに書き込まれた `CodeDOMCreatedClass` という名前のクラスになります。  
  
2.  生成クラスで、CodeDOM グラフを初期化し、生成されたクラスのメンバー、コンストラクター、およびエントリ ポイント \(`Main` メソッド\) を CodeDOM メソッドを使用して定義します。  
  
     この例では、生成されたクラスには 2 つのフィールド、3 つのプロパティ、1 つのコンストラクター、1 つのメソッド、および `Main` メソッドがあります。  
  
3.  生成クラスで、言語に固有のコード プロバイダーを作成し、その <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> メソッドを呼び出して、グラフからコードを生成します。  
  
4.  アプリケーションをコンパイルおよび実行して、コードを生成します。  
  
     この例では、生成されたコードは SampleCode という名前のファイルに書き込まれています。  そのコードをコンパイルおよび実行して、サンプル出力を確認します。  
  
### CodeDOM コードを実行するアプリケーションを作成するには  
  
-   CodeDOM コードを含むコンソール アプリケーション クラスを作成します。  クラスでアセンブリ \(<xref:System.CodeDom.CodeCompileUnit>\) およびクラス \(<xref:System.CodeDom.CodeTypeDeclaration>\) を参照するために使用するグローバル フィールドを定義し、生成されたソース ファイルの名前を指定し、`Main` メソッドを宣言します。  
  
     [!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]
     [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]  
  
### CodeDOM グラフを初期化するには  
  
-   コンソール アプリケーション クラス用のコンストラクターで、アセンブリおよびクラスを初期化し、適切な宣言を CodeDOM グラフに追加します。  
  
     [!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]
     [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]  
  
### CodeDOM グラフにメンバーを追加するには  
  
-   クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeMemberField> オブジェクトを追加することによって、CodeDOM グラフにフィールドを追加します。  
  
     [!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]
     [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]  
  
-   クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeMemberProperty> オブジェクトを追加することによって、CodeDOM グラフにプロパティを追加します。  
  
     [!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]
     [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]  
  
-   クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeMemberMethod> オブジェクトを追加することによって、CodeDOM グラフにメソッドを追加します。  
  
     [!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]
     [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]  
  
-   クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeConstructor> オブジェクトを追加することによって、CodeDOM グラフにコンストラクターを追加します。  
  
     [!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]
     [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]  
  
-   クラスの <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> プロパティに <xref:System.CodeDom.CodeEntryPointMethod> オブジェクトを追加することによって、CodeDOM グラフにエントリ ポイントを追加します。  
  
     [!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]
     [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]  
  
### CodeDOM グラフからコードを生成するには  
  
-   <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> メソッドを呼び出すことによって、CodeDOM グラフからソース コードを生成します。  
  
     [!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]
     [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]  
  
### グラフを作成し、コードを生成するには  
  
1.  最初の手順で定義した `Main` メソッドに、前の手順で作成したメソッドを追加します。  
  
     [!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]
     [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]  
  
2.  生成クラスをコンパイルおよび実行します。  
  
## 使用例  
 前の手順のコードを、次のコード例に示します。  
  
 [!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)]
 [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]  
  
 前の例をコンパイルおよび実行すると、次のソース コードが生成されます。  
  
 [!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)]
 [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]  
  
 生成されたソース コードをコンパイルおよび実行すると、次の出力が生成されます。  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## コードのコンパイル  
  
-   このコード例を正常に実行するには、`FullTrust` アクセス許可セットが必要です。  
  
## 参照  
 [CodeDOM の使用方法](../../../docs/framework/reflection-and-codedom/using-the-codedom.md)   
 [CodeDOM グラフからのソース コードの生成およびコンパイル](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)