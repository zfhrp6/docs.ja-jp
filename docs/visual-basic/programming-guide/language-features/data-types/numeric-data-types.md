---
title: 数値データ型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
ms.openlocfilehash: 8fa88172c9914a071e1b24e959c9030e6d219a30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654204"
---
# <a name="numeric-data-types-visual-basic"></a>数値データ型 (Visual Basic)
Visual Basic では、いくつかを指定*数値データ型*さまざまな表現で数値を処理するためです。 *整数*型を表す整数のみ (正、負の値、および 0)、および*非整数*型は整数と小数部の両方で数値を表します。  
  
 Visual Basic データ型のサイド バイ サイドの比較を示す表を参照してください[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)です。  
  
## <a name="integral-numeric-types"></a>整数数値型  
 *整数データ型*は小数部のない数だけを表すです。  
  
 *署名*整数データ型は[SByte データ型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)(8 ビット)、 [Short データ型](../../../../visual-basic/language-reference/data-types/short-data-type.md)(16 ビット)、[整数データ型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)(32 ビット)、および[Long データ型](../../../../visual-basic/language-reference/data-types/long-data-type.md)(64 ビット)。 変数は、小数部ではなく、整数を常に保存する場合は、これらの型のいずれかとしてを宣言します。  
  
 *符号なし*整数型では[Byte データ型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)(8 ビット)、 [UShort データ型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)(16 ビット)、 [UInteger データ型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)(32 ビット)、および[Ulong 型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)(64 ビット)。 変数にバイナリ データ、または不明な性質のデータが含まれる場合は、これらの型のいずれかとしてを宣言します。  
  
### <a name="performance"></a>パフォーマンス  
 算術演算は、他のデータ型よりも整数型の高速です。 最も高速、`Integer`と`UInteger`Visual Basic では型です。  
  
### <a name="large-integers"></a>大きな整数  
 大きい整数値を保持する必要がある場合、`Integer`データ型を保持できる、使用することができます、`Long`データ型の代わりにします。 `Long` 変数は、9,223,372,036,854,775,807 を通じて-9,223,372,036,854,775,808 から番号を保持できます。 操作を`Long`でよりも少し遅くなります`Integer`です。  
  
 使用することがより大きな値を必要がある場合、 [Decimal データ型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)です。 79,228,162,514,264,337,593,543,950,335 を通じて-79,228,162,514,264,337,593,543,950,335 から番号を保持できる、`Decimal`変数の場合は、小数点以下桁数を使用しないでください。 ただし、操作を`Decimal`番号は、その他の数値データ型よりもかなり遅くなります。  
  
### <a name="small-integers"></a>小さい整数  
 すべての範囲を必要としない場合、`Integer`できますを使用するデータ型、`Short`データ型は、-32,768 ~ 32,767 の整数を格納することができます。 最小の整数の範囲の`SByte`データ型は-128 から 127 までの整数値を格納します。 非常に多数の小さな整数を格納する変数がある場合は場合、共通言語ランタイムを格納できる場合があります、`Short`と`SByte`変数より効率的かつメモリ消費量を保存します。 ただし、操作を`Short`と`SByte`でよりもやや遅くなります`Integer`です。  
  
### <a name="unsigned-integers"></a>符号なし整数  
 変数が負の値を保持する必要はありません、使用できますがわかっている場合、*型の符号なし*`Byte`、 `UShort`、 `UInteger`、および`ULong`です。 正の整数を 2 回よりも小さい符号付きの型がそれに対応するこれらのデータ型の各保持できます (`SByte`、 `Short`、 `Integer`、および`Long`)。 パフォーマンスの観点からは、各符号なしの型は、対応する符号付きの型と同じくらい効率的です。 具体的には、`UInteger`と共有`Integer`の最も効率的なすべての基本の数値データ型が区別されます。  
  
## <a name="nonintegral-numeric-types"></a>非整数の数値型  
 *非整数のデータ型*は整数と小数部の両方で数値を表すです。  
  
 非整数の数値データ型は、 `Decimal` (128 ビットの固定小数点)、 [Single データ型](../../../../visual-basic/language-reference/data-types/single-data-type.md)(32 ビット浮動小数点数)、および[Double データ型](../../../../visual-basic/language-reference/data-types/double-data-type.md)(64 ビット浮動小数点)。 これらは、すべて署名済みの型です。 変数には、小数が含まれることができる場合、は、これらの型のいずれかとしてを宣言します。  
  
 `Decimal` 浮動小数点データ型がありません。 `Decimal` 番号は、バイナリの整数値と値のどの部分が、小数を指定する整数のスケール ファクターがあります。  
  
 使用することができます`Decimal`money 値として変数をします。 利点は、値の有効桁数です。 `Double`データ型が高速より少ないメモリが必要ですが、丸め誤差が発生します。 `Decimal`データ型は小数点以下桁数が 28 を完全な精度が保持されます。  
  
 浮動小数点 (`Single`と`Double`) 番号がよりも大きい範囲を持つ`Decimal`番号が、丸め誤差が発生することができます。 浮動小数点型サポートの有効桁数よりも少ない`Decimal`ですより大きい値を表すことができます。  
  
 非整数の数値として表現できます mmmEeee にある mmm、*仮数*(有効桁数) であり、廃棄、*指数*(10 の累乗) します。 非整数型の最上位の正の値は 7.9228162514264337593543950335 e + 28 `Decimal`、3.4028235 e + 38 `Single`、および 1.79769313486231570 e + 308 の`Double`します。  
  
### <a name="performance"></a>パフォーマンス  
 `Double` 最も効率的な小数部のデータ型の現在のプラットフォーム上のプロセッサの倍精度浮動小数点演算を実行するためです。 ただし、操作を`Double`などの整数型と同様に高速ではない`Integer`です。  
  
### <a name="small-magnitudes"></a>小さい絶対値  
 (0 に最も近い)、最小の可能な大きさの数値の`Double`変数に保持できます - 4.94065645841246544E と同じくらい小さい-324 の負の値および 4.94065645841246544E-の正の値。  
  
### <a name="small-fractional-numbers"></a>小さい小数  
 すべての範囲を必要としない場合、`Double`できますを使用するデータ型、 `Single` 3.4028235 e + 38 から 3.4028235 e + 38 から浮動小数点数を格納できるデータ型。 最も小さいマグニチュード`Single`変数は、- 1.401298E-45 の負の値および 1.401298E-正の値の 45。 非常に多数の小規模の浮動小数点数を保持する変数がある場合は場合、共通言語ランタイムを格納できる場合があります、`Single`変数より効率的かつメモリ消費量を保存します。  
  
## <a name="see-also"></a>関連項目  
 [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [文字データ型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [その他のデータ型](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)  
 [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [方法 : 符号なしの型を使用する Windows の機能を呼び出す](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
