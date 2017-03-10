---
title: "using ステートメント (C# リファレンス) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "using ステートメント [C#]"
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# using ステートメント (C# リファレンス)
<xref:System.IDisposable> オブジェクトの正しい使用を保証する簡易構文を提供します。  
  
## 使用例  
 using ステートメントの使用方法を次の例に示します。  
  
 [!code-cs[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/csharp/using-statement_1.cs)]  
  
## 解説  
 <xref:System.IO.File> および <xref:System.Drawing.Font> は、アンマネージ リソース \(この場合はファイル ハンドルとデバイス コンテキスト\) にアクセスするマネージ型の例です。  アンマネージ リソースや、それをカプセル化するクラス ライブラリ型は他にもたくさんあります。  そのような型はすべて、<xref:System.IDisposable> インターフェイスを実装する必要があります。  
  
 一般に、`IDisposable` オブジェクトを使用するときは、それを `using` ステートメントで宣言して、インスタンス化する必要があります。  `using` ステートメントは、オブジェクトで正しく <xref:System.IDisposable.Dispose%2A> メソッドを呼び出します。\(前述のようにこのステートメントを使用する場合\) <xref:System.IDisposable.Dispose%2A> が呼び出されるとすぐに、オブジェクト自体がスコープの外側に出されます。  オブジェクトは、`using` ブロック内では読み取り専用です。変更したり再割り当てしたりすることはできません。  
  
 `using` ステートメントを使うと、オブジェクトでのメソッドの呼び出し中に例外が発生した場合でも <xref:System.IDisposable.Dispose%2A> が必ず呼び出されます。  オブジェクトを try ブロックに配置し、finally ブロックで <xref:System.IDisposable.Dispose%2A> を呼び出しても、同じ結果が得られます。実際には、コンパイラは `using` ステートメントをこのように変換します。  前のコード例は、コンパイル時に次のコードに展開されます \(オブジェクトのスコープの範囲を定義する中かっこが加えられています\)。  
  
 [!code-cs[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/csharp/using-statement_2.cs)]  
  
 `using` ステートメントでは、次の例に示すように、型のインスタンスを複数宣言できます。  
  
 [!code-cs[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/csharp/using-statement_3.cs)]  
  
 リソース オブジェクトをインスタンス化して、変数を `using` ステートメントに渡すことは可能ですが、これはベスト プラクティスではありません。  この場合、アンマネージ リソースへのアクセスはおそらくできなくなっているのにもかかわらず、制御が `using` ブロックを離れた後もオブジェクトはスコープ内に残ります。  つまり、完全に初期化されることはありません。  `using` ブロックの外側でオブジェクトを使おうとすると、例外がスローされる可能性があります。  このため、通常は、オブジェクトを `using` でインスタンス化して、そのスコープを `using` ブロックに制限することをお勧めします。  
  
 [!code-cs[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/csharp/using-statement_4.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [using ディレクティブ](../../../csharp/language-reference/keywords/using-directive.md)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)   
 [Implementing a Dispose Method](../Topic/Implementing%20a%20Dispose%20Method.md)