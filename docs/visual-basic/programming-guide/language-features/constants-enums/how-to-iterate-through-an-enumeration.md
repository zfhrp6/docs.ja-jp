---
title: "方法 : Visual Basic で列挙型を反復処理する"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 439e6eae7d475316625a2cc1d3a70a9e7181f68a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
