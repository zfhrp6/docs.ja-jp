---
title: "Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39; | Microsoft Docs"
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
  - "vbc40007"
  - "bc40007"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC40007"
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Default property &#39;&lt;propertyname1&gt;&#39; conflicts with default property &#39;&lt;propertyname2&gt;&#39; in &#39;&lt;classname&gt;&#39; and so should be declared &#39;Shadows&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

基本クラスで定義されているプロパティと同じ名前のプロパティが宣言されています。  この場合、このクラスのプロパティは基本クラスのプロパティをシャドウする必要があります。  
  
 このメッセージは警告です。  `Shadows` が既定で使用されます。  警告を表示しない方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](/visual-studio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **Error ID:** BC40007  
  
### このエラーを解決するには  
  
-   `Shadows` キーワードを宣言に追加するか、宣言されているプロパティの名前を変更します。  
  
## 参照  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)