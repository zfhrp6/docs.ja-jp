---
title: 拡大変換と縮小変換 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 960b4e4c7184309b6a84247d86fb94ccb2faf877
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>拡大変換と縮小変換 (Visual Basic)
型変換で重要な考慮事項は、変換の結果が対象のデータ型の範囲内かどうかです。  
  
 A*拡大変換*元のデータのすべての値のことが許可されるデータ型に値を変更します。  拡大変換では、元の値を保持するが、その表現を変更できます。 これから整数型に変換する場合に発生`Decimal`、またはから`Char`に`String`です。  
  
 *縮小変換* により、有効値の一部を保持できない可能性のあるデータ型に値が変更されます。 たとえば、小数部の値は、整数型、および変換される数値型に変換されるときに丸められます`Boolean`がいずれかに縮小された`True`または`False`です。  
  
## <a name="widening-conversions"></a>拡大変換  
 次の表は、標準の拡大変換を示します。  
  
|データの種類|データ型に拡大変換<sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single`、`Double`|  
|[Short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|いずれかの列挙型 ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|基になる整数型と任意の型を基になる型が拡大変換されます。|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char` 配列|`Char` 配列、 `String`|  
|任意の型|[オブジェクト](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|すべての派生型|任意の派生元となる型の基本<sup>3</sup>です。|  
|任意の型|任意のインターフェイスを実装します。|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|任意のデータ型またはオブジェクトの種類。|  
  
 <sup>1</sup>定義では、すべてのデータ型は自動的に拡大します。  
  
 <sup>2</sup>から変換`Integer`、 `UInteger`、 `Long`、 `ULong`、または`Decimal`に`Single`または`Double`大きさが失われることはありませんが、精度が失われる可能性があります。 この意味でこれらが発生しない情報が失われる。  
  
 <sup>3</sup>派生型からその基本型のいずれかへの変換を拡大することにより意外かもしれません。 理由は、基本型のインスタンスと見なされるにように、派生型にはで、基本型のすべてのメンバーが含まれているです。 反対の方向に基本型では、派生型によって定義されたメンバーは含まれません。  
  
 拡大変換は実行時に常に成功して、データの損失が発生することはありません。 暗黙的に常に実行しているかどうか、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)チェックするスイッチの種類を設定`On`または`Off`です。  
  
## <a name="narrowing-conversions"></a>縮小変換  
 標準の縮小変換は次のとおりです。  
  
-   逆方向の拡大変換、上記のテーブル (する点を除いてすべての型は、自動的に拡大)  
  
-   どちらの方向との間で変換[ブール](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)と任意の数値型  
  
-   列挙型のいずれかの任意の数値型に変換 (`Enum`)  
  
-   どちらの方向との間で変換[文字列](../../../../visual-basic/language-reference/data-types/string-data-type.md)と任意の数値型`Boolean`、または[日付](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
-   それから派生した型に型またはオブジェクトのデータ型からの変換  
  
 縮小変換は常にではありません、実行時に成功し失敗したり、データの損失を伴うできます。 対象のデータ型が変換される値を受信できない場合は、エラーが発生します。 たとえば、数値の変換はオーバーフローになります。 コンパイラがしない限り、縮小変換を暗黙的に実行を許可していない、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)チェックするスイッチの種類を設定`Off`です。  
  
> [!NOTE]
>  内の要素からの変換の縮小変換エラーは出力されず、`For Each…Next`ループ コントロール変数のコレクション。 詳細と例については、「縮小変換」セクションを参照して[ごとにしています.次のステートメントの](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)します。  
  
### <a name="when-to-use-narrowing-conversions"></a>縮小変換を使用する場合  
 元の値は、エラーやデータ損失なし、移行先のデータ型に変換できることがわかっている場合に、縮小変換を使用します。 ある場合など、`String`がわかっている"True"または"False"を含む、行うこともできます、`CBool`に変換するキーワード`Boolean`です。  
  
## <a name="exceptions-during-conversion"></a>変換中に例外  
 拡大変換は常に、成功しますが、例外をスローしないでください。 縮小変換、失敗した場合は、最もよく、次の例外をスローします。  
  
-   <xref:System.InvalidCastException> -次の 2 つの型の間で変換が定義されていない場合  
  
-   <xref:System.OverflowException> — (整数型のみ) 指定した型の変換後の値が大きすぎる場合  
  
 クラスまたは構造体が定義されている場合、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)そのクラスまたは構造体、または変換演算子として使用するを`CType`適切と見なされるすべての例外をスローすることができます。 さらを`CType`Visual Basic の関数を呼び出すことがありますまたは[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]メソッドで、さらに、さまざまな例外をスローする可能性があります。  
  
## <a name="changes-during-reference-type-conversions"></a>参照型の変換中の変更  
 変換、*型参照*ポインターだけが、値をコピーします。 値そのものがコピーも、任意の方法で変更します。 変更可能な唯一の機能は、ポインターを保持する変数のデータ型です。 次の例では、その基本クラスに、派生クラスからデータ型が変換されますが、両方の変数をポイントするようになりましたオブジェクトは変更されません。  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>関連項目  
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [文字列とその他の型との変換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [方法: オブジェクトを Visual Basic での別の型に変換](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [配列変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
