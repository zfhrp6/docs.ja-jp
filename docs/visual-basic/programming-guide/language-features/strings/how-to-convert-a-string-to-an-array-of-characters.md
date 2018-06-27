---
title: '方法 : Visual Basic で文字列を文字の配列に変換する'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: c109143601e304b1ec15a60c71d65fe6bd15aae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648620"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>方法 : Visual Basic で文字列を文字の配列に変換する
文字、文字列および文字列を解析する際など、文字列内の文字の位置に関するデータが存在すると便利ですがあります。 この例を呼び出して、文字列の文字列の文字の配列を取得する方法を示しています。<xref:System.String.ToCharArray%2A>メソッドです。  
  
## <a name="example"></a>例  
 文字列を分割する方法を示します、`Char`に文字列を分割する方法と、配列、 `String` Unicode テキスト文字の配列。 この違いの理由は 2 つ以上の Unicode テキスト文字を構成することできます`Char`文字 (サロゲート ペアなど、組み合わせ文字のシーケンス)。 詳細については、次を参照してください。 <xref:System.Globalization.TextElementEnumerator> "で Unicode 標準"と http://www.unicode.org です。  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>例  
 Unicode テキスト文字、文字列に分割することは困難ですが、これは、文字列のビジュアル表現に関する情報が必要な場合。 この例では、<xref:System.Globalization.StringInfo.SubstringByTextElements%2A>メソッド (string) を構成する Unicode 文字に関する情報を取得します。  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [方法 : 文字列の文字にアクセスする](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [Visual Basic で、文字列型とその他のデータ型との変換を行う](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [文字列](../../../../visual-basic/programming-guide/language-features/strings/index.md)
