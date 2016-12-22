---
title: "&#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning) | Microsoft Docs"
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
  - "vbc40008"
  - "bc40008"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40008"
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;elementname&gt;&#39; is obsolete (Visual Basic Warning)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ステートメントが、<xref:System.ObsoleteAttribute> 属性でマーク付けされているプログラミング要素にアクセスしています。また、ディレクティブがそれを警告として扱うように設定されています。  
  
 <xref:System.ObsoleteAttribute> を適用することで、任意のプログラミング要素を使用しない要素としてマークできます。  これを行う場合は、属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False` に設定します。  `True` に設定した場合、コンパイラは要素を使用する試みをエラーとして扱います。  `False` に設定した場合、または既定値の `False` を使用した場合、コンパイラは要素を使用する試みに対して警告を発行します。  
  
 既定では、<xref:System.ObsoleteAttribute> の <xref:System.ObsoleteAttribute.IsError%2A> プロパティが `False` であるため、これは警告メッセージになります。  警告を表示しない方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **Error ID:** BC40008  
  
### このエラーを解決するには  
  
-   ソース コード参照で要素名のスペルが正しいことを確認します。  
  
## 参照  
 [属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)