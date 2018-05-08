---
title: '方法: Visual Basic でオブジェクトを別の型に変換する'
ms.date: 07/20/2015
helpviewer_keywords:
- objects [Visual Basic], converting
ms.assetid: 60cb5fc7-7ba4-4ab5-9c24-480fa12ddcdc
ms.openlocfilehash: 367991e4bbca710df54edf73179f855ff79bb56e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-convert-an-object-to-another-type-in-visual-basic"></a>方法: Visual Basic でオブジェクトを別の型に変換する
変換する、`Object`変数などの変換キーワードを使用して、別のデータ型を[CType 関数](../../../../visual-basic/language-reference/functions/ctype-function.md)です。  
  
## <a name="example"></a>例  
 次の例では、変換、`Object`変数を`Integer`と`String`です。  
  
```  
Public Sub objectConversion(ByVal anObject As Object)  
    Dim anInteger As Integer  
    Dim aString As String  
    anInteger = CType(anObject, Integer)  
    aString = CType(anObject, String)  
End Sub  
```  
  
 わかっている場合の内容、`Object`変数は、特定のデータ型の方が優れている変数をそのデータ型に変換します。 引き続き使用する場合、`Object`いずれかが発生する変数、*ボックス化*と*アンボックス*(の値型) または*遅延バインディング*(の参照型)。 これらの操作では追加の実行時間がかかるすべてで、パフォーマンスが低下します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   <xref:System?displayProperty=nameWithType> 名前空間への参照  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Object>  
 [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [文字列とその他の型との変換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [配列変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
