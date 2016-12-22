---
title: "Object required (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID424"
dev_langs: 
  - "VB"
ms.assetid: afdc660b-81a5-4c92-ac7e-9c3a3105fc16
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Object required (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

プロパティまたはメソッドへの参照では、通常、オブジェクト修飾子を明示的に指定する必要があります。  これが通常の場合です。  
  
### このエラーを解決するには  
  
1.  オブジェクトのプロパティまたはメソッドを参照する際に、有効なオブジェクト修飾子が指定してあることを確認します。  オブジェクト修飾子を指定していなかった場合は指定します。  
  
2.  オブジェクト修飾子のスペルを確認し、プログラム内の参照位置からオブジェクトを参照できることを確認します。  
  
3.  ホスト アプリケーションの **File Open** コマンドにパスを指定している場合は、コマンドの引数が正しいことを確認します。  
  
4.  オブジェクトのドキュメントを参照して、このアクションが有効であることを確認します。  
  
## 参照  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)