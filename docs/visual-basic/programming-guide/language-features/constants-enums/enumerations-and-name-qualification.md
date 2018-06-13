---
title: 列挙型と名前修飾 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: eb1f5653d968e81168833cd57813219e8f049b70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648581"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>列挙型と名前修飾 (Visual Basic)
通常、列挙体のメンバーを指す場合は、列挙型の名前でメンバー名を修飾する必要があります。 例についてを参照する、`Sunday`のメンバー、`Days`列挙型では、次の構文を使用します。  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a>Imports ステートメントを使用  
 完全修飾名を使用して追加することで回避することができます、`Imports`名前空間の宣言セクションに次の例のように、コードのステートメント。  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 `Imports`ステートメントは参照先のプロジェクトおよびアセンブリからと内から名前空間の名前をインポート、ステートメントが表示されるモジュールと同じプロジェクトです。 このステートメントが追加されると、次の例のように、修飾なしの列挙メンバーに参照できます。  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 列挙体に関連する定数のセットを整理するには、別のコンテキストで同じ定数名を使用できます。 たとえば、同じ名前に、平日定数を使用することができます、`Days`と`WorkDays`列挙体です。 使用する場合、`Imports`列挙型でステートメントでは、する必要がありますあいまいな参照を回避するように注意します。 次に例を示します。  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 想定される`Monday`両方のメンバーである、`Days`列挙と`Workdays`列挙型、このコードはコンパイラ エラーが生成されます。 あいまいな参照を避けるためには、定数を個別に参照するとき、するには、その列挙体で定数名を修飾します。 次のコードを指す、`Saturday`内の定数、`Days`と`WorkDays`列挙体です。  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a>関連項目  
 [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [方法 : 列挙型のメンバーを参照する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [方法: Visual Basic で列挙型を反復処理します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [方法 : 列挙値に関連付けられている文字列を確認する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [列挙型を使用する状況](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [定数とリテラルのデータ型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Enum ステートメント](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
