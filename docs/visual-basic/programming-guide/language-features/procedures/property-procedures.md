---
title: "Property プロシージャ (Visual Basic) | Microsoft Docs"
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
  - "Set ステートメント、Property プロシージャ"
  - "Visual Basic コード、プロシージャ"
  - "戻り値、Property プロシージャ"
  - "構文、Property プロシージャ"
  - "プロシージャ、プロパティ"
  - "Visual Basic コード、プロパティ"
  - "プロシージャ、呼び出し"
  - "プロパティ [Visual Basic]、カスタム"
  - "Property プロシージャ"
  - "Get ステートメント、Property プロシージャ"
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Property プロシージャ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Property プロシージャは、モジュール、クラス、または構造体のカスタム プロパティを操作する一連の [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ステートメントです。  Property プロシージャは、*プロパティ アクセサー*とも呼ばれます。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には次の Property プロシージャが用意されています。  
  
-   `Get` プロシージャは、プロパティの値を返します。  式の中でプロパティにアクセスするときに呼び出されます。  
  
-   `Set` プロシージャは、プロパティに値 \(オブジェクト参照を含む\) を設定します。  プロパティに値を代入するときに呼び出されます。  
  
 Property プロシージャは、通常は `Get`ステートメントと `Set` ステートメントを使ってペアで定義しますが、プロパティが読み取り専用 \([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)\) または書き込み専用 \([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)\) の場合は、一方のプロシージャだけを定義できます。  
  
 自動実装プロパティを使用する場合は、`Get` プロシージャおよび `Set` プロシージャを省略できます。  詳細については、「[Auto\-Implemented Properties](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)」を参照してください。  
  
 プロパティは、クラス、構造体、およびモジュールで定義できます。  プロパティは既定で `Public` になります。つまり、プロパティのコンテナーにアクセスできるアプリケーションであればどこからでも、プロパティを呼び出すことができます。  
  
 プロパティと変数の比較については、「[Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)」を参照してください。  
  
## 宣言の構文  
 プロパティ自体は、[Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) と `End Property` ステートメントに囲まれたコード ブロックで定義されます。  このブロック内に、宣言ステートメント \(`Get` または `Set`\) とそれに対応する `End` の宣言で囲まれた内部ブロックとして、各 Property プロシージャを記述します。  
  
 プロパティとそのプロシージャを宣言する構文は、次のとおりです。  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 `Modifiers` はアクセス レベルの他、オーバーロード、オーバーライド、共有、シャドウに関する情報、またはプロパティが読み取り専用か、書き込み専用かを指定します。  `Get` または `Set` の手順の `AccessLevel` は、プロパティに指定されたアクセス レベルよりも制限レベルです。  詳細については、「[Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)」を参照してください。  
  
### \[データ型\]  
 プロパティのデータ型とアクセス レベルは、Property プロシージャではなく、`Property` ステートメントに定義します。  プロパティに定義できるデータ型は 1 つだけです。  たとえば、`Decimal` 型で値を格納するが、`Double` 型の値を取得するようなプロパティを定義することはできません。  
  
### アクセス レベル  
 プロパティ自体に定義したアクセス レベルよりも制限の多いアクセスレベルを、Property プロシージャに定義できます。  たとえば、`Public` プロパティを定義しておいて、`Private Set` プロシージャを定義するなどが可能です。  このとき、一方の `Get` プロシージャは `Public` のままです。  一方の Property プロシージャのアクセス レベルだけを変更できます。また、プロパティ自体のアクセス レベルよりも制限の多いレベルにしか変更できません。  詳細については、「[How to: Declare a Property with Mixed Access Levels](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)」を参照してください。  
  
## パラメーター宣言  
 各パラメーターの宣言は、[Sub Procedures](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)の場合と同じ方法で行います。ただし、`ByVal` で渡す必要がある点が異なります。  
  
 パラメーター リストの各パラメーターの構文は次のとおりです。  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 パラメーターを省略可能にする場合は、宣言内で既定値を指定する必要があります。  既定値を指定する構文は次のとおりです。  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## プロパティ値  
 `Get` プロシージャでは、戻り値がプロパティの値として呼び出し元の式に返されます。  
  
 `Set` プロシージャでは、新しいプロパティ値を `Set` ステートメントのプロパティに渡します。  パラメーターを明示的に宣言する場合は、プロパティと同じデータ型で宣言する必要があります。  パラメーターを宣言しなければ、コンパイラはプロパティに代入する新しい値を表すために、暗黙のパラメーター `Value` を使用します。  
  
## 呼び出し構文  
 Property プロシージャは、プロパティを参照することによって暗黙的に呼び出されます。  変数の名前を使用するのと同じように、プロパティの名前を使用します。ただし、省略できないすべての引数の値を指定し、引数のリストをかっこで囲む必要があります。  指定する引数がない場合は、かっこを省略することもできます。  
  
 `Set` プロシージャを暗黙的に呼び出す構文は次のとおりです。  
  
 `propertyname[(argumentlist)] = expression`  
  
 `Get` プロシージャを暗黙的に呼び出す構文は次のとおりです。  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### 宣言と呼び出しの説明  
 次のプロパティは、フル ネームをファースト ネームとラスト ネームの 2 つの部分に分けて格納します。  呼び出しコードが  `fullName` を読み込むと、`Get` プロシージャが 2 つの部分を組み合わせてフル ネームを返します。  呼び出しコードが新しいフル ネームを代入すると、`Set` プロシージャはそれを 2 つの部分に分割します。  フル ネームに空白が含まれない場合は、全体をファースト ネームとして格納します。  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 `fullName` の Property プロシージャを呼び出す一般的な例は次のとおりです。  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [Function プロシージャ](../../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Operator Procedures](../../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [How to: Create a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-create-a-property.md)   
 [How to: Call a Property Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-a-property-procedure.md)   
 [How to: Declare and Call a Default Property in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)   
 [How to: Put a Value in a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-put-a-value-in-a-property.md)   
 [How to: Get a Value from a Property](../../../../visual-basic/programming-guide/language-features/procedures/how-to-get-a-value-from-a-property.md)