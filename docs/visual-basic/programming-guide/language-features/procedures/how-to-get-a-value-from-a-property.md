---
title: "方法: プロパティから値を取得する (Visual Basic)"
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
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cde5408ea09398a79a3da01ae9b2d0202c58eaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a>方法: プロパティから値を取得する (Visual Basic)
プロパティの値を取得するには、式の中で、プロパティ名を含めます。  
  
 プロパティの`Get`プロシージャが、値を取得しますが、呼び出すことはありません明示的にその名前でします。 変数を使用すると同様に、プロパティを使用します。 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]プロパティのプロシージャを呼び出します。  
  
### <a name="to-retrieve-a-value-from-a-property"></a>プロパティから値を取得するには  
  
1.  式の中で変数名を使用するのと同様に対応するプロパティ名を使用します。 プロパティを使用する変数または定数を使用する任意の場所。  
  
     または  
  
     等号の後、プロパティ名を使用して (`=`) 代入ステートメントにサインインします。  
  
     次の例の値を読み取ります、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `Now`プロパティ、暗黙的に呼び出してその`Get`プロシージャです。  
  
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
