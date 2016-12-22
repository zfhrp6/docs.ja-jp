---
title: "#warning (C# リファレンス) | Microsoft Docs"
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
  - "#warning"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#warning ディレクティブ [C#]"
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #warning (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#warning` を使用すると、コードの特定の位置でレベル 1 警告を表示できます。  次に例を示します。  
  
```  
#warning Deprecated code in this method.  
```  
  
## 解説  
 `#warning` は、一般に、条件付きディレクティブ内で使用します。  また、[\#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md) でユーザー定義のエラーを生成することもできます。  
  
## 使用例  
  
```  
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# プリプロセッサ ディレクティブ](../../../visual-basic/reference/command-line-compiler/index.md)