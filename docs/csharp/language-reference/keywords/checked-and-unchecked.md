---
title: "Checked と Unchecked (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 744f59dbf7ee8370010ff76d4e9dde20490de403
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

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

