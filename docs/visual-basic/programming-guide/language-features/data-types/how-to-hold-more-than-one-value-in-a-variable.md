---
title: "How to: Hold More Than One Value in a Variable (Visual Basic) | Microsoft Docs"
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
  - "classes [Visual Basic], composite data types"
  - "composite types"
  - "composite data types"
  - "data types [Visual Basic], composite"
  - "arrays [Visual Basic], composite data types"
  - "structures, composite data types"
  - "arrays [Visual Basic], compilation errors"
  - "types [Visual Basic], composite"
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Hold More Than One Value in a Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数を*複合データ型*として宣言すると、変数は複数の値を保持します。  
  
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) には、構造体、配列、およびクラスが含まれます。  複合データ型の変数は、基本データ型とその他の複合型を組み合わせて保持できます。  構造体とクラスは、データだけでなくコードも保持できます。  
  
### 変数内で複数の値を保持するには  
  
1.  変数で使用する複合データ型を決定します。  
  
2.  複合データ型がまだ定義されていない場合は、それを定義して変数で使用できるようにします。  
  
    -   [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md) を使用して構造体を宣言します。  
  
    -   [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) を使用して配列を定義します。  
  
    -   [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) を使用してクラスを定義します。  
  
3.  `Dim` ステートメントを使用して変数を宣言します。  
  
4.  変数名の後に `As` 句を指定します。  
  
5.  `As` キーワードの後ろに、適切な複合データ型の名前を指定します。  
  
## 参照  
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)