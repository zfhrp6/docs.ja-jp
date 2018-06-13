---
title: Visual Basic の制限事項
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: 57378c3aa18a5cc108c10e8654e55803f3cf9052
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649930"
---
# <a name="visual-basic-limitations"></a>Visual Basic の制限事項
以前のバージョンの Visual Basic では、変数名、モジュール、およびモジュールのサイズで許可される変数の数の長さなどのコード内の境界が適用されます。 Visual Basic .net では、これらの制限が緩和されました、記述と、コードの配置をより自由が提供します。  
  
 物理的な制限よりも実行時のメモリ上よりするコンパイル時の考慮事項に依存します。 万全を期してのプログラミング方法を使用して大規模なアプリケーションを複数のクラスとモジュールに分割する場合は、内部の Visual Basic の制限にぶつかる可能性はほとんどです。  
  
 極端なケースで発生する可能性のあるいくつかの制限を次に示します。  
  
-   **名の長さ。** すべての宣言されたプログラミング要素の名前の文字の最大数があります。 この最大値は、要素名が修飾されている場合に、全体の修飾文字列に適用されます。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。  
  
-   **行の長さ。** これは、ソース コードの物理的な行で値 65535 文字の最大です。 論理ソース コード行を行継続文字を使用する場合は、長いことはできます。 参照してください[する方法: 分割および連結コード内でステートメント](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)です。  
  
-   **配列の次元です。** 配列で宣言できるディメンションの最大数があります。 これにより、配列の要素を指定する使用できるインデックスの数が制限されます。 参照してください[Visual Basic でのディメンションを配列](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)です。  
  
-   **文字列の長さ。** 1 つの文字列に格納できる Unicode 文字の最大数があります。 参照してください[文字列データ型](../../../visual-basic/language-reference/data-types/string-data-type.md)です。  
  
-   **環境文字列の長さ。** これは、コマンドライン引数として使用される任意の環境文字列 32768 文字の最大です。 これは、すべてのプラットフォームでの制限です。  
  
## <a name="see-also"></a>関連項目  
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
