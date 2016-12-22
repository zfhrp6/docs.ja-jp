---
title: "Resume without error | Microsoft Docs"
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
  - "vbrID20"
dev_langs: 
  - "VB"
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Resume without error
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`Resume` ステートメントがエラー処理コードの外にあるか、またはエラーが発生していないのにエラー ハンドラー内にジャンプしました。  
  
### このエラーを解決するには  
  
1.  `Resume` ステートメントをエラー ハンドラー内に移動するか、削除します。  
  
2.  プロシージャ間にまたがってラベルにジャンプすることはできないため、エラー ハンドラーを識別するラベルをプロシージャ内で探してください。  `On Error GoTo` ステートメントではなく `GoTo` ステートメントのターゲットとして重複するラベルが指定されている場合は、目的のターゲットに合わせて行ラベルを変更します。  
  
## 参照  
 [Resume Statement](../../../visual-basic/language-reference/statements/resume-statement.md)   
 [On Error Statement](../../../visual-basic/language-reference/statements/on-error-statement.md)