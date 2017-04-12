---
title: "Visual Basic の制限事項 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- limits
- limitations, Visual Basic
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: d556b045b4ebae6ba24c0571a6cb7e5337c6a8f2
ms.lasthandoff: 03/13/2017

---
# <a name="visual-basic-limitations"></a>Visual Basic の制限事項
以前のバージョンの[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]モジュール、およびモジュールのサイズで許可される変数の数、変数名の長さなどのコード内の境界を適用します。 [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]、記述し、コードを配置するをより自由を与える、これらの制限は緩和されています。  
  
 物理的な制限よりも実行時のメモリ上よりするコンパイル時の考慮事項に依存します。 ごくわずかな内部が発生する可能性があるかどうかは、慎重なプログラミングの方法を使用して大規模なアプリケーションを複数のクラスと、モジュールに分割[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]制限します。  
  
 極端なケースで発生する可能性のあるいくつかの制限を次に示します。  
  
-   **名の長さ。** これは、プログラミングのすべての宣言された要素の名前を文字の最大数です。 この最大値は、要素名が修飾されている場合に、全体の修飾文字列に適用されます。 参照してください[宣言された要素の名前](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。  
  
-   **行の長さ。** これは、ソース コードの物理的な行で 65535 文字の最大です。 論理ソース コード行は行継続文字を使用する場合は、長くすることはできます。 参照してください[方法: 分割およびコード内でステートメントを連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)です。  
  
-   **配列の次元。** これは、配列の場合、宣言するディメンションの最大数です。 これにより、配列要素を指定してインデックスの数が制限されます。 参照してください[Visual Basic における次元の配列](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)します。  
  
-   **文字列の長さ。** これは、1 つの文字列に格納できる Unicode 文字の最大数です。 参照してください[文字列データ型](../../../visual-basic/language-reference/data-types/string-data-type.md)します。  
  
-   **環境文字列長。** コマンドライン引数として使用される任意の環境文字列の 32768 文字の最大値があります。 これは、すべてのプラットフォームでの制限です。  
  
## <a name="see-also"></a>関連項目  
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
