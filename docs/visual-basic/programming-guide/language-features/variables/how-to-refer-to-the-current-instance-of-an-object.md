---
title: "方法: オブジェクトの現在のインスタンスを参照する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33ea612253b00e12f47258189da4ac7d8d98ade5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a>方法: オブジェクトの現在のインスタンスを参照する (Visual Basic)
*現在のインスタンス*オブジェクトが現在のコードが実行されているインスタンス。  
  
 使用する、`Me`キーワードを現在のインスタンスを参照します。  
  
### <a name="to-refer-to-the-current-instance"></a>現在のインスタンスを参照するには  
  
-   使用して、`Me`オブジェクト変数の名前をここで通常使用するキーワードです。  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     `Me`オブジェクトのように動作変数、宣言またはできませんに割り当てるものです。 `Me`現在のインスタンスを指します。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [オブジェクト変数の代入](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
