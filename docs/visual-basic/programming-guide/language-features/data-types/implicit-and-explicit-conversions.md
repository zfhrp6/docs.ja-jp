---
title: 暗黙の型変換と明示的な型変換 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9827cecce0a15d37d2ffe3ccf691404149b156fb
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>暗黙の型変換と明示的な型変換 (Visual Basic)
*暗黙的な変換*特別な構文のソース コードでは必要ありません。 次の例では、Visual Basic に暗黙的の値を変換`k`単精度浮動小数点値を割り当てる前に`q`です。  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 *明示的な変換*型の変換キーワードを使用します。 Visual Basic では、いくつかそのようなキーワード、目的のデータ型をかっこで指定した式変換を提供します。 関数と同様、これらのキーワードの動作が、コンパイラは、実行は、関数呼び出しよりもわずかに高速に、コード インラインを生成します。  
  
 前の例では、次の拡張機能に、`CInt`キーワードの値を変換する`q`に割り当てる前に整数に戻す`k`です。  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a>変換キーワード  
 次の表は、使用可能な変換のキーワードを示します。  
  
|型変換キーワード|データ型の式に変換します。|変換する式のデータ型|  
|---|---|---|  
|`CBool`|[Boolean データ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `String`、 `Object`|  
|`CByte`|[Byte データ型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|任意の数値型 (など`SByte`および列挙型)、 `Boolean`、 `String`、 `Object`|  
|`CChar`|[Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|  
|`CDate`|[Date データ型](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|  
|`CDbl`|[Double 型](../../../../visual-basic/language-reference/data-types/double-data-type.md)|任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、 `Object`|  
|`CDec`|[Decimal データ型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、 `Object`|  
|`CInt`|[整数データ型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、 `Object`|  
|`CLng`|[Long データ型](../../../../visual-basic/language-reference/data-types/long-data-type.md)|任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、 `Object`|  
|`CObj`|[Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)|任意の型|  
|`CSByte`|[SByte データ型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|任意の数値型 (など`Byte`および列挙型)、 `Boolean`、 `String`、 `Object`|  
|`CShort`|[Short データ型](../../../../visual-basic/language-reference/data-types/short-data-type.md)|任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、 `Object`|  
|`CSng`|[Single データ型](../../../../visual-basic/language-reference/data-types/single-data-type.md)|任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、 `Object`|  
|`CStr`|[String データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)|任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `Char`、`Char`配列、 `Date`、 `Object`|  
|`CType`|コンマの後に指定された型 (`,`)|変換する際、*基本データ型*(基本型の配列を含む)、同じ種類として、対応する変換キーワードの許可<br /><br /> 変換する際、*複合データ型*、実装するインターフェイスとその継承元となるクラス<br /><br /> オーバー ロードしたクラスまたは構造体に変換するときに`CType`、そのクラスまたは構造体|  
|`CUInt`|[UInteger データ型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、 `Object`|  
|`CULng`|[ULong データ型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、 `Object`|  
|`CUShort`|[UShort データ型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|任意の数値型 (など`Byte`、 `SByte`、および列挙型)、 `Boolean`、 `String`、 `Object`|  
  
## <a name="the-ctype-function"></a>CType 関数  
 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)は 2 つの引数で動作します。 1 つは、変換する式、2 番目の変換先のデータ型またはオブジェクト クラス。 最初の引数は型ではなく、式である必要がありますに注意してください。  
  
 `CType` *インライン関数*変換は、コンパイルされたコードの意味、多くの場合、呼び出す関数は生成されません。 これにより、パフォーマンスが向上します。  
  
 比較について`CType`他の型変換のキーワードと、次を参照してください。 [DirectCast 演算子](../../../../visual-basic/language-reference/operators/directcast-operator.md)と[TryCast 演算子](../../../../visual-basic/language-reference/operators/trycast-operator.md)です。  
  
### <a name="elementary-types"></a>基本型  
 次の例は、`CType` の使い方を示しています。  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a>複合型  
 使用することができます`CType`値複合データ型および基本型に変換します。 また、次の例のように、そのインターフェイスのいずれかの型にオブジェクト クラスを強制的に使用することができます。  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a>配列型  
 `CType` 次の例のように、配列のデータ型を変換することもできます。  
  
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
  
 例および詳細については、次を参照してください。[配列変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)です。  
  
### <a name="types-defining-ctype"></a>CType を定義する型  
 定義できます`CType`クラスまたは定義した構造にします。 これにより、クラスまたは構造体の型との間の値を変換することができます。 例および詳細については、次を参照してください。[する方法: 変換演算子を定義する](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)です。  
  
> [!NOTE]
>  変換キーワードと共に使用される値を変換先データ型に対して有効にする必要があります。 またはエラーが発生します。 変換しようとする場合など、`Long`を`Integer`の値、`Long`の有効な範囲内である必要があります、`Integer`データ型。  
  
> [!CAUTION]
>  指定する`CType`ソースの種類が変換先の型から派生していない場合は、実行時に別の失敗を 1 つのクラス型から変換します。 このようなエラーをスロー、<xref:System.InvalidCastException>例外。  
  
 ただし、構造体またはクラスを定義した型の 1 つが、定義した場合`CType`その構造体またはクラスで、変換が成功する場合の要件を満たしていれば、`CType`です。 参照してください[する方法: 変換演算子を定義する](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)です。  
  
 明示的な変換を実行するとも呼ばれます*キャスト*指定されたデータ型またはオブジェクト クラスへの式。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [文字列とその他の型との変換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [方法: オブジェクトを Visual Basic での別の型に変換](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
