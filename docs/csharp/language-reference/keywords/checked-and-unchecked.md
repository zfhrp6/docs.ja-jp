---
title: Checked と Unchecked (C# リファレンス)
ms.date: 07/20/2015
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 26ea8a7864d93b8d64661db2b0dc1df6634f989a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
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
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [ステートメントのキーワード](../../../csharp/language-reference/keywords/statement-keywords.md)
