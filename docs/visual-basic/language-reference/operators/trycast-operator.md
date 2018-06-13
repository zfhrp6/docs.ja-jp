---
title: TryCast 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords:
- TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
ms.openlocfilehash: d8825b8eee35ea514d4001a6a5c1cc5139c67454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600151"
---
# <a name="trycast-operator-visual-basic"></a>TryCast 演算子 (Visual Basic)
例外をスローしない型変換操作について説明します。  
  
## <a name="remarks"></a>コメント  
 実行しようとした変換が失敗した場合、`CType`と`DirectCast`両方をスロー、<xref:System.InvalidCastException>エラーです。 これは、アプリケーションのパフォーマンスに悪影響を与える。 `TryCast` 返します[Nothing](../../../visual-basic/language-reference/nothing.md)、可能性のある例外を処理するのではなく、に対して返される結果をテストする必要があるだけように`Nothing`です。  
  
 使用する、`TryCast`キーワードを使用するのと同様、 [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)と[DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)キーワード。 最初の引数と型に変換するために 2 番目の引数として式を指定します。 `TryCast` クラスとインターフェイスなど、参照型でしか動作しません。 2 つの型間の継承または実装のリレーションシップが必要です。 これは、1 つの型が継承する必要があるかどうか、または、他の実装していることを意味します。  
  
## <a name="errors-and-failures"></a>エラーや障害  
 `TryCast` 継承または実装のリレーションシップが存在しないことが検出された場合は、コンパイラ エラーを生成します。 コンパイラ エラーがないことに成功した変換が保証されません。 必要な変換は縮小すると、実行時に失敗する可能性がします。 この場合、`TryCast`返します[Nothing](../../../visual-basic/language-reference/nothing.md)です。  
  
## <a name="conversion-keywords"></a>変換キーワード  
 型変換のキーワードの比較は次のとおりです。  
  
|キーワード|データの種類|引数の関係|実行時エラー|  
|---|---|---|---|  
|[CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)|すべてのデータ型|2 つのデータ型の間では、拡大または縮小変換を定義する必要があります。|スローされます。 <xref:System.InvalidCastException>|  
|[DirectCast 演算子](../../../visual-basic/language-reference/operators/directcast-operator.md)|すべてのデータ型|1 つの型を継承または、他の型を実装する必要があります。|スローされます。 <xref:System.InvalidCastException>|  
|`TryCast`|参照型のみ|1 つの型を継承または、他の型を実装する必要があります。|返します[何も行われません](../../../visual-basic/language-reference/nothing.md)|  
  
## <a name="example"></a>例  
 次の例は、`TryCast` を使用する方法を示しています。  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
