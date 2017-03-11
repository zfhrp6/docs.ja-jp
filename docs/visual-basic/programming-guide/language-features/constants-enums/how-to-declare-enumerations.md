---
title: "How to: Declare Enumerations (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declarations, enumerations"
  - "enumerations [Visual Basic], declaring"
  - "declaring enumerations"
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# How to: Declare Enumerations (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

列挙型を作成するには、クラスまたはモジュールの宣言セクションで `Enum` ステートメントを使います。  列挙型をメソッド内で宣言することはできません。  適切なレベルのアクセスを指定するには、`Private`、`Protected`、`Friend`、または `Public` を使用します。  
  
 `Enum` 型には、名前、基になる型、およびフィールドのセットがあり、各フィールドは定数を表します。  名前は、有効な [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] 修飾子である必要があります。  基になる型は、`Byte`、`Short`、`Long` または `Integer` の整数型のいずれかである必要があります。  `Integer` が既定値です。  列挙型は常に厳密に型指定され、整数の数値型と互いに置き換えることはできません。  
  
 列挙型は、浮動小数点値を持つことはできません。  `Option Strict On` を使用して、列挙型に浮動小数点値を代入すると、コンパイラ エラーになります。  `Option Strict` が `Off` である場合、値が自動的に `Enum` 型に変換されます。  
  
 名前について、および `Imports` ステートメントを使用して名前の修飾をしなくて済む方法については、「[Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)」を参照してください。  
  
### 列挙型を宣言するには  
  
1.  それぞれで異なる `Enum` が宣言されている次のコード例のように、コード アクセス レベル、`Enum` キーワード、および有効な名前が含まれる宣言を記述します。  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#3)]  
  
2.  列挙型で定数を定義します。  既定では、列挙型の中の最初の定数は `0` に初期化され、それに続く定数は、それぞれ前の定数に 1 を加えた値に初期化されます。  たとえば、次の列挙型 `Days` では、`Sunday` の値は `0`、`Monday` の値は `1`、`Tuesday` の値は `2` になります。  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#4)]  
  
3.  代入ステートメントを使うと、列挙型の中の定数に明示的に値を代入できます。  定数には、負の数を含む任意の整数値を代入できます。  たとえば、エラーの状況を表すために、0 よりも小さな値の定数を使うことができます。  次の列挙型では、定数 `Invalid` に値 `–1` が明示的に代入されます。また、定数 `Sunday` に、値 `0` が代入されます。  これは列挙型の最初の定数であるため、`Saturday` も値 `0` に初期化されます。  `Monday` の値は `1` です \(`Sunday` の値よりも 1 つ多い\)。また、`Tuesday` の値は `2`、のように続きます。  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#5)]  
  
### 列挙型を明示的な型として宣言するには  
  
-   次の例に示すように、`As` 句を使用して列挙型を指定します。  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/WindowsApplication1/Class2.vb#6)]  
  
## 参照  
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)   
 [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)