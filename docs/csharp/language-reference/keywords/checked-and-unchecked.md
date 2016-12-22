---
title: "Checked と Unchecked (C# リファレンス) | Microsoft Docs"
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
  - "checked ステートメント [C#]"
  - "例外 [C#], オーバーフロー チェック"
  - "演算子 [C#], checked と unchecked"
  - "オーバーフロー チェック [C#]"
  - "ステートメント [C#], checked と unchecked"
  - "unchecked ステートメント [C#]"
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Checked と Unchecked (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# のステートメントは、checked または unchecked のいずれかのコンテキストで実行できます。  checked コンテキストでは、算術オーバーフローにより例外が発生します。  unchecked コンテキストでは、算術オーバーフローは無視され、結果は切り捨てられます。  
  
-   [checked](../../../csharp/language-reference/keywords/checked.md) checked コンテキストを指定します。  
  
-   [unchecked](../../../csharp/language-reference/keywords/unchecked.md) unchecked コンテキストを指定します。  
  
 `checked` と `unchecked` が両方とも指定されない場合、既定のコンテキストはコンパイラ オプションなどの外的要因に依存します。  
  
 オーバーフロー チェックにより、次の操作が影響を受けます。  
  
-   整数型で次の定義済み演算子を使用する式:  
  
     `++`  `--` \- \(単項\)   `+` \-   `*` `/`  
  
-   整数型間の明示的な数値変換。  
  
 [\/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) コンパイラ オプションにより、`checked` または `unchecked` キーワードの明示的な範囲内にはないすべての整数の算術ステートメントに対して、checked コンテキストまたは unchecked コンテキストを指定できます。  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [ステートメントのキーワード](../../../csharp/language-reference/keywords/statement-keywords.md)