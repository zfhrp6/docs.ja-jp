---
title: Throw ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: cfa53b3585846da25711739fb7af4bde21746b29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602854"
---
# <a name="throw-statement-visual-basic"></a>Throw ステートメント (Visual Basic)
プロシージャ内で例外をスローします。  
  
## <a name="syntax"></a>構文  
  
```  
Throw [ expression ]  
```  
  
## <a name="part"></a>パーツ  
 `expression`  
 スローする例外に関する情報を提供します。 内に存在する場合はオプション、`Catch`ステートメントでは、それ以外の場合に必要です。  
  
## <a name="remarks"></a>コメント  
 `Throw`構造化例外処理コードで処理できる例外をスローするステートメント (`Try`.`Catch`...`Finally`) または非構造化例外処理コード (`On Error GoTo`)。 使用することができます、 `Throw` Visual Basic は、適切な例外処理コードが見つかるまで、呼び出し履歴を移動するために、コード内でエラーをトラップするステートメント。  
  
 A`Throw`式を指定しないステートメントでのみ使用できます、`Catch`ステートメントでは、case ステートメントが現在処理中の例外を再スロー、`Catch`ステートメントです。  
  
 `Throw`ステートメントの呼び出し履歴をリセットする、`expression`例外。 場合`expression`が指定されていない、呼び出し履歴は変更されません。 例外の呼び出し履歴を表示する、<xref:System.Exception.StackTrace%2A>プロパティです。  
  
## <a name="example"></a>例  
 次のコードでは、`Throw`例外をスローするステートメント。  
  
 [!code-vb[VbVbalrStatements#84](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/throw-statement_1.vb)]  
  
## <a name="requirements"></a>要件  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **モジュール:** `Interaction`  
  
 **アセンブリ:** Visual Basic Runtime Library (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目  
 [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)
