---
title: "ブール型 (Boolean) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdc106f1ec874c1a2165df069d5f3485fe5b2e43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-data-type-visual-basic"></a>ブール型 (Boolean) (Visual Basic)
値を保持できるのみ`True`または`False`です。 キーワード`True`と`False`の 2 つの状態に対応している`Boolean`変数。  
  
## <a name="remarks"></a>コメント  
 使用して、[ブール データ型 (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) true または false などの 2 つの状態値が含まれてはい/いいえ、またはオン/オフにします。  
  
 `Boolean` の既定値は `False` です。  
  
 `Boolean`値は、数値としては格納されませんし、格納された値が数値に相当するものではありません。 数値と等価の値に依存するコードを記述する必要がありますしない`True`と`False`です。 使用を制限する必要があります、可能な限り`Boolean`仕様で定められている論理値変数。  
  
## <a name="type-conversions"></a>型変換  
 Visual Basic でに数値データ型の値を変換するときに`Boolean`、0 になります`False`になり、その他のすべての値`True`です。 Visual Basic の変換と`Boolean`値、数値型を`False`が 0 になったと`True`-1 になります。  
  
 間で変換する際に`Boolean`値と、数値データ型は、する .NET Framework 変換メソッドは、常に生成しない変換の Visual Basic のキーワードと同じ結果に留意してください。 Visual Basic の変換には、以前のバージョンと互換性のある動作が保持されるためです。 詳細についてを参照してください「ブール型は変換する数値型不適切」[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)です。  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
-   **負の数。** `Boolean`数値型ではないと、負の値を表すことはできません。 いずれの場合は、使用しないで`Boolean`数値の値を保持します。  
  
-   **型宣言文字。** `Boolean`リテラルの型文字または識別子の型文字がありません。  
  
-   **Framework の型。** .NET Framework において対応する型は、<xref:System.Boolean?displayProperty=nameWithType> 構造体です。  
  
## <a name="example"></a>例  
 次の例では、`runningVB`は、`Boolean`単純なはい/いいえの設定を格納する変数。  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Boolean?displayProperty=nameWithType>  
 [データの種類](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [トラブルシューティング (データ型)](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)
