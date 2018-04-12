---
title: Skip While 句 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f447a6d9b2eb58fa546ced6c96b987caf68fb3e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="skip-while-clause-visual-basic"></a>Skip While 句 (Visual Basic)
指定された条件が `true` である限り、コレクションの要素をバイパスし、残りの要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`expression`|必須です。 要素をテストするための条件を表す式。 式を返す必要があります、`Boolean`値またはそれと同等の機能など、`Integer`として評価される、`Boolean`です。|  
  
## <a name="remarks"></a>コメント  
 `Skip While`句が指定されたまで、クエリ結果の先頭から要素をバイパス`expression`返します`false`です。 後に`expression`返します`false`クエリが、残りのすべての要素を返します。 `expression`残りの結果は無視されます。  
  
 `Skip While`句とは異なります、`Where`を内の句、`Where`を特定の条件を満たさないクエリからすべての要素を除外する句を使用できます。 `Skip While`句は、条件が満たされていない最初の時刻までの要素を除外します。 `Skip While`句は、順序付けられたクエリ結果を使用しているときに最も役立ちます。  
  
 使用して特定のクエリ結果の先頭からの結果数を省略することができます、`Skip`句。  
  
## <a name="example"></a>例  
 次のコード例では、`Skip While`米国から最初の顧客が見つかるまで、結果をバイパスする句。  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [クエリ](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Skip 句](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take While 句](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [WHERE 句](../../../visual-basic/language-reference/queries/where-clause.md)
