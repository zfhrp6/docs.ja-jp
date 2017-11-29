---
title: Widening (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 034099397c1d296a42712b8c202e2ac99a0fb43b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
示します変換演算子 (`CType`) クラスまたは構造体を元のクラスまたは構造体のすべての可能な値を保持できる型に変換します。  
  
## <a name="converting-with-the-widening-keyword"></a>拡大のキーワードを使用して変換します。  
 変換のプロシージャを指定する必要があります`Public Shared`に加えて`Widening`です。  
  
 拡大変換は実行時に常に成功して、データの損失が発生することはありません。 例としては、`Single`に`Double`、`Char`に`String`、およびその基本型を派生型です。 この最後の変換は、派生型は、基本型のすべてのメンバーが含まれており、したがって、基本データ型のインスタンスに拡大変換がします。  
  
 コンシューマー コードが使用する必要はありません`CType`拡大変換、たとえ`Option Strict`は`On`します。  
  
 `Widening`キーワードは、このコンテキストで使用できます。  
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 たとえば拡大変換と縮小変換演算子の定義を参照してください[する方法: 変換演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [方法 : 演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [方法 : 変換演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
