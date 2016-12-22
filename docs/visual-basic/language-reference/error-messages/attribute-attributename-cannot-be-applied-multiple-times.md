---
title: "Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times | Microsoft Docs"
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
  - "bc30663"
  - "vbc30663"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30663"
ms.assetid: 3760e7ff-7238-40a1-8676-77d858a64fc0
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Attribute &#39;&lt;attributename&gt;&#39; cannot be applied multiple times
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

この属性は 1 回しか適用できません。  属性を複数回適用できるかどうかは、`AttributeUsage` 属性によって決まります。  
  
 **Error ID:** BC30663  
  
### このエラーを解決するには  
  
1.  属性が適用されているのが 1 回だけであることを確認します。  
  
2.  独自に作成したカスタム属性を使用している場合は、複数の属性を使用できるよう、次に示す例のように `AttributeUsage` 属性を変更することを検討します。  
  
    ```  
    <AttributeUsage(AllowMultiple := True)>  
    ```  
  
## 参照  
 <xref:System.AttributeUsageAttribute>   
 [カスタム属性の作成](../Topic/Creating%20Custom%20Attributes%20\(C%23%20and%20Visual%20Basic\).md)   
 [AttributeUsage](../Topic/AttributeUsage%20\(C%23%20and%20Visual%20Basic\).md)