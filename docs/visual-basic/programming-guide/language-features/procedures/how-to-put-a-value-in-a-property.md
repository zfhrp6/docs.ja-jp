---
title: "方法: プロパティに値を格納する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44e7c4a92ea3d087c12e74aa2ede33a52c8730cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a>方法: プロパティに値を格納する (Visual Basic)
プロパティに値を格納するには、代入ステートメントの左側にあるプロパティの名前を置きます。  
  
 プロパティの`Set`プロシージャが、値を格納しますが、呼び出すことはありません明示的にその名前でします。 変数を使用すると同様に、プロパティを使用します。 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]プロパティのプロシージャを呼び出します。  
  
### <a name="to-store-a-value-in-a-property"></a>プロパティの値を格納するには  
  
1.  代入ステートメントの左側にあるプロパティの名前を使用します。  
  
     次の例の値の設定、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `TimeOfDay`プロパティ、正午を暗黙的に呼び出してその`Set`プロシージャです。  
  
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
