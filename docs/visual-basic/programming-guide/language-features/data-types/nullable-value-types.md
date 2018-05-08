---
title: null 許容値型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: bb44ad85347b494b63dde964b2b407d8f038f2b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="nullable-value-types-visual-basic"></a>null 許容値型 (Visual Basic)
特定の状況で定義されている値を持たない値の型と連携することがあります。 たとえば、データベース内のフィールドは、意味のある割り当てられた値を持つ、割り当てられた値がないとを区別する必要があります。 値の型は、通常の値または null 値のいずれかを拡張できます。 このような拡張機能が呼び出された、 *null 許容型*です。  
  
 各 null 許容型がジェネリックから構築された<xref:System.Nullable%601>構造体。 作業に関連するアクティビティを追跡するデータベースを検討してください。 次の例は、null 許容型を構築`Boolean`を入力し、その型の変数を宣言します。 宣言は、次の 3 つの方法で記述できます。  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]  
  
 変数`ridesBusToWork`の値を保持できる`True`、値の`False`、またはすべての値はありません。 初期の既定値はありません値すべての例ではこの可能性があること、情報がない取得されていないこのユーザーの。 これに対し、`False`情報が取得され、ユーザーが仕事のバスをオーバーライドしていないことを意味します。  
  
 変数とプロパティを宣言するには、null 許容型で、null 許容型の要素を含む配列を宣言することができます。 Null 許容型をパラメーターとしてでプロシージャを宣言してから null 許容型を返すことができます、`Function`プロシージャです。  
  
 参照型、配列などに null 許容型を構築することはできません、 `String`、またはクラス。 基になる型は、値型である必要があります。 詳細については、次を参照してください。[値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)です。  
  
## <a name="using-a-nullable-type-variable"></a>Null 許容型の変数を使用します。  
 Null 許容型の最も重要なメンバーは、その<xref:System.Nullable%601.HasValue%2A>と<xref:System.Nullable%601.Value%2A>プロパティです。 Null 許容型の変数に対して<xref:System.Nullable%601.HasValue%2A>変数が定義済みの値を含むかどうかがわかります。 場合<xref:System.Nullable%601.HasValue%2A>は`True`から値を読み取ることができます<xref:System.Nullable%601.Value%2A>です。 なお両方<xref:System.Nullable%601.HasValue%2A>と<xref:System.Nullable%601.Value%2A>は`ReadOnly`プロパティです。  
  
### <a name="default-values"></a>既定値  
 Null 許容型を持つ変数を宣言するときにその<xref:System.Nullable%601.HasValue%2A>プロパティの既定値を持つ`False`します。 つまり、既定では、変数がない基になる値の型の既定値ではなく、定義済みの値。 次の例では、変数`numberOfChildren`最初に値を持たない値が定義されていなくても、既定の`Integer`型は 0 です。  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]  
  
 Null 値は、未定義または不明な値を示すために役立ちます。 場合`numberOfChildren`として宣言された`Integer`情報が現在使用できないことを示す値になりますありません。  
  
### <a name="storing-values"></a>値を格納します。  
 一般的な方法で変数または null 許容型のプロパティ値を格納します。 次の例では、変数に値を割り当てます`numberOfChildren`前の例で宣言します。  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]  
  
 変数または null 許容型のプロパティには定義済みの値がある場合は、割り当てられている値を持っていないの初期状態に戻すを生成できます。 変数またはプロパティを設定して、これを行う`Nothing`次の例を示します。  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]  
  
> [!NOTE]
>  割り当てることはできます`Nothing`、null 許容型の変数にすることはできないことをテスト用`Nothing`等号 (=) を使用しています。 等号 (=) を使用する比較`someVar = Nothing`、常に評価`Nothing`です。 変数をテストする<xref:System.Nullable%601.HasValue%2A>プロパティ`False`、またはを使用してテスト、`Is`または`IsNot`演算子。  
  
### <a name="retrieving-values"></a>値を取得します。  
 Null 許容型の変数の値を取得する必要があります最初をテストするその<xref:System.Nullable%601.HasValue%2A>プロパティに値を使用していることを確認します。 値を読み取るしようとする場合と<xref:System.Nullable%601.HasValue%2A>は`False`、Visual Basic をスロー、<xref:System.InvalidOperationException>例外。 次の例では、変数を読み取ることをお勧め`numberOfChildren`前の例です。  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]  
  
## <a name="comparing-nullable-types"></a>Null 許容型を比較します。  
 Null 許容と`Boolean`変数がブール式で使用される、結果を指定できます`True`、 `False`、または`Nothing`です。 真理値表を次に示します`And`と`Or`です。 `b1`と`b2`3 つの値があるようになりました 9 つの組み合わせを評価します。  
  
|B1|B2|b1 と b2|b1 または b2|  
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
  
 ブール値変数または式の値が`Nothing`はどちらも`true`も`false`します。 例を次に示します。  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]  
  
 この例では`b1 And b2`に評価される`Nothing`です。 その結果、`Else`各句が実行されて`If`ステートメントでは、呼び出し力には、次のようにします。  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  `AndAlso` および`OrElse`、最初の評価が、2 番目のオペランドを評価する必要がありますを使用するショート サーキット評価、`Nothing`です。  
  
## <a name="propagation"></a>伝達  
 算術演算子、比較、shift キーを押し、または種類の操作のオペランドの一方または両方が null 許容の場合は、操作の結果も null 値を許容できます。 両方のオペランドが値ではない`Nothing`、どちらもが場合と同様に、オペランドの基になる値に対して操作を実行 null 許容型。 次の例では、変数`compare1`と`sum1`は暗黙的に型指定されています。 上にマウス ポインターを置くと場合、コンパイラがそれらの両方に対して null 許容型を推測することが表示されます。  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]  
  
 1 つまたは両方のオペランドの値を持つ場合`Nothing`、結果になります`Nothing`です。  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]  
  
## <a name="using-nullable-types-with-data"></a>Null 許容型のデータを使用します。  
 データベースは、null 許容型を使用する最も重要な場所の 1 つです。 すべてのデータベース オブジェクトは null 許容の型を現在サポートしていますが、デザイナーで生成されたテーブルのアダプターです。 「Null 許容型の TableAdapter サポート」を参照してください[TableAdapter の概要](/visualstudio/data-tools/tableadapter-overview)です。
  
## <a name="see-also"></a>関連項目  
 <xref:System.InvalidOperationException>  
 <xref:System.Nullable%601.HasValue%2A>  
 [Null 許容型の使用](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [TableAdapter の概要](/visualstudio/data-tools/tableadapter-overview)  
 [If 演算子](../../../../visual-basic/language-reference/operators/if-operator.md)  
 [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)
