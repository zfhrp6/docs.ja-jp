---
title: Take While 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 7e0a6bd77ca2594e9d74e669fcd9cddf91ee1cad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600911"
---
# <a name="take-while-clause-visual-basic"></a>Take While 句 (Visual Basic)
指定された条件が `true` である限り、コレクションの要素を含むようにし、残りの要素をバイパスします。  
  
## <a name="syntax"></a>構文  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`expression`|必須。 要素をテストするための条件を表す式。 式を返す必要があります、`Boolean`値またはそれと同等の機能など、`Integer`として評価される、`Boolean`です。|  
  
## <a name="remarks"></a>コメント  
 `Take While`句には、まで、指定されたクエリの結果の先頭から要素が含まれる`expression`返します`false`です。 後に、`expression`返します`false`クエリの残りのすべての要素をバイパスします。 `expression`残りの結果は無視されます。  
  
 `Take While`句とは異なります、`Where`を内の句、`Where`クエリから特定の条件を満たすすべての要素を含める句を使用できます。 `Take While`句には、条件が満たされていない最初の時刻までの要素が含まれています。 `Take While`句は、順序付けられたクエリ結果を使用しているときに最も役立ちます。  
  
## <a name="example"></a>例  
 次のコード例では、`Take While`句を任意の注文数が、最初の顧客が見つかるまで、結果を取得します。  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [クエリ](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Take 句](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [WHERE 句](../../../visual-basic/language-reference/queries/where-clause.md)
