---
title: "Identifier is too long | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30033"
  - "vbc30033"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30033"
ms.assetid: 3d07f6d0-9a2f-49ca-94e8-1e354932e855
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Identifier is too long
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

各プログラミング要素の名前、つまり識別子は 1023 文字に制限されています。  また、完全限定名は 1023 文字を超過できません。  つまり、識別子の文字列全体 \(`<namespace>.<...>.<namespace>.<class>.<element>`\) の長さは 1023 文字を超過できません。文字列には、メンバー アクセス演算子 \(`.`\) も含みます。  
  
 **Error ID:** BC30033  
  
### このエラーを解決するには  
  
-   識別子の文字数を減らします。  
  
## 参照  
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)