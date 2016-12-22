---
title: "Function evaluation is disabled because a previous function evaluation timed out | Microsoft Docs"
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
  - "bc30957"
  - "vbc30957"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30957"
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Function evaluation is disabled because a previous function evaluation timed out
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

前の関数の評価がタイムアウトしたため、関数の評価は無効になりました。関数の評価をもう一度有効にするには、もう一度ステップを実行するか、またはデバッグを再起動してください。  
  
 Visual Studio デバッガーで、プロシージャ呼び出しが式に指定されていますが、別の評価がタイムアウトしています。  
  
 プロシージャ呼び出しがタイム アウトした原因には、*無限ループ*などが考えられます。  詳細については、「[For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)」を参照してください。  
  
 無限ループの特殊なケースが*再帰*です。  詳細については、「[Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)」を参照してください。  
  
 **Error ID:** BC30957  
  
### このエラーを解決するには  
  
1.  可能であれば、前回の関数の評価がどれかを判断し、タイムアウトした理由を調べます。  判断できない場合、このエラーが再度表示される可能性があります。  
  
2.  デバッガーのステップをもう一度実行するか、デバッガーを終了させて再起動します。  
  
## 参照  
 [Visual Studio でのデバッグ](/visual-studio/debugger/debugging-in-visual-studio)   
 [デバッガーでのコード間の移動](/visual-studio/debugger/navigating-through-code-with-the-debugger)   
 [Visual Basic の式](../Topic/Expressions%20in%20Visual%20Basic.md)