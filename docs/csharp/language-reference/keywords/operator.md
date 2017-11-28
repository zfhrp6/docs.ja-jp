---
title: "operator (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords: operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8fae5487d5daa5ada52d45919598d1abd217aee9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="operator-c-reference"></a>operator (C# リファレンス)
`operator` キーワードを使用して、組み込みの演算子をオーバーロードしたり、クラスまたは構造体宣言内でユーザー定義の変換を行ったりすることができます。  
  
## <a name="example"></a>例  
 小数を処理する非常に簡単なクラスを次に示します。 このクラスは、小数の加算および乗算を実行するために + 演算子および * 演算子をオーバーロードします。また、小数型を倍精度浮動小数点型に変換する変換演算子も提供します。  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [C# のキーワード](../../../csharp/language-reference/keywords/index.md)  
 [implicit](../../../csharp/language-reference/keywords/implicit.md)  
 [explicit](../../../csharp/language-reference/keywords/explicit.md)  
 [方法: 構造体間にユーザー定義の変換を実装する](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
