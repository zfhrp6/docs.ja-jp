---
title: "拡大変換と縮小変換 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- widening conversions
- narrowing conversions
- conversions, type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions, exceptions during conversion
- type conversion, exceptions during conversion
- conversions, data type
- conversions, narrowing
- type conversion, narrowing
- data type conversion, widening
- data type conversion, narrowing
- changing data types
- type conversion, widening
- data type conversion, exceptions during conversion
- conversions, widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 88c5db6e7e82a88ae8015b581e5a795ec389d003
ms.lasthandoff: 03/13/2017

---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>拡大変換と縮小変換 (Visual Basic)
型変換で重要な考慮事項は、変換の結果が先のデータ型の範囲内かどうかです。  
  
 A*拡大変換*の元のデータのすべての値が許容されるデータ型に値を変更します。  拡大変換では、元の値を保持できますが、その表現を変更することができます。 これから整数型に変換する場合に発生`Decimal`、またはから`Char`に`String`します。  
  
 *縮小変換* により、有効値の一部を保持できない可能性のあるデータ型に値が変更されます。 たとえば、小数部の値は、整数型に変換する数値型を変換するときに丸められます`Boolean`がいずれかに減少`True`または`False`です。  
  
## <a name="widening-conversions"></a>拡大変換  
 次の表は、標準の上位変換を示します。  
  
|データ型|データ型に拡大変換<sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single`、`Double`|  
|[短い](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[整数](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[長い](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|いずれかの列挙型 ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|その基になる整数型と任意の型を基になる型が拡大します。|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char` 配列|`Char`配列、`String`|  
|任意の型|[オブジェクト](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|すべての派生型|いずれかの基本データ型の派生元である<sup>3</sup>します。|  
|任意の型|任意のインターフェイスを実装します。|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|任意のデータ型またはオブジェクトの種類。|  
  
 <sup>1</sup>定義では、すべてのデータ型は自動的に拡大します。  
  
 <sup>2</sup>から変換`Integer`、 `UInteger`、 `Long`、 `ULong`、または`Decimal`に`Single`または`Double`大きさが失われることはありませんが、精度が失われる可能性があります。 この意味は情報の損失は発生しません。  
  
 <sup>3</sup>派生型からその基本型のいずれかへの変換を広げることは驚くかもしれません。 理由は、派生型には、基本型のインスタンスとして扱うことのように、基本型のすべてのメンバーが含まれています。 反対の方向に、基本データ型に派生型で定義されたメンバーは含まれません。  
  
 拡大変換では、実行時に常に成功して、データの損失を発生することはありません。 暗黙的に常に実行しているかどうか、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)チェックするスイッチの種類を設定`On`または`Off`です。  
  
## <a name="narrowing-conversions"></a>縮小変換  
 標準的な縮小変換を以下に示します。  
  
-   (すべての型は、自動的に拡大) する点を除いて逆方向の拡大変換前の表にします。  
  
-   いずれかの方向の間で変換[ブール](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)と任意の数値型  
  
-   列挙型のいずれかの任意の数値型に変換 (`Enum`)  
  
-   いずれかの方向の間で変換[文字列](../../../../visual-basic/language-reference/data-types/string-data-type.md)と任意の数値型`Boolean`、または[日付](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
-   派生した型に型のデータ型またはオブジェクトからの変換  
  
 縮小変換は常にではありません、実行時に成功してことができます。 または失敗データ消失が発生します。 マッピング先データ型に変換される値を受信できない場合は、エラーが発生します。 たとえば、数値の変換は、オーバーフローが発生する可能性です。 コンパイラがしない限り、縮小変換を暗黙的に実行を許可していない、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)チェックするスイッチの種類を設定`Off`します。  
  
> [!NOTE]
>  内の要素からの変換の縮小変換エラーは出力されず、`For Each…Next`ループ制御変数のコレクション。 詳細と例については、「縮小変換」セクションを参照して[ごとにしています.次のステートメントの](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)です。  
  
### <a name="when-to-use-narrowing-conversions"></a>縮小変換を使用する場合  
 変換元の値は、エラーやデータ損失なし先のデータ型に変換できることがわかっている場合は、縮小変換を使用します。 ある場合など、`String`使用できますがわかっている"True"または"False"を含む、`CBool`キーワードに変換を`Boolean`します。  
  
## <a name="exceptions-during-conversion"></a>変換中に例外  
 拡大変換を常に成功、例外をスローしません。 縮小変換を失敗した場合は、最もよく、次の例外をスローします。  
  
-   <xref:System.InvalidCastException>-2 つの型の間で変換が定義されていない場合</xref:System.InvalidCastException>  
  
-   <xref:System.OverflowException>-(整数型のみ) のターゲット タイプについては、変換後の値が大きすぎる場合</xref:System.OverflowException>  
  
 クラスまたは構造体が定義されている場合、 [CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)そのクラスまたは構造体、または変換演算子として機能するを`CType`は適切な処置をとり、例外をスローします。 さらを`CType`呼び出すことが[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]関数または[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]メソッドで、さらに、さまざまな例外をスローする可能性があります。  
  
## <a name="changes-during-reference-type-conversions"></a>参照型の変換中の変更  
 変換、*型参照*ポインターだけが、値をコピーします。 値そのものがコピーも、任意の方法で変更します。 変更できることだけは、ポインターを保持する変数のデータ型です。 次の例では、データ型が派生クラスからその基本クラスに変換されますが、両方の変数は、これが指すオブジェクトは変更されません。  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>関連項目  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [明示的および暗黙的な変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [文字列とその他の型の間の変換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)   
 [方法: Visual Basic での別の型のオブジェクトの変換](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [配列の変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
