---
title: "Join 句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2bb25c9dac8994e7f975539c1d036f0f0d9d239e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="join-clause-visual-basic"></a>Join 句 (Visual Basic)
2 つのコレクションを単一のコレクションに結合します。 結合操作を一致するキーに基づいて、使用、`Equals`演算子。  
  
## <a name="syntax"></a>構文  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a>指定項目  
 `element`  
 必須です。 結合するコレクションの制御変数にします。  
  
 `collection`  
 必須です。 左側にあるで識別されるコレクションと結合するコレクション、`Join`演算子。 A`Join`句は、別の入れ子にすることができます`Join`句、または、`Group Join`句。  
  
 `joinClause`  
 省略可能です。 1 つ以上の追加`Join`をさらに句がクエリを変更します。  
  
 `groupJoinClause`  
 省略可能です。 1 つ以上の追加`Group Join`をさらに句がクエリを変更します。  
  
 `key1``Equals``key2`  
 必ず指定します。 結合するコレクションのキーを識別します。 使用する必要があります、`Equals`演算子を結合するコレクションからキーを比較します。 使用して結合条件を組み合わせることができます、`And`演算子を複数のキーを識別します。 `key1`左側にあるコレクションからある必要があります、`Join`演算子。 `key2`右側にあるコレクションからある必要があります、`Join`演算子。  
  
 結合条件で使用されるキーには、コレクションの 1 つ以上の項目を含む式を指定できます。 ただし、それぞれのキー式は、該当するコレクションの項目のみを含めることができます。  
  
## <a name="remarks"></a>コメント  
 `Join`句が一致する結合するコレクションからキー値に基づいて 2 つのコレクションを結合します。 結果のコレクションの左側にあるで識別されるコレクションの値の任意の組み合わせを含めることができます、`Join`演算子およびで識別されるコレクション、`Join`句。 によって指定された条件の結果のみが返されます、`Equals`演算子が満たされています。 これに相当する`INNER JOIN`SQL にします。  
  
 複数回使用することができます`Join`を単一のコレクションに 2 つまたは複数のコレクションを結合するクエリ内の句。  
  
 なしのコレクションを結合する暗黙の結合を行うことができます、`Join`句。 これを行うには、複数を含める`In`内の句、`From`句を指定し、`Where`結合に使用するキーを識別する句。  
  
 使用することができます、`Group Join`句を単一の階層コレクションに結合します。 これはのように、 `LEFT OUTER JOIN` SQL でします。  
  
## <a name="example"></a>例  
 次のコード例では、その注文と顧客のリストを結合する暗黙の結合を実行します。  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_1.vb)]  
  
## <a name="example"></a>例  
 次のコード例では、2 つのコレクションを結合を使用して、`Join`句。  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_2.vb)]  
  
 この例では、次のような出力を得られます。  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a>例  
 次のコード例では、2 つのコレクションを結合を使用して、 `Join` 2 つのキー列を含む句。  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/join-clause_3.vb)]  
  
 例では、次のような出力が生成されます。  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [クエリ](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Group Join 句](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [WHERE 句](../../../visual-basic/language-reference/queries/where-clause.md)
