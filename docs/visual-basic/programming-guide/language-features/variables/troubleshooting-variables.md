---
title: "Visual Basic における変数のトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "トラブルシューティング [Visual Basic], 変数"
  - "変数 [Visual Basic], トラブルシューティング"
ms.assetid: 928a2dc8-e565-4ae4-8ba3-80cc0cb50090
caps.latest.revision: 20
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Visual Basic における変数のトラブルシューティング
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

ここでは、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] で変数を使用するときに発生する可能性のある、いくつかの一般的な問題について説明します。  
  
## オブジェクトのメンバーにアクセスできない  
 コードからオブジェクトのプロパティまたはメソッドにアクセスしようとしたときに、発生する可能性があるエラーは 2 つあります。  
  
-   オブジェクト変数を特定の型として宣言した後、その型で定義されていないメンバーを参照すると、コンパイラによってエラー メッセージが生成されることがあります。  
  
-   オブジェクト変数に代入されたオブジェクトが、コードからアクセスしようとしたメンバーを公開していないと、ランタイム <xref:System.MemberAccessException> が発生します。[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) の変数の場合は、メンバーが `Public` でないときにもこの例外が発生します。 この原因は、遅延バインディングで許可されているのは、`Public` メンバーへのアクセスのみのためです。  
  
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)で型チェックが `On` に設定されている場合、オブジェクト変数がアクセスできるのは、その変数の宣言時に指定したクラスのメソッドとプロパティだけです。 次に例を示します。  
  
 [!CODE [VbVbalrStatements#49](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrStatements#49)]  
  
 [!code-vb[VbVbalrVariables#2](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/troubleshooting-variables_2.vb)]  
  
 この例の場合、`p` で使用できるのは <xref:System.Object> クラス自体のメンバーのみです。`Left` プロパティは含まれません。 一方、`q` は、<xref:System.Windows.Forms.Label> 型として宣言されているため、<xref:System.Windows.Forms> 名前空間の <xref:System.Windows.Forms.Label> クラスのすべてのメソッドとプロパティを使用できます。  
  
### 修正方法  
 特定のクラスのオブジェクトにあるすべてのメンバーにアクセスできるようにするには、オブジェクト変数をできる限りそのクラスの型で宣言します。 オブジェクト型がコンパイル時にわからないなどの理由で、それができない場合は、`Option Strict` を `Off` に設定し、変数を [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) として宣言します。 これにより任意の型のオブジェクトを変数に代入できます。また、現在変数に代入されているオブジェクトが受け入れ可能な型であることを確認する必要があります。 この確認には、[TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) を使用できます。  
  
## 他のコンポーネントが変数にアクセスできない  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] では、名前の*大文字と小文字は区別されません*。 2 つの名前の違いが英字の大文字と小文字の違いだけの場合、コンパイラでは 2 つを同じ名前と解釈します。 たとえば、`ABC` と `abc` は、宣言された同じ要素を参照していると見なされます。  
  
 しかし、共通言語ランタイム \(CLR\) のバインディングでは*大文字と小文字が区別されます*。 このため、アセンブリまたは DLL を作成し、他のアセンブリで使用できるようにすると、名前の大文字と小文字が区別されるようになります。 たとえば、`ABC` という名前の要素を持つクラスを定義し、他のアセンブリから共通言語ランタイムを通じてこのクラスを使用する場合は、この要素を `ABC` として参照する必要があります。 後でクラスを再コンパイルして要素の名前を `abc` に変更すると、このクラスを使用していた他のアセンブリがこの要素にアクセスできなくなります。 したがって、アセンブリを更新してリリースするときは、パブリックな要素の名前の大文字と小文字を変更しないでください。  
  
 詳細については、「[共通言語ランタイム](../Topic/Common%20Language%20Runtime%20\(CLR\).md)」を参照してください。  
  
### 修正方法  
 他のコンポーネントから変数にアクセスできるようにするには、その変数の名前を、大文字と小文字が区別されるものとして扱います。 作成したクラスまたはモジュールをテストするときには、他のアセンブリが適切な変数にバインドされることを確認します。 コンポーネントの公開後は、大文字と小文字の変更を含め、既存の変数名は変更しないようにします。  
  
## 誤った変数が使用される  
 同じ名前の変数が複数存在すると、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラは、その名前への参照をそれぞれ解決しようと試みます。 変数のスコープが異なる場合、コンパイラは、参照を最も狭いスコープの宣言に解決します。 変数のスコープが同じ場合、解決は失敗し、コンパイラはエラーを発行します。 詳細については、「[References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」を参照してください。  
  
### 修正方法  
 同じ名前でスコープが異なる変数を使わないようにします。 他のアセンブリまたはプロジェクトを使用している場合は、その外部コンポーネントで定義された名前を使うことはできるだけ避けてください。 同じ名前の変数が複数ある場合は、変数への参照ごとに修飾子を付けるようにしてください。 詳細については、「[References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」を参照してください。  
  
## 参照  
 [Variables](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)   
 [How to: Access Members of an Object](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)   
 [Object Variable Values](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)   
 [How to: Determine What Type an Object Variable Refers To](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)