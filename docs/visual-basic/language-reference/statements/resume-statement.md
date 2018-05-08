---
title: Resume ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: 1d03f631893be51529f29af824de0d684bf43804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="resume-statement"></a>Resume ステートメント
エラー処理ルーチンが終了した後は、実行を再開します。  
  
 非構造化例外処理を使用するのではなく、可能な限り、コードに構造化例外処理を使用することをお勧めおよび`On Error`と`Resume`ステートメントです。 詳しくは、「[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」をご覧ください。  
  
## <a name="syntax"></a>構文  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>指定項目  
 `Resume`  
 必須。 エラー ハンドラーと同じ手順でエラーが発生した場合、エラーの原因となったステートメントを使用して実行が再開されます。 呼び出されたプロシージャでエラーが発生した場合は、最後に、エラー処理ルーチンを含むプロシージャから呼び出されたステートメントの実行が再開されます。  
  
 `Next`  
 任意。 エラー ハンドラーと同じ手順でエラーが発生した場合、エラーが発生したステートメントの直後のステートメントの実行が再開されます。 呼び出されたプロシージャでエラーが発生した、最後に、エラー処理ルーチンを含むプロシージャから呼び出されたステートメントの直後のステートメントを使用して、実行が再開されます (または`On Error Resume Next`ステートメント)。  
  
 `line`  
 任意。 要求で指定した行で実行が再開される`line`引数。 `line`引数を行ラベルまたは行番号、エラー ハンドラーと同じ手順である必要があります。  
  
## <a name="remarks"></a>コメント  
  
> [!NOTE]
>  非構造化例外処理を使用するのではなく、可能な限り、コードに構造化例外処理を使用することをお勧めおよび`On Error`と`Resume`ステートメントです。 詳しくは、「[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」をご覧ください。  
  
 使用する場合、`Resume`ステートメント任意の場所以外のエラー処理ルーチンで、エラーが発生します。  
  
 `Resume`いずれかのプロシージャを含むステートメントは使用できません、`Try...Catch...Finally`ステートメントです。  
  
## <a name="example"></a>例  
 この例では、`Resume`ステートメントをプロシージャのエラー処理を終了してエラーが発生したステートメントの実行を再開します。 使用方法を説明するエラー番号 55 が生成された、`Resume`ステートメントです。  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a>要件  
 **Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **アセンブリ:** Visual Basic Runtime Library (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目  
 [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Error ステートメント](../../../visual-basic/language-reference/statements/error-statement.md)  
 [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)
