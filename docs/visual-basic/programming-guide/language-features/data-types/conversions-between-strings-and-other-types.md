---
title: 文字列とその他の型との変換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: 40a28d664bc6ed3d094ccc7c342d6411fe88fd7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>文字列とその他の型との変換 (Visual Basic)
数値を変換する`Boolean`、または日付/時刻値を`String`です。 逆方向に変換することもできます。-数値、文字列値から`Boolean`、または`Date`— 先のデータ型の有効な値として解釈される場合、文字列の内容。 できない場合は、実行時エラーが発生します。  
  
 いずれかの方向で、これらすべての割り当ては縮小変換します。 型変換のキーワードを使用する必要があります (`CBool`、 `CByte`、 `CDate`、 `CDbl`、 `CDec`、 `CInt`、 `CLng`、 `CSByte`、 `CShort`、 `CSng`、 `CStr`、`CUInt`、 `CULng`、 `CUShort`、および`CType`)。 <xref:Microsoft.VisualBasic.Strings.Format%2A>と<xref:Microsoft.VisualBasic.Conversion.Val%2A>関数は、文字列や数値の間の変換の詳細に制御を提供します。  
  
 クラスまたは構造体を定義した場合は、間の型変換演算子を定義できます`String`とクラスまたは構造体の型。 詳細については、次を参照してください。[する方法: 変換演算子を定義する](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)です。  
  
## <a name="conversion-of-numbers-to-strings"></a>数値の文字列への変換  
 使用することができます、`Format`だけでなく、適切な桁の数字を含めることができます、書式設定された文字列を数値に変換する機能しますが、ありますも通貨記号などのシンボルの書式設定 (など`$`)、何千もの区切り記号または*桁区切りシンボル*(など`,`)、および小数点記号 (など`.`)。 `Format` に従って適切なシンボルを自動的に使用して、**地域のオプション**、Windows で指定された設定**コントロール パネル**の です。  
  
 なお、連結したもの (`&`) 演算子は文字列に数値を暗黙的に、次の例のように変換できます。  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>数値の文字列の変換  
 使用することができます、`Val`関数を明示的に文字列内の数字を数値に変換します。 `Val` 数字、スペース、タブ、改行、またはピリオド以外の文字を検出するまでは、文字列を読み取ります。 シーケンスは、"& O"と「(& H)」と、数値の底を変更して、スキャンが終了します。 読み取りを停止するまで`Val`すべての適切な文字の数値に変換します。 たとえば、次のステートメントが、値を返す`141.825`です。  
  
 `Val("   14   1.825 miles")`  
  
 Visual Basic では、文字列を数値に変換して、時に使用、**地域のオプション**、Windows の設定**コントロール パネル**何千もの解釈の区切り記号、桁区切り記号、および通貨記号。 これは、変換は成功可能性がありますも、別の設定の 1 つ下にあることを意味します。 たとえば、`"$14.20"`が許容される任意のフランス語のロケールではなく、英語 (米国) ロケールにします。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [方法: オブジェクトを Visual Basic での別の型に変換](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [配列変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [.NET Framework ベースの国際対応アプリケーションの概要](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
