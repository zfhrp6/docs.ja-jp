---
title: 定数とリテラルのデータ型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 8d110ec17bcdb03f339d779b2950ba56d77957cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="constant-and-literal-data-types-visual-basic"></a>定数とリテラルのデータ型 (Visual Basic)
リテラルは、変数の値または数値 3 または文字列「こんにちは」など、式の結果ではなく自体として表される値です。 定数は、わかりやすい名前を受け取り、リテラルの代わりに値を変更することがあります、変数ではなく、プログラム全体で同じ値を保持します。  
  
 ときに[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)は`Off`と[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)は`On`データ型を持つすべての定数を明示的に宣言する必要があります。 データ型を次の例では、`MyByte`データ型として明示的に宣言されて`Byte`:  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 ときに`Option Infer`は`On`または`Option Strict`は`Off`を持つデータ型を指定せずに定数を宣言することができます、`As`句。 コンパイラでは、定数式の型からの型を決定します。 既定でに整数リテラルをキャスト、`Integer`データ型。 既定のデータ型は、浮動小数点数の`Double`、およびキーワード`True`と`False`指定、`Boolean`定数。  
  
## <a name="literals-and-type-coercion"></a>リテラルおよび強制型変換  
 場合によってを特定のデータ型にリテラルを適用する場合があります。たとえば、型の変数に特に大きな整数リテラル値を割り当てる際`Decimal`です。 次の例では、エラーが生成されます。  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 リテラルの表現から、エラーが発生します。 `Decimal`データ型値を保持できるこの大きさがリテラルは暗黙的に表されてとして、 `Long`、することはできません。  
  
 2 つの方法で特定のデータ型をリテラルを強制することができます: に、型文字を追加することによって、または文字を囲む内に配置することによってです。 型文字または文字を囲む必要がありますすぐに前やなし、介在する領域または任意の種類の文字、リテラルに従います。  
  
 前の例を実行するために、追加することができます、`D`文字入力すると、リテラルとして表現されていること、 `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 次の例では、型文字と囲み文字の正しい使用法を示しています。  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 次の表は、それを囲む文字と Visual Basic で使用可能な型宣言文字。  
  
|データの種類|囲み文字|末尾の型文字|  
|---|---|---|  
|`Boolean`|(なし)|(なし)|  
|`Byte`|(なし)|(なし)|  
|`Char`|"|C|  
|`Date`|#|(なし)|  
|`Decimal`|(なし)|D または @|  
|`Double`|(なし)|R または #|  
|`Integer`|(なし)|$I または %|  
|`Long`|(なし)|L または (& a)|  
|`Short`|(なし)|S|  
|`Single`|(なし)|F または!|  
|`String`|"|(なし)|  
  
## <a name="see-also"></a>関連項目  
 [ユーザー定義定数](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [方法 : 定数を宣言する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Option Explicit ステートメント](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
