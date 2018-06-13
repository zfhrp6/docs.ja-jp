---
title: '方法 : Visual Basic で文字列の文字にアクセスする'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 48507cade639660e6ce36697975d09fb29206c20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649153"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>方法 : Visual Basic で文字列の文字にアクセスする
この例で使用する方法、<xref:System.String.Chars%2A>文字列で指定した場所にある文字にアクセスするプロパティです。  
  
## <a name="example"></a>例  
 文字、文字列と、文字列内の文字の位置に関するデータが存在すると便利ですがあります。 文字の配列として文字列の考えることができます (`Char`インスタンス); 特定の文字を取得するには、その文字のインデックスを参照する、<xref:System.String.Chars%2A>プロパティです。  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 `index`のパラメーター、<xref:System.String.Chars%2A>プロパティは 0 から始まる。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 <xref:System.String.Chars%2A>プロパティが指定した位置にある文字を返します。 ただし、Unicode 文字の一部は、1 つ以上の文字によって表されることができます。 Unicode 文字を使用する方法の詳細については、次を参照してください。[する方法: 文字列、配列の文字を変換](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)です。  
  
 <xref:System.String.Chars%2A>プロパティがスローされます、<xref:System.IndexOutOfRangeException>例外場合、`index`パラメーターは、文字列の長さ以上には 0 より小さい場合、または  
  
## <a name="see-also"></a>関連項目  
 <xref:System.String.Chars%2A>  
 [方法 : 文字列を文字の配列に変換する](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [Visual Basic で、文字列型とその他のデータ型との変換を行う](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [文字列](../../../../visual-basic/programming-guide/language-features/strings/index.md)
