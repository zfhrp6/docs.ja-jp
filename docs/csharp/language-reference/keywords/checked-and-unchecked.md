---
title: "Checked と Unchecked (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4b7b18b39dbfa7ed0818d9ea6e9e62ef79a9f5b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="checked-and-unchecked-c-reference"></a>Checked と Unchecked (C# リファレンス)
C# のステートメントは、checked または unchecked のいずれかのコンテキストで実行できます。 checked コンテキストでは、算術オーバーフローにより例外が発生します。 unchecked コンテキストでは、算術オーバーフローは無視され、結果は切り捨てられます。  
  
-   [checked](../../../csharp/language-reference/keywords/checked.md): checked コンテキストを指定します。  
  
-   [unchecked](../../../csharp/language-reference/keywords/unchecked.md): unchecked コンテキストを指定します。  
  
 `checked` と `unchecked` が両方とも指定されない場合、既定のコンテキストはコンパイラ オプションなどの外的要因に依存します。  
  
 オーバーフロー チェックにより、次の操作が影響を受けます。  
  
-   整数型で次の定義済み演算子を使用する式:  
  
     `++` `--` - (単項)   `+` -   `*` `/`  
  
-   整数型間の明示的な数値変換。  
  
 [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) コンパイラ オプションにより、`checked` または `unchecked` キーワードの明示的な範囲内にはないすべての整数の算術ステートメントに対して、checked コンテキストまたは unchecked コンテキストを指定できます。  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [ステートメントのキーワード](../../../csharp/language-reference/keywords/statement-keywords.md)
