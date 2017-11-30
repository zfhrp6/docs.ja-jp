---
title: "方法: 変数に値を格納する、および変数から値を取得する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], retrieving values
- variables [Visual Basic], storing data
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fefb1979e35cd7b5fa1917f8f1a57af575e51234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-data-into-and-out-of-a-variable-visual-basic"></a>方法: 変数に値を格納する、および変数から値を取得する (Visual Basic)
変数に値を格納するには、代入ステートメントの左側にある変数名を置きます。  
  
## <a name="putting-data-in-a-variable"></a>変数にデータを配置します。  
  
#### <a name="to-store-a-value-in-a-variable"></a>変数に値を格納するには  
  
-   代入ステートメントの左側にある変数名を使用します。  
  
     次の例は、変数の値を設定`alpha`です。  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     代入ステートメントの右側にある生成された値は、変数に格納されます。  
  
## <a name="getting-data-from-a-variable"></a>変数からのデータの取得  
 変数の値を取得するには、式の中で変数名を含めます。  
  
#### <a name="to-retrieve-a-value-from-a-variable"></a>変数から値を取得するには  
  
-   式の中で、変数名を使用します。 変数を使用する任意の場所で使用できる、定数またはリテラルを除き、定数の値を定義する式。  
  
     または  
  
-   等号の後、変数名を使用して (`=`) 代入ステートメントにサインインします。  
  
     次の例は、変数の値を読み取ります`startValue`し、変数の値を使用して`counter`式でします。  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     変数の値は、のみと同じよう、定数、変数または代入ステートメントの左側にあるプロパティに格納し、式に参加します。  
  
## <a name="see-also"></a>関連項目  
 [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
