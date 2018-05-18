---
title: let 句 (C# リファレンス)
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 9d625db1231687cdad2e24303b2e08ecf736a50c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="let-clause-c-reference"></a>let 句 (C# リファレンス)
クエリ式では、後続の句で使用するために、サブ式の結果を保存すると便利な場合があります。 `let` キーワードを使用してこれを行うことができます。これにより新しい範囲変数を作成し、指定した式の結果でそれを初期化します。 値で初期化されると、範囲変数を使用して別の値を格納することはできません。 ただし、範囲変数がクエリ可能型を保持している場合、クエリを実行できます。  
  
## <a name="example"></a>例  
 次の例で、`let` は 2 つの方法で使用されます。  
  
1.  それ自体を照会できる列挙可能な型を作成します。  
  
2.  クエリが値変数 `word` に対して `ToLower` を 1 回のみ呼び出すことができるようにします。 `let` を使用しない場合、`where` 句の各述語内で、`ToLower` を呼び出す必要があります。  
  
 [!code-csharp[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# リファレンス](../../../csharp/language-reference/index.md)  
 [クエリ キーワード (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [C# の LINQ の概要](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [方法: クエリ式の例外を処理する](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)
