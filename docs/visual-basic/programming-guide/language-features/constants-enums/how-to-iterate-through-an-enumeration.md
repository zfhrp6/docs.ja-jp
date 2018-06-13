---
title: '方法 : Visual Basic で列挙型を反復処理する'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 06609d38c805e5f073a2f3a299ecc3aa7cf7be01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646579"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>方法 : Visual Basic で列挙型を反復処理する
一連の関連する定数を操作する場合や、定数値に名前を関連付ける場合は、列挙型を使うと便利です。 列挙体を反復処理に移動できますが使用して、配列、<xref:System.Enum.GetValues%2A>メソッドです。 使用して、列挙型を反復処理することも、`For...Each`ステートメントを使用して、<xref:System.Enum.GetNames%2A>または<xref:System.Enum.GetValues%2A>文字列または数値の値を抽出する方法です。  
  
### <a name="to-iterate-through-an-enumeration"></a>列挙体を反復処理するには  
  
-   配列を宣言し、列挙型に変換して、<xref:System.Enum.GetValues%2A>メソッドとして、配列を渡す前に、他の変数です。 次の例には、列挙体の各メンバーが表示されます。<xref:Microsoft.VisualBasic.FirstDayOfWeek>ように、列挙型を反復処理します。  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [列挙型の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [列挙型を使用する状況](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [方法 : 列挙値に関連付けられている文字列を確認する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [方法 : 列挙型のメンバーを参照する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
