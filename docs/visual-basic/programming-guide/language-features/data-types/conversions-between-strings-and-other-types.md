---
title: "文字列とその他の型 (Visual Basic) 間で変換 |Microsoft ドキュメント"
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
- data type conversion, string
- conversions, type
- string conversion
- conversions, data type
- type conversion, string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: 16
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
ms.openlocfilehash: 2d0a5fc7327ecd6339b5021e1b4cb87cc54bd2bc
ms.lasthandoff: 03/13/2017

---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>文字列とその他の型との変換 (Visual Basic)
数値を変換する`Boolean`、または日付/時刻値を`String`です。 逆方向に変換することもできます。-数値、文字列値から`Boolean`、または`Date`: 文字列の内容はマッピング先データ型の有効な値として解釈されることができます。 できない場合は、実行時エラーが発生します。  
  
 どちらの方向に、これらすべての代入の変換には縮小変換を使用します。 You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`). <xref:Microsoft.VisualBasic.Strings.Format%2A>と<xref:Microsoft.VisualBasic.Conversion.Val%2A>関数は、文字列や数値の間の変換の詳細に制御を提供します</xref:Microsoft.VisualBasic.Conversion.Val%2A></xref:Microsoft.VisualBasic.Strings.Format%2A>。  
  
 クラスまたは構造体を定義した場合は、間の型変換演算子を定義できます`String`とクラスまたは構造体の型。 詳細については、次を参照してください。[方法: 変換演算子を定義する](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)です。  
  
## <a name="conversion-of-numbers-to-strings"></a>数値の文字列への変換  
 使用することができます、`Format`だけでなく、適切な桁の数字を含めることができます、書式設定された文字列に数値を変換する機能しますが、通貨記号などのシンボルの書式設定も (など`$`)、何千もの区切り記号または*桁区切り記号*(など`,`)、および小数点記号 (など`.`)。 `Format`」の手順に従って適切なシンボルを自動的に使用して、**地域のオプション**、Windows で指定された設定**コントロール パネルの **します。  
  
 なお、連結 (`&`) 演算子は文字列に数値を暗黙的に、次の例のように変換できます。  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>文字列の数値への変換  
 使用することができます、`Val`関数を明示的に文字列内の数字を数値に変換します。 `Val`数字、スペース、タブ、ライン フィード、またはピリオド以外の文字に到達するまでは、文字列を読み取ります。 シーケンスは、"< O"と">/reportbuilder/reportbuilder_3_0_0_0.application H"数値の底を変更し、スキャンが終了します。 読み取りを停止するまで`Val`値を数値にすべての適切な文字を変換します。 たとえば、次のステートメントが、値を返す`141.825`します。  
  
 `Val("   14   1.825 miles")`  
  
 ときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、文字列、数値を変換を使用して、**地域のオプション**、Windows の設定**コントロール パネルの **何千もの解釈に区切り記号、桁区切り記号および通貨記号。 つまり、変換では、設定も、別の&1; つ下にある成功する可能性があります。 たとえば、`"$14.20"`が許容されるフランス語のロケールではなく英語 (米国) ロケールでします。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [明示的および暗黙的な変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)   
 [方法: Visual Basic での別の型のオブジェクトの変換](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)   
 [配列の変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)   
 [データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [.NET Framework ベースの国際対応アプリケーションの概要](https://docs.microsoft.com/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
