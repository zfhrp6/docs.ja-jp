---
title: "Assembly (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Assembly"
  - "vb.AssemblyAttribute"
  - "Assembly"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Assembly modifier"
  - "Assembly keyword"
  - "attribute blocks, Assembly keyword"
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Assembly (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ソース ファイルの冒頭にある属性がアセンブリ全体に適用されることを示します。  
  
## 解説  
 多くの属性は、クラスまたはプロパティなどの個別のプログラミング要素に適用されます。  このような属性は、宣言ステートメントに直接、山かっこ \(`< >`\) で囲んだ属性ブロックを割り当てることで適用します。  
  
 属性が、次の要素だけでなくアセンブリ全体に適用される場合、属性ブロックはソース ファイルの冒頭に記述し、`Assembly` キーワードで属性を明示します。  これが現在のアセンブリ モジュールに適用される場合、[Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) キーワードを使用します。  
  
 AssemblyInfo.vb ファイルでは、属性をアセンブリに適用できます。この場合、メインのソース コード ファイルで属性ブロックを使用する必要はありません。  
  
## 参照  
 [Module \<keyword\>](../../../visual-basic/language-reference/modifiers/module-keyword.md)   
 [属性](../Topic/Attributes%20\(C%23%20and%20Visual%20Basic\).md)