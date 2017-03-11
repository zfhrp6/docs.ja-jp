---
title: "Optional (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Optional"
  - "vb.optional"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Optional keyword, contexts"
  - "Optional keyword"
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Optional (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャを呼び出すとき省略できる引数であることを示すキーワードです。  
  
## 解説  
 各省略可能なパラメーターに対して、このパラメーターの既定値として定数式を指定します。  式が [何も](../../../visual-basic/language-reference/nothing.md)と評価されると、パラメーターの既定値として値のデータ型の既定値が使用されます。  
  
 パラメーター リストに省略可能なパラメーターが含まれている場合、後続のすべてのパラメーターは、すべて省略可能である必要があります。  
  
 修飾子 `Optional` は、次の構文で使用します。  
  
-   [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  プロシージャを省略可能なパラメーターなしで呼び出すと、によってまたは名前の引数を位置渡すことができます。  詳細については、「[Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)」を参照してください。  
  
> [!NOTE]
>  また、オーバーロードを使用して、省略可能なパラメーターのプロシージャを定義できます。  1 種類の省略可能なパラメーターがある場合、パラメーターを受け入れるとして手順 1、 1 の 2 種類のオーバーロードされたバージョンを定義できます。  詳細については、「[Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)」を参照してください。  
  
## 使用例  
 次の例は、省略可能なパラメーターを持つプロシージャを定義しています。  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## 使用例  
 次の例では、場所を渡された引数と名前で渡された引数のプロシージャをダイヤルする方法を示します。  プロシージャに 2 個の省略可能なパラメーターがあります。  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/visualbasic/optional_1.vb)]  
  
## 参照  
 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)   
 [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)