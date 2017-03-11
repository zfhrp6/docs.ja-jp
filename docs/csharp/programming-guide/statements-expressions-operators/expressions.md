---
title: "式 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, 式"
  - "式 [C#]"
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# 式 (C# プログラミング ガイド)
*式*とは、1 つの値、オブジェクト、メソッド、または名前空間に評価できる、1 つ以上のオペランドと 0 個以上の演算子のシーケンスです。  式には、リテラル値、メソッドの呼び出し、演算子とそのオペランド、または*簡易名*を含めることができます。  簡易名には、変数、型のメンバー、メソッドのパラメーター、名前空間、または型の名前を指定できます。  
  
 式では、他の式をパラメーターとして使用する演算子や、他のメソッド呼び出しとなるパラメーターを持つメソッド呼び出しを使用できます。そのため、式には単純なものもあれば、非常に複雑なものもあります。  次に式の例を 2 つ示します。  
  
```  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25))   
System.Convert.ToInt32("35")  
```  
  
## 式の値  
 ステートメントやメソッド パラメーターなど、式が使用されるコンテキストの大部分では、式はなんらかの値に評価されることが期待されます。  たとえば、x と y が整数である場合、式 `x + y` は数値に評価されます。  式 `new MyClass()` は、`MyClass` オブジェクトの新しいインスタンスへの参照に評価されます。  式 `myClass.ToString()` は、メソッドの戻り値の型である文字列に評価されます。  ただし、名前空間名については、分類上は式として扱われますが、値には評価されないため、式の最終結果になることはありません。  名前空間名は、メソッド パラメーターに渡すことはできません。また、新しい式で使用したり、変数に割り当てたりすることもできません。  名前空間名は、より大きい式の部分式としてのみ使用できます。  同じことが、型 \(<xref:System.Type?displayProperty=fullName> オブジェクトとは異なります\)、メソッド グループ名 \(特定のメソッドとは異なります\)、およびイベント アクセサーである [add](../../../csharp/language-reference/keywords/add.md) と [remove](../../../csharp/language-reference/keywords/remove.md) にも当てはまります。  
  
 すべての値には、型が関連付けられています。  たとえば、x と y が両方とも型 `int` の変数である場合、式 `x + y` の値も `int` として型指定されます。  異なる型の変数に値が割り当てられた場合や、x と y の型が異なる場合は、型変換の規則が適用されます。  このような変換の動作方法の詳細については、「[キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)」を参照してください。  
  
## オーバーフロー  
 値の型の最大値よりも値が大きくなると、数式でオーバーフローが発生することがあります。  詳細については、「[Checked と Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md)」および「[明示的な数値変換の一覧表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)」を参照してください。  
  
## 演算子の優先順位と結合規則  
 式の評価方法は、結合規則と演算子の優先順位によって決まります。  詳細については、「[演算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)」を参照してください。  
  
 代入式とメソッドの呼び出し式を除き、ほとんどの式はステートメントに埋め込む必要があります。  詳細については、「[ステートメント](../../../csharp/programming-guide/statements-expressions-operators/statements.md)」を参照してください。  
  
## リテラルと簡易名  
 式の中で最も単純なのがリテラルと簡易名の 2 つのタイプです。  リテラルは、名前を持たない定数値です。  たとえば、次のコード例の `5` と `"Hello World"` は共にリテラル値です。  
  
 [!code-cs[csProgGuideStatements#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/expressions_1.cs)]  
  
 リテラルの詳細については、「[型](../../../csharp/language-reference/keywords/types.md)」を参照してください。  
  
 前の例の `i` と `s` は、どちらもローカル変数を識別する簡易名です。  これらの変数を式で使用すると、変数名は、変数のメモリ位置に現在格納されている値に評価されます。  これを次の例に示します。  
  
 [!code-cs[csProgGuideStatements#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/expressions_2.cs)]  
  
## 呼び出し式  
 次のコード例では、`DoWork` の呼び出しが呼び出し式です。  
  
```  
DoWork();  
```  
  
 メソッドの呼び出しでは、メソッドの名前 \(上の例のような名前、または別の式の結果としての名前\) を使用し、その後にかっことメソッド パラメーターを記述する必要があります。  詳細については、「[メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)」を参照してください。  デリゲートの呼び出しでは、デリゲートの名前とメソッド パラメーターをかっこで囲んで使用します。  詳細については、「[デリゲート](../../../csharp/programming-guide/delegates/index.md)」を参照してください。  メソッドの呼び出しとデリゲートの呼び出しは、メソッドが値を返す場合、メソッドの戻り値に評価されます。  void を返すメソッドは、式の値の代わりに使用できません。  
  
## クエリ式  
 一般的な式の規則と同じ規則がクエリ式に適用されます。  詳細については、「[LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)」を参照してください。  
  
## ラムダ式  
 ラムダ式は、名前がないが入力パラメーターおよび複数のステートメントを持つことができる "インライン メソッド" を表します。  LINQ では、メソッドに引数を渡すために広く使用されています。  ラムダ式は、使用されるコンテキストに応じて、デリゲートまたは式ツリーにコンパイルされます。  詳細については、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。  
  
## 式ツリー  
 式ツリーを使用すると、式をデータ構造体として表すことができます。  クエリ式を、SQL データベースなどの他のコンテキストで意味を持つコードに変換するために、LINQ プロバイダーにより広く使用されています。  詳細については、「[式ツリー](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
## 解説  
 変数、オブジェクト プロパティ、またはオブジェクトのインデクサー アクセスが式によって識別されると、その項目の値が式の値として使用されます。  C\# の式は、式が最終的に必要な型に評価される限り、値やオブジェクトが必要とされる任意の位置に配置できます。  
  
## 参考書籍の該当する章  
 [Variables and Expressions](http://go.microsoft.com/fwlink/?LinkId=221228) 入力 [Beginning Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)   
 [演算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)   
 [型](../../../csharp/programming-guide/types/index.md)   
 [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)