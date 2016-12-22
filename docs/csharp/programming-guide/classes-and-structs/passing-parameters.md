---
title: "パラメーターの引き渡し (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "引数 [C#]"
  - "C# 言語, メソッド パラメーター"
  - "メソッド [C#], 渡す (パラメーターを)"
  - "パラメーター [C#], 渡す"
  - "渡す (パラメーターを) [C#]"
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# パラメーターの引き渡し (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# では、引数が、値または参照でパラメーターに渡されます。  引数を参照で渡すと、関数メンバー \(メソッド、プロパティ、インデクサー、演算子、およびコンストラクター\) は、パラメーターの値を変更でき、その変更を呼び出し元の環境で永続化できます。  パラメーターを参照で渡すには、`ref` キーワードまたは `out` キーワードを使用します。  ここでは、説明を簡単にするために、例に `ref` キーワードだけを使用しています。  `ref` と `out` の違いの詳細については、「[ref](../../../csharp/language-reference/keywords/ref.md)」、「[out](../../../csharp/language-reference/keywords/out.md)」、および「[ref と out を使用した配列の引き渡し](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)」を参照してください。  
  
 次の例は、値パラメーターと参照パラメーターの違いを示しています。  
  
 [!code-cs[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 詳細については、次のトピックを参照してください。  
  
-   [値型のパラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [参照型のパラメーターの引き渡し](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [メソッド](../../../fsharp/language-reference/members/methods.md)