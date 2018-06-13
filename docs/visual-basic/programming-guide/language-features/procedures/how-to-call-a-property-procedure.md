---
title: '方法: プロパティ プロシージャを呼び出す (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 61d79b9ff99ec144a9c629872abd2a7e7ebda4d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654818"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>方法: プロパティ プロシージャを呼び出す (Visual Basic)
プロパティ プロシージャを呼び出すには、「プロパティ値を格納するか値を取得します。 プロパティは、変数にアクセスする同じ方法でアクセスします。  
  
 プロパティの`Set`プロシージャは値を格納して、その`Get`プロシージャが値を取得します。 ただし、明示的に呼び出さないこれらのプロシージャ名でします。 格納したり、変数の値を取得すると同様に、代入ステートメントまたは式のプロパティを使用します。 Visual Basic では、プロパティのプロシージャ呼び出しを行います。  
  
### <a name="to-call-a-propertys-get-procedure"></a>プロパティの Get プロシージャを呼び出しています  
  
1.  式の中で変数名を使用するのと同様に対応するプロパティ名を使用します。 プロパティを使用する変数または定数を使用する任意の場所。  
  
     - または -  
  
     等号の後、プロパティ名を使用して (`=`) 代入ステートメントにサインインします。  
  
     次の例の値を読み取ります、<xref:Microsoft.VisualBasic.DateAndTime.Now%2A>プロパティ、暗黙的に呼び出してその`Get`プロシージャです。  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  プロパティが引数を受け取る場合は、プロパティ名を引数リストを囲むかっこに従います。 引数がない場合は、かっこを省略することができます。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 プロパティが、対応するパラメーターを定義する、同じ順序で引数を指定することを確認します。  
  
 プロパティの値が、式、変数と同様に参加する定数または変数または代入ステートメントの左側にあるプロパティに格納されます。  
  
### <a name="to-call-a-propertys-set-procedure"></a>プロパティを呼び出すための手順を設定します。  
  
1.  代入ステートメントの左側にあるプロパティの名前を使用します。  
  
     次の例の値の設定、<xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>プロパティ、暗黙的に呼び出して、`Set`プロシージャです。  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  プロパティが引数を受け取る場合は、プロパティ名を引数リストを囲むかっこに従います。 引数がない場合は、かっこを省略することができます。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 プロパティが、対応するパラメーターを定義する、同じ順序で引数を指定することを確認します。  
  
 代入ステートメントの右側にある生成された値は、プロパティに格納されます。  
  
## <a name="see-also"></a>関連項目  
 [Property プロシージャ](./property-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [Visual Basic でのプロパティと変数の違い](./differences-between-properties-and-variables.md)  
 [方法 : プロパティを作成する](./how-to-create-a-property.md)  
 [方法 : 複数のアクセス レベルを持つプロパティを宣言する](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)  
 [方法 : プロパティに値を格納する](./how-to-put-a-value-in-a-property.md)  
 [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)  
 [Get ステートメント](../../../../visual-basic/language-reference/statements/get-statement.md)  
 [Set ステートメント](../../../../visual-basic/language-reference/statements/set-statement.md)
