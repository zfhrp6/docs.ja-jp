---
title: "Parameter List (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, procedures"
  - "parameters, Visual Basic"
  - "parameters, lists"
  - "parameter lists"
  - "Visual Basic code, parameter lists"
  - "arguments [Visual Basic], Visual Basic"
  - "procedures, parameter lists"
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Parameter List (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

呼び出し時に、プロシージャが受け取ることのできるパラメーターを指定します。  複数のパラメーターを指定するときは、コンマ \(,\) で区切ります。  パラメーターを 1 つ定義する場合の構文は次のとおりです。  
  
## 構文  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## 指定項目  
 `attributelist`  
 省略可能です。  このパラメーターに適用する属性の一覧を指定します。  [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) は、山かっこ \(`<` および `>`\) で囲む必要があります。  
  
 `Optional`  
 省略可能です。  プロシージャを呼び出すときに、このパラメーターを省略できることを示します。  
  
 `ByVal`  
 省略可能です。  呼び出し元のコードにある、対応する引数の基になる可変要素を、プロシージャが置き換えたり再割り当てしたりできないことを示します。  
  
 `ByRef`  
 省略可能です。  呼び出し元のコードにある基の可変要素を、呼び出し元のコード自体と同じようにプロシージャが変更できることを示します。  
  
 `ParamArray`  
 省略可能です。  パラメーター リストの最後のパラメーターが、指定されたデータ型の省略可能な要素の配列であることを示します。  これを指定すると、呼び出し元のコードから任意の数の引数をプロシージャに渡すことができます。  
  
 `parametername`  
 必ず指定します。  パラメーターを表すローカル変数の名前を指定します。  
  
 `parametertype`  
 `Option Strict` が `On` の場合は、必ず指定します。  パラメーターを表すローカル変数のデータ型を指定します。  
  
 `defaultvalue`  
 `Optional` パラメーターの場合は必ず指定します。  任意の定数、または結果がパラメーターのデータ型になる定数式を指定します。  型が `Object`、つまりクラス、インターフェイス、配列、または構造体の場合、既定値に指定できるのは `Nothing` だけです。  
  
## 解説  
 パラメーターはかっこで囲み、コンマで区切って指定します。  パラメーターはどのデータ型でも宣言できます。  `parametertype` を指定しなかった場合は、既定値の `Object` に設定されます。  
  
 呼び出し元のコードはプロシージャを呼び出すとき、各必須パラメーターに*引数*を渡します。  詳細については、「[Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md)」を参照してください。  
  
 呼び出し元のコードが各パラメーターに渡す引数は、呼び出し元のコードにある基の要素へのポインターです。  この要素が*不変* \(定数、リテラル、列挙値、または式\) である場合、どのコードからも要素を変更できません。  要素が*可変* \(宣言された変数、フィールド、プロパティ、配列要素、構造体要素\) である場合は、呼び出し元のコードから要素を変更できます。  詳細については、「[Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md)」を参照してください。  
  
 可変要素が `ByRef` で渡された場合は、プロシージャからも要素を変更できます。  詳細については、「[Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md)」を参照してください。  
  
## 規則  
  
-   **かっこ。**パラメーター リストを指定する場合は、かっこで囲む必要があります。  パラメーターを指定しない場合でも、空のリストをかっこで囲むことができます。  こうすると、プロシージャであると明確に示すことができるので、コードが読みやすくなります。  
  
-   **省略可能なパラメーター。**パラメーターに `Optional` 修飾子を指定すると、リスト内の後続のすべてのパラメーターにも `Optional` 修飾子を使用し、オプションで宣言することが必要になります。  
  
     省略可能なパラメーターの宣言には、それぞれ `defaultvalue` 句を指定する必要があります。  
  
     詳細については、「[Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)」を参照してください。  
  
-   **パラメーター配列。** `ParamArray` パラメーターには、`ByVal` を指定する必要があります。  
  
     同じパラメーター リストに `Optional` と `ParamArray` の両方を指定することはできません。  
  
     詳細については、「[Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)」を参照してください。  
  
-   **値渡し。**既定では、すべての引数が `ByVal` で渡されます。つまり、プロシージャは基になる可変要素を変更できません。  ただし、要素が参照型であれば、プロシージャは基になるオブジェクトの内容やメンバーを更できます \(オブジェクト自体を置き換えたり再割り当てしたりすることはできません\)。  
  
-   **パラメーター名。**パラメーターのデータ型が配列である場合は、`parametername` のすぐ後にかっこを続けます。  パラメーター名の詳細については、「[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
## 使用例  
 パラメーターが 2 つ定義された `Function` プロシージャの例は、次のようになります。  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/parameter-list_1.vb)]  
  
## 参照  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)