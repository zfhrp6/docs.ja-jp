---
title: "方法: 定数 (Visual Basic) を宣言 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.constant
dev_langs:
- VB
helpviewer_keywords:
- Integer data type, declaring constants
- Single data type, declaring constants
- Const statement [Visual Basic], declaring constants
- procedures, declaration
- data types [Visual Basic], constants
- Long data type, declaring constants
- Visual Basic code, declaring variables and constants
- Double data type, declaring constants
- Boolean data type, declaring constants
- modules, declaring constants
- Byte data type, declaring constants
- constants, declaring
- Date data type, declaring constants
- String data type, declaring constants
- declaring constants, const keyword
- Currency data type, declaring constants and variants
- module-level constants and variables
- Object data type, declaring constants
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
caps.latest.revision: 20
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
ms.openlocfilehash: 401d0feb85fccf94a25308d38c3c75198ef9294c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-declare-a-constant-visual-basic"></a>方法: 定数を宣言する (Visual Basic)
使用する、`Const`定数を宣言し、その値を設定するステートメントです。 定数を宣言することでは、値をわかりやすい名前を割り当てます。 定数が宣言されると、変更または新しい値を代入することはできません。  
  
 プロシージャ内で、またはモジュール、クラスまたは構造体の宣言セクションに定数を宣言します。 クラスまたは構造のレベルの定数は、`Private`既定としても宣言することがありますが、 `Public`、 `Friend`、 `Protected`、または`Protected Friend`コードへのアクセスの適切なレベルとして。  
  
 定数は、(、規則は、同じ変数名を作成するためのものと)、有効なシンボリック名と数値または文字列定数、演算子、(関数を呼び出す) を組み合わせた式が必要です。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-declare-a-constant"></a>定数を宣言するには  
  
-   アクセス指定子を含む宣言を書き込む、`Const`キーワード、および次の例のように、式。  
  
     [!code-vb[VbEnumsTask&#8;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md)は`Off`と[Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)は`On`、データ型を指定して定数を明示的に宣言する必要があります (`Boolean`、 `Byte`、 `Char`、 `DateTime`、 `Decimal`、 `Double`、 `Integer`、 `Long`、 `Short`、 `Single`、または`String`)。  
  
     `Option Infer`は`On`または`Option Strict`は`Off`を持つデータ型を指定せずに定数を宣言することができます、`As`句。 コンパイラでは、式の型の定数の型を決定します。 詳細については、次を参照してください。[定数とリテラルのデータ型](constant-and-literal-data-types.md)します。  
  
### <a name="to-declare-a-constant-that-has-an-explicitly-stated-data-type"></a>明示的に定められたデータ型を持つ定数を宣言するのには  
  
-   含む宣言を書き込む、`As`次の例のように、キーワードと明示的なデータを入力します。  
  
     [!code-vb[VbEnumsTask&#9;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     コードが読みやすく&1; 行につき&1; つの定数のみを宣言する場合は、1 行に複数の定数を宣言できます。 1 行に複数の定数を宣言する場合が必要にすべて同じアクセス レベル (`Public`、 `Private`、 `Friend`、 `Protected`、または`Protected Friend`)。  
  
### <a name="to-declare-multiple-constants-on-a-single-line"></a>1 行に複数の定数を宣言するには  
  
-   宣言は、次の例のように、スペースとコンマで区切ってください。  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## <a name="see-also"></a>関連項目  
 [Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [定数とリテラルのデータ型](constant-and-literal-data-types.md)   
 [定数の概要](constants-overview.md)
 [方法: 定数を宣言](how-to-declare-a-constant.md)
 [ユーザー定義定数](user-defined-constants.md)
 [定数とリテラルのデータ型](constant-and-literal-data-types.md)
 [する方法: 関連する定数値をまとめてグループ](how-to-group-related-constant-values-together.md)
 [列挙型の概要](enumerations-overview.md)
 [する方法: 列挙型を宣言](how-to-declare-enumerations.md)
 [方法: 列挙型のメンバーを参照してください](how-to-refer-to-an-enumeration-member.md)
 [列挙型と名前修飾](enumerations-and-name-qualification.md)
 [する方法: 列挙型を反復](how-to-iterate-through-an-enumeration.md)
 [する方法: 文字列を確認します。列挙値に関連付けられている](how-to-determine-the-string-associated-with-an-enumeration-value.md)
 [列挙体を使用する場合](when-to-use-an-enumeration.md)

 [列挙型の概要](enumerations-overview.md)   
 [定数の概要](constants-overview.md)   
 [方法: 列挙型を宣言](how-to-declare-enumerations.md)   
 [列挙型と名前修飾](enumerations-and-name-qualification.md)   
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)

