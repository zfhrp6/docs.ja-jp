---
title: "方法: プロパティ (Visual Basic の場合) から値を取得 |Microsoft ドキュメント"
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
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: 11
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
ms.openlocfilehash: 7487e4cde724c46a193639f2ad116d25e4ff834c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>方法: プロパティから値を取得する (Visual Basic)
プロパティの値を取得するには、式の中でプロパティ名を含めます。  
  
 プロパティの`Get`プロシージャが値を取得が明示的に呼び出さないことを名前です。 変数と同じように、プロパティを使用します。 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロパティのプロシージャを呼び出します。  
  
### <a name="to-retrieve-a-value-from-a-property"></a>プロパティから値を取得するには  
  
1.  式の中で変数名を使用すると同じように対応するプロパティ名を使用します。 プロパティを使用する変数または定数を使用する任意の場所。  
  
     または  
  
     後に続くプロパティ名を使用して (`=`)、代入ステートメントにサインインします。  
  
     次の例は、値を読み取って、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `Now`プロパティには、暗黙的に呼び出すことの`Get`プロシージャです。  
  
     [!code-vb[VbVbalrDateProperties&4;](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  プロパティは、引数を受け取る場合は、かっこで囲んだ引数リストのプロパティ名に従ってください。 引数がない場合は、かっこを省略することができます。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 プロパティが対応するパラメーターを定義する順序と同じ順序で引数を指定することを確認します。  
  
 プロパティの値が、式、変数と同様に参加する定数または変数または代入ステートメントの左側にあるプロパティに格納されます。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [プロパティ プロシージャ](./property-procedures.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)   
 [Visual Basic のプロパティと変数の違い](./differences-between-properties-and-variables.md)   
 [方法: プロパティを作成します。](./how-to-create-a-property.md)   
 [方法: 混合アクセス レベルを持つプロパティの宣言](./how-to-declare-a-property-with-mixed-access-levels.md)   
 [方法: プロパティ プロシージャを呼び出す](./how-to-call-a-property-procedure.md)   
 [方法: 宣言し、Visual Basic では、既定のプロパティを呼び出す](./how-to-declare-and-call-a-default-property.md)   
 [方法 : プロパティに値を格納する](./how-to-put-a-value-in-a-property.md)
