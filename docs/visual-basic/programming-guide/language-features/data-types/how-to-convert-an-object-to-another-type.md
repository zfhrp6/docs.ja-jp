---
title: "How to: Convert an Object to Another Type in Visual Basic | Microsoft Docs"
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
  - "objects [Visual Basic], converting"
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Convert an Object to Another Type in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`Object` 変数を他のデータ型に変換するには、[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md) などの変換キーワードを使用します。  
  
## 使用例  
 次に示すのは、`Object` 変数を `Integer` 型から `String` 型へ変換する例です。  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 `Object` 変数の内容が特定のデータ型であることがわかっている場合は、変数をそのデータ型に変換することをお勧めします。  `Object` 変数を使い続けると、*ボックス化*および*ボックス化解除* \(値型の場合\)、または*遅延バインディング* \(参照型の場合\) が行われます。  これらの操作はいずれも余分な実行時間を必要とするため、パフォーマンスが低下します。  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   <xref:System?displayProperty=fullName> 名前空間への参照  
  
## 参照  
 <xref:System.Object>   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)