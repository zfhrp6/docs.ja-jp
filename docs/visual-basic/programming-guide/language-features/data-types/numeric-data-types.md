---
title: "数値データ型 (Visual Basic) |Microsoft ドキュメント"
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
- integral types, Visual Basic
- Short data type, numeric data types
- Double data type, numeric data types
- Long data type, Visual Basic numeric data types
- numbers, whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers, integer
- fractional data types
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type, numeric data types
- exponent, of fractional numbers
- integers
- numeric data types, Visual Basic
- Single data type, numeric types
- Decimal data type, numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
caps.latest.revision: 25
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
ms.openlocfilehash: 3c3098370b8d9dcb6aafcb06dcfb8f4e144b899a
ms.lasthandoff: 03/13/2017

---
# <a name="numeric-data-types-visual-basic"></a>数値データ型 (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]いくつか提供*数値データ型*さまざまな表現で数値を処理するためです。 *整数*型を表す整数のみ (正、負、およびゼロ)、および*非整数*型では、数値を表す整数と小数部の両方にします。  
  
 サイド バイ サイドの比較を示す表に、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]データ型を参照してください[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)します。  
  
## <a name="integral-numeric-types"></a>整数数値型  
 *整数データ型*は小数部のない数だけを表す。  
  
 *署名*整数データ型は[SByte データ型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)(8 ビット)、 [Short データ型](../../../../visual-basic/language-reference/data-types/short-data-type.md)(16 ビット)、[整数データ型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)(32 ビット) および[Long データ型](../../../../visual-basic/language-reference/data-types/long-data-type.md)(64 ビット)。 変数は、小数部ではなく、整数を常に保存する場合は、これらの型のいずれかとしてを宣言します。  
  
 *符号なし*整数型では[Byte データ型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)(8 ビット)、 [UShort データ型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)(16 ビット)、 [UInteger データ型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)(32 ビット) および[ULong データ型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)(64 ビット)。 変数にバイナリ データ、または不明のデータが含まれる場合は、これらの型のいずれかとしてを宣言します。  
  
### <a name="performance"></a>パフォーマンス  
 算術演算は、他のデータ型よりも整数型の高速化します。 最も高速なは、`Integer`と`UInteger`型[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。  
  
### <a name="large-integers"></a>大きな整数  
 大きい整数値を保持する必要がある場合、`Integer`使用すると、データ型を保持できる、`Long`代わりにデータを入力します。 `Long`変数は、9,223,372,036,854,775,807 を通じて-9,223,372,036,854,775,808 から数値を保持できます。 操作が`Long`でよりも少し低速`Integer`します。  
  
 さらに大きな値が必要な場合を使用できます、 [Decimal データ型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)します。 79,228,162,514,264,337,593,543,950,335 を通じて-79,228,162,514,264,337,593,543,950,335 から数値を保持することができます、`Decimal`変数の場合は、小数点以下桁数を使用しないでください。 ただし、操作が`Decimal`番号は、その他の数値データ型よりもかなり遅くなります。  
  
### <a name="small-integers"></a>小さい整数  
 すべての範囲を必要としない場合、`Integer`に使用できるデータの種類、`Short`データ型は、-32,768 ~ 32,767 の整数を格納することができます。 最小の整数の範囲の`SByte`データ型は-128 ~ 127 の整数値を格納します。 非常に多くの小さい整数を保持する変数を設定していれば、共通言語ランタイムを格納できる場合があります、`Short`と`SByte`変数より効率的かつメモリ消費量を保存します。 ただし、操作が`Short`と`SByte`でよりもやや低速`Integer`します。  
  
### <a name="unsigned-integers"></a>符号なし整数  
 変数が負の値を保持する必要はありません、使用することがわかっている場合、*型の符号なし*`Byte`、 `UShort`、 `UInteger`、および`ULong`です。 正の整数を&2; 回よりも小さい符号付きの型を対応するこれらのデータ型の各保持できます (`SByte`、 `Short`、 `Integer`、および`Long`)。 パフォーマンスの面では、各符号なしの型は、対応する符号付きの型と同じくらい効率的です。 具体的には、`UInteger`と共有`Integer`の最も効率的なすべての基本的な数値データ型が区別されます。  
  
## <a name="nonintegral-numeric-types"></a>非整数の数値型  
 *整数以外のデータ型*は整数と小数部の両方で数値を表す。  
  
 非整数の数値データ型は`Decimal`(128 ビットの固定小数点)、 [Single データ型](../../../../visual-basic/language-reference/data-types/single-data-type.md)(32 ビット浮動小数点数)、および[Double データ型](../../../../visual-basic/language-reference/data-types/double-data-type.md)(64 ビットの浮動小数点)。 これらは、すべて署名済みの種類です。 変数には、小数が含まれることができます、これらの型のいずれかとしてを宣言します。  
  
 `Decimal`浮動小数点データ型がありません。 `Decimal`数値は、バイナリの整数値と値のどの部分が、小数を指定する整数値のスケール ファクターがあります。  
  
 使用する`Decimal`money 値として変数をします。 利点は、値の有効桁数です。 `Double`データ型が高速より少ないメモリが必要ですが、丸め誤差が発生します。 `Decimal`データ型は小数点以下桁数が 28 の完全な精度を保持します。  
  
 浮動小数点 (`Single`と`Double`) の数値よりも大きい範囲がある`Decimal`番号が、丸め誤差が発生することができます。 浮動小数点型サポートの有効桁数よりも少ない`Decimal`ですより大きい値を表すことができます。  
  
 非整数の数値として表現できます mmmEeee にある mmm、*仮数*(有効桁数)、eee、*指数*(10 の累乗) します。 非整数型の最も高い正の値は 7.9228162514264337593543950335 e + 28 `Decimal`、3.4028235 e + 38 `Single`、および 1.79769313486231570 e + 308 の`Double`です。  
  
### <a name="performance"></a>パフォーマンス  
 `Double`小数部のデータ型の最も効率的な現在のプラットフォーム上のプロセッサでは、倍精度浮動小数点演算を実行するためです。 ただし、操作が`Double`などの整数型と同様に高速ではない`Integer`します。  
  
### <a name="small-magnitudes"></a>小さい絶対値  
 (0 に最も近い)、可能な大きさの最小の数値の`Double`変数に保持できます - 4.94065645841246544E ように小規模の 324 の負の値および 4.94065645841246544E-の正の値。  
  
### <a name="small-fractional-numbers"></a>小さい小数値  
 すべての範囲を必要としない場合、`Double`に使用できるデータの種類、 `Single` 3.4028235 e + 38 から 3.4028235 e + 38 までの浮動小数点数を保持できるデータ型。 最も小さいマグニチュード`Single`変数は、- 1.401298E-45 の負の値および 1.401298-の正の値。 共通言語ランタイムを格納できますも非常に多くの小規模の浮動小数点数を保持する変数があれば、`Single`変数より効率的かつメモリ消費量を保存します。  
  
## <a name="see-also"></a>関連項目  
 [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [文字データ型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [その他のデータ型](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)   
 [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [方法 : 符号なしの型を使用する Windows の機能を呼び出す](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
