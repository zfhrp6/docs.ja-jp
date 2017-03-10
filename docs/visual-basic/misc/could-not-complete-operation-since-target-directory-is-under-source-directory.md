---
title: "ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrIO_CyclicOperation"
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# ターゲット ディレクトリがソース ディレクトリ内にあるため、操作を完了できませんでした
循環操作が失敗しました。 循環操作は循環しているため、完了できません。 たとえば、オブジェクト A がオブジェクト B の継承を試行し、同様にオブジェクト B がオブジェクト A の継承を試行するような場合です。  
  
### このエラーを解決するには  
  
-   継承を行うときには、参照の循環がないことを確認します。  
  
## 参照  
 [Error Types](../../visual-basic/programming-guide/language-features/error-types.md)   
 [Debugging Basics: Breakpoints](http://msdn.microsoft.com/ja-jp/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)