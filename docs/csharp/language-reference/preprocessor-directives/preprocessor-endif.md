---
title: "#endif (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#endif"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#endif ディレクティブ [C#]"
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #endif (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#endif` は、[\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ディレクティブで始まる条件付きディレクティブの終了を示します。  次に例を示します。  
  
```  
  
      #define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## 解説  
 `#if` で始まる条件付きディレクティブは、`#endif` ディレクティブで明示的に終了する必要があります。  `#endif` の使用例については、「[\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)」を参照してください。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# プリプロセッサ ディレクティブ](../../../visual-basic/reference/command-line-compiler/index.md)