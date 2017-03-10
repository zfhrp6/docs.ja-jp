---
title: "コンストラクターの使用 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "コンストラクター [C#], コンストラクターの概要"
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# コンストラクターの使用 (C# プログラミング ガイド)
[クラス](../../../csharp/language-reference/keywords/class.md) か [構造体](../../../csharp/language-reference/keywords/struct.md) が作成されると、コンストラクターが呼び出されます。  コンストラクターがクラスまたは構造体と同じ名前を持ち、通常、新しいオブジェクトのデータ メンバーを初期化します。  
  
 次の例では、`Taxi` というクラスを簡単なコンストラクターを使用して定義しています。  このクラスは、次に [new](../../../csharp/language-reference/keywords/new.md) 演算子によってインスタンス化されます。  新しいオブジェクトにメモリが割り当てられるとすぐに、`Taxi` コンストラクターが `new` 演算子によって呼び出されます。  
  
 [!code-cs[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_1.cs)]  
  
 パラメーターを受け取らないコンストラクターを*既定のコンストラクター*と呼びます。  既定のコンストラクターは、`new` 演算子を使用してオブジェクトをインスタンス化する際に `new` に引数が渡されない場合に呼び出されます。  詳細については、「[インスタンス コンストラクター](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)」を参照してください。  
  
 クラスが[静的](../../../csharp/language-reference/keywords/static.md)である場合を除き、コンストラクターが存在しないクラスには、C\# コンパイラによりパブリックな既定のコンストラクターが割り当てられ、クラスをインスタンス化できるようになります。  詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
 次のようにコンストラクターをプライベートにすると、クラスがインスタンス化されないようにできます。  
  
 [!code-cs[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_2.cs)]  
  
 詳細については、「[プライベート コンストラクター](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)」を参照してください。  
  
 [struct](../../../csharp/language-reference/keywords/struct.md) 型のコンストラクターはクラス コンストラクターに似ていますが、`struct` には、既定のコンストラクターがコンパイラによって自動的に提供されるため、明示的な既定のコンストラクターを含めることができません。  このコンストラクターは、`struct` 内の各フィールドを既定値に初期化します。  詳細については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。  ただし、この既定のコンストラクターは、`struct` が `new` によってインスタンス化される場合にのみ呼び出されます。  たとえば、次のコードでは、<xref:System.Int32> の既定のコンストラクターが使用されるため、確実に整数を初期化できます。  
  
```  
int i = new int();  
Console.WriteLine(i);  
```  
  
 しかし、次のコードでは、`new` を使用せず、初期化されていないオブジェクトを使用するため、コンパイラ エラーになります。  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 これに対して、`struct` に基づくオブジェクト \(組み込みのすべての数値型を含む\) は、次の例のように、初期化または代入してから使用することができます。  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 そのため、値型の既定のコンストラクターを呼び出す必要がありません。  
  
 クラスも `struct` も共に、パラメーターを受け取るコンストラクターを定義できます。  パラメーターを受け取るコンストラクターは、`new` ステートメントまたは [base](../../../csharp/language-reference/keywords/base.md) ステートメントを使用して呼び出す必要があります。  クラスと `structs` では複数のコンストラクターも定義でき、クラスと構造体のどちらも既定のコンストラクターを定義する必要はありません。  次に例を示します。  
  
 [!code-cs[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_3.cs)]  
  
 このクラスは、次のいずれかのステートメントを使用して作成できます。  
  
 [!code-cs[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_4.cs)]  
  
 コンストラクターでは、`base` キーワードを使用して、基本クラスのコンストラクターを呼び出すことができます。  次に例を示します。  
  
 [!code-cs[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_5.cs)]  
  
 この例では、コンストラクターのブロックを実行する前に基本クラスのコンストラクターを呼び出しています。  `base` キーワードは、パラメーターの有無に関係なく使用することもできます。  コンストラクターのパラメーターは、`base` のパラメーターまたは、式の一部として使用できます。  詳細については、「[base](../../../csharp/language-reference/keywords/base.md)」を参照してください。  
  
 派生クラスでは、`base` キーワードを使用して基本クラスのコンストラクターを明示的に呼び出さないと、既定のコンストラクター \(存在する場合\) が暗黙的に呼び出されます。  そのため、次に示すコンストラクターの宣言も実質的に同じです。  
  
 [!code-cs[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_6.cs)]  
  
 [!code-cs[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_7.cs)]  
  
 基本クラスが既定のコンストラクターを提供しない場合、派生クラスでは、`base` を使って基本コンストラクターを明示的に呼び出す必要があります。  
  
 コンストラクターで [this](../../../csharp/language-reference/keywords/this.md) キーワードを使用すると、同じオブジェクトの別のコンストラクターを呼び出すことができます。  `base` と同様に、`this` もパラメーターの有無に関係なく使用でき、コンストラクターのパラメーターはいずれも `this` のパラメーターとしても、式の一部としても使用できます。  たとえば、上の例の 2 番目のコンストラクターは、`this` を使用して次のように書き直すことができます。  
  
 [!code-cs[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_8.cs)]  
  
 上の例で `this` キーワードを使用すると、このコンストラクターが呼び出されます。  
  
 [!code-cs[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/using-constructors_9.cs)]  
  
 コンストラクターは、[public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、または `protected` `internal` とマークできます。  これらのアクセス修飾子により、クラスのユーザーがクラスを作成する方法が定義されます。  詳細については、「[アクセス修飾子 \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
 コンストラクターは、[static](../../../csharp/language-reference/keywords/static.md) キーワードを使用して静的と宣言できます。  静的コンストラクターは、静的フィールドがアクセスされる直前に自動的に呼び出され、一般に静的なクラス メンバーを初期化するために使用されます。  詳細については、「[静的コンストラクター \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)」を参照してください。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [デストラクター](../../../csharp/programming-guide/classes-and-structs/destructors.md)