---
title: "方法: クエリでラムダ式を使用する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ラムダ式 [C#], LINQ で"
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# 方法: クエリでラムダ式を使用する (C# プログラミング ガイド)
クエリ構文でラムダ式を直接使用することはありませんが、メソッド呼び出しでラムダ式を使用し、メソッド呼び出しをクエリ式に含めることができます。  実際、メソッド構文でしか表現できないクエリ操作もあります。  クエリ構文とメソッド構文の違いの詳細については、「[Query Syntax and Method Syntax in LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)」を参照してください。  
  
## 使用例  
 次の例は、<xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> 標準クエリ演算子を使用してメソッド ベースのクエリでラムダ式を使用する方法を示しています。  この例の <xref:System.Linq.Enumerable.Where%2A> メソッドはデリゲート型 <xref:System.Func%601> の入力パラメーターを持ち、このデリゲートは整数を入力として受け取ってブール値を返します。  ラムダ式をそのデリゲートに変換することができます。  これが、<xref:System.Linq.Queryable.Where%2A?displayProperty=fullName> メソッドを使用する [!INCLUDE[vbtecdlinq](../../../csharp/includes/vbtecdlinq-md.md)] クエリだった場合、パラメーターの型は `Expression<Func\<int,bool>>` になりますが、ラムダ式はまったく同じに見えます。  式の型の詳細については、「<xref:System.Linq.Expressions.Expression?displayProperty=fullName>」を参照してください。  
  
 [!code-cs[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#1)]  
  
## 使用例  
 次の例は、クエリ式のメソッド呼び出しでラムダ式を使用する方法を示しています。  ラムダが必要なのは、クエリ構文を使用して <xref:System.Linq.Enumerable.Sum%2A> 標準クエリ演算子を呼び出すことはできないためです。  
  
 クエリではまず、`GradeLevel` 列挙体での定義に従って、学生を成績レベルに基づいてグループ化します。  次に、グループごとに各学生の合計得点を加算します。  これには、2 つの `Sum` 操作が必要です。  内側の `Sum` は各学生の合計得点を計算し、外側の `Sum` は、グループに含まれる全学生の現在の総計を保持します。  
  
 [!code-cs[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csrefLINQHowTos.cs#2)]  
  
## コードのコンパイル  
 このコードを実行するには、メソッドをコピーして「[方法 : オブジェクトのコレクションを照会する](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md)」にある `StudentClass` に貼り付け、`Main` メソッドから呼び出します。  
  
## 参照  
 [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [式ツリー](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)