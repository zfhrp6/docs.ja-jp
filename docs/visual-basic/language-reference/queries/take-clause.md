---
title: "Take 句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ee289a24c15226126a526af116ed53b4a9055b35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="take-clause-visual-basic"></a>Take 句 (Visual Basic)
コレクションの先頭から、指定された数の連続する要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Take count  
```  
  
## <a name="parts"></a>指定項目  
 `count`  
 必須です。 返すシーケンスの要素の数に評価される式または値。  
  
## <a name="remarks"></a>コメント  
 `Take`句により、クエリに指定された数の結果一覧の先頭からの連続する要素を含めます。 含まれる要素の数がで指定された、`count`パラメーター。  
  
 使用することができます、`Take`句、`Skip`句をクエリの任意のセグメントからのデータの範囲を返します。 これを行うには、範囲の最初の要素のインデックスを渡す、`Skip`句と範囲のサイズ、`Take`句。 ここで、`Take`後句を指定する必要があります、`Skip`句。  
  
 使用すると、`Take`クエリ内の句、する必要がありますも順序が有効になります結果が返されるように、`Take`に目的の結果を含める句。 クエリの結果を順序付けの詳細については、次を参照してください。 [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)です。  
  
 使用することができます、`TakeWhile`句を指定した条件に応じて特定の要素だけを返すことを指定します。  
  
## <a name="example"></a>例  
 次のコード例では、`Take`句と共に、`Skip`句をページのクエリからデータを返します。 GetCustomers 関数は、`Skip`値、および使用して、指定した開始インデックスを作成するまで、リスト内の顧客をバイパスする句、`Take`句をインデックス値から顧客のページを返します。  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [クエリ](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Take While 句](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Skip 句](../../../visual-basic/language-reference/queries/skip-clause.md)
