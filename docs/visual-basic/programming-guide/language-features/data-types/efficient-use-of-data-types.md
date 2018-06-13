---
title: データ型の有効な使用方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 6e71c4e2225bbcde3bb2bd20ae098f5600990051
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647762"
---
# <a name="efficient-use-of-data-types-visual-basic"></a>データ型の有効な使用方法 (Visual Basic)
宣言されていない変数とデータ型なしで宣言された変数が割り当てられている、`Object`データ型。 実行速度が低下することができるプログラムを迅速に作成するが容易になります。 可能性がします。  
  
## <a name="strong-typing"></a>厳密な型指定  
 すべての変数のデータ型の指定と呼びます*厳密な型指定*です。 厳密な型指定を使用すると、いくつかの利点があります。  
  
-   IntelliSense をサポートしている変数を使用できます。 これにより、コードに入力すると、そのプロパティおよびその他のメンバーを参照してください。  
  
-   コンパイラの型チェックの利点がかかります。 これは、実行時のオーバーフローなどのエラーにより失敗するステートメントをキャッチします。 それらをサポートしないオブジェクトに対するメソッドの呼び出しをキャッチします。  
  
-   コードの実行を高速になります。  
  
## <a name="most-efficient-data-types"></a>最も効率的なデータ型  
 小数を含まない変数の場合は、整数データ型は、非整数型よりも効率的です。 Visual basic で`Integer`と`UInteger`最も効率的な数値型です。  
  
 小数値は、`Double`最も効率的なデータ型では、現在のプラットフォーム上のプロセッサの倍精度浮動小数点演算を実行するためです。 ただし、操作を`Double`などの整数型と同様に高速ではない`Integer`です。  
  
## <a name="specifying-data-type"></a>データ型の指定  
 使用して、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)特定の型の変数を宣言します。 使用して、アクセス レベルを指定することが同時に、[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)、または[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)に示すように、キーワード、次の例です。  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>文字の変換  
 `AscW`と`ChrW`関数は Unicode に操作します。 優先的に使用する必要があります`Asc`と`Chr`Unicode との間に変換する必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [数値のデータ型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [IntelliSense の使用](/visualstudio/ide/using-intellisense)
