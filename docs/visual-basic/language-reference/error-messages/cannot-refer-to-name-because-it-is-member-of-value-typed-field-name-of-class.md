---
title: "Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30310"
  - "bc30310"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30310"
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Cannot refer to &#39;&lt;name&gt;&#39; because it is a member of the value-typed field &#39;&lt;name&gt;&#39; of class &#39;&lt;classname&gt;&#39; which has &#39;System.MarshalByRefObject&#39; as a base class
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`System.MarshalByRefObject` クラスを使用すると、リモート処理をサポートするアプリケーションは、アプリケーション ドメインの境界を越えてオブジェクトにアクセスできます。  型がアプリケーション ドメインの境界を越えて使用される場合は、`MarshalByRejectObject` クラスから型を継承する必要があります。  オブジェクトの状態はコピーしないでください。オブジェクトのメンバーは、それらが作成されたアプリケーション ドメインの外部では使用できません。  
  
 **Error ID:** BC30310  
  
### このエラーを解決するには  
  
1.  参照を確認して、参照されているメンバーが有効であることを確認します。  
  
2.  `Me` キーワードを使用して、メンバーを明示的に限定します。  
  
## 参照  
 <xref:System.MarshalByRefObject>   
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)