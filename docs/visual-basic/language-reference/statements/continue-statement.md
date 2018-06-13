---
title: Continue ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: eb8596c43bf6232eec4bcb844e6202c5de373404
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602724"
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
