---
title: "Widening and Narrowing Conversions (Visual Basic) | Microsoft Docs"
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
  - "widening conversions"
  - "narrowing conversions"
  - "conversions, type"
  - "data types [Visual Basic], changing"
  - "variables [Visual Basic], changing data type"
  - "conversions, exceptions during conversion"
  - "type conversion, exceptions during conversion"
  - "conversions, data type"
  - "conversions, narrowing"
  - "type conversion, narrowing"
  - "data type conversion, widening"
  - "data type conversion, narrowing"
  - "changing data types"
  - "type conversion, widening"
  - "data type conversion, exceptions during conversion"
  - "conversions, widening"
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
caps.latest.revision: 27
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 27
---
# Widening and Narrowing Conversions (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

型変換で考慮しなければならない重要な点は、変換結果が変換先データ型の範囲内に入るかどうかということです。  
  
 *拡大変換では* 変換元のデータの各値を可能にするデータ型に変更します。  拡大変換では、元の値は保持されますが、その表現は変化する場合があります。  これは整数型から `Decimal` に変換する場合は`Char` から `String` に発生します。  
  
 *縮小変換*では、値の一部を保持できない可能性があるデータ型に変更されます。  たとえば小数値は整数型に変換される`Boolean` 数値型はに変換されると `True` かになります `False` とはどちらも。  
  
## 拡大変換  
 次の表は、標準の拡大変換を示しています。  
  
|||  
|-|-|  
|データ型|拡大変換後のデータ型 <sup>1</sup>|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[整数型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double` <sup>2</sup>|  
|[Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double` <sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double` <sup>2</sup>|  
|[10 進数](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double` <sup>2</sup>|  
|[Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|すべての列挙型 \([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)\)|その基になる整数型や基になる型に相当する型。|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char` 配列|`Char` 配列、`String`|  
|任意の型|[Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|すべての派生型|派生元の基本 <sup>3</sup> 型。|  
|任意の型|このインターフェイスを実装します。|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|データ型またはオブジェクト型。|  
  
 <sup>1</sup> 定義上、すべてのデータ型は自動的に拡大されます。  
  
 <sup>2</sup> `Integer`、`UInteger`、`Long`、`ULong`、または `Decimal` から `Single` または `Double` への変換は、精度が失われる結果となる可能性がありますが、桁数が失われることはありません。  この意味で考えると、情報の損失は起こりません。  
  
 <sup>3</sup> 派生型からその基本型への変換は拡大変換になります。  派生型には基本型のすべてのメンバーが含まれるため、基本型のインスタンスとして扱うことができるためです。  逆に、基本型では派生型で定義されたメンバーが含まれていません。  
  
 拡大変換は、実行時には常に正常に行われ、データ消失が発生することはありません。  [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)で型チェック スイッチを `On` または `Off` に設定して、拡大変換を常に暗黙的に実行できます。  
  
## 縮小変換  
 標準の縮小変換は次のとおりです。  
  
-   前の表で示した拡大変換の逆方向 \(それ自体に拡大変換する場合の型を除く\)  
  
-   ブール型 \([Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)\) と任意の数値型の間の相互変換  
  
-   任意の数値型から任意の列挙型への変換 \(`Enum`\)  
  
-   [文字列型](../../../../visual-basic/language-reference/data-types/string-data-type.md)と、任意の数値型、`Boolean`、または[日付型](../../../../visual-basic/language-reference/data-types/date-data-type.md)の間の相互変換  
  
-   データ型またはオブジェクト型の、その派生型への変換  
  
 縮小変換は、実行時に常に正しく実行されるとは限りません。したがって失敗またはデータを消失する可能性があります。  変換先のデータ型で変換対象の値を受け入れることができない場合に、エラーが発生します。  たとえば、数値変換ではオーバーフローが発生することがあります。  コンパイラは、[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)で型チェック スイッチが `Off` に設定されていない限り、暗黙的な縮小変換の実行を許可しません。  
  
> [!NOTE]
>  `For Each…Next` コレクション内の要素からループ制御変数への変換に対して縮小変換エラーが抑制されます。  詳細および例については、「[For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)」の「縮小変換」セクションを参照してください。  
  
### 縮小変換を使用するタイミング  
 変換元の値を変換先のデータ型に変換でき、エラーまたはデータの消失が発生しないことがわかっている場合に、縮小変換を使用します。  たとえば含む 「 true 」または 「 false を `String` がわかっている場合は」`Boolean` に変換するために `CBool` のキーワードを使用します。  
  
## 変換中の例外  
 拡大変換は常に正しく実行されるため、例外をスローすることはありません。  縮小変換が失敗すると、通常は次の例外をスローします。  
  
-   <xref:System.InvalidCastException> — 2 つの型の間で変換が定義されていない場合  
  
-   <xref:System.OverflowException> — \(整数型の場合のみ\) 変換された値が対象の型にしては大きすぎる場合  
  
 クラスまたは構造体で [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)を定義して、そのクラスまたは構造体の間の変換演算子として機能させると、その `CType` は適切と見なされる例外をスローできます。  さらに、その `CType` は [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 関数または [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] メソッドを呼び出して、さまざまな例外を順番にスローできます。  
  
## 参照型変換での変化  
 *参照型*からの変換では、値へのポインターだけがコピーされます。  値自体のコピーや変更は行われません。  変化する可能性があるのは、ポインターを保持する変数のデータ型だけです。  次の例では、データ型が派生クラスから基本クラスに変換されますが、両方の変数が指すことになるオブジェクトは変化しません。  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## 参照  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [Implicit and Explicit Conversions](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [Conversions Between Strings and Other Types](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Type Conversion Functions](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)