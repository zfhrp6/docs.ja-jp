---
title: Aggregate 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 1db4b7fdcf9c8a38c2c49eca9d874eccea90ab1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604901"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate 句 (Visual Basic)
コレクションに 1 つまたは複数の集計関数を適用します。  
  
## <a name="syntax"></a>構文  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`element`|必須。 変数なコレクションの要素を反復処理するために使用します。|  
|`type`|任意。 `element` の型。 型が指定されていない場合の種類`element`から推論される`collection`です。|  
|`collection`|必須。 操作対象のコレクションを参照します。|  
|`clause`|任意。 1 つまたは複数の句がクエリなど、 `Where` aggregate 句または句を適用するクエリの結果を絞り込むの句。|  
|`expressionList`|必須。 1 つまたは複数カンマ区切りの式をコレクションに適用する集計関数を識別します。 エイリアスは、クエリ結果のメンバー名を指定する集計関数に適用できます。 別名が指定されていない場合は、集計関数の名前が使用されます。 例については、このトピックの後半の集計関数に関するセクションを参照してください。|  
  
## <a name="remarks"></a>コメント  
 `Aggregate`に集計関数をクエリに含める句を使用できます。 集計関数は、値のセットに対してチェックと計算を実行し、1 つの値を返します。 クエリ結果の型のメンバーを使用して計算値にアクセスすることができます。 使用できる標準の集計関数は、 `All`、 `Any`、 `Average`、 `Count`、 `LongCount`、 `Max`、 `Min`、および`Sum`関数。 これらの関数は、SQL での集計に慣れている開発者に習熟しています。 これらは、このトピックの次のセクションで説明します。  
  
 集計関数の結果は、クエリ結果の型のフィールドとして、クエリ結果に含まれます。 集計値を保持するクエリ結果の型のメンバーの名前を指定する集計関数の結果のエイリアスを指定することができます。 別名が指定されていない場合は、集計関数の名前が使用されます。  
  
 `Aggregate`句は、クエリを開始するかは、クエリで追加の句として追加できます。 場合、`Aggregate`句がクエリを開始すると、結果は、1 つの値で指定された集計関数の結果では、`Into`句。 1 つ以上の集計関数がで指定されている場合、`Into`句内の各集計関数の結果を参照する別のプロパティを持つ 1 つの型が返されます、`Into`句。 場合、`Aggregate`句がクエリの他の句として含まれていますが、クエリのコレクションに返される型が内の各集計関数の結果を参照する個別のプロパティ、`Into`句。  
  
## <a name="aggregate-functions"></a>集計関数  
 次のリストで使用できる標準の集計関数の説明、`Aggregate`句。  
  
|関数|説明|  
|---|---|  
|`All`|返します`true`がコレクション内のすべての要素が指定された条件を満たす場合、それ以外の場合を返します`false`です。 例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#5](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_1.vb)]|  
|`Any`|返します`true`返しますそれ以外の場合、コレクション内の要素が指定された条件を満たす場合`false`です。 例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#6](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_2.vb)]|  
|`Average`|コレクションまたはコレクション内のすべての要素に指定された計算式のすべての要素の平均を計算します。 例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#7](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_3.vb)]|  
|`Count`|コレクション内の要素の数をカウントします。 省略可能なを指定することができます`Boolean`式、条件を満たす、コレクション内の要素の数のみをカウントします。 例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#8](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_4.vb)]|  
|`Group`|結果としてグループ化されているクエリの結果を指す、`Group By`または`Group Join`句。 `Group`関数がでのみ有効では、`Into`の句、`Group By`または`Group Join`句。 詳細と例については、次を参照してください。[グループ By 句](../../../visual-basic/language-reference/queries/group-by-clause.md)と[Group Join 句](../../../visual-basic/language-reference/queries/group-join-clause.md)です。|  
|`LongCount`|コレクション内の要素の数をカウントします。 省略可能なを指定することができます`Boolean`式、条件を満たす、コレクション内の要素の数のみをカウントします。 結果として返します、`Long`です。 例については、次を参照してください。、`Count`集計関数。|  
|`Max`|をコレクションから最大値を計算またはコレクション内のすべての要素に対して指定された式を計算します。 例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#9](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_5.vb)]|  
|`Min`|をコレクションから最小値を計算またはコレクション内のすべての要素に対して指定された式を計算します。 例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#10](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_6.vb)]|  
|`Sum`|コレクション内のすべての要素の合計を計算またはコレクション内のすべての要素に対して指定された式を計算します。 例を次に示します。<br /><br /> [!code-vb[VbSimpleQuerySamples#15](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_7.vb)]|  
  
## <a name="example"></a>例  
 次のコード例を使用する方法を示しています、`Aggregate`句を集計関数、クエリ結果に適用します。  
  
 [!code-vb[VbSimpleQuerySamples#4](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_8.vb)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>ユーザー定義集計関数を作成します。  
 拡張メソッドを追加することによって、クエリ式で、独自のカスタム集計関数を含めることができます、<xref:System.Collections.Generic.IEnumerable%601>型です。 カスタム メソッドでは計算または集計関数が参照する列挙可能なコレクションの操作を実行できます。 拡張メソッドについて詳しくは、「[拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)」をご覧ください。  
  
 たとえば、次のコード例は、数値のコレクションの中央値を計算するカスタムの集計関数を示します。 2 つのオーバー ロードがあります、`Median`拡張メソッド。 最初のオーバー ロードを受け入れると、入力として型のコレクション`IEnumerable(Of Double)`です。 場合、`Median`型のクエリ フィールドの集計関数が呼び出されます`Double`、このメソッドが呼び出されます。 2 番目のオーバー ロード、`Median`任意のジェネリック型をメソッドに渡すことができます。 ジェネリック オーバー ロード、`Median`メソッドが参照する 2 番目のパラメーターを受け取り、`Func(Of T, Double)`型の対応する値として (コレクション) から型の値を射影する、ラムダ式`Double`です。 その他のオーバー ロードに中央値の計算をデリゲートして、`Median`メソッドです。 ラムダ式について詳しくは、「[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」をご覧ください。  
  
 [!code-vb[VbSimpleQuerySamples#18](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_9.vb)]  
  
 次のコード例は例のクエリを呼び出すことを示して、`Median`集計関数の種類のコレクションを`Integer`、およびコレクションの型の`Double`します。 呼び出すクエリ、`Median`集計関数の型のコレクション`Double`のオーバー ロードを呼び出して、`Median`型のコレクションを入力として受け取るメソッド`Double`です。 呼び出すクエリ、`Median`集計関数の型のコレクションに対する`Integer`のジェネリック オーバー ロードを呼び出して、`Median`メソッドです。  
  
 [!code-vb[VbSimpleQuerySamples#19](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/aggregate-clause_10.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [クエリ](../../../visual-basic/language-reference/queries/queries.md)  
 [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From 句](../../../visual-basic/language-reference/queries/from-clause.md)  
 [WHERE 句](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Group By 句](../../../visual-basic/language-reference/queries/group-by-clause.md)
