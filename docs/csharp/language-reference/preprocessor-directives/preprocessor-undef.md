---
title: "#undef (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "#undef"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#undef ディレクティブ [C#]"
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# #undef (C# リファレンス)
`#undef` を使用すると、シンボルを未定義状態にできます。たとえば、未定義状態のシンボルを [\#iff](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ディレクティブで式として使用すると、その式は `false` と評価されます。  
  
 シンボルは、[\#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) ディレクティブまたは [\/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) コンパイラ オプションで定義できます。  `#undef` ディレクティブをファイルに記述する場合は、ディレクティブやそれ以外のステートメントよりも前に記述する必要があります。  
  
## 使用例  
  
```  
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass   
{  
    static void Main()   
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```  
  
  **DEBUG is not defined**   
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)