---
title: "Where 句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8c2572f513d00bc72e869cf28d382be799f7a303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="where-clause-visual-basic"></a>Where 句 (Visual Basic)
クエリのフィルター処理条件を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
Where condition  
```  
  
## <a name="parts"></a>指定項目  
 `condition`  
 必須です。 コレクションの現在のアイテムの値を出力コレクションに含めるかどうかを決定する式。 式を評価する、`Boolean`値またはのそれと同等、`Boolean`値。 条件の評価が場合`True`要素は、それ以外のクエリの結果に含まれている、要素が、クエリ結果から除外します。  
  
## <a name="remarks"></a>コメント  
 `Where`句では、特定の条件を満たす要素のみを選択してクエリのデータをフィルター処理することができます。 要素の値を持つが発生する、`Where`句を評価する`True`クエリの結果に含まれるその他の要素が除外されます。 式で使用されている、`Where`に句を評価する必要があります、`Boolean`またはのそれと同等、`Boolean`に評価される整数など`False`その値が 0 の場合。 複数の式を組み合わせることができます、`Where`句などの論理演算子を使用して、 `And`、 `Or`、 `AndAlso`、 `OrElse`、 `Is`、および`IsNot`です。  
  
 既定では、クエリ式は評価されませんがアクセスしない — たとえば、ときにデータ バインドまたはで反復されたり、`For`ループします。 その結果、`Where`句は、クエリがアクセスされるまでは評価されません。 外部で使用されるクエリに値があるかどうか、`Where`句で、適切な値が使用されるように、`Where`句、クエリの実行時にします。 クエリの実行の詳細については、次を参照してください。[書き込み、最初の LINQ クエリの](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)します。  
  
 内で関数を呼び出すことができます、`Where`句をコレクション内の現在の要素から計算または値に対して操作を実行します。 関数を呼び出して、`Where`句には、それが定義されている場合の代わりにアクセスしたときの直前に実行するクエリ可能性があります。 クエリの実行の詳細については、次を参照してください。[書き込み、最初の LINQ クエリの](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)します。  
  
## <a name="example"></a>例  
 次のクエリ式は、`From`範囲変数を宣言する句`cust`各`Customer`内のオブジェクト、`customers`コレクション。 `Where`句では、範囲変数を使用して、顧客に指定した領域から出力を制限します。 `For Each`ループでは、クエリ結果の各顧客の会社名が表示されます。  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a>例  
 次の例で`And`と`Or`論理演算子で、`Where`句。  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [クエリ](../../../visual-basic/language-reference/queries/queries.md)  
 [From 句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
