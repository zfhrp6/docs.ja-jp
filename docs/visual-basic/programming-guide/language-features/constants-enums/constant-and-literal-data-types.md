---
title: "定数とリテラルのデータ型 (Visual Basic) |Microsoft ドキュメント"
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
- declaring constants, literal data types
- data types [Visual Basic], declaring
- constants, declaring
- explicit declarations
- literals, coercing data type
- declarations, data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: 19
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
ms.openlocfilehash: 22ad31415ab560b7fd0180a6dadd6d2dcd7ec77a
ms.lasthandoff: 03/13/2017

---
# <a name="constant-and-literal-data-types-visual-basic"></a>定数とリテラルのデータ型 (Visual Basic)
リテラルは、変数の値または数値 3 または文字列「こんにちは」など、式の結果ではなく自体として表現される値です。 定数とは、リテラルの発生し、値が変化し、変数ではなく、プログラム全体で同じ値を保持するわかりやすい名前。  
  
 [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)は`Off`と[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)は`On`データ型を持つすべての定数を明示的に宣言する必要があります。 データ型を次の例で`MyByte`データ型として明示的に宣言されて`Byte`:  
  
 [!code-vb[VbVbalrConstants&#1;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 `Option Infer`は`On`または`Option Strict`は`Off`を持つデータ型を指定せずに定数を宣言することができます、`As`句。 コンパイラでは、式の型の定数の型を決定します。 既定で整数リテラルをキャスト、`Integer`データ型。 浮動小数点数は、の既定のデータ型`Double`、およびキーワード`True`と`False`指定、`Boolean`定数です。  
  
## <a name="literals-and-type-coercion"></a>リテラル値、および強制型変換  
 場合によっては、特定のデータ型をリテラルを強制する可能性があります。たとえば、型の変数を特に大きな整数リテラル値を割り当てる場合は`Decimal`です。 次の例では、エラーが生成されます。  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 リテラルの形式から、エラーが発生します。 `Decimal`データ型値を保持できるこの大きさが、リテラルが暗黙的として表される、 `Long`、することはできません。  
  
 2 つの方法で特定のデータ型のリテラルを強制することができます。 または文字を囲む内に配置することによって、型の文字を追加することによってです。 型文字または文字を囲む必要がありますすぐの前およびなしに余分な空白、または任意の種類の文字、リテラルに従います。  
  
 前の例を実行するために、追加することができます、`D`文字入力すると、表現されている場合は、リテラル、 `Decimal`:  
  
 [!code-vb[VbVbalrConstants&#2;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 次の例では、型の文字と囲み文字の正しい使用法を示します。  
  
 [!code-vb[VbVbalrConstants&#3;](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 周囲の文字と型の文字で使用できる次の表は[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]です。  
  
|データ型|囲み文字|末尾の型文字|  
|---|---|---|  
|`Boolean`|(なし)|(なし)|  
|`Byte`|(なし)|(なし)|  
|`Char`|"|C|  
|`Date`|#|(なし)|  
|`Decimal`|(なし)|D または @|  
|`Double`|(なし)|R または #|  
|`Integer`|(なし)|I または %|  
|`Long`|(なし)|L または >/documents/report1.rdl」の|  
|`Short`|(なし)|S|  
|`Single`|(なし)|F または!|  
|`String`|"|(なし)|  
  
## <a name="see-also"></a>関連項目  
 [ユーザー定義定数](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)   
 [方法: 定数の宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)   
 [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Option Explicit ステートメント](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
