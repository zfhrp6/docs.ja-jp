---
title: '方法: プロシージャから値を返す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 62e8a52e488247d4dfcde2a560920447abe1c182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651835"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>方法: プロシージャから値を返す (Visual Basic)
A`Function`プロシージャに値を返す呼び出し元のコードを実行するか、`Return`ステートメントまたはを戻したり、`Exit Function`または`End Function`ステートメントです。  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Return ステートメントを使用して値を返す  
  
1.  Put、`Return`プロシージャのタスクが完了した時点でのステートメント。  
  
2.  以下の`Return`呼び出し元のコードを取得するキーワード、値を生成する式でします。  
  
3.  同じプロシージャ内に複数の `Return` ステートメントを含めることができます。  
  
     次`Function`プロシージャが長い側またはの三角形の斜辺を計算し、呼び出し元のコードを返します。  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     次の例では、一般的な呼び出しを`hypotenuse`、返された値を格納します。  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Exit 関数または終了関数を使用して値を返す  
  
1.  内の少なくとも 1 つの場所で、`Function`プロシージャ、値、プロシージャの名前を割り当てます。  
  
2.  実行すると、`Exit Function`または`End Function`ステートメントでは、Visual Basic は、プロシージャの名前を最も最近割り当てられた値を返します。  
  
3.  同じプロシージャ内に複数の `Exit Function` ステートメントを含めることができ、さらに同じプロシージャ内に `Return` ステートメントと `Exit Function` ステートメントを混在させることができます。  
  
4.  1 つだけ持つことができます`End Function`内のステートメント、`Function`プロシージャです。  
  
     詳細と例を参照してください「戻り値」[関数ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)です。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Sub プロシージャ](./sub-procedures.md)  
 [Property プロシージャ](./property-procedures.md)  
 [演算子プロシージャ](./operator-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [Return ステートメント](../../../../visual-basic/language-reference/statements/return-statement.md)  
 [方法 : 値を返すプロシージャを作成する](./how-to-create-a-procedure-that-returns-a-value.md)  
 [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)
