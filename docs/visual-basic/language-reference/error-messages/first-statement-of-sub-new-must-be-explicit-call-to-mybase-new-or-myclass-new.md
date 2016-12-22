---
title: "First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30920"
  - "bc30920"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30920"
ms.assetid: e47dc755-4294-4368-b813-2177b7677957
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# First statement of this &#39;Sub New&#39; must be an explicit call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; because the &#39;&lt;constructorname&gt;&#39; in the base class &#39;&lt;baseclassname&gt;&#39; of &#39;&lt;derivedclassname&gt;&#39; is marked obsolete: &#39;&lt;errormessage&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

クラス コンストラクターが基本クラスのコンストラクターを明示的に呼び出していません。暗黙の基本クラスのコンストラクターは <xref:System.ObsoleteAttribute> 属性でマークされ、その属性のディレクティブで、これをエラーとして扱うように指定されています。  
  
 派生クラスのコンストラクターが基本クラスのコンストラクターを呼び出さない場合、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は、パラメーターなしの基本クラス コンストラクターに対する暗黙的な呼び出しを生成しようとします。  引数なしで呼び出されるアクセス可能なコンストラクターが基本クラスに存在しないと、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] は暗黙的な呼び出しを生成できません。  ここでは、必要なコンストラクターが <xref:System.ObsoleteAttribute> 属性でマークされているため、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] から呼び出すことができません。  
  
 <xref:System.ObsoleteAttribute> を適用することで、任意のプログラミング要素を使用しない要素としてマークできます。  これを行う場合は、属性の <xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False` に設定します。  `True` に設定した場合、コンパイラは要素を使用する試みをエラーとして扱います。  `False` に設定した場合、または既定値の `False` を使用した場合、コンパイラは要素を使用する試みに対して警告を発行します。  
  
 **Error ID:** BC30920  
  
### このエラーを解決するには  
  
1.  二重引用符で囲まれたエラー メッセージを確認し、適切なアクションを実行します。  
  
2.  `MyBase.New()` または `MyClass.New()` の呼び出しを派生クラスの `Sub New` の最初のステートメントとして記述します。  
  
## 参照  
 [属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)