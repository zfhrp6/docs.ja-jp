---
title: '方法: 定数を宣言する (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.constant
helpviewer_keywords:
- Integer data type [Visual Basic], declaring constants
- Single data type [Visual Basic], declaring constants
- Const statement [Visual Basic], declaring constants
- procedures [Visual Basic], declaration
- data types [Visual Basic], constants
- Long data type [Visual Basic], declaring constants
- Visual Basic code, declaring variables and constants
- Double data type [Visual Basic], declaring constants
- Boolean data type [Visual Basic], declaring constants
- modules, declaring constants
- Byte data type [Visual Basic], declaring constants
- constants [Visual Basic], declaring
- Date data type [Visual Basic], declaring constants
- String data type [Visual Basic], declaring constants
- declaring constants [Visual Basic], const keyword
- Currency data type [Visual Basic], declaring constants and variants
- module-level constants and variables
- Object data type [Visual Basic], declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
ms.openlocfilehash: ce45e4df7f74cd68bde0fb2adba10197a11edb1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649738"
---
# <a name="how-to-declare-a-constant-visual-basic"></a>方法: 定数を宣言する (Visual Basic)
使用する、`Const`定数を宣言し、その値を設定するステートメント。 定数を宣言すると、値にわかりやすい名前を割り当てます。 定数が宣言されると、変更または新しい値を代入することはできません。  
  
 プロシージャ内で、またはモジュール、クラスまたは構造体の宣言セクションに定数を宣言します。 クラスまたは構造体レベルの定数が`Private`既定としても宣言することがありますが、 `Public`、 `Friend`、 `Protected`、または`Protected Friend`適切なレベルのコード アクセスします。  
  
 定数は、(、規則は、同じ変数名を作成するためのものとして) 有効なシンボリック名および数値または文字列定数、演算子、(関数の呼び出しはありません) を組み合わせた式が必要です。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-declare-a-constant"></a>定数を宣言するには  
  
-   アクセス指定子を含む宣言を記述、`Const`キーワード、および次の例のように、式。  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     ときに[Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)は`Off`と[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)は`On`、データ型を指定することによって、定数を明示的に宣言する必要があります (`Boolean`、 `Byte`、 `Char`、 `DateTime`、 `Decimal`、 `Double`、 `Integer`、 `Long`、 `Short`、 `Single`、または`String`)。  
  
     ときに`Option Infer`は`On`または`Option Strict`は`Off`を持つデータ型を指定せずに定数を宣言することができます、`As`句。 コンパイラでは、定数式の型からの型を決定します。 詳細については、次を参照してください。[定数とリテラルのデータ型](constant-and-literal-data-types.md)です。  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>明示的に指定されたデータ型を持つ定数を宣言するのには  
  
-   含む宣言を記述、`As`次の例のように、キーワードと明示的なデータを入力します。  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     コードが読みやすく 1 行につき 1 つの定数のみを宣言する場合は、単一行で複数の定数を宣言できます。 1 行に複数の定数を宣言する場合、すべて必要があります、同じアクセス レベル (`Public`、 `Private`、 `Friend`、 `Protected`、または`Protected Friend`)。  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>1 行に複数の定数を宣言するには  
  
-   コンマと空白に次の例のように、宣言に分割します。  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [定数とリテラルのデータ型](constant-and-literal-data-types.md)  
 [定数の概要](constants-overview.md)[する方法: 定数を宣言](how-to-declare-a-constant.md)[ユーザー定義定数](user-defined-constants.md)[定数とリテラルのデータ型](constant-and-literal-data-types.md)[する方法: グループ関連する定数値を一緒に](how-to-group-related-constant-values-together.md)[列挙型の概要](enumerations-overview.md)[する方法: 列挙型を宣言](how-to-declare-enumerations.md)[する方法: 列挙体のメンバーを参照してください](how-to-refer-to-an-enumeration-member.md)[列挙型と名前修飾](enumerations-and-name-qualification.md)[する方法: 列挙型を反復](how-to-iterate-through-an-enumeration.md)[する方法: 列挙値に関連付けられている文字列を確認する](how-to-determine-the-string-associated-with-an-enumeration-value.md)[列挙体を使用する場合](when-to-use-an-enumeration.md)

 [列挙型の概要](enumerations-overview.md)  
 [定数の概要](constants-overview.md)  
 [方法: 列挙型を宣言](how-to-declare-enumerations.md)  
 [列挙型と名前の修飾](enumerations-and-name-qualification.md)  
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
