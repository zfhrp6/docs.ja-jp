---
title: "データ型 (Visual Basic) を効率的に使用 |Microsoft ドキュメント"
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
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function, preferred to Asc
- data types [Visual Basic], using efficiently
- optimization, data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function, preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
caps.latest.revision: 16
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
ms.openlocfilehash: b81a1c81d970beee32925c3f2fe6ca3bcad79151
ms.lasthandoff: 03/13/2017

---
# <a name="efficient-use-of-data-types-visual-basic"></a>データ型の有効な使用方法 (Visual Basic)
宣言されていない変数とデータ型なしで宣言された変数が割り当てられている、`Object`データ型。 これにより、プログラムの記述を簡単にが実行速度が低下します。  
  
## <a name="strong-typing"></a>厳密な型指定  
 すべての変数のデータ型の指定と呼ばれます*厳密な型指定*します。 厳密な型指定を使用すると、いくつかの利点があります。  
  
-   これにより、IntelliSense での変数をサポートできます。 これにより、コードに入力すると、そのプロパティおよびその他のメンバーを参照してください。  
  
-   これは、コンパイラの型チェック利用をします。 これは、実行時のオーバーフローなどのエラーにより失敗するステートメントを検出します。 サポートしていないオブジェクトに対するメソッドの呼び出しをキャッチします。  
  
-   コードの実行を高速になります。  
  
## <a name="most-efficient-data-types"></a>最も効率的なデータ型  
 小数を含まない変数の場合は、整数データ型は、非整数型よりも効率的です。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、`Integer`と`UInteger`は最も効率的な数値型。  
  
 小数値`Double`を最も効率的なデータ型は、現在のプラットフォーム上のプロセッサでは、倍精度浮動小数点演算を実行するためです。 ただし、操作が`Double`などの整数型と同様に高速ではない`Integer`します。  
  
## <a name="specifying-data-type"></a>データ型の指定  
 使用して、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)特定の型の変数を宣言します。 同時に使用してアクセス レベルを指定することができます、[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)、または[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワードは、次の例に示すようにします。  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a>文字の変換  
 `AscW`と`ChrW`関数は Unicode に操作します。 優先的に使用する必要があります`Asc`と`Chr`Unicode との間に変換する必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A></xref:Microsoft.VisualBasic.Strings.Asc%2A>   
 <xref:Microsoft.VisualBasic.Strings.AscW%2A></xref:Microsoft.VisualBasic.Strings.AscW%2A>   
 <xref:Microsoft.VisualBasic.Strings.Chr%2A></xref:Microsoft.VisualBasic.Strings.Chr%2A>   
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A></xref:Microsoft.VisualBasic.Strings.ChrW%2A>   
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [数値データ型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [IntelliSense の使用](https://docs.microsoft.com/visualstudio/ide/using-intellisense)
