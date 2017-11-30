---
title: "Continue ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a47819600a6c1d58f09c2f8ed3443632e9dab68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="continue-statement-visual-basic"></a>Continue ステートメント (Visual Basic)
ループの次のイテレーションにすぐに制御を転送します。  
  
## <a name="syntax"></a>構文  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>コメント  
 転送できます内、 `Do`、 `For`、または`While`ループを使用して、ループの次の反復処理します。 すぐに転送するのにはループの条件のテストにパスを制御、`For`または`While`ステートメント、または、`Do`または`Loop`ステートメントを含む、`Until`または`While`句。  
  
 使用することができます`Continue`転送を許可するループ内の任意の場所でします。 同じで、制御の転送を許可する規則は、 [GoTo ステートメント](../../../visual-basic/language-reference/statements/goto-statement.md)です。  
  
 たとえば、ループ処理が完全に含まれている場合、`Try`ブロック、`Catch`ブロック、または`Finally`ブロック、使用することができます`Continue`ループの外に転送します。 その一方の場合、`Try`しています.`End Try` 、ループ内に含まれる構造体では使用できません`Continue`out の制御を転送する、`Finally`ブロックして、転送に使用できるの`Try`または`Catch`ブロックするを完全に転送する場合にのみ、`Try`...`End Try`構造体。  
  
 たとえば、同じ型での入れ子になったループがあるかどうか、`Do`別内でループ`Do`ループ、`Continue Do`ステートメントでは、最も内側の次のイテレーションへスキップ`Do`それを含むループ。 使用することはできません`Continue`同じ種類の外側のループの次のイテレーションにスキップします。  
  
 たとえば、さまざまな種類の入れ子になったループがあるかどうか、`Do`内でループ、`For`ループにスキップできますいずれかのループの次のイテレーションを使用して`Continue Do`または`Continue For`です。  
  
## <a name="example"></a>例  
 次のコード例では、`Continue While`除数がゼロの場合は、配列の次の列をスキップするステートメント。 `Continue While`内部にある、`For`ループします。 転送します。、`While col < lastcol`ステートメントでは、最も内側の次のイテレーションである`While`ループを含む、`For`ループします。  
  
 [!code-vb[VbVbalrStatements#14](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/continue-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
