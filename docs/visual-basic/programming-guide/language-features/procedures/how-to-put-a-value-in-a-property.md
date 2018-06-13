---
title: '方法: プロパティに値を格納する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
ms.openlocfilehash: 29e68ca2b9436921c81346eb1def2417157aae9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650372"
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>方法: プロパティに値を格納する (Visual Basic)
プロパティに値を格納するには、代入ステートメントの左側にあるプロパティの名前を置きます。  
  
 プロパティの`Set`プロシージャが、値を格納しますが、呼び出すことはありません明示的にその名前でします。 変数を使用すると同様に、プロパティを使用します。 Visual Basic では、プロパティのプロシージャ呼び出しを行います。  
  
### <a name="to-store-a-value-in-a-property"></a>プロパティの値を格納するには  
  
1.  代入ステートメントの左側にあるプロパティの名前を使用します。  
  
     次の例は、Visual Basic の値を設定`TimeOfDay`プロパティ、正午を暗黙的に呼び出してその`Set`プロシージャです。  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  プロパティが引数を受け取る場合は、プロパティ名を引数リストを囲むかっこに従います。 引数がない場合は、かっこを省略することができます。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 プロパティが、対応するパラメーターを定義する、同じ順序で引数を指定することを確認します。  
  
4.  代入ステートメントの右側にある生成された値は、プロパティに格納されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>  
 [Property プロシージャ](./property-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Visual Basic でのプロパティと変数の違い](./differences-between-properties-and-variables.md)  
 [方法 : プロパティを作成する](./how-to-create-a-property.md)  
 [方法 : 複数のアクセス レベルを持つプロパティを宣言する](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [方法 : プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)  
 [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)  
 [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)
