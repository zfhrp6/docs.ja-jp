---
title: "方法: 変換演算子を定義する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0f9e63ba039a48226186fa4ce118d3e47b5673e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>方法: 変換演算子を定義する (Visual Basic)
クラスまたは構造体を定義している場合は、クラスまたは構造体の型と別のデータ型の型変換演算子を定義することができます (など`Integer`、 `Double`、または`String`)。  
  
 として型の変換を定義、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)クラスまたは構造内のプロシージャです。 変換のすべてのプロシージャである必要があります`Public Shared`、どちらか 1 つを指定する必要がありますと[Widening](../../../../visual-basic/language-reference/modifiers/widening.md)または[Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)です。  
  
 クラスまたは構造体で演算子を定義とも呼びます*オーバー ロード*演算子。  
  
## <a name="example"></a>例  
 次の例と呼ばれる構造との間の変換演算子を定義する`digit`と`Byte`です。  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 構造体をテストする`digit`を次のコード。  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [演算子プロシージャ](./operator-procedures.md)  
 [方法 : 演算子を定義する](./how-to-define-an-operator.md)  
 [方法 : 演算子プロシージャを呼び出す](./how-to-call-an-operator-procedure.md)  
 [方法: 演算子を定義するクラスを使用する](./how-to-use-a-class-that-defines-operators.md)  
 [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [方法 : 構造体を宣言する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
