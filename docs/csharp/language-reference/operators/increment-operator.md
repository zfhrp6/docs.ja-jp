---
title: "++ 演算子 (C# リファレンス) | Microsoft Docs"
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
  - "++_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "++ 演算子 [C#]"
  - "インクリメント演算子 (++) [C#]"
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ++ 演算子 (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

インクリメント演算子 \(`++`\) は、オペランドを 1 ずつインクリメントします。 インクリメント演算子はそのオペランド \(`++variable` および `variable++`\) の前後に指定できます。  
  
## 解説  
 1 番目の形式は前置インクリメント演算です この演算の結果は、インクリメント後のオペランドの値になります。  
  
 2 番目の形式は後置インクリメント演算です。 この演算の結果は、インクリメント前のオペランドの値になります。  
  
 数値型と列挙型には事前定義のインクリメント演算子があります。 ユーザー定義型は `++` 演算子をオーバーロードできます。 整数型に対する演算は、通常、列挙型で使用できます。  
  
## 使用例  
 [!CODE [csRefOperators#3](../CodeSnippet/VS_Snippets_VBCSharp/csrefOperators#3)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# 演算子](../../../csharp/language-reference/operators/index.md)