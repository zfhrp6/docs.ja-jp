---
title: '方法: 関連する定数値をまとめてグループ化する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 320373116ad4d61293690353fce6b7b152e79a4f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646405"
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
