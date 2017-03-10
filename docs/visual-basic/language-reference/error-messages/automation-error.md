---
title: "Automation error | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID440"
dev_langs: 
  - "VB"
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Automation error
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

メソッドの実行中、またはオブジェクト変数のプロパティの取得中または設定中にエラーが発生しました。  エラーは、オブジェクトを作成したアプリケーションによって報告されました。  
  
### このエラーを解決するには  
  
1.  `Err` オブジェクトのプロパティをチェックし、エラーの原因と性質を確認します。  
  
2.  アクセス ステートメントの直前で `On Error Resume Next` ステートメントを使用し、アクセス ステートメントの直後のエラーを確認します。  
  
## 参照  
 [Error Types](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [ご意見](/visual-studio/ide/talk-to-us)