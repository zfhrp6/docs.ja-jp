---
title: "Return ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b66d16a249164b8989f05f10c785b97055bfde9e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="return-statement-visual-basic"></a>Return ステートメント (Visual Basic)
呼び出したコードに制御を返す、 `Function`、 `Sub`、 `Get`、 `Set`、または`Operator`プロシージャです。  
  
## <a name="syntax"></a>構文  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>パーツ  
 `expression`  
 必要な`Function`、 `Get`、または`Operator`プロシージャです。 呼び出し元のコードに返される値を表す式です。  
  
## <a name="remarks"></a>コメント  
 `Sub`または`Set`プロシージャ、`Return`ステートメントは等価、`Exit Sub`または`Exit Property`ステートメント、および`expression`を指定しないでください。  
  
 `Function`、 `Get`、または`Operator`プロシージャ、`Return`ステートメントを含める必要があります`expression`、および`expression`プロシージャの戻り値の型に変換できるデータ型に評価される必要があります。 `Function`または`Get`プロシージャもがある場合、戻り値として機能するように、プロシージャ名に式を割り当てると、実行しても、`Exit Function`または`Exit Property`ステートメントです。 `Operator`使用する必要がありますプロシージャ、`Return``expression`です。  
  
 多くとして含めることができます`Return`同じプロシージャ内に適切なステートメントです。  
  
> [!NOTE]
>  内のコード、`Finally`ブロックが実行した後、`Return`内のステートメント、`Try`または`Catch`ブロックが発生した場合は、その前に`Return`ステートメントを実行します。 A`Return`にステートメントを含めることはできません、`Finally`ブロックします。  
  
## <a name="example"></a>例  
 次の例では、`Return`ステートメント、プロシージャが何を持っていない場合に、呼び出し元のコードに戻るに複数回です。  
  
 [!code-vb[VbVbalrStatements#53](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/return-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
