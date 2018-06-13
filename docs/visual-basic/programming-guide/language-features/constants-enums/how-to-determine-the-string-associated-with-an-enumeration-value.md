---
title: '方法: 列挙値に関連付けられている文字列を確認する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: c14ea61feba7d7d85f9a4fc377aefdd8fa240c45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651701"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>方法: 列挙値に関連付けられている文字列を確認する (Visual Basic)
<xref:System.Enum.GetValues%2A>と<xref:System.Enum.GetNames%2A>メソッドを使用する文字列と列挙型のメンバーに関連付けられている値を特定できます。  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>列挙体に関連付けられている文字列を決定するには  
  
-   使用して、<xref:System.Enum.GetNames%2A>列挙型のメンバーに関連付けられている文字列を取得します。 この例は、列挙体を宣言`flavorEnum`を使用して、<xref:System.Enum.GetNames%2A>メソッドの各メンバーに関連付けられている文字列を表示します。  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Enum.GetValues%2A>  
 <xref:System.Enum.GetNames%2A>  
 <xref:System.Enum>  
 [方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [方法 : 列挙型のメンバーを参照する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [方法: Visual Basic で列挙型を反復処理します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [列挙型を使用する状況](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [Enum ステートメント](../../../../visual-basic/language-reference/statements/enum-statement.md)
