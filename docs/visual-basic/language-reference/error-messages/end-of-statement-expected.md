---
title: "ステートメントの終わりを指定してください。 | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30205"
  - "vbc30205"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30205"
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# ステートメントの終わりを指定してください。
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ステートメントは構文的に完了していますが、ステートメントを終了させる要素の後ろにプログラミング要素があります。  すべてのステートメントの最後には、行の終端記号が必要です。  
  
 行の終端記号が行に Visual Basic のソース ファイルの文字を分割します。  行終端記号の例は、Unicode の復帰文字 \(Unicode\) &HD、改行文字 \(&HA\)、および Unicode の改行文字が続く Unicode の復帰文字です。  行終端記号に関する詳細については、[Visual Basic Language Specification](../../../visual-basic/reference/language-specification.md)\) を参照してください。  
  
 **Error ID:** BC30205  
  
### このエラーを解決するには  
  
1.  2 つの異なるステートメントが誤って同じ行に記述されていないかどうかを確認します。  
  
2.  ステートメントを終了させる要素の後ろに行の終端記号を挿入します。  
  
## 参照  
 [方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)   
 [Statements](../../../visual-basic/programming-guide/language-features/statements.md)