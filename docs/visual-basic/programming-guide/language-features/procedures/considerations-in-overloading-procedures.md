---
title: "Considerations in Overloading Procedures (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "signatures, ParamArray arguments"
  - "ParamArray keyword, parameter arrays"
  - "ParamArray keyword, arguments and signatures"
  - "function overloading, implicit overloads for ParamArray"
  - "ParamArray keyword, signatures"
  - "Visual Basic code, procedures"
  - "arguments [Visual Basic], parameter arrays"
  - "procedures, overloading"
  - "parameters, lists"
  - "function overloading, typeless programming"
  - "typeless programming"
  - "function overloading, restrictions"
  - "arguments [Visual Basic], optional"
  - "optional arguments, overloading"
  - "signatures, procedure"
  - "parameter lists"
  - "parameter arrays, overloading arguments"
  - "Visual Basic code, parameter lists"
  - "procedure overloading, considerations"
  - "Option Explicit statement"
  - "restrictions, overloading procedures"
  - "procedures, parameter lists"
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
caps.latest.revision: 26
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 26
---
# Considerations in Overloading Procedures (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャをオーバーロードする場合、オーバーロードされる各バージョンに別々の*シグネチャ*を使用する必要があります。  通常は、各バージョンに別々のパラメーター リストを指定します。  詳細については、「[Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)」の「別のシグネチャ」を参照してください。  
  
 シグネチャが異なる場合は、`Function` プロシージャと `Sub` プロシージャとの間のオーバーロードも可能です。  戻り値を持つか持たないかという点だけが異なる 2 つのオーバーロードが共存することはできません。  
  
 プロパティは、プロシージャと同じようにオーバーロードでき、同じ制約を受けます。  ただし、プロシージャによるプロパティのオーバーロード、またはその逆のオーバーロードを行うことはできません。  
  
## オーバーロードされたバージョンの代替手段  
 特に、引数が省略可能な場合や引数の数が可変である場合、オーバーロードされたバージョンの代替手段を利用できる場合があります。  
  
 ただし、省略可能な引数はすべての言語でサポートされているとは限りません。また、パラメーターの配列は [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のみに限定されています。  他のいくつかの言語で書かれているコードから呼び出されるプロシージャを作成する場合、オーバーロードされたバージョンによって柔軟性が向上します。  
  
### オーバーロードと省略可能な引数  
 呼び出し元のコードが 1 つ以上の引数を指定または省略できる場合は、複数のオーバーロードされたバージョンを定義するか、省略可能なパラメーターを使用できます。  
  
#### オーバーロードされたバージョンを使用する場合  
 オーバーロードされたバージョンを定義するのは、次のような場合です。  
  
-   呼び出し元のコードが省略可能な引数を使用するかどうかによって、プロシージャ コード内のロジックが大きく異なる  
  
-   プロシージャのコードが、呼び出し元のコードが省略可能な引数を使っているかどうかを確認する有効な手段がない  これは、呼び出し元のコードからの提供が期待できない引数に、既定値として使用できる値がない場合などです。  
  
#### 省略可能なパラメーターを使用する場合  
 1 つ以上の省略可能なパラメーターを使用すると有効なのは、次のような場合です。  
  
-   呼び出し元のコードが省略可能な引数を使用していない場合に、パラメーターを既定値に設定する  この場合、1 つ以上の `Optional` パラメーターで 1 つのバージョンを定義すると、プロシージャのコードを単純化できます。  
  
 詳細については、「[Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)」を参照してください。  
  
### オーバーロードと ParamArray  
 呼び出し元のコードが使用する引数の数が可変の場合、複数のオーバーロードされたバージョンを定義するか、パラメーターの配列を使用します。  
  
#### オーバーロードされたバージョンを使用する場合  
 オーバーロードされたバージョンを定義するのは、次のような場合です。  
  
-   呼び出し元のコードがパラメーターの配列に格納する値の数が、少ないことが明らかな場合  
  
-   プロシージャのコード内のロジックが、呼び出し元のコードから提供される値の数によって大きく異なる  
  
-   呼び出し元のコードから、データ型の異なる値が提供されることがある  
  
#### パラメーターの配列を使用する場合  
 次の場合は、`ParamArray` を使用するのが適しています。  
  
-   呼び出し元のコードからパラメーターの配列に提供される値の数が予測できず、多数になる可能性がある場合  
  
-   プロシージャのロジックが、呼び出し元のコードから提供されたすべての値を反復処理し、すべての値にほぼ同じ操作を行う場合  
  
 詳細については、「[Parameter Arrays](../../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)」を参照してください。  
  
## 省略可能なパラメーターの暗黙のオーバーロード  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) パラメーターを持つプロシージャは、省略可能なパラメーターを持つバージョンと持たないバージョンの 2 つのオーバーロードされたプロシージャと同じです。  このようなプロシージャは、これらのいずれかに対応するパラメーターのリストではオーバーロードできません。  次の宣言はこのことを示しています。  
  
 [!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 省略可能なパラメーターが複数あるプロシージャでは、上の例と同様の理由で、暗黙のオーバーロードがいくつかあることになります。  
  
## パラメーター ParamArray の暗黙のオーバーロード  
 コンパイラは、[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) パラメーターを持つプロシージャが、パラメーター配列に渡される内容によって異なる無限の数のオーバーロードを持つと見なします。次に示すのは、それらのオーバーロードを大別したものです。  
  
-   呼び出し元のコードが `ParamArray` に引数を渡さない場合のオーバーロード  
  
-   呼び出し元のコードが `ParamArray` 要素型の 1 次元配列を渡す場合のオーバーロード  
  
-   呼び出し元のコードが  `ParamArray` 要素型の引数をその数だけ渡す場合のオーバーロード \(すべての正の整数に対して 1 つ\)  
  
 次の宣言は、これらの暗黙のオーバーロードを示しています。  
  
 [!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 このようなプロシージャは、パラメーター配列として 1 次元配列を受け取るパラメーター リストではオーバーロードできません。  ただし、他の暗黙のオーバーロードのシグネチャは使用できます。  次の宣言はこのことを示しています。  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## オーバーロードの代わりとしての型宣言を省略したプログラミング  
 呼び出し元のコードがパラメーターに異なるデータ型を渡す場合は、ような方法は、 JScript プログラミングです。  [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)または [\/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) のいずれかのコンパイラ オプションを使用すると、型チェックのスイッチを `Off` にできます。  これで、パラメーターのデータ型を宣言する必要がなくなります。  ただし、この方法には、オーバーロードとは違って次のような問題があります。  
  
-   型宣言を省略したプログラミングでは、実行コードが非効率的になります。  
  
-   渡される可能性があるすべてのデータ型をプロシージャでテストする必要があります。  
  
-   プロシージャがサポートしていないデータ型を呼び出し元のコードが渡しても、コンパイラでエラーが生成されません。  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Troubleshooting Procedures](../../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)