---
title: "When to Use an Enumeration (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "enumerations [Visual Basic]"
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# When to Use an Enumeration (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

列挙型を使用すると、関連する定数のセットを扱うのが簡単になります。  列挙型 \(`Enum`\) は、値のセットを表すシンボル名です。  列挙型はデータ型として扱われ、これを使用して変数およびプロパティで使用する定数のセットを作成できます。  
  
## 列挙型を使用する状況  
 限定された変数のセットをプロシージャが受け取ったときは、列挙型を使用してください。  特に意味のある名前が使用されている場合は、列挙型によってわかりやすく読みやすいコードになります。  
  
 列挙型を使用する利点は、次のとおりです。  
  
-   数値の置き換えやタイプミスによるエラーが減少する  
  
-   将来、値を変更しやすい  
  
-   コードが読みやすくなり、エラーが発生しにくくなる  
  
-   上位互換性が確保できる  列挙型を使用すると、メンバーの名前に対応する値を将来だれかが変更した場合、コードがエラーになる可能性が低くなります。  
  
## 列挙型の名前付け  
 列挙型メンバーの名前付け規則を使用します。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] によって列挙型のメンバー名が検出されると、他の参照される型のライブラリに同じ名前が含まれている場合、例外がスローされることがあります。  アプリケーションまたはコンポーネントの値を識別する一意のプレフィックスを使用します。  
  
 列挙型のメンバーを参照するとき、列挙型の名前でメンバー名を修飾するか、または `Imports` ステートメントを使用する必要があります。  詳細については、「[Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)」を参照してください。  
  
## 定義済み列挙型  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] には、コードの記述を簡単にするために、`FirstDayOfWeek`、`MsgBoxResul`t などの、いくつかの定義済み列挙型が用意されています。  これらの一覧については、「[Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)」を参照してください。  
  
## 参照  
 [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [How to: Iterate Through An Enumeration in Visual Basic](../Topic/How%20to:%20Iterate%20Through%20An%20Enumeration%20in%20Visual%20Basic.md)   
 [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)