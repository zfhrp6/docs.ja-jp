---
title: '方法: 列挙型を宣言する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
ms.openlocfilehash: e2dbdbbf6bf7fe3e4b71cbe7edc7a19b18f96ef2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650804"
---
# <a name="how-to-declare-enumerations-visual-basic"></a>方法: 列挙型を宣言する (Visual Basic)
持つ列挙体を作成する、`Enum`クラスまたはモジュールの宣言セクション内のステートメント。 メソッド内の列挙体を宣言することはできません。 適切なアクセス レベルを指定する`Private`、 `Protected`、 `Friend`、または`Public`です。  
  
 `Enum`型は、名前、基になる型では、および一連のフィールド、それぞれが表す定数。 名前は、有効な Visual Basic .NET 修飾子にする必要があります。 基になる型は整数型のいずれかを指定する必要があります:`Byte`、 `Short`、`Long`または`Integer`です。 `Integer` が既定値です。 列挙体は、常に厳密に型指定し、整数の数値型に置き換えることはできません。  
  
 列挙体には、浮動小数点値を持つことはできません。 列挙体には、浮動小数点値が割り当てられる場合`Option Strict On`、コンパイラ エラーが発生します。 場合`Option Strict`は`Off`、値が自動的に変換する、`Enum`型です。  
  
 使用する方法および名について、`Imports`ステートメントに名前の修飾を不要な場合を参照してください[列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)です。  
  
### <a name="to-declare-an-enumeration"></a>列挙体を宣言するには  
  
1.  コードのアクセス レベルを含む宣言を記述、`Enum`キーワード、および有効な名前、次の例のように、別の宣言`Enum`です。  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  列挙体の定数を定義します。 既定では、最初の定数、列挙型でに初期化`0`、それに続く定数は、前の定数に詳細のいずれかの値に初期化されます。 たとえば、次の列挙型、 `Days`、名前付き定数が含まれる`Sunday`値を持つ`0`、という名前の定数`Monday`値を持つ`1`、という名前の定数`Tuesday`の値を持つ`2`のようにします。  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  代入ステートメントを使用して、列挙型の定数に値を割り当てることができますに明示的にします。 負の数値を含む、任意の整数値を割り当てることができます。 たとえば、エラー条件を表す 0 より小さい値を持つ定数をする可能性があります。 次の列挙型定数`Invalid`値を明示的に割り当てられて`–1`、および定数`Sunday`値が割り当てられている`0`です。 最初の定数、列挙型であるため`Saturday`は、値に初期化も`0`します。 値`Monday`は`1`(いずれかの値よりも詳細`Sunday`); の値`Tuesday`は`2`のようにします。  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a>列挙型を明示的な型として宣言するには  
  
-   使用して、列挙型の型を指定、`As`句、次の例で示すようにします。  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [方法 : 列挙型のメンバーを参照する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [方法: Visual Basic で列挙型を反復処理します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [方法 : 列挙値に関連付けられている文字列を確認する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [列挙型を使用する状況](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
