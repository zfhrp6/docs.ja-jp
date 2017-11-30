---
title: "方法: 関連する定数値をまとめてグループ化する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be57b56047654d6eb3536bb0b8f63eca27decdb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a>方法: 関連する定数値をまとめてグループ化する (Visual Basic)
列挙型は、関連する定数をグループ化する最善の方法です。 持つ列挙体を作成する、`Enum`クラスまたはモジュールの宣言セクション内のステートメント。 詳細については、次を参照してください。[する方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)です。  
  
### <a name="to-group-related-constant-values"></a>グループに関連する定数値  
  
1.  コードのアクセス レベルを含む宣言を書き込み、`Enum`キーワード、および有効な名前です。 この例で作成、`Private`列挙型、`temperatureValues`です。  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  列挙体の定数を定義します。 この例で作成、`Public`列挙`temperatureValues`し、その値を割り当てます。  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [方法 : 列挙型のメンバーを参照する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [列挙型を使用する状況](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [定数の概要](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
