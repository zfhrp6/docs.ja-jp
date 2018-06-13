---
title: 比較演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basicl
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: 4e37f55b4c873c3dbea22a8edf0e5e2b58824720
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604927"
---
# <a name="comparison-operators-visual-basic"></a>比較演算子 (Visual Basic)
Visual Basic で定義されている比較演算子を次に示します。  
  
 `<` 演算子  
  
 `<=` 演算子  
  
 `>` 演算子  
  
 `>=` 演算子  
  
 `=` 演算子  
  
 `<>` 演算子  
  
 [Is 演算子](../../../visual-basic/language-reference/operators/is-operator.md)  
  
 [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md)  
  
 [Like 演算子](../../../visual-basic/language-reference/operators/like-operator.md)  
  
 これらの演算子は、それらが等しいか、およびいない場合は、どのように異なるかどうかを決定する 2 つの式を比較します。 `Is`、 `IsNot`、および`Like`は別々 のヘルプ ページに詳しく説明します。 比較演算子は、このページで詳しく説明します。  
  
## <a name="syntax"></a>構文  
  
```  
      result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 A`Boolean`比較の結果を表す値です。  
  
 `expression`  
 必須。 任意の式。  
  
 `comparisonoperator`  
 必須。 任意の比較演算子です。  
  
 `object1`, `object2`  
 必須。 いずれかは、オブジェクト名を参照します。  
  
 `string`  
 必須。 任意のブール型 (`String`) の式を指定します。  
  
 `pattern`  
 必須。 どの`String`式または文字の範囲です。  
  
## <a name="remarks"></a>コメント  
 次の表は、比較演算子と判断する条件の一覧を含むかどうか`result`は`True`または`False`です。  
  
|演算子|`True` もし|`False` もし|  
|--------------|---------------|----------------|  
|`<` (より小さい)|`expression1` < `expression2`|`expression1` >= `expression2`|  
|`<=` (以下を)|`expression1` <= `expression2`|`expression1` > `expression2`|  
|`>` (より大きい)|`expression1` > `expression2`|`expression1` <= `expression2`|  
|`>=` (より大きいまたは等しい)|`expression1` >= `expression2`|`expression1` < `expression2`|  
|`=` (等しい)|`expression1` = `expression2`|`expression1` <> `expression2`|  
|`<>` (等しくない)|`expression1` <> `expression2`|`expression1` = `expression2`|  
  
> [!NOTE]
>  [演算子を =](../../../visual-basic/language-reference/operators/assignment-operator.md)代入演算子としても使用されます。  
  
 `Is` 、演算子、`IsNot`演算子、および`Like`演算子が前の表に、演算子とは異なる特定の比較機能があります。  
  
## <a name="comparing-numbers"></a>数値を比較します。  
 型の式を比較するときに`Single`型のいずれかに`Double`、`Single`式に変換されます`Double`です。 この動作は、Visual Basic 6 で動作するので、します。  
  
 同様に、型の式を比較するときに`Decimal`型の式を`Single`または`Double`、`Decimal`式に変換されます`Single`または`Double`です。 `Decimal`式、小数部の値より小さい 1E 28 は失われる可能性があります。 このような小数部の値が失われるがいない場合、等しいと比較する 2 つの値があります。 このため、注意してください等しいかどうかを使用する場合 (`=`) 2 つの浮動小数点変数を比較します。 2 つの数値の差の絶対値が許容差より小さいかどうかをテストすることができます。  
  
### <a name="floating-point-imprecision"></a>浮動小数点は誤差  
 浮動小数点数を使用する場合は、ことが常に正確に表現でないメモリに留意してください。 これにより予期しない結果を比較値などの特定の操作から、 [Mod 演算子](../../../visual-basic/language-reference/operators/mod-operator.md)です。 詳細については、次を参照してください。[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)です。  
  
## <a name="comparing-strings"></a>文字列の比較  
 依存する、アルファベット順の並べ替え順序に基づいて、文字列式を評価する文字列を比較するときに、`Option Compare`設定します。  
  
 `Option Compare Binary` ベース文字列の文字の内部バイナリ表現から派生した並べ替え順序で比較します。 並べ替え順序は、コード ページによって決まります。 次の例では、一般的なバイナリ並べ替え順序を示します。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text` ベースでは、アプリケーションのロケールによって決まる、大文字と小文字、テキストの並べ替え順序での比較を文字列です。 設定すると`Option Compare Text`前の例での文字を並べ替えると、次のテキストの並べ替え順序が適用されます。  
  
 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`  
  
### <a name="locale-dependence"></a>ロケール依存性  
 設定すると`Option Compare Text`、文字列比較の結果が、アプリケーションが実行されている、ロケールに依存することができます。 2 つの文字は、等しいと評価別ではなく 1 つのロケールで比較可能性があります。 ログオンを許可するかどうかなど、重要な意思決定を行う、文字列の比較を使用している場合は、ロケールと小文字の区別にアラートがあります。 いずれかの設定を検討してください`Option Compare Binary`または呼び出して、<xref:Microsoft.VisualBasic.Strings.StrComp%2A>ロケールにが考慮されます。  
  
## <a name="typeless-programming-with-relational-comparison-operators"></a>リレーショナル比較演算子を省略したプログラミング  
 リレーショナル比較演算子の使用`Object`で式が許可されていません`Option Strict On`です。 ときに`Option Strict`は`Off`、いずれかと`expression1`または`expression2`は、`Object`式では、実行時の型は、それらを比較する方法を決定します。 次の表は、式を比較する方法と、ランタイムのオペランドの型に応じて、比較の結果を示します。  
  
|オペランドの場合|比較では、|  
|---------------------|-------------------|  
|両方とも `String`|文字列の並べ替え特性に基づく比較を並べ替えます。|  
|両方の数値|オブジェクトに変換されます`Double`、数値比較します。|  
|1 つの数値型と 1 つ `String`|`String`に変換されますが、`Double`数値比較を実行します。 場合、`String`に変換できない`Double`、<xref:System.InvalidCastException>がスローされます。|  
|一方または両方が以外の参照型です。 `String`|<xref:System.InvalidCastException> がスローされます。|  
  
 数値の比較が扱う`Nothing`0 とします。 文字列比較扱う`Nothing`として`""`(空の文字列)。  
  
## <a name="overloading"></a>オーバーロード  
 比較演算子 (`<`です。 `<=`、 `>`、 `>=`、 `=`、 `<>`) を指定できます*オーバー ロードされた*、つまり、あるクラスまたは構造体できます動作を再定義オペランドは、そのクラスまたは構造体の型を持ちます。 コードは、このようなクラスまたは構造体で、これらの演算子のいずれかを使用している場合は、再定義された動作を理解することを確認します。 詳細については、次を参照してください。[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)です。  
  
 注意して、[演算子を =](../../../visual-basic/language-reference/operators/assignment-operator.md)比較演算子としてのみ、代入演算子としてではなく、オーバー ロードされたを指定できます。  
  
## <a name="example"></a>例  
 次の例では、式の比較に使用するは、リレーショナル比較演算子のさまざまな使用を示します。 リレーショナル比較演算子を返す、`Boolean`を指定した式を評価するかどうかを表す結果`True`です。 適用すると、`>`と`<`文字列への演算子、比較を使用して、通常のアルファベット順の文字列の。 この順序は、ロケールの設定に依存できます。 かどうか、並べ替えが大文字かによって異なります、 [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)設定します。  
  
 [!code-vb[VbVbalrOperators#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 前の例では、最初に比較を返します`False`し、残りの比較を返します`True`です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.InvalidCastException>  
 [= 演算子](../../../visual-basic/language-reference/operators/assignment-operator.md)  
 [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [トラブルシューティング (データ型)](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Visual Basic における比較演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
