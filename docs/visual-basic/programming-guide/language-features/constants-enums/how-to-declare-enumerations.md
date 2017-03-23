---
title: "方法: 列挙型 (Visual Basic) を宣言 |Microsoft ドキュメント"
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
- declarations, enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: 24
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
ms.openlocfilehash: 8ff8bf2df39bed0597740bcda968283ec854f447
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-enumerations-visual-basic"></a>方法: 列挙型を宣言する (Visual Basic)
持つ列挙体を作成する、`Enum`クラスまたはモジュールの宣言セクション内のステートメントです。 メソッド内で列挙体を宣言することはできません。 適切なアクセス レベルを指定する`Private`、 `Protected`、 `Friend`、または`Public`です。  
  
 `Enum`型は、名前、基になる型では、および一連のフィールド、それぞれが表す定数。 名前を有効にする必要があります[!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]修飾子です。 基になる型は整数型のいずれかを指定する必要があります:`Byte`、 `Short`、`Long`または`Integer`です。 `Integer` が既定値です。 列挙型は、常に厳密に型指定し、整数の数値型に置き換えることはできません。  
  
 列挙体には、浮動小数点値を持つことはできません。 列挙体には、浮動小数点値が割り当てられる場合`Option Strict On`、コンパイラ エラーが発生します。 場合`Option Strict`は`Off`、値が自動的に変換する、`Enum`型です。  
  
 使用する方法および名について、`Imports`ステートメントを名前の修飾を不要なを参照してください[列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)します。  
  
### <a name="to-declare-an-enumeration"></a>列挙型を宣言するには  
  
1.  コード アクセス レベルでは、宣言を書き込む、`Enum`キーワード、および有効な名前、次の例のように、別の宣言`Enum`します。  
  
     [!code-vb[VbEnumsTask&#3;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  列挙型の定数を定義します。 既定では、列挙体の最初の定数に初期化`0`、それに続く定数よりも前の定数のいずれかの値に初期化されます。 たとえば、次の列挙`Days`、という名前の定数が含まれています`Sunday`値を持つ`0`、という名前の定数`Monday`値を持つ`1`、という名前の定数`Tuesday`の値を持つ`2`、という具合です。  
  
     [!code-vb[VbEnumsTask&4;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  代入ステートメントを使用して列挙で定数に値を明示的に代入できます。 負の数値を含む任意の整数値を割り当てることができます。 たとえば、エラー状態を表す&0; より小さい値を持つ定数ができます。 次の列挙型定数`Invalid`、値が明示的に割り当てられた`–1`と定数`Sunday`、値が割り当てられた`0`します。 最初の定数、列挙型であるため`Saturday`は、値に初期化も`0`です。 値`Monday`は`1`(いずれかの値よりも詳細`Sunday`); の値`Tuesday`は`2`、という具合です。  
  
     [!code-vb[VbEnumsTask&#5;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>明示的な型として列挙型を宣言するには  
  
-   使用して列挙型の型を指定する、`As`句は、次の例で示すようにします。  
  
     [!code-vb[VbEnumsTask&6;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 [列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [方法: 列挙型のメンバーを参照してください](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [方法: Visual Basic で列挙型を反復処理します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [方法: 列挙値に関連付けられている文字列を確認します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [列挙体を使用する場合](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
