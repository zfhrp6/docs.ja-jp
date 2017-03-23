---
title: "&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30910"
  - "bc30910"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30910"
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# &#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

基本クラスまたはインターフェイスを継承したクラスまたはインターフェイスの、アクセス レベルの制限が低くなっています。  
  
 たとえば、`Public` インターフェイスが `Friend` インターフェイスを継承する、または `Protected` クラスが `Private` クラスを継承するなどの例が挙げられます。  この場合、基本クラスまたはインターフェイスへのアクセスが、指定したレベルで制限されません。  
  
 **Error ID:** BC30910  
  
### このエラーを解決するには  
  
-   派生クラスまたはインターフェイスのアクセス レベルを、基本クラスまたはインターフェイスと少なくとも同じレベルで制限するように変更します。  
  
     または  
  
-   制限の低いアクセス レベルを使用する必要がある場合は、`Inherits` ステートメントを削除します。  より制限の高い基本クラスまたはインターフェイスは継承できません。  
  
## 参照  
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)