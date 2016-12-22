---
title: "Implicit and Explicit Conversions (Visual Basic) | Microsoft Docs"
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
  - "conversions, type"
  - "variables [Visual Basic], changing data type"
  - "casting"
  - "conversions, data type"
  - "type conversion, implicit conversions"
  - "CType function, conversions"
  - "casting, data types"
  - "data type conversion, explicit"
  - "type conversion, explicit conversions"
  - "data types [Visual Basic], casting"
  - "conversions, implicit"
  - "explicit data type conversions"
  - "conversions"
  - "changing data types"
  - "conversions, explicit"
  - "data type conversion, implicit"
  - "implicit data type conversions"
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Implicit and Explicit Conversions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

*暗黙の型変換*では、ソース コードに特殊な構文は不要です。  次の例では、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は、`k` の値を暗黙的に単精度の浮動小数点値に変換してから `q` に代入しています。  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 *明示的な型変換*では、型変換キーワードを使用します。  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] には、このようなキーワードが複数用意されており、かっこ内に指定した式を目的のデータ型に変換できます。  これらのキーワードは関数のように動作しますが、コンパイラによってコード インラインが生成されるため、実行速度は関数呼び出しよりも多少速くなります。  
  
 次に示すのは上の例の続きですが、`CInt` キーワードによって `q` の値を整数に変換してから、`k` に代入しています。  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## 型変換のキーワード  
 次の表は、使用できる変換キーワードを示しています。  
  
||||  
|-|-|-|  
|型変換キーワード|変換後のデータ型|変換できる式のデータ型|  
|`CBool`|[Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|すべての数値型 \(`Byte`、`SByte`、および列挙型を含む\)、`String`、`Object`|  
|`CByte`|[Byte Data Type](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|すべての数値型 \(`SByte` および列挙型を含む\)、`Boolean`、`String`、`Object`|  
|`CChar`|[Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|  
|`CDate`|[Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|  
|`CDbl`|[Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md)|すべての数値型 \(`Byte`、`SByte`、および列挙型を含む\)、`Boolean`、`String`、`Object`|  
|`CDec`|[Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|すべての数値型 \(`Byte`、`SByte`、および列挙型を含む\)、`Boolean`、`String`、`Object`|  
|`CInt`|[Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|すべての数値型 \(`Byte`、`SByte`、および列挙型を含む\)、`Boolean`、`String`、`Object`|  
|`CLng`|[Long Data Type](../../../../visual-basic/language-reference/data-types/long-data-type.md)|すべての数値型 \(`Byte`、`SByte`、および列挙型を含む\)、`Boolean`、`String`、`Object`|  
|`CObj`|[Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)|任意の型|  
|`CSByte`|[SByte Data Type](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|すべての数値型 \(`Byte` および列挙型を含む\)、`Boolean`、`String`、`Object`|  
|`CShort`|[Short Data Type](../../../../visual-basic/language-reference/data-types/short-data-type.md)|すべての数値型 \(`Byte`、`SByte`、および列挙型を含む\)、`Boolean`、`String`、`Object`|  
|`CSng`|[Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md)|すべての数値型 \(`Byte`、`SByte`、および列挙型を含む\)、`Boolean`、`String`、`Object`|  
|`CStr`|[String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md)|すべての数値型 \(`Byte`、`SByte`、および列挙型を含む\)、`Boolean`、`Char`、`Char` 配列、`Date`、`Object`|  
|`CType`|コンマ \(`,`\) の後に指定する型|*基本データ型* \(基本型の配列を含む\) に変換する場合は、対応する変換キーワードで使用できるのと同じ型。<br /><br /> *複合データ型*に変換する場合は、それが実装するインターフェイス、およびそれが継承するクラス。<br /><br /> `CType` をオーバーロードしたクラスまたは構造体に変換する場合は、そのクラスまたは構造体|  
|`CUInt`|[UInteger Data Type](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|すべての数値型 \(`Byte`、`SByte`、および列挙型を含む\)、`Boolean`、`String`、`Object`|  
|`CULng`|[ULong Data Type](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|すべての数値型 \(`Byte`、`SByte`、および列挙型を含む\)、`Boolean`、`String`、`Object`|  
|`CUShort`|[UShort Data Type](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|すべての数値型 \(`Byte`、`SByte`、および列挙型を含む\)、`Boolean`、`String`、`Object`|  
  
## CType 関数  
 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md) は 2 つの引数について実行されます。  最初の引数は変換対象の式であり、2 番目の引数は変換先のデータ型またはオブジェクト クラスです。  最初の引数は、型ではなく、式である必要があることに注意してください。  
  
 `CType` は*インライン関数*です。つまり、変換を行うコードはコンパイルによって生成されます。多くの場合、このコードに関数呼び出しは含まれていません。  これにより、パフォーマンスが向上します。  
  
 `CType` とその他の型変換キーワードとの比較については、「[DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md)」および「[TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md)」を参照してください。  
  
### 基本型  
 次の例は `CType` の使い方を示しています。  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### 複合型  
 `CType` を使用して、値を複合データ型および基本型に変換できます。  また、次の例のように、オブジェクト クラスをそのインターフェイスの型に強制的に変換することもできます。  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### 配列型  
 `CType` は、次の例のように配列データ型を変換することもできます。  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 詳細および使用例については、「[Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)」を参照してください。  
  
### CType を定義する型  
 独自に定義したクラスや構造体に対して `CType` を定義できます。  これによって、独自のクラスや構造体の型と別の型の間で値を相互に変換できます。  詳細および使用例については、「[How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)」を参照してください。  
  
> [!NOTE]
>  変換キーワードと共に使用する値は、変換先のデータ型において有効な値である必要があります。有効でない場合はエラーが発生します。  たとえば、長**整数型 \(**`Long`**\)** を**整数型 \(**`Integer`**\)** に変換する場合は、その長**整数型 \(**`Long`**\)** の値が**整数型 \(**`Integer`**\)** の有効範囲内に含まれている必要があります。  
  
> [!CAUTION]
>  あるクラス型から別のクラス型に変換する `CType` を指定する場合、変換先の型が変換元の型から派生した型でなければ、実行時に失敗します。  そのようなエラーが発生すると、<xref:System.InvalidCastException> 例外がスローされます。  
  
 ただし、型の一方が独自に定義した構造体またはクラスであり、その構造体またはクラスに `CType` が定義してある場合、この `CType` の要件を満たしていれば変換は正常に実行されます。  [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md) を参照してください。  
  
 明示的な型変換は、ある式から指定のデータ型またはオブジェクト クラスへの*キャスト*とも呼ばれます。  
  
## 参照  
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)