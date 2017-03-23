---
title: "関数式 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9b181b18a28a8b92a392fffdc10e08690d54f545
ms.lasthandoff: 03/13/2017

---
# <a name="function-expression-visual-basic"></a>Function 式 (Visual Basic)
パラメーターと関数のラムダ式を定義するコードを宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`parameterlist`|省略可能です。 このプロシージャのパラメーターを表すローカル変数名の一覧。 かっこは、リストが空の場合にも存在する必要があります。 参照してください[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)します。|  
|`expression`|必須です。 1 つの式。 式の型は、関数の戻り値の型です。|  
|`statements`|必須です。 使用して値を返すステートメントの一覧、`Return`ステートメントです。 (参照[Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md))。返される値の型は、関数の戻り値の型です。|  
  
## <a name="remarks"></a>コメント  
 A*ラムダ式*を計算し、値を返し、名前を持たない関数です。 ラムダ式を使用する引数として使用する以外にデリゲート型を使用する任意の場所`RemoveHandler`します。 詳細については、デリゲート、およびデリゲートでのラムダ式を使用する、次を参照してください。 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)と[厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)します。  
  
## <a name="lambda-expression-syntax"></a>ラムダ式の構文  
 標準的な関数のラムダ式の構文に似ています。 相違点は次のとおりです。  
  
-   ラムダ式には、名前がありません。  
  
-   ラムダ式がなど、修飾子を持つことはできません`Overloads`または`Overrides`です。  
  
-   ラムダ式は使用しないでください、`As`関数の戻り値の型を指定する句。 代わりに、型は、単一行のラムダ式の本体に評価される値または複数行のラムダ式の戻り値から推論されます。 たとえば、単一行のラムダ式の本体が`Where cust.City = "London"`、戻り値の型`Boolean`します。  
  
-   単一行のラムダ式の本体は、ステートメントではなく、式である必要があります。 本文は、関数プロシージャへの呼び出しがない sub プロシージャの呼び出しで構成できます。  
  
-   データ型、またはすべてを推論する必要がありますかすべてパラメーターが指定する必要があります。  
  
-   省略可能と Paramarray パラメーターを指定することはできません。  
  
-   ジェネリック パラメーターを指定することはできません。  
  
## <a name="example"></a>例  
 次の例では、単純なラムダ式を作成する&2; つの方法を示します。 最初の使用、`Dim`関数の名前を指定します。 関数を呼び出すには、パラメーターの値で送信します。  
  
 [!code-vb[VbVbalrLambdas&#1;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas&#2;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a>例  
 またはを宣言し、同時に、関数を実行します。  
  
 [!code-vb[VbVbalrLambdas&#3;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a>例  
 引数をインクリメントし、値を返すラムダ式の例を次に示します。 この例では、単一行および複数行のラムダ式の両方の構文、関数を示します。 例については、次を参照してください。[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)します。  
  
 [!code-vb[VbVbalrLambdas&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a>例  
 ラムダ式では、多くのクエリ演算子の基本となる[!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)]、メソッド ベースのクエリで明示的に使用できます。 次の例は、標準的な[!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)]メソッド形式に、クエリの変換後にクエリします。  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 クエリ メソッドの詳細については、次を参照してください。[クエリ](../../../visual-basic/language-reference/queries/queries.md)します。 標準クエリ演算子の詳細については、次を参照してください。[標準クエリ演算子の概要](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)します。  
  
## <a name="see-also"></a>関連項目  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)   
 [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [演算子よぶ式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)   
 [値の比較](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [ブール式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [場合演算子](../../../visual-basic/language-reference/operators/if-operator.md)   
 [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
