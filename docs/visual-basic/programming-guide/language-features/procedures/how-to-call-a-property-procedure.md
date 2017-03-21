---
title: "方法: プロパティ プロシージャ (Visual Basic) を呼び出す |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures, calling
- properties [Visual Basic], property procedures
- procedure calls, property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7dd3d53f602886f65c951de34b915b2672b1a817
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>方法: プロパティ プロシージャを呼び出す (Visual Basic)
プロパティ プロシージャを呼び出すには、「プロパティに値を格納するかの値を取得しますします。 プロパティは変数にアクセスする同じ方法でアクセスします。  
  
 プロパティの`Set`プロシージャは、値を格納し、その`Get`プロシージャが値を取得します。 ただし、明示的に呼び出さないこれらのプロシージャ名。 格納および変数の値を取得すると同様に、代入ステートメント、または式でプロパティを使用するとします。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロパティのプロシージャを呼び出します。  
  
### <a name="to-call-a-propertys-get-procedure"></a>プロパティの Get プロシージャを呼び出す  
  
1.  式の中で変数名を使用すると同じように対応するプロパティ名を使用します。 プロパティを使用する変数または定数を使用する任意の場所。  
  
     または  
  
     後に続くプロパティ名を使用して (`=`)、代入ステートメントにサインインします。  
  
     次の例は、値を読み取って、<xref:Microsoft.VisualBasic.DateAndTime.Now%2A>プロパティには、暗黙的に呼び出すことの`Get`プロシージャ</xref:Microsoft.VisualBasic.DateAndTime.Now%2A>。  
  
     [!code-vb[VbVbalrDateProperties&4;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  プロパティは、引数を受け取る場合は、かっこで囲んだ引数リストのプロパティ名に従ってください。 引数がない場合は、かっこを省略することができます。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 プロパティが対応するパラメーターを定義する順序と同じ順序で引数を指定することを確認します。  
  
 プロパティの値が、式、変数と同様に参加する定数または変数または代入ステートメントの左側にあるプロパティに格納されます。  
  
### <a name="to-call-a-propertys-set-procedure"></a>プロパティを呼び出すための手順を設定します。  
  
1.  代入ステートメントの左側にあるプロパティの名前を使用します。  
  
     次の例の値の設定、<xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>プロパティには、暗黙的に呼び出す、`Set`プロシージャ</xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>。  
  
     [!code-vb[VbVbcnProcedures&#11;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  プロパティは、引数を受け取る場合は、かっこで囲んだ引数リストのプロパティ名に従ってください。 引数がない場合は、かっこを省略することができます。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 プロパティが対応するパラメーターを定義する順序と同じ順序で引数を指定することを確認します。  
  
 代入ステートメントの右側にある生成された値は、このプロパティに格納されます。  
  
## <a name="see-also"></a>関連項目  
 [プロパティ プロシージャ](./property-procedures.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Visual Basic のプロパティと変数の違い](./differences-between-properties-and-variables.md)   
 [方法: プロパティを作成します。](./how-to-create-a-property.md)   
 [方法: 混合アクセス レベルを持つプロパティの宣言](./how-to-declare-a-property-with-mixed-access-levels.md)   
 [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)   
 [方法: プロパティに値を格納します。](./how-to-put-a-value-in-a-property.md)   
 [方法: プロパティから値を取得します。](./how-to-get-a-value-from-a-property.md)   
 [Get ステートメント](../../../../visual-basic/language-reference/statements/get-statement.md)   
 [Set ステートメント](../../../../visual-basic/language-reference/statements/set-statement.md)
