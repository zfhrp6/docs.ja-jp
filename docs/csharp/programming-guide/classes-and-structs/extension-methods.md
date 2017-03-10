---
title: "拡張メソッド (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "拡張メソッド [C#]"
  - "メソッド [C#], 追加 (既存の型に)"
  - "メソッド [C#], 拡張機能"
ms.assetid: 175ce3ff-9bbf-4e64-8421-faeb81a0bb51
caps.latest.revision: 35
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 35
---
# 拡張メソッド (C# プログラミング ガイド)
拡張メソッドを使用すると、新規の派生型の作成、再コンパイル、または元の型の変更を行うことなく既存の型にメソッドを "追加" できます。  拡張メソッドは特別な種類の静的メソッドですが、拡張された型のインスタンス メソッドのように呼び出します。  C\# および Visual Basic で作成されたクライアント コードの場合は、拡張メソッドの呼び出しと、型で実際に定義されたメソッドの呼び出しに明確な違いはありません。  
  
 最も一般的な拡張メソッドは、既存の <xref:System.Collections.IEnumerable?displayProperty=fullName> 型および <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> 型にクエリ機能を追加する [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq-md.md)] 標準クエリ演算子です。  この標準クエリ演算子を使用するには、まず `using System.Linq` ディレクティブを使用して、スコープに含めます。  <xref:System.Collections.Generic.IEnumerable%601> を実装するすべての型は、<xref:System.Linq.Enumerable.GroupBy%2A>、<xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.Average%2A> などのインスタンス メソッドを持っていると考えられます。  <xref:System.Collections.Generic.List%601>、<xref:System.Array> などの <xref:System.Collections.Generic.IEnumerable%601> 型のインスタンスの後に "ドット" を入力すると、IntelliSense により、ステートメントの入力候補としてこれらの追加メソッドが表示されます。  
  
 整数の配列において、標準クエリ演算子の `OrderBy` メソッドを呼び出す方法を次の例に示します。  かっこ内の式はラムダ式です。  標準クエリ演算子の多くはパラメーターとしてラムダ式を受け取りますが、拡張メソッドでは、これは必須ではありません。  詳細については、「[ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。  
  
 [!code-cs[csProgGuideExtensionMethods#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/extension-methods_1.cs)]  
  
 拡張メソッドは、静的メソッドとして定義しますが、インスタンス メソッドの構文を使用して呼び出します。  最初のパラメーターでは、メソッドが操作する型を指定します。このパラメーターの前には [this](../../../csharp/language-reference/keywords/this.md) 修飾子を付加します。  `using` ディレクティブを使用して名前空間をソース コードに明示的にインポートした場合、拡張メソッドはそのスコープでのみ有効です。  
  
 <xref:System.String?displayProperty=fullName> クラスに対して拡張メソッドを定義する例を次に示します。  入れ子になっていない、非ジェネリックの静的クラス内で定義されていることに注意してください。  
  
 [!code-cs[csProgGuideExtensionMethods#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/extension-methods_2.cs)]  
  
 この `using` ディレクティブを使用することで、`WordCount` 拡張メソッドをスコープに取り込むことができます。  
  
```  
using ExtensionMethods;  
```  
  
 また、この構文を使用することで、アプリケーションから呼び出すことができます。  
  
```  
string s = "Hello Extension Methods";  
int i = s.WordCount();  
```  
  
 コードでは、インスタンス メソッドの構文を使用して拡張メソッドを呼び出します。  ただし、コンパイラが生成する中間言語 \(IL: Intermediate Language\) により、コードは静的メソッドに対する呼び出しに変換されます。  したがって、カプセル化の原則には実質的に違反していません。  実際に、拡張メソッドは、それらが拡張している型のプライベート変数にはアクセスできません。  
  
 詳細については、「[方法 : カスタム拡張メソッドを実装して呼び出す](../../../csharp/programming-guide/classes-and-structs/how-to-implement-and-call-a-custom-extension-method.md)」を参照してください。  
  
 一般的には、独自の拡張メソッドを実装するよりも、拡張メソッドを呼び出すことの方がはるかに多くなります。  拡張メソッドは、インスタンス メソッドの構文を使用して呼び出すので、特別な知識がなくてもクライアント コードからそれらを使用できます。  メソッドが定義されている名前空間に関する `using` ディレクティブを追加するだけで、特定の型の拡張メソッドを使用できるようになります。  たとえば、標準クエリ演算子を使用するには、次の `using` ディレクティブをコードに追加します。  
  
```  
using System.Linq;  
```  
  
 場合によっては、System.Core.dll への参照も追加する必要があります。ほとんどの <xref:System.Collections.Generic.IEnumerable%601> 型で利用できる追加メソッドとして、標準クエリ演算子が IntelliSense により表示されるようになりました。  
  
> [!NOTE]
>  <xref:System.String> の場合、IntelliSense により標準クエリ演算子は表示されませんが、利用できます。  
  
## コンパイル時の拡張メソッドのバインディング  
 拡張メソッドを使用してクラスまたはインターフェイスを拡張することはできますが、これらをオーバーライドすることはできません。  インターフェイス メソッドまたはクラス メソッドと同じ名前およびシグネチャを持つ拡張メソッドは決して呼び出されません。  コンパイル時に、型自体で定義されているインスタンス メソッドよりも低い優先順位が拡張メソッドには必ず設定されます。  つまり、型に `Process(int i)` という名前のメソッドがあり、これと同じシグネチャの拡張メソッドがある場合、コンパイラは必ずインスタンス メソッドにバインドします。  コンパイラは、メソッド呼び出しを検出すると、最初に型のインスタンス メソッドから一致するものを探します。  一致するものが見つからない場合、型に対して定義されている拡張メソッドを検索し、見つかった最初の拡張メソッドにバインドします。  次の例は、コンパイラが拡張メソッドとインスタンス メソッドのどちらにバインドするかを決定する方法を示しています。  
  
## 使用例  
 次の例は、C\# のコンパイラがメソッド呼び出しを型のインスタンス メソッドにバインドするか、拡張メソッドにバインドするかを決定するときに従う規則を示しています。  `Extensions` 静的クラスには、`IMyInterface` を実装する型に対して定義された拡張メソッドが含まれています。  `A`、`B`、および `C` の各クラスはすべてこのインターフェイスを実装しています。  
  
 `MethodB` 拡張メソッドは、その名前とシグネチャがクラスにより既に実装されているメソッドと完全に一致しているため、呼び出されることはありません。  
  
 コンパイラは、一致するシグネチャを持つインスタンス メソッドを検出できない場合、一致する拡張メソッド \(存在する場合\) にバインドします。  
  
 [!code-cs[csProgGuideExtensionMethods#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/extension-methods_3.cs)]  
  
## 一般的なガイドライン  
 拡張メソッドは、一般的に、必要な場合に限り注意して実装することをお勧めします。  クライアント コードで既存の型を拡張する必要がある場合、可能であれば既存の型から派生した新しい型を作成することで行ってください。  詳細については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。  
  
 拡張メソッドを使用して、変更できないソース コードのある型を拡張する場合、型の実装の変更により拡張メソッドが破損するというリスクを負うことになります。  
  
 所定の型の拡張メソッドを実装する場合、次の点に注意してください。  
  
-   拡張メソッドが型で定義されているメソッドと同じシグネチャを持つ場合、その拡張メソッドは呼び出されません。  
  
-   拡張メソッドは名前空間レベルでスコープ内に取り込まれます。  たとえば、`Extensions` という名前の単一の名前空間に、拡張メソッドを含む複数の静的クラスがある場合、`using Extensions;` ディレクティブによって、それらのすべての拡張メソッドがスコープ内に取り込まれます。  
  
 実装したクラス ライブラリでは、アセンブリのバージョン番号のインクリメントを避けるために、拡張メソッドは使用しないでください。  ソース コードを所有するライブラリに重要な機能を追加する場合は、アセンブリのバージョン管理について標準の .NET Framework ガイドラインに従う必要があります。  詳細については、「[アセンブリのバージョン管理](../Topic/Assembly%20Versioning.md)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [Parallel Programming Samples \(並列プログラミングのサンプル\) \(拡張メソッドの例を多数含みます\)](http://code.msdn.microsoft.com/Samples-for-Parallel-b4b76364)   
 [ラムダ式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Standard Query Operators Overview](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Conversion rules for Instance parameters and their impact \(インスタンス パラメーターの変換規則とその影響\)](http://go.microsoft.com/fwlink/?LinkId=112385)   
 [Extension methods Interoperability between languages \(拡張メソッドの言語間での相互運用性\)](http://go.microsoft.com/fwlink/?LinkId=112386)   
 [Extension methods and Curried Delegates \(拡張メソッドとカリー化デリゲート\)](http://go.microsoft.com/fwlink/?LinkId=112387)   
 [Extension method Binding and Error reporting \(バインディングとエラー報告に関する拡張メソッド\)](http://go.microsoft.com/fwlink/?LinkId=112388)