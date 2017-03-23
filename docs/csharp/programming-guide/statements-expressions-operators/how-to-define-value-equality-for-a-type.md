---
title: "方法: 型の値の等価性を定義する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Equals メソッド [C#], オーバーライド"
  - "等価性 [C#]"
  - "オブジェクトの等価性 [C#]"
  - "オーバーライド (Equals メソッドを) [C#]"
  - "値の等価性 [C#]"
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# 方法: 型の値の等価性を定義する (C# プログラミング ガイド)
クラスまたは構造体を定義する場合は、型の値の等価性 \(同値\) のカスタム定義を作成することが適切かどうかを判断します。  通常、値の等価性を実装するのは、その型のオブジェクトがある種のコレクションに追加されることが予期される場合、または、そのオブジェクトの主な目的が一連のフィールドまたはプロパティを格納することである場合です。  値の等価性の定義は、特定の型のすべてのフィールドおよびプロパティに基づくか、特定の型のフィールドおよびプロパティのサブセットに基づくことができます。  ただし、いずれの場合も、クラスおよび構造体の両方について、実装は等価性を保証する  5 つの条件に従う必要があります。  
  
1.  x.`Equals`\(x\) は `true` を返します。これは再帰プロパティと呼ばれます。  
  
2.  x.`Equals`\(y\) は、y.`Equals`\(x\) と同じ値を返します。  これは対照プロパティと呼ばれます。  
  
3.  \(x.`Equals`\(y\) && y.`Equals`\(z\)\) が `true` を返す場合、x.`Equals`\(z\) も `true` を返します。  これは推移的プロパティと呼ばれます。  
  
4.  x.`Equals`\(y\) が連続して呼び出された場合は、x および y によって参照されるオブジェクトが変更されていない限り、同じ値を返します。  
  
5.  x.`Equals` \(null\) が `false` を返します。  ただし、null.Equals\(null\) は例外をスローするため、上の 2 番目の規則には従っていないことになります。  
  
 独自に定義する構造体には、<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> メソッドの <xref:System.ValueType?displayProperty=fullName> から値の等価性を継承する既定の実装が既に存在します。   この実装では、リフレクションを使用して、特定の型のパブリック フィールドおよび非パブリック フィールドとプロパティをすべて調べます。  この実装では正しい結果が生成されますが、その型専用に記述するカスタム実装と比較すると処理にかなり時間がかかります。  
  
 値の等価性に関する実装の詳細は、クラスの場合と構造体の場合で異なります。  ただし、クラスと構造体の両方で、等価性の実装に必要な基本手順は同じです。手順は次のとおりです。  
  
1.  [仮想](../../../csharp/language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> メソッドをオーバーライドします。  ほとんどの場合、`bool Equals( object obj )` の実装で必要なのは、<xref:System.IEquatable%601?displayProperty=fullName> インターフェイスの実装である型固有の `Equals` メソッドを呼び出すことだけです   \(手順 2 を参照\)。  
  
2.  型固有の `Equals` メソッドを指定することによって <xref:System.IEquatable%601?displayProperty=fullName> インターフェイスを実装します。  ここで実際の等価性の比較を実行します。  たとえば、型のフィールドを 1 つか 2 つだけ比較することによって等価性を定義できます。  `Equals` から例外をスローしないでください。  クラスの場合に限り、このメソッドはクラスで宣言されているフィールドのみを調べます。  基本クラスに含まれるフィールドを調べるには、`base.Equals` を呼び出す必要があります   \(<xref:System.Object> から直接継承された型である場合は、この呼び出しを行わないでください。<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> の <xref:System.Object> 実装では参照の等価性チェックが実行されるためです\)。  
  
3.  省略可能、ただし推奨: [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md) 演算子および [\!\=](../../../csharp/language-reference/operators/not-equal-operator.md) 演算子をオーバーロードします。  
  
4.  <xref:System.Object.GetHashCode%2A?displayProperty=fullName> をオーバーライドし、値の等価性を持つ 2 つのオブジェクトが同じハッシュ コードを生成するようにします。  
  
5.  省略可能: "大なり" または "少なり" の定義をサポートするには、型に対して <xref:System.IComparable%601> インターフェイスを実装し、また、[\<\=](../../../csharp/language-reference/operators/less-than-equal-operator.md) 演算子および [\>\=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) 演算子をオーバーロードします。  
  
 次に示す最初の例は、クラスの実装です。  2 番目の例は構造体の実装を示します。  
  
## 使用例  
 次の例は、クラス \(参照型\) に値の等価性を実装する方法を示します。  
  
 [!code-cs[csProgGuideStatements#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_1.cs)]  
  
 クラス \(参照型\) に対して、両方の <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> メソッドの既定の実装では、参照の等価性の比較を実行し、値の等価性のチェックを実行しません。  実装側が仮想メソッドをオーバーライドする場合、仮想メソッドに値の等価性のセマンティクスを提供することが目的です。  
  
 `==` 演算子と `!=` 演算子をオーバーロードしないクラスでも、これらの演算子を使用できます。  ただし、既定の動作では参照の等価性のチェックが実行されます。  クラスで `Equals` メソッドをオーバーロードする場合は、`==` 演算子と `!=` 演算子をオーバーロードすることをお勧めしますが、必須ではありません。  
  
## 使用例  
 構造体 \(値型\) に値の等価性を実装する方法を次の例に示します。  
  
 [!code-cs[csProgGuideStatements#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_2.cs)]  
  
 構造体の場合、<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> \(<xref:System.ValueType?displayProperty=fullName> でオーバーライドされるバージョン\) の既定の実装は、リフレクションを使用して特定の型の全フィールドの値を比較することによって、値の等価性のチェックを実行します。  実装側が構造体の `Equals` 仮想メソッドをオーバーライドする場合、その目的は、値の等価性のチェックをより効率的に実行することと、オプションで構造体のフィールドまたはプロパティの一部のサブセットを比較することです。  
  
 [\=\=](../../../csharp/language-reference/operators/equality-comparison-operator.md) 演算子および [\!\=](../../../csharp/language-reference/operators/not-equal-operator.md) 演算子は、構造体が明示的にこれらの演算子をオーバーロードしない限り構造体を操作できません。  
  
## 参照  
 [等価比較](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)