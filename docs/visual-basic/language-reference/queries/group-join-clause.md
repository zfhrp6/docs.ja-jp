---
title: "Group Join 句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c43b41336393b40684aee79f88c1e6999ebda674
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="group-join-clause-visual-basic"></a>Group Join 句 (Visual Basic)
2 つのコレクションを、単一の階層コレクションに結合します。 結合操作は、一致するキーに基づいています。  
  
## <a name="syntax"></a>構文  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`element`|必須です。 結合するコレクションの制御変数にします。|  
|`type`|省略可能です。 `element` の型。 ない場合は`type`が指定されているの種類`element`から推論される`collection`です。|  
|`collection`|必須です。 左側にあるコレクションと結合するコレクション、`Group Join`演算子。 A`Group Join`句で入れ子にでき、`Join`句または別の`Group Join`句。|  
|`key1``Equals``key2`|必ず指定します。 結合するコレクションのキーを識別します。 使用する必要があります、`Equals`演算子を結合するコレクションからキーを比較します。 使用して結合条件を組み合わせることができます、`And`演算子を複数のキーを識別します。 `key1`の左側にあるコレクションからパラメーターがある必要があります、`Join`演算子。 `key2`の右側にあるコレクションからパラメーターがある必要があります、`Join`演算子。<br /><br /> 結合条件で使用されるキーには、コレクションの 1 つ以上の項目を含む式を指定できます。 ただし、それぞれのキー式は、該当するコレクションの項目のみを含めることができます。|  
|`expressionList`|必須です。 コレクションから要素のグループの集計方法を識別する 1 つまたは複数の式。 グループ化した結果のメンバー名を指定するのには、使用、`Group`キーワード (`<alias> = Group`)。 グループに適用する集計関数を含めることもできます。|  
  
## <a name="remarks"></a>コメント  
 `Group Join`句が一致する結合するコレクションからキー値に基づいて 2 つのコレクションを結合します。 結果のコレクションには、最初のコレクションからキーの値に一致する 2 番目のコレクションから要素のコレクションを参照するメンバーを含めることができます。 第 2 のコレクションをグループ化された要素に適用する集計関数を指定することもできます。 集計関数については、次を参照してください。 [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)です。  
  
 たとえば、マネージャーのコレクションと従業員のコレクションに検討してください。 両方のコレクションからの要素では、特定の管理者に報告する従業員を識別する ManagerID プロパティがあります。 結合操作の結果には、各マネージャーと従業員 ManagerID 値が一致する結果が含まれます。 結果を`Group Join`操作には、管理者の完全な一覧にが含まれます。 各管理者の結果が必要で、特定のマネージャーと一致する従業員の一覧を参照するメンバーがあります。  
  
 コレクションから結果として得られる、`Group Join`操作で識別されるコレクションの値の任意の組み合わせを含めることができます、`From`句と、式で識別される、`Into`の句、`Group Join`句。 有効な式の詳細については、`Into`句を参照してください[Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)です。  
  
 A`Group Join`操作ではすべての結果を返しますの左側で指定したコレクションから、`Group Join`演算子。 これは、結合対象のコレクションに一致がない場合でも当てはまります。 これはのように、 `LEFT OUTER JOIN` SQL でします。  
  
 使用することができます、`Join`句を 1 つのコレクションをコレクションに結合します。 これに相当する`INNER JOIN`SQL にします。  
  
## <a name="example"></a>例  
 次のコード例では、2 つのコレクションを結合を使用して、`Group Join`句。  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [クエリ](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Join 句](../../../visual-basic/language-reference/queries/join-clause.md)  
 [WHERE 句](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Group By 句](../../../visual-basic/language-reference/queries/group-by-clause.md)
