---
title: "方法: 列挙値に関連付けられている文字列を確認する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 01e2b0cfa6b1e426b38198581c7d493c8907b79b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
