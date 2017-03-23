---
title: "How to: Move Data Into and Out of a Variable (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "variables [Visual Basic], retrieving values"
  - "variables [Visual Basic], storing data"
ms.assetid: 93744f46-bf78-4fa0-9640-1de01bc38d9a
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Move Data Into and Out of a Variable (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数にデータを格納するには、代入ステートメントの左側に変数名を置きます。  
  
## 変数にデータを代入する  
  
#### 変数に値を格納するには  
  
-   代入ステートメントの左側に変数名を指定します。  
  
     次の例は、変数 `alpha` に値を設定します。  
  
    ```  
    alpha = (beta * 6.27) / (gamma + 2.1)  
    ```  
  
     代入ステートメントの右側で生成された値が、変数に格納されます。  
  
## 変数からデータを取得する  
 変数の値を取得するには、式に変数名を含めます。  
  
#### 変数から値を取得するには  
  
-   式の中で変数名を使用します。  定数またはリテラルが使用できる場所ならどこでも変数を使用できます。ただし、定数の値を定義するための式の中を除きます。  
  
     または  
  
-   代入ステートメントの等号 \(`=`\) 記号の後ろに変数名を使用します。  
  
     次の例では、変数 `startValue` の値を読み込み、次に変数 `counter` の値を式の中で使用します。  
  
    ```  
    counter = startValue  
    cellValue = (counter + 5) ^ 2  
    ```  
  
     変数の値は、定数を指定した場合と同じように式の中で使用されます。式の結果は、代入ステートメントの左側にある変数またはプロパティに格納されます。  
  
## 参照  
 [Variables](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)