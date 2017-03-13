---
title: "Query Syntax and Method Syntax in LINQ (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "LINQ [C#], query syntax vs. method syntax"
  - "queries [LINQ in C#], syntax comparisons"
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 28
---
# Query Syntax and Method Syntax in LINQ (C#)
入門統合言語クエリ \([!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)]\) ドキュメントのほとんどのクエリでは、LINQ の宣言クエリ構文を使用して書き込まれます。  ただし、クエリの構文は、.NET 共通言語ランタイム \(CLR\) のメソッド呼び出しにコードがコンパイルされるときに変換する必要があります。  これらのメソッドの呼び出しは、`Where`、`Select`、`GroupBy`、`Join`、`Max`と `Average`のような名前を持つ標準クエリ演算子を開始します。  クエリ構文ではなくメソッド構文を使用してそれらを直接呼び出すことができます。  
  
 クエリ構文とメソッド構文の意味は同じですが、多くのユーザーが読みやすく、すぐにクエリの構文を検索します。  一部のクエリはメソッド呼び出しとして表現する必要があります。  たとえば、指定した条件に一致する要素の数を取得するクエリを表現するためにメソッドの呼び出しを使用する必要があります。  また、ソース シーケンス内で最大値を持つ要素を取得するクエリのメソッドの呼び出しを使用する必要があります。  <xref:System.Linq> 名前空間の標準クエリ演算子のリファレンス ドキュメントでは、通常はメソッド構文を使用しています。  このため、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] クエリを初めて作成する場合でも、クエリとクエリ式自体でメソッド構文を使用する方法に慣れておくと便利です。  
  
## 標準クエリ演算子の拡張メソッド  
 単純な*クエリ式*と、*メソッド ベースのクエリ*として作成された意味的に同等のクエリを次の例に示します。  
  
 [!code-cs[csLINQGettingStarted#22](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/query-syntax-and-method-syntax-in-linq_1.cs)]  
  
 2 つの例の出力結果は同じです。  どちらの形式でも、クエリ変数の型は同じ <xref:System.Collections.Generic.IEnumerable%601> であることがわかります。  
  
 メソッド ベースのクエリを理解するために、この例を詳しく見てみましょう。  式の右側では、`where` 句が `numbers` オブジェクトのインスタンス メソッドとして表されています。このオブジェクトを後で呼び出すとき、型は `IEnumerable<int>` になります。  ジェネリック <xref:System.Collections.Generic.IEnumerable%601> インターフェイスに慣れている方は、このインターフェイスが `Where` メソッドを持たないことにお気付きでしょう。  しかし、Visual Studio IDE で IntelliSense のコンプリート リストを呼び出すと、`Where` メソッドだけでなく、`Select`、`SelectMany`、`Join`、`Orderby` などの他の多くのメソッドも表示されます。  これらはすべて標準クエリ演算子です。  
  
 ![Intellisense の標準クエリ演算子](../../../../csharp/programming-guide/concepts/linq/media/standardqueryops.png "StandardQueryOps")  
  
 <xref:System.Collections.Generic.IEnumerable%601> は、これらの追加メソッドを含むように再定義されたように見えますが、実際にはそうではありません。  標準クエリ演算子は、*拡張メソッド*という新しい種類のメソッドとして実装されます。  拡張メソッドは既存の型を "拡張" し、その型のインスタンス メソッドであるかのように呼び出すことができます。   `numbers.Where(...)` という記述ができるのは、標準クエリ演算子によって <xref:System.Collections.Generic.IEnumerable%601> が拡張されるためです。  
  
 初めて [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] を使用する場合、拡張メソッドに関しては、正しい `using` ディレクティブを使用してアプリケーションのスコープに取り込む方法のみを理解しておけば十分です。  これについては、「[How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md)」で詳しく説明しています。  アプリケーション側から見ると、拡張メソッドと通常のインスタンス メソッドは同じです。  
  
 拡張メソッドの詳細については、「[拡張メソッド](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)」を参照してください。  標準クエリ演算子の詳細については、「[Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)」を参照してください。  [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)] や [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] などの一部の [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] プロバイダーは、独自の標準クエリ演算子と、<xref:System.Collections.Generic.IEnumerable%601> 以外の型に対応する追加の拡張メソッドを実装しています。  
  
## ラムダ式  
 前の例では、条件式 \(`num % 2 == 0`\) が `Where` のインライン メソッドに引数として渡すことに注意してください: `Where(num => num % 2 == 0).`このインライン式はラムダ式と呼ばれます。  これは、匿名メソッド、汎用デリゲート、または式ツリーのような複雑な形式で記述する必要のあるコードを作成するのに便利な方法です。  C\# では、`=>` がラムダ演算子で、"～に入力" という意味を持ちます。  演算子の左側の `num` は、クエリ式の `num` に対応する入力変数です。  `numbers` はジェネリック <xref:System.Collections.Generic.IEnumerable%601> 型であることがわかっているため、コンパイラは `num` の型を推論できます。  ラムダの本体は、クエリ構文での式や、他の C\# 式またはステートメントでの式と同じです。これには、メソッド呼び出しやその他の複雑なロジックを含めることができます。  "戻り値" は式の結果です。  
  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] を使い始めるうえで、ラムダを多用する必要はありません。  ただし、メソッド構文でしか表せないクエリもあり、その一部ではラムダ式が必要になります。  ラムダに慣れると、[!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] ツールボックスの中でも強力かつ柔軟なツールであることがわかります。  詳細については、「[ラムダ式](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。  
  
## クエリの作成のしやすさ  
 前のコード例では、`OrderBy` メソッドは `Where` の呼び出しに対してドット演算子を使用することで呼び出されています。  `Where` はフィルター処理されたシーケンスを生成し、`Orderby` はそのシーケンスを操作して並べ替えます。  クエリは `IEnumerable` を返すため、メソッド構文では、メソッド呼び出しを連結することでクエリを作成します。  クエリ構文を使用してクエリを作成すると、この処理がコンパイラの内部で行われます。  クエリ変数はクエリの結果を格納しないため、クエリを実行した後でも、いつでもクエリを変更したり、新しいクエリの基として使用したりできます。  
  
## 参照  
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)