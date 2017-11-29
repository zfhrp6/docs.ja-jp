---
title: "方法: 値を返すプロシージャを作成する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 787eddc1fd1cdb9dd6b655a8556b75044b2a49dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>方法: 値を返すプロシージャを作成する (Visual Basic)
使用する、`Function`呼び出しコードに値を返すプロシージャです。  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>値を返すプロシージャを作成するのには  
  
1.  その他のすべてのプロシージャの外側を使用して、`Function`ステートメントの後に、`End Function`ステートメントです。  
  
2.  `Function`ステートメントでは、以下の`Function`キーワード、プロシージャとし、かっこで囲まれたパラメーター リストの名前に置き換えます。  
  
3.  かっこの後に、`As`句を戻り値のデータ型を指定します。  
  
4.  間に、プロシージャのコード ステートメントを配置、`Function`と`End Function`ステートメントです。  
  
5.  使用して、`Return`ステートメントを呼び出し元のコードに値を返します。  
  
     次`Function`最長側では、やの他の 2 つの辺の値を指定、直角三角形の斜辺を計算します。  
  
     [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_1.vb)]  
  
     次の例では、一般的な呼び出しを`hypotenuse`です。  
  
     [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/how-to-create-a-procedure-that-returns-a-value_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Sub プロシージャ](./sub-procedures.md)  
 [Property プロシージャ](./property-procedures.md)  
 [演算子プロシージャ](./operator-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [方法 : プロシージャから値を返す](./how-to-return-a-value-from-a-procedure.md)  
 [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)
