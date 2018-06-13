---
title: '方法: プロパティから値を取得する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 9f97669e8d18e7fc633cb0e691d973a611a8cea0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648409"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>方法: プロパティから値を取得する (Visual Basic)
プロパティの値を取得するには、式の中で、プロパティ名を含めます。  
  
 プロパティの`Get`プロシージャが、値を取得しますが、呼び出すことはありません明示的にその名前でします。 変数を使用すると同様に、プロパティを使用します。 Visual Basic では、プロパティのプロシージャ呼び出しを行います。  
  
### <a name="to-retrieve-a-value-from-a-property"></a>プロパティから値を取得するには  
  
1.  式の中で変数名を使用するのと同様に対応するプロパティ名を使用します。 プロパティを使用する変数または定数を使用する任意の場所。  
  
     - または -  
  
     等号の後、プロパティ名を使用して (`=`) 代入ステートメントにサインインします。  
  
     次の例は、Visual Basic の値を読み取ります`Now`プロパティ、暗黙的に呼び出してその`Get`プロシージャです。  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  プロパティが引数を受け取る場合は、プロパティ名を引数リストを囲むかっこに従います。 引数がない場合は、かっこを省略することができます。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 プロパティが、対応するパラメーターを定義する、同じ順序で引数を指定することを確認します。  
  
 プロパティの値が、式、変数と同様に参加する定数または変数または代入ステートメントの左側にあるプロパティに格納されます。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [Property プロシージャ](./property-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Visual Basic でのプロパティと変数の違い](./differences-between-properties-and-variables.md)  
 [方法 : プロパティを作成する](./how-to-create-a-property.md)  
 [方法 : 複数のアクセス レベルを持つプロパティを宣言する](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [方法 : プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)  
 [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)  
 [方法 : プロパティに値を格納する](./how-to-put-a-value-in-a-property.md)
