---
title: "Value Types and Reference Types | Microsoft Docs"
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
  - "reference data types"
  - "reference types"
  - "value types"
  - "value data types"
  - "types [Visual Basic]"
  - "data types [Visual Basic], value types"
  - "data types [Visual Basic], reference types"
ms.assetid: fc82ce15-5a40-4c5c-a1e1-a556830e7391
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Value Types and Reference Types
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic ではデータ型がクラスに基づいて実行されます。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のデータ型は、その型の変数にデータそのものが格納されるのか、それともデータへのポインターが格納されるのかによって分類されます。  データそのものが格納される場合は*値型*、メモリのどこか別の場所にあるデータへのポインターを格納する場合は*参照型*になります。  
  
## 値型  
 データ型が自身のメモリ内にデータを保持する場合、そのデータ型は*値型*です。  値型には、次のようなものがあります。  
  
-   すべての数値データ型  
  
-   `Boolean`、`Char`、および `Date`  
  
-   すべての構造体 \(メンバーが参照型の場合でも\)  
  
-   列挙型 \(基になる型が常に `SByte`、`Short`、`Integer`、`Long`、`Byte`、`UShort`、`UInteger`、または `ULong` であるため\)  
  
 すべての構造体は参照型のメンバーを持っていても値型です。  したがって`Char` などの値型と `Integer` は.NET Framework の構造体によって実装されます。  
  
 値型は、`Decimal` などの予約済みのキーワードを使用して宣言できます。  値型を初期化するときにも `New` キーワードを使用できます。  これは、その型にパラメーターをとるコンストラクターがある場合に特に有効です。  これに関する例は、指定した部分から新しい `Decimal` 値を作成する、<xref:System.Decimal.%23ctor%28System.Int32%2CSystem.Int32%2CSystem.Int32%2CSystem.Boolean%2CSystem.Byte%29> コンストラクターです。  
  
## 参照型  
 *参照型*には、データを保持する別のメモリ位置へのポインターが格納されます。  参照型には、次のようなものがあります。  
  
-   `String`  
  
-   すべての配列 \(要素が値型の場合でも\)  
  
-   クラス型 \(<xref:System.Windows.Forms.Form> など\)  
  
-   デリゲート  
  
 クラスは*参照型*です。  このため、`Object` や `String` などの参照型は、[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] クラスによってサポートされます。  メンバーが値型であっても、配列はすべて参照型です。  
  
 すべての参照型は基になる .NET Framework のクラスを表すため初期化と [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) のキーワードを使用する必要があります。  次のステートメントで配列を初期化します。  
  
```  
Dim totals() As Single = New Single(8) {}  
```  
  
## 型ではない要素  
 次のプログラミング要素は、宣言された要素のデータ型として指定できないため、型として修飾しません。  
  
-   名前空間  
  
-   モジュール  
  
-   イベント  
  
-   プロパティおよびプロシージャ  
  
-   変数、定数およびフィールド  
  
## オブジェクトのデータ型の操作  
 `オブジェクト型 (Object)` の変数には参照型と値型のどちらでも代入できます。  `オブジェクト型 (Object)` の変数は常にデータそのものではなくデータへのポインターを保持します。  ただし、`オブジェクト型 (Object)` の変数に値型を代入すると、独自のデータを保持しているように動作します。  詳細については、「[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)」を参照してください。  
  
 `Object` の変数が参照型または値型として <xref:Microsoft.VisualBasic?displayProperty=fullName> の名前空間の <xref:Microsoft.VisualBasic.Information> クラスの <xref:Microsoft.VisualBasic.Information.IsReference%2A> のメソッドに渡して動作しているかを調べることができます。  `Object` 変数の内容が参照型を表している場合、<xref:Microsoft.VisualBasic.Information.IsReference%2A?displayProperty=fullName> は `True` を返します。  
  
## 参照  
 [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Efficient Use of Data Types](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)   
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)   
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)