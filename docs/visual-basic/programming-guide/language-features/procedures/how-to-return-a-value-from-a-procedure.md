---
title: "方法: プロシージャ (Visual Basic の場合) から値を返す |Microsoft ドキュメント"
ms.custom: 
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
- Visual Basic code, procedures
- procedures, returning from
- procedures, returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
caps.latest.revision: 12
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
ms.openlocfilehash: 98f0fb0740a021a16e87454bfaebbfad7858477c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>方法: プロシージャから値を返す (Visual Basic)
A`Function`プロシージャに値を返す、呼び出し元コードを実行していずれか、`Return`ステートメントまたはを戻したり、`Exit Function`または`End Function`ステートメントです。  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Return ステートメントを使用して値を返す  
  
1.  Put、`Return`ステートメント、プロシージャのタスクが完了した時点です。  
  
2.  次の`Return`呼び出し元のコードに戻したいキーワードの値を生成する式を使用します。  
  
3.  1 つ以上が持てる`Return`同じプロシージャ内のステートメントです。  
  
     次`Function`プロシージャと最も長い辺または直角三角形の斜辺を計算し、呼び出し元のコードを返します。  
  
     [!code-vb[VbVbcnProcedures&#1;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_1.vb)]  
  
     次の例では、一般的な呼び出しを`hypotenuse`、返される値を格納します。  
  
     [!code-vb[VbVbcnProcedures&6;](./codesnippet/VisualBasic/how-to-return-a-value-from-a-procedure_2.vb)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Exit 関数または終了関数を使用して値を返す  
  
1.  内の少なくとも&1; つの場所で、`Function`プロシージャ、プロシージャの名前に値を代入します。  
  
2.  実行すると、`Exit Function`または`End Function`ステートメント、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロシージャの名前に最も最近割り当てられた値を返します。  
  
3.  1 つ以上を持つことができます`Exit Function`して、同じプロシージャ内のステートメントを混在させること`Return`と`Exit Function`同じプロシージャ内のステートメントです。  
  
4.  1 つだけ持つことができます`End Function`内のステートメントで、`Function`プロシージャです。  
  
     詳細と例を参照してください「戻り値」 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)します。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [Sub プロシージャ](./sub-procedures.md)   
 [プロパティ プロシージャ](./property-procedures.md)   
 [演算子プロシージャ](./operator-procedures.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)   
 [Return ステートメント](../../../../visual-basic/language-reference/statements/return-statement.md)   
 [方法: 値を返すプロシージャを作成します。](./how-to-create-a-procedure-that-returns-a-value.md)   
 [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)
