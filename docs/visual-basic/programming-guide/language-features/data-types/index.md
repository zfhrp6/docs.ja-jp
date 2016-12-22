---
title: "Visual Basic におけるデータ型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "データ型 [Visual Basic]、宣言"
  - "型指定"
  - "データ型 [Visual Basic]"
  - "Visual Basic コード、データ型"
  - "データ型 [Visual Basic]、向上 (速度を)"
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
caps.latest.revision: 28
caps.handback.revision: 28
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Visual Basic におけるデータ型
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

プログラミング要素の*データ型*は、保持できるデータの種類やデータの格納方法を示します。  データ型は、コンピューターのメモリに格納できるすべての値に適用され、式の評価にも関与します。  変数、リテラル、定数、列挙値、プロパティ、プロシージャのパラメーター、プロシージャの引数、およびプロシージャの戻り値にはすべてデータ型があります。  
  
## データ型の宣言  
 プログラミング要素は宣言ステートメントで定義し、`As` 句を使用してデータ型を指定します。  さまざまな要素の宣言に使用するステートメントを次の表に示します。  
  
|プログラミング要素|データ型の宣言|  
|---------------|-------------|  
|変数|[Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) 内で宣言<br /><br /> `Dim`   `amount As Double`<br /><br /> `Static`   `yourName As String`<br /><br /> `Public`   `billsPaid As Decimal = 0`|  
|Literal|リテラルの型宣言文字を使用する場合は、「[Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)」の「リテラルの型文字」を参照してください。<br /><br /> `Dim searchChar As Char = "."`  `C`|  
|定数|[Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) 内で宣言<br /><br /> `Const`   `modulus As Single = 4.17825F`|  
|列挙型|[Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md) 内で宣言<br /><br /> `Public`   `Enum`   `colors`|  
|プロパティ|[Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) 内で宣言<br /><br /> `Property`   `region() As String`|  
|プロシージャ パラメーター|[Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md)、[Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md)、または [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)内で宣言<br /><br /> `Sub addSale(ByVal`   `amount`   `As Double)`|  
|プロシージャの引数|呼び出し元のコードでは、宣言済みのプログラミング要素、または宣言済みの要素を含む式を各引数に指定<br /><br /> `subString = Left(`  `inputString`  `,`   `5`  `)`|  
|プロシージャの戻り値|[Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) または [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)内で宣言<br /><br /> `Function convert(ByVal b As Byte)`   `As String`|  
  
 Visual Basic のデータ型の一覧については、[Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)を参照してください。  
  
## 参照  
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Efficient Use of Data Types](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)