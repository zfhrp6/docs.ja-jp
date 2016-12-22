---
title: "How to: Declare A Constant (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.constant"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Integer data type, declaring constants"
  - "Single data type, declaring constants"
  - "Const statement [Visual Basic], declaring constants"
  - "procedures, declaration"
  - "data types [Visual Basic], constants"
  - "Long data type, declaring constants"
  - "Visual Basic code, declaring variables and constants"
  - "Double data type, declaring constants"
  - "Boolean data type, declaring constants"
  - "modules, declaring constants"
  - "Byte data type, declaring constants"
  - "constants, declaring"
  - "Date data type, declaring constants"
  - "String data type, declaring constants"
  - "declaring constants, const keyword"
  - "Currency data type, declaring constants and variants"
  - "module-level constants and variables"
  - "Object data type, declaring constants"
ms.assetid: f901b4fa-481f-4621-822e-427060577ad1
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Declare A Constant (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

定数を宣言して値を設定するには、`Const` ステートメントを使います。  定数を宣言すると、値にわかりやすい名前を割り当てることができます。  一度宣言した定数は、変更したり新しい値を代入したりはできません。  
  
 定数は、プロシージャ内で宣言するか、モジュール、クラス、または構造体の宣言セクションで宣言します。  クラスまたは構造体のレベルの定数は、既定では `Private` ですが、コード アクセスの必要なレベルに応じて `Public`、`Friend`、`Protected`、または `Protected Friend` として宣言することもできます。  
  
 定数には、有効なシンボル名 \(変数の名前付け規則と同じ規則に従う\)、および数値や文字列の定数と演算子とを組み合わせた式を指定する必要があります。関数呼び出しを含むことはできません。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### 定数を宣言するには  
  
-   次の例に示すように、アクセス指定子、`Const` キーワード、および式を含む宣言を記述します。  
  
     [!code-vb[VbEnumsTask#8](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_1.vb)]  
  
     [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) が `Off` で [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) が `On` である場合、明示的にデータ型 \(`Boolean`、`Byte`、`Char`、`DateTime`、`Decimal`、`Double`、`Integer`、`Long`、`Short`、`Single` または `String`\) を指定して定数を宣言する必要があります。  
  
     `Option Infer` が `On`、または `Option Strict` が `Off` である場合、`As` 句でデータ型を指定せずに定数を宣言する必要があります。  コンパイラにより、式の種類から定数の型が決定されます。  詳細については、「[Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)」を参照してください。  
  
### 明示的に指定されたデータ型を持つ定数を宣言するには  
  
-   次の例に示すように、`As` キーワードおよび明示的なデータ型が含まれる宣言を記述します。  
  
     [!code-vb[VbEnumsTask#9](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-a-constant_2.vb)]  
  
     複数の定数を 1 行で宣言することもできますが、1 行で宣言する定数は 1 つだけにした方がコードが読みやすくなります。  1 行で複数の定数を宣言した場合、すべてが同じアクセス レベル \(`Public`、`Private`、`Friend`、`Protected`、または `Protected Friend`\) を持っている必要があります。  
  
### 複数の定数を 1 行で宣言するには  
  
-   次の例に示すように、宣言をコンマと空白で区切ります。  
  
    ```  
    Public Const Four As Integer = 4, Five As Integer = 5, Six As Integer = 44  
    ```  
  
## 参照  
 [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)   
 [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constants and Enumerations](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)   
 [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)   
 [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)