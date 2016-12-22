---
title: "yield (C# リファレンス) | Microsoft Docs"
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
  - "yield"
  - "yield_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "yield キーワード [C#]"
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
caps.latest.revision: 46
caps.handback.revision: 46
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# yield (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

ステートメントで `yield` キーワードを使用した場合、メソッド、演算子、または `get` アクセサーが反復子であることを示します。  `yield` を使用して反復子を定義すると、カスタム コレクション型の <xref:System.Collections.IEnumerable> および <xref:System.Collections.IEnumerator> パターンを実装するときに明示的な余分なクラス \(列挙の状態を保持するクラス。たとえば <xref:System.Collections.Generic.IEnumerator%601> を参照\) が不要になります。  
  
 `yield` ステートメントの 2 つの形式を次の例に示します。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
## 解説  
 各要素を 1 つずつ返すには、`yield return` ステートメントを使用します。  
  
 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントまたは LINQ クエリを使用することにより、Iterator メソッドを処理します。  `foreach` ループの各イテレーションは、Iterator メソッドを呼び出します。  `yield return` ステートメントが Iterator メソッドに到達すると、`expression` が返され、コードの現在の位置が保持されます。  次回、Iterator 関数が呼び出されると、この位置から実行が再開されます。  
  
 `yield break` ステートメントを使用すると、反復を終了できます。  
  
 反復子の詳細については、「[反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## Iterator メソッドと get アクセサー  
 反復子の宣言は、次の要件を満たす必要があります。  
  
-   戻り値の型は、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601> であることが必要です。  
  
-   この宣言には、[ref](../../../csharp/language-reference/keywords/ref.md) パラメーターまたは [out](../../../csharp/language-reference/keywords/out.md) パラメーターを含めることはできません。  
  
 <xref:System.Collections.IEnumerable> または <xref:System.Collections.IEnumerator> を返す反復子の `yield` 型は `object` です。反復子が <xref:System.Collections.Generic.IEnumerable%601> または <xref:System.Collections.Generic.IEnumerator%601> を返す場合、`yield return` ステートメント内の式の型から、ジェネリック型パラメーターへの暗黙的な変換が存在する必要があります。  
  
 次の特性を持つメソッドに `yield return` ステートメントまたは `yield break` ステートメントを含めることはできません。  
  
-   匿名メソッド。  詳細については、「[匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)」を参照してください。  
  
-   unsafe ブロックを含むメソッド。  詳細については、「[安全でない](../../../csharp/language-reference/keywords/unsafe.md)」を参照してください。  
  
## 例外処理  
 `yield return` ステートメントは、try\-catch ブロックに配置することはできません。  `yield return` ステートメントは、try\-finally ステートメントの try ブロックに配置できます。  
  
 `yield break` ステートメントは、try ブロックまたは catch ブロックには配置できますが、finally ブロックには配置できません。  
  
 `foreach` 本体 \(Iterator メソッドの外部\) で例外がスローされた場合、Iterator メソッドの `finally` ブロックが実行されます。  
  
## 技術的な実装  
 次のコードは、iterator メソッドから `IEnumerable<string>` を返した後、要素を反復処理します。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
 `MyIteratorMethod` への呼び出しでは、メソッドの本体は実行されません。  この呼び出しでは、`IEnumerable<string>` が `elements` 変数に返されます。  
  
 `foreach` ループの反復処理では、`elements` について <xref:System.Collections.IEnumerator.MoveNext%2A> メソッドが呼び出されます。  この呼び出しでは、次の `yield return` ステートメントに到達するまで、`MyIteratorMethod` の本体が実行されます。  `yield return` ステートメントによって返される式は、ループ本体による処理に対する `element` 変数の値だけでなく、`IEnumerable<string>` である要素の <xref:System.Collections.Generic.IEnumerator%601.Current%2A> プロパティも決定します。  
  
 `foreach` ループの以降の各反復処理では、反復子本体の実行が中断した場所から続行し、`yield return` ステートメントに到達したときに再度停止します。  iterator メソッドまたは `yield break` ステートメントの最後に到達すると、`foreach` ループは完了します。  
  
## 使用例  
 次の例では、`for` ループ内に `yield return` ステートメントが含まれます。  `Process` 内の `foreach` ステートメント本体の各反復処理では、`Power` Iterator 関数が呼び出されます。  Iterator 関数を呼び出すごとに、`yield return` ステートメントの次の実行に進みます。これは、`for` ループの次の反復処理で行われます。  
  
 Iterator メソッドの戻り値の型は <xref:System.Collections.IEnumerable> であり、これは反復子インターフェイス型です。  Iterator メソッドが呼び出されると、数値の累乗を含む列挙可能なオブジェクトが返されます。  
  
 [!code-cs[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]  
  
## 使用例  
 次の例は、反復子である `get` アクセサーを示しています。  この例では、各 `yield return` ステートメントがユーザー定義クラスのインスタンスを返します。  
  
 [!code-cs[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [foreach、in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)