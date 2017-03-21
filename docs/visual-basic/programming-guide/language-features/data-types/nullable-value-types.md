---
title: "Null 許容値型 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Nullable
dev_langs:
- VB
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: 23
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9cdf1864fe955a082936596821ee84c831b86444
ms.lasthandoff: 03/13/2017

---
# <a name="nullable-value-types-visual-basic"></a>null 許容値型 (Visual Basic)
特定の状況で 定義済みの値がない値型を操作することがあります。 たとえば、データベース内のフィールドは、意味のある割り当てられた値を持つと、割り当てられた値がないとを区別する必要があります。 値型は、通常の値または null 値のいずれかを拡張できます。 このような拡張機能と呼ばれる、 *null 許容型*します。  
  
 各 null 許容型がジェネリックから構築された<xref:System.Nullable%601>構造体</xref:System.Nullable%601>。 仕事に関連するアクティビティを追跡するデータベースを検討してください。 次の例は、null 許容型を構築`Boolean`を入力し、その型の変数を宣言します。 次の&3; つの方法では、宣言を記述できます。  
  
 [!code-vb[VbVbalrNullableValue&#1;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]  
  
 変数`ridesBusToWork`の値を保持できる`True`の値`False`、またはすべてに値がありません。 初期の既定値値はありません、ここで可能性があることについては、いないまだに対して取得されたこの人。 これに対し、`False`情報を取得、ユーザーが仕事のバスをオーバーライドしていないことを示します。  
  
 変数とプロパティを宣言するには null 許容型と null 許容型の要素を持つ配列を宣言することができます。 プロシージャを宣言するには、パラメーターとして null 許容型およびから null 許容型を返すことができます、`Function`プロシージャです。  
  
 配列などの参照型で null 許容型を構築することはできません、 `String`、またはクラスです。 基になる型は、値型である必要があります。 詳細については、次を参照してください。[値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)します。  
  
## <a name="using-a-nullable-type-variable"></a>Null 許容型の変数を使用します。  
 Null 許容型の最も重要なメンバーは、その<xref:System.Nullable%601.HasValue%2A>と<xref:System.Nullable%601.Value%2A>プロパティ</xref:System.Nullable%601.Value%2A></xref:System.Nullable%601.HasValue%2A>。 Null 許容型の変数の<xref:System.Nullable%601.HasValue%2A>変数が定義済みの値を含むかどうかがわかります</xref:System.Nullable%601.HasValue%2A>。 場合<xref:System.Nullable%601.HasValue%2A>は`True`、 <xref:System.Nullable%601.Value%2A>.</xref:System.Nullable%601.Value%2A>から値を読み取ることができます</xref:System.Nullable%601.HasValue%2A> 両方<xref:System.Nullable%601.HasValue%2A>と<xref:System.Nullable%601.Value%2A>は`ReadOnly`プロパティ</xref:System.Nullable%601.Value%2A></xref:System.Nullable%601.HasValue%2A>。  
  
### <a name="default-values"></a>既定値  
 Null 許容型を持つ変数を宣言するときにその<xref:System.Nullable%601.HasValue%2A>プロパティには、既定値は`False`</xref:System.Nullable%601.HasValue%2A>。 つまり、既定では、変数がない、基になる値型の既定値ではなく、定義済みの値。 次の例では、変数`numberOfChildren`最初に値を持たない値が定義されても、既定の`Integer`型は 0 です。  
  
 [!code-vb[VbVbalrNullableValue&#2;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]  
  
 Null 値は、未定義または未知の値を指定すると便利です。 場合`numberOfChildren`として宣言されていた`Integer`がなくなることは、情報が現在使用できないことを示す値。  
  
### <a name="storing-values"></a>値を格納します。  
 一般的な方法で変数または null 許容型のプロパティ値を格納します。 次の例では、その値を変数に代入`numberOfChildren`前の例で宣言します。  
  
 [!code-vb[VbVbalrNullableValue&#3;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]  
  
 変数または null 許容型のプロパティには定義済みの値がある場合、値を割り当てる必要があるの初期状態に戻すことが発生することができます。 変数またはプロパティを設定して、これを行う`Nothing`次の例を示します。  
  
 [!code-vb[VbVbalrNullableValue&4;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]  
  
> [!NOTE]
>  割り当てることはできます`Nothing`null 許容型の変数をテストできません`Nothing`等号 (=) を使用しています。 比較に等号 (=) を使用して`someVar = Nothing`、常に評価`Nothing`します。 変数をテストして<xref:System.Nullable%601.HasValue%2A>プロパティを`False`、またはを使用してテスト、`Is`または`IsNot`演算子</xref:System.Nullable%601.HasValue%2A>。  
  
### <a name="retrieving-values"></a>値を取得します。  
 Null 許容型の変数の値を取得するには、テストしてください、<xref:System.Nullable%601.HasValue%2A>プロパティに値を使用していることを確認します</xref:System.Nullable%601.HasValue%2A>。 値を読み取るしようとする場合と<xref:System.Nullable%601.HasValue%2A>は`False`、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]スロー、<xref:System.InvalidOperationException>例外</xref:System.InvalidOperationException></xref:System.Nullable%601.HasValue%2A>。 次の例では、変数を読み取ることをお勧め`numberOfChildren`上の例です。  
  
 [!code-vb[VbVbalrNullableValue&#5;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]  
  
## <a name="comparing-nullable-types"></a>Null 許容型を比較します。  
 Null 許容型と`Boolean`ブール式で変数が使用を定義できます。 `True`、 `False`、または`Nothing`です。 次の真理値表は、`And`と`Or`です。 `b1`と`b2`これで&3; つの値がある&9; つの組み合わせを評価します。  
  
|b1|b2|b1 および b2|b1 または b2|  
|--------|--------|---------------|--------------|  
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|  
|`Nothing`|`True`|`Nothing`|`True`|  
|`Nothing`|`False`|`False`|`Nothing`|  
|`True`|`Nothing`|`Nothing`|`True`|  
|`True`|`True`|`True`|`True`|  
|`True`|`False`|`False`|`True`|  
|`False`|`Nothing`|`False`|`Nothing`|  
|`False`|`True`|`False`|`True`|  
|`False`|`False`|`False`|`False`|  
  
 ブール型の変数または式の値が`Nothing`はどちらも`true`も`false`です。 例を次に示します。  
  
 [!code-vb[VbVbalrNullableValue&6;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]  
  
 この例では`b1 And b2`に評価`Nothing`します。 その結果、`Else`句が各実行`If`ステートメント、および、出力を次に示します。  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  `AndAlso``OrElse`、1 つ目の評価が、2 番目のオペランドを評価する必要がありますなるショート サーキット評価、`Nothing`です。  
  
## <a name="propagation"></a>伝達  
 算術演算子、比較、shift キー、または種類の操作のオペランドの一方または両方が null 許容型の場合は、操作の結果も null 値を許容できます。 両方のオペランドが値ではない`Nothing`がどちらも場合と同様に、オペランドの基になる値で、操作を実行、null 許容型です。 次の例では、変数`compare1`と`sum1`は暗黙的に型指定されています。 上にマウス ポインターを置く場合、コンパイラは、それらの両方に対して null 許容型を推測が表示されます。  
  
 [!code-vb[VbVbalrNullableValue&#7;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]  
  
 1 つまたは両方のオペランドの値であれば`Nothing`、結果になります`Nothing`します。  
  
 [!code-vb[VbVbalrNullableValue&#8;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]  
  
## <a name="using-nullable-types-with-data"></a>Null 許容型のデータを使用します。  
 データベースは、null 許容型を使用する最も重要な場所の&1; つです。 すべてのデータベース オブジェクトが現在 null 許容型をサポートしますが、テーブルのデザイナーで生成されるアダプターします。 「TableAdapter で null 許容型のサポート」を参照してください[TableAdapter の概要](https://docs.microsoft.com/visualstudio/data-tools/tableadapter-overview)します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.InvalidOperationException></xref:System.InvalidOperationException>   
 <xref:System.Nullable%601.HasValue%2A></xref:System.Nullable%601.HasValue%2A>   
 [Null 許容型の使用](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)   
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [TableAdapter の概要](https://docs.microsoft.com/visualstudio/data-tools/tableadapter-overview)   
 [場合演算子](../../../../visual-basic/language-reference/operators/if-operator.md)   
 [ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)
