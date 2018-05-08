---
title: Skip 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 1810bf4a6573c6fa36f1d8149bf341d45cfd6f52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="skip-clause-visual-basic"></a>Skip 句 (Visual Basic)
コレクション内の指定された数の要素をバイパスし、残りの要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Skip count  
```  
  
## <a name="parts"></a>指定項目  
 `count`  
 必須。 スキップするシーケンスの要素の数に評価される式または値。  
  
## <a name="remarks"></a>コメント  
 `Skip`句によってクエリ結果リストの先頭の要素をバイパスし、残りの要素を返します。 スキップする要素の数がによって識別される、`count`パラメーター。  
  
 使用することができます、`Skip`句、`Take`句をクエリの任意のセグメントからのデータの範囲を返します。 これを行うには、範囲の最初の要素のインデックスを渡す、`Skip`句と範囲のサイズ、`Take`句。  
  
 使用すると、`Skip`クエリ内の句、する必要がありますも順序が有効になります結果が返されるように、`Skip`を意図した結果をバイパスする句。 クエリの結果を順序付けの詳細については、次を参照してください。 [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)です。  
  
 使用することができます、`SkipWhile`句を指定した条件に応じて特定の要素だけを無視することを指定します。  
  
## <a name="example"></a>例  
 次のコード例では、`Skip`句と共に、`Take`句をページのクエリからデータを返します。 `GetCustomers`関数は、`Skip`値、および使用して、指定した開始インデックスを作成するまで、リスト内の顧客をバイパスする句、`Take`句をインデックス値から顧客のページを返します。  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [クエリ](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take 句](../../../visual-basic/language-reference/queries/take-clause.md)
