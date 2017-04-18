---
title: "方法: プロパティ (Visual Basic) に値を格納 |Microsoft ドキュメント"
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
- property values
- Visual Basic code, procedures
- values, properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: e3b2336589b525756a92cb3e26ab6c1950118b01
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>方法: プロパティに値を格納する (Visual Basic)
プロパティに値を格納するには、代入ステートメントの左側にあるプロパティ名を置きます。  
  
 プロパティの`Set`プロシージャは値を格納するが、明示的に呼び出さないことを名前です。 変数と同じように、プロパティを使用します。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロパティのプロシージャを呼び出します。  
  
### <a name="to-store-a-value-in-a-property"></a>プロパティの値を格納するには  
  
1.  代入ステートメントの左側にあるプロパティの名前を使用します。  
  
     次の例の値の設定、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `TimeOfDay`プロパティ、正午を暗黙的に呼び出す、`Set`プロシージャです。  
  
     [!code-vb[VbVbcnProcedures&#11;](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]  
  
2.  プロパティは、引数を受け取る場合は、かっこで囲んだ引数リストのプロパティ名に従ってください。 引数がない場合は、かっこを省略することができます。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 プロパティが対応するパラメーターを定義する順序と同じ順序で引数を指定することを確認します。  
  
4.  代入ステートメントの右側にある生成された値は、このプロパティに格納されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>   
 [プロパティ プロシージャ](./property-procedures.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Visual Basic のプロパティと変数の違い](./differences-between-properties-and-variables.md)   
 [方法: プロパティを作成します。](./how-to-create-a-property.md)   
 [方法: 混合アクセス レベルを持つプロパティの宣言](./how-to-declare-a-property-with-mixed-access-levels.md)   
 [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)   
 [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)   
 [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)
