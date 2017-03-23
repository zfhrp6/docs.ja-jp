---
title: "オブジェクト (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "オブジェクト [C#], オブジェクトの概要"
  - "変数 [C#]"
ms.assetid: af4a5230-fbf3-4eea-95e1-8b883c2f845c
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# オブジェクト (C# プログラミング ガイド)
クラスまたは構造体の定義は、型が実行できる操作を指定する設計図のようなものです。  オブジェクトとは、基本的に、設計図に基づいて割り当ておよび構成されたメモリ ブロックです。  プログラムでは、同じクラスの多数のオブジェクトを作成できます。  オブジェクトはインスタンスとも呼ばれ、名前付き変数か、配列またはコレクションに格納できます。  クライアント コードは、これらの変数を使用してメソッドを呼び出し、オブジェクトのパブリック プロパティにアクセスするコードです。  C\# などのオブジェクト指向言語の場合、一般的なプログラムは、動的に対話する複数のオブジェクトで構成されます。  
  
> [!NOTE]
>  静的な型の動作は、ここでの説明とは異なります。  詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
## 構造体のインスタンスと. クラスのインスタンス  
 クラスは参照型であるため、クラス オブジェクトの変数は、マネージ ヒープ上のオブジェクトのアドレスへの参照を保持します。  同じ型の 2 番目のオブジェクトが最初のオブジェクトに割り当てられる場合は、両方の変数がそのアドレスのオブジェクトを参照します。  この点については、後で詳しく説明します。  
  
 クラスのインスタンスは、[new 演算子](../../../csharp/language-reference/keywords/new-operator.md)を使用して作成されます。  次の例では、`Person` が型であり、`person1` と `person 2` がその型のインスタンス \(つまりオブジェクト\) です。  
  
 [!code-cs[csProgGuideStatements#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_1.cs)]  
  
 構造体は値型であるため、構造体オブジェクトの変数は、オブジェクト全体のコピーを保持します。  次の例に示すように、構造体のインスタンスも `new` 演算子を使用して作成できますが、これは必須ではありません。  
  
 [!code-cs[csProgGuideStatements#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_2.cs)]  
  
 `p1` と `p2` のメモリは、スレッド スタックに割り当てられています。  メモリは、それが宣言されている型やメソッドと共に再利用されます。  これは、構造体が代入時にコピーされる 1 つの理由でもあります。  これとは対照的に、クラスのインスタンスに割り当てられるメモリは、オブジェクトへのすべての参照がスコープ外に出ると、共通言語ランタイムによって自動的にクリア \(ガベージ コレクト\) されます。  C\+\+ で行うようにクラス オブジェクトを確定的に破棄することはできません。  [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] のガベージ コレクションの詳細については、「[Garbage Collection](../Topic/Garbage%20Collection.md)」を参照してください。  
  
> [!NOTE]
>  マネージ ヒープ上のメモリの割り当てと解放は、共通言語ランタイムで高度に最適化されます。  ほとんどの場合、ヒープへのクラス インスタンスの割り当てとスタックへの構造体のインスタンスの割り当ての間で、パフォーマンスに対する影響が大きく変わることはありません。  
  
## オブジェクトIDとValueの. 等価性  
 2 つのオブジェクトの等価性を比較するときは、2 つの変数がメモリ内の同じオブジェクトを表すかどうか、または 1 つ以上のオブジェクトのフィールドの値が等しいかどうかのどちらを特定する必要があるのかを最初に区別する必要があります。  値を比較する場合は、オブジェクトが値型 \(構造体\) と参照型 \(クラス、デリゲート、配列\) のどちらのインスタンスであるかを考慮してください。  
  
-   2 つのクラスのインスタンスがメモリ内の同じ場所を参照する \(つまり、*ID* が同じである\) かどうかを確認するには、静的メソッド <xref:System.Object.Equals%2A> を使用します   \(<xref:System.Object?displayProperty=fullName> は、ユーザー定義の構造体とクラスを含む、すべての値型および参照型の暗黙の基本クラスです\)。  
  
-   2 つの構造体のインスタンスのインスタンス フィールドの値が同じかどうかを確認するには、<xref:System.ValueType.Equals%2A?displayProperty=fullName> メソッドを使用します。  すべての構造体は暗黙に <xref:System.ValueType?displayProperty=fullName> を継承するため、次の例に示すように、オブジェクトで直接メソッドを呼び出します。  
  
 [!code-cs[csProgGuideStatements#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/objects_3.cs)]  
  
 `Equals` の <xref:System.ValueType?displayProperty=fullName> 実装では、任意の構造体にどのようなフィールドが含まれているかを判断する必要があるため、リフレクションが使用されます。  独自の構造体を作成する場合は、`Equals` メソッドをオーバーライドして、効率的に等価性を判断する型固有のアルゴリズムを実装してください。  
  
-   クラスの 2 つのインスタンスのフィールドの値が等しいかどうかを判断するには、<xref:System.Object.Equals%2A> メソッドまたは [\=\= 演算子](../../../csharp/language-reference/operators/equality-comparison-operator.md)を使用できます。  ただし、これらを使用できるのは、この型のオブジェクトに対して "等しい" ということが何であるのかについてのカスタム定義を提供するために、クラスがオーバーライドまたはオーバーロードされている場合に限られます。  クラスには、<xref:System.IEquatable%601> インターフェイスまたは <xref:System.Collections.Generic.IEqualityComparer%601> インターフェイスが実装されている必要もあります。  どちらのインターフェイスも、値が等価であることのテストに使用できるメソッドを提供します。  `Equals` をオーバーライドする独自のクラスを設計するときには、「[方法: 型の値の等価性を定義する](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)」と「<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName>」で述べられているガイドラインに従ってください。  
  
## 関連項目  
 詳細情報  
  
-   [クラス](../../../csharp/programming-guide/classes-and-structs/classes.md)  
  
-   [構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)  
  
-   [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [デストラクター](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [イベント](../../../csharp/programming-guide/events/index.md)  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [object](../../../csharp/language-reference/keywords/object.md)   
 [継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [クラス](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [new 演算子](../../../csharp/language-reference/keywords/new-operator.md)   
 [共通型システム](../../../standard/base-types/common-type-system.md)