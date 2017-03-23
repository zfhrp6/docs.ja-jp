---
title: "型パラメーターの制約 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ジェネリック [C#], 型制約"
  - "型制約 [C#]"
  - "型パラメーター [C#], 制約"
  - "非バインド型パラメーター [C#]"
ms.assetid: 141b003e-1ddb-4e1c-bcb2-e1c3870e6a51
caps.latest.revision: 41
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 41
---
# 型パラメーターの制約 (C# プログラミング ガイド)
ジェネリック クラスを定義するときは、クライアント コードでクラスをインスタンス化するときに型引数に使用できる型の種類に制限を適用できます。  クライアント コードで、制限で許可されていない型を使ってクラスをインスタンス化しようとすると、コンパイル時にエラーが発生します。  このような制限を制約と呼びます。  制約は、`where` コンテキスト キーワードで指定します。  6 種類の制約を次に示します。  
  
|制約|Description|  
|--------|-----------------|  
|where T: struct|型引数は、値型である必要があります。  <xref:System.Nullable> 以外のすべての値型を指定できます。  詳細については、「[Null 許容型の使用](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)」を参照してください。|  
|where T : class|型引数は、参照型である必要があります。このことは、クラス型、インターフェイス型、デリゲート型、配列型についても当てはまります。|  
|where T : new\(\)|型引数は、パラメーターなしのパブリック コンストラクターを持つ必要があります。  `new()` 制約を別の制約と併用する場合、この制約を最後に指定する必要があります。|  
|where T : \<基本クラス名\>|型引数は、指定した基本クラスであるか、または指定した基本クラスから派生する必要があります。|  
|where T : \<インターフェイス名\>|型引数は、指定したインターフェイスであるか、または指定したインターフェイスを実装する必要があります。  インターフェイス制約は複数指定できます。  制約元のインターフェイスもジェネリックにできます。|  
|where T : U|T の位置にある型引数は、U の位置にある引数であるか、またはその引数から派生する必要があります。|  
  
## 制約を使用する理由  
 ジェネリック リストの項目をチェックして、その項目が有効であるかどうかを確認したり、他の項目と比較したりする場合は、コンパイラが呼び出す必要がある演算子やメソッドが、クライアント コードで指定される可能性があるすべての型引数でサポートされるというある程度の保証をコンパイラに与える必要があります。  この保証が、ジェネリック クラス定義に 1 つ以上の制約を適用することで得られます。  たとえば、基本クラス制約では、この型のオブジェクトまたはこの型から派生したオブジェクトだけが型引数として使用されることをコンパイラに伝えます。  この保証が得られると、コンパイラは、その型のメソッドをジェネリック クラス内で呼び出すことを許可できます。  制約は、`where` コンテキスト キーワードを使用して適用します。  基本クラス制約を適用することによって、「[ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)」 の `GenericList<T>` クラスに追加できる機能を次のコード例に示します。  
  
 [!code-cs[csProgGuideGenerics#11](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_1.cs)]  
  
 制約により、T 型のすべての項目が `Employee` オブジェクト、または `Employee` から継承されたオブジェクトのいずれかであることが保証されるため、ジェネリック クラスは、`Employee.Name` プロパティを使用できます。  
  
 制約は、次のように同じ型パラメーターに複数適用でき、制約自体をジェネリック型にできます。  
  
 [!code-cs[csProgGuideGenerics#12](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_2.cs)]  
  
 型パラメーターを制約することで、許容される操作の数と、制約している型とその継承階層内のすべての型でサポートされるメソッドへのメソッド呼び出しの数が増えます。  そのため、ジェネリック クラスやジェネリック メソッドを設計するときに、簡単な代入を超える操作を汎用メンバーに対して実行したり、`System.Object` でサポートされていないメソッドを呼び出したりする場合は、型パラメーターに制約を適用する必要があります。  
  
 `where T : class` 制約を適用するときは、`==` 演算子と `!=` 演算子を型パラメーターで使用しないでください。これらの演算子は、値の等価性ではなく、参照 ID のみをテストするからです。  これらの演算子が、引数として使用される型でオーバーロードされた場合でも同じです。  次のコードは、この点を示しています。このコードの出力は、<xref:System.String> クラスが `==` 演算子をオーバーロードしても false です。  
  
 [!code-cs[csProgGuideGenerics#13](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_3.cs)]  
  
 false が出力されるのは、コンパイル時に、コンパイラが、T が参照型であるということしか認識しないため、すべての参照型に有効な既定の演算子を使用する必要があるからです。  値の等価性をテストする必要がある場合も、`where T : IComparable<T>` 制約を適用し、ジェネリック クラスの構成に使用されるすべてのクラスでそのインターフェイスを実装することをお勧めします。  
  
## 複数のパラメーターに対する制約  
 次の例に示されているように、複数のパラメーターに制約を適用したり、単一のパラメーターに複数の制約を適用したりできます。  
  
 [!code-cs[csProgGuideGenerics#64](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_4.cs)]  
  
## 非バインド型パラメーター  
 `SampleClass<T>{}` パブリック クラスの T など、制約を持たない型パラメーターは、非バインド型パラメーターと呼ばれます。  非バインド型パラメーターには、次の規則が適用されます。  
  
-   `!=` 演算子と `==` 演算子は、具象型引数がこれらの演算子をサポートするという保証がないため、使用できません。  
  
-   これらのパラメーターは、`System.Object` との間で変換できます。またはインターフェイス型に明示的に変換できます。  
  
-   [null](../../../csharp/language-reference/keywords/null.md) と比較できます。  非バインド パラメーターを `null` に比較したときに型引数が値型の場合は、常に false が返されます。  
  
## 制約としての型パラメーター  
 ジェネリック型パラメーターを制約として使用することは、固有の型パラメーターを持つメンバー関数で、そのパラメーターを、メンバー関数を包含する側の型の型パラメーターに制約する必要があるときに便利です。このコード例を次に示します。  
  
 [!code-cs[csProgGuideGenerics#14](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_5.cs)]  
  
 上の例で、`T` は、`Add` メソッドのコンテキストでは型制約であり、`List` クラスのコンテキストでは非バインド型パラメーターです。  
  
 型パラメーターも、ジェネリック クラスの定義で制約として使用できます。  この型パラメーターも他の型パラメーターと同様に山かっこで囲んで宣言する必要があります。  
  
 [!code-cs[csProgGuideGenerics#15](../../../csharp/programming-guide/generics/codesnippet/CSharp/constraints-on-type-parameters_6.cs)]  
  
 ジェネリック クラスを使用した制約としての型パラメーターの有効性は非常に限られます。というのも、型パラメーターが `System.Object` から派生したことしかコンパイラでは認識できないからです。  ジェネリック クラスでの制約としての型パラメーターは、2 つの型パラメーターの間に継承関係を適用する場合に使用します。  
  
## 参照  
 <xref:System.Collections.Generic>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ジェネリックの概要](../../../csharp/programming-guide/generics/introduction-to-generics.md)   
 [ジェネリック クラス](../../../csharp/programming-guide/generics/generic-classes.md)   
 [new 制約](../../../csharp/language-reference/keywords/new-constraint.md)