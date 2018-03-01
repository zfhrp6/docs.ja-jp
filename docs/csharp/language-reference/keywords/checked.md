---
title: "checked (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- checked_CSharpKeyword
- checked
helpviewer_keywords:
- checked keyword [C#]
ms.assetid: 718a1194-988d-48a3-b089-d6ee8bd1608d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ae77894cdc94e41dfa281b92ed3304e0dc25731
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="checked-c-reference"></a>checked (C# リファレンス)
`checked` キーワードは、整数型の算術演算と変換に対してオーバーフロー チェックを明示的に有効にするために使用します。  
  
 既定では、定数値のみを含む式がチェック先の型の範囲外にある値を生成した場合、コンパイラ エラーが発生します。 式が 1 つ以上の非定数値を含む場合、コンパイラはオーバーフローを検出しません。 次の例で `i2` に割り当てられた式を評価しても、コンパイラ エラーは発生しません。  
  
 [!code-csharp[csrefKeywordsChecked#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_1.cs)]  
  
 既定では、これらの非定数式のオーバーフローは実行時にもチェックされず、オーバーフロー例外も発生しません。 前の例では、2 つの正の整数の合計として -2,147,483,639 が表示されます。  
  
 オーバーフロー チェックを有効にするには、コンパイラ オプション、環境設定、または `checked` キーワードを使用します。 `checked` 式または `checked` ブロックを使用して、前の合計によって生じたオーバーフローを実行時に検出する方法を次の例に示します。 どちらの例でもオーバーフロー例外が発生します。  
  
 [!code-csharp[csrefKeywordsChecked#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_2.cs)]  
  
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md) キーワードを使用してオーバーフロー チェックを行わないようにすることもできます。  
  
## <a name="example"></a>例  
 この例では、`checked` を使用して実行時のオーバーフロー チェックを有効にする方法を示します。  
  
 [!code-csharp[csrefKeywordsChecked#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/checked_3.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [Checked と Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md)
