---
title: DirectCast 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.directCast
- directCast
helpviewer_keywords:
- DirectCast keyword [Visual Basic]
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
ms.openlocfilehash: 534e94ecc0a394caa2865c2da754ad8f4dbc6f44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604225"
---
# <a name="directcast-operator-visual-basic"></a>DirectCast 演算子 (Visual Basic)
継承または実装に基づいて、型変換操作をについて説明します。  
  
## <a name="remarks"></a>コメント  
 `DirectCast` 実行時のヘルパー ルーチンに多少を提供するための変換よりもパフォーマンスが向上、Visual Basic を使用しない`CType`データ型に変換するときに`Object`です。  
  
 使用する、`DirectCast`キーワードを使用するのと同様、 [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)と[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)キーワード。 最初の引数と型に変換するために 2 番目の引数として式を指定します。 `DirectCast` 2 つの引数のデータ型間の継承または実装のリレーションシップが必要です。 これは、1 つの型が継承する必要があるかどうか、または、他の実装していることを意味します。  
  
## <a name="errors-and-failures"></a>エラーや障害  
 `DirectCast` 継承または実装のリレーションシップが存在しないことが検出された場合は、コンパイラ エラーを生成します。 コンパイラ エラーがないことに成功した変換が保証されません。 必要な変換は縮小すると、実行時に失敗する可能性がします。 この場合、ランタイムは、スロー、<xref:System.InvalidCastException>エラーです。  
  
## <a name="conversion-keywords"></a>変換キーワード  
 型変換のキーワードの比較は次のとおりです。  
  
|キーワード|データの種類|引数の関係|実行時エラー|  
|---|---|---|---|  
|[CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)|すべてのデータ型|2 つのデータ型の間では、拡大または縮小変換を定義する必要があります。|スローされます。 <xref:System.InvalidCastException>|  
|`DirectCast`|すべてのデータ型|1 つの型を継承または、他の型を実装する必要があります。|スローされます。 <xref:System.InvalidCastException>|  
|[TryCast 演算子](../../../visual-basic/language-reference/operators/trycast-operator.md)|参照型のみ|1 つの型を継承または、他の型を実装する必要があります。|返します[何も行われません](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>例  
 次の例では、2 つの用途の`DirectCast`、いずれかのいずれかの実行時に失敗することは成功します。  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/VisualBasic/directcast-operator_1.vb)]  
  
 前の例で、実行時の入力の`q`は`Double`します。 `CType` 成功`Double`に変換できる`Integer`です。 ただし、最初の`DirectCast`、実行時の入力のために、実行時に失敗`Double`継承関係を持たない`Integer`変換が存在する場合でも、します。 2 番目`DirectCast`が型から変換が成功した<xref:System.Windows.Forms.Form>入力<xref:System.Windows.Forms.Control>、元となる<xref:System.Windows.Forms.Form>を継承します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Convert.ChangeType%2A?displayProperty=nameWithType>  
 [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
