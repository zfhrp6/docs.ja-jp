---
title: "* 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "*_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "* 演算子 [C#]"
  - "乗算演算子 (*) [C#]"
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# * 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

乗算演算子 \(`*`\) です。オペランドの積を計算します。  また、ポインターの読み取りと書き込みを有効にする逆参照演算子でもあります。  
  
## 解説  
 すべての数値型には定義済みの乗算演算子があります。  
  
 `*` 演算子は、ポインター型の宣言やポインターの逆参照にも使用します。  この演算子は、[unsafe \(C\# リファレンス\)](../../../csharp/language-reference/keywords/unsafe.md) キーワードにより示される unsafe コンテキストでのみ使用できます。この場合、[\/unsafe \(unsafe モードの有効化\) \(C\# コンパイラ オプション\)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) コンパイラ オプションが必要です。  逆参照演算子は、間接演算子とも呼ばれます。  
  
 `*` 二項演算子はユーザー定義型でオーバーロードできます。詳細については、「[operator](../../../csharp/language-reference/keywords/operator.md)」を参照してください。  二項演算子をオーバーロードすると、対応する代入演算子がある場合には、この演算子も暗黙でオーバーロードされます。  
  
## 使用例  
 [!CODE [csRefOperators#50](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#50)]  
  
## 使用例  
 [!CODE [csRefOperators#51](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#51)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [unsafe コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)