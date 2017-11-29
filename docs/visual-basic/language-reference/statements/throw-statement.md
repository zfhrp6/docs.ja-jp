---
title: "Throw ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Throw
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 50ada551c32b8296f0dad2ae929ca9c81a14a711
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
  
 **モジュール:**`Interaction`  
  
 **アセンブリ:** Visual Basic Runtime Library (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目  
 [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)
