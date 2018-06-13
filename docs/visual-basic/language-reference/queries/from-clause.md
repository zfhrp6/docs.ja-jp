---
title: From 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: 1f113444efae83de7d299db330593937c7800bb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604719"
---
# <a name="from-clause-visual-basic"></a>From 句 (Visual Basic)
1 つまたは複数の範囲変数およびコレクションのクエリを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`element`|必須。 A*範囲変数*コレクションの要素を反復処理するために使用します。 各メンバーを参照する、範囲変数が使用される、`collection`を反復処理クエリとして、`collection`です。 列挙可能な型である必要があります。|  
|`type`|任意。 `element` の型。 ない場合は`type`が指定されているの種類`element`から推論される`collection`です。|  
|`collection`|必須。 コレクションを参照するクエリを実行します。 列挙可能な型である必要があります。|  
  
## <a name="remarks"></a>コメント  
 `From`句を使用して、ソース データ クエリと、ソース コレクションから要素を参照するために使用される変数を識別します。 これらの変数といいます*範囲変数*です。 `From`句が必要な場合を除き、クエリ、`Aggregate`句を使用する集計された結果だけを返します。 クエリを識別します。 詳細については、次を参照してください。 [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)です。  
  
 複数を指定する`From`結合する複数のコレクションを識別するクエリ内の句。 複数のコレクションを指定すると、それらは別々 に反復処理、または関連している場合に参加することができます。 使用してコレクションに暗黙的に参加することができます、`Select`句、またはを使用して明示的に、`Join`または`Group Join`句。 代わりで指定できる複数の範囲変数とコレクション、1 つ`From`句は、各関連の範囲変数と、他のユーザーから、コンマで区切られたコレクションを使用します。 次のコード例は、両方の構文のオプションを示しています、`From`句。  
  
 [!code-vb[VbSimpleQuerySamples#21](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_1.vb)]  
  
 `From`句のスコープに似ていますが、クエリのスコープを定義する、`For`ループします。 したがって、各`element`クエリのスコープの範囲変数は一意の名前を持つ必要があります。 倍数を指定することができますので`From`、クエリは、後続の句`From`句できます内の範囲変数を参照してください、`From`以前、句、またはこれらの範囲変数を参照してできます`From`句。 たとえば、次の例、入れ子になった`From`2 番目の句内のコレクションは、最初の句の範囲変数のプロパティをに基づいて句。  
  
 [!code-vb[VbSimpleQuerySamples#22](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_2.vb)]  
  
 各`From`句の後に、クエリを絞り込む追加のクエリ句の任意の組み合わせをできます。 次の方法でクエリを絞り込むことができます。  
  
-   使用して暗黙的に複数のコレクションを組み合わせて、`From`と`Select`句、またはを使用して明示的に、`Join`または`Group Join`句。  
  
-   使用して、`Where`句をクエリの結果をフィルター処理します。  
  
-   使用して、結果を並べ替える、`Order By`句。  
  
-   使用して同様の結果をグループ化、`Group By`句。  
  
-   使用して、`Aggregate`句全体のクエリの結果を評価する集計関数を識別します。  
  
-   使用して、`Let`句を反復変数の値は、コレクションではなく式によって決定されます。  
  
-   使用して、`Distinct`重複するクエリの結果を無視する句。  
  
-   使用して返される結果の部分を特定、 `Skip`、 `Take`、 `Skip While`、および`Take While`句。  
  
## <a name="example"></a>例  
 次のクエリ式は、`From`範囲変数を宣言する句`cust`各`Customer`内のオブジェクト、`customers`コレクション。 `Where`句では、範囲変数を使用して、顧客に指定した領域から出力を制限します。 `For Each`ループでは、クエリ結果の各顧客の会社名が表示されます。  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/from-clause_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 [クエリ](../../../visual-basic/language-reference/queries/queries.md)  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [WHERE 句](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Distinct 句](../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [Join 句](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Group Join 句](../../../visual-basic/language-reference/queries/group-join-clause.md)  
 [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Let 句](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Skip 句](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Take 句](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take While 句](../../../visual-basic/language-reference/queries/take-while-clause.md)
