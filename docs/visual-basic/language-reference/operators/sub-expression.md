---
title: "部分式 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 43e35bd0386bc56478603ec36437981785cc8ffb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sub-expression-visual-basic"></a>部分式 (Visual Basic)
パラメーターとサブルーチン ラムダ式を定義するコードを宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`parameterlist`|省略可能です。 プロシージャのパラメーターを表すローカル変数名の一覧。 かっこは、リストが空の場合にも存在する必要があります。 詳細については、次を参照してください。[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)です。|  
|`statement`|必須です。 1 つのステートメント。|  
|`statements`|必須です。 ステートメントの一覧。|  
  
## <a name="remarks"></a>コメント  
 A*ラムダ式*名前がないサブルーチンは、1 つまたは複数のステートメントを実行します。 任意の場所、ラムダ式を使用することができますを使える、デリゲート型以外に引数として`RemoveHandler`です。 デリゲート、およびデリゲートでのラムダ式の使用に関する詳細については、次を参照してください。 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)と[厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)です。  
  
## <a name="lambda-expression-syntax"></a>ラムダ式の構文  
 標準のサブルーチンのラムダ式の構文に似ています。 相違点は次のとおりです。  
  
-   ラムダ式には、名前がありません。  
  
-   ラムダ式はなどの修飾子を持つことはできません`Overloads`または`Overrides`です。  
  
-   単一行のラムダ式の本体は、ステートメント、式ではないをする必要があります。 本文は、sub プロシージャへの呼び出しがない、プロシージャの呼び出しを関数で構成できます。  
  
-   ラムダ式では、すべてのパラメーターまたはデータ型を推論する必要がありますすべてパラメーターのどちらかを指定した必要があります。  
  
-   省略可能なと`ParamArray`パラメーターはラムダ式で許可されていません。  
  
-   ジェネリック パラメーターは、ラムダ式では使用できません。  
  
## <a name="example"></a>例  
 値をコンソールに出力するラムダ式の例を次に示します。 この例では、単一行および複数行ラムダ式の両方の構文のサブルーチンを示します。 例については、次を参照してください。[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)です。  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)  
 [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
