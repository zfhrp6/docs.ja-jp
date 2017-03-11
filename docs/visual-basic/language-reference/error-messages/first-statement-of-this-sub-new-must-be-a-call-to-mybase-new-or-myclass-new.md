---
title: "First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30148"
  - "vbc30148"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30148"
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

この 'Sub New' の最初のステートメントは、'MyBase.New' または 'MyClass.New' の呼び出しである必要があります。これは、'\<derivedname\>' の基本クラス '\<basename\>' が、引数なしで呼び出すことのできるアクセス可能な 'Sub New' を持たないためです。  
  
 派生クラスの各コンストラクターは、基本クラスのコンストラクター \(`MyBase.New`\) を呼び出す必要があります。  派生クラスがアクセスできるパラメーターなしのコンストラクターが基本クラスにある場合は、`MyBase.New` を自動的に呼び出すことができます。  それ以外の場合は、パラメーターを使用して基本クラスのコンストラクターを呼び出す必要があります。この呼び出しは、自動的に行うことはできません。  その場合、派生クラスのあらゆるコンストラクターの最初のステートメントでは、基本クラスに対してパラメーター化されたコンストラクターを呼び出すか、基本クラスのコンストラクターを呼び出す、派生クラス内の別のコンストラクターを呼び出す必要があります。  
  
 **Error ID:** BC30148  
  
### このエラーを解決するには  
  
-   必要なパラメーターを指定して `MyBase.New` を呼び出すか、またはそのような呼び出しを行うピア コンストラクターを呼び出します。  
  
     たとえば、基本クラスに `Public Sub New(ByVal index as Integer)`として宣言されたコンストラクターがある場合は、派生クラスのコンストラクターの最初のステートメントは `MyBase.New(100)`である場合があります。  
  
## 参照  
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)