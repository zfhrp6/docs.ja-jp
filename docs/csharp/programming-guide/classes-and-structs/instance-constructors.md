---
title: "インスタンス コンストラクター (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "コンストラクター [C#], インスタンス コンストラクター"
  - "インスタンス コンストラクター [C#]"
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# インスタンス コンストラクター (C# プログラミング ガイド)
インスタンス コンストラクターを使用すると、[new](../../../csharp/language-reference/keywords/new.md) 式を使用して[クラス](../../../csharp/language-reference/keywords/class.md)のオブジェクトを作成する際に、任意のインスタンス メンバー変数を作成および初期化できます。  [静的](../../../csharp/language-reference/keywords/static.md)クラスを初期化する場合や、非静的クラスの静的変数を初期化する場合は、静的コンストラクターを定義する必要があります。  詳細については、「[静的コンストラクター](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)」を参照してください。  
  
 インスタンス コンストラクターの例を次に示します。  
  
 [!code-cs[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]  
  
> [!NOTE]
>  このクラスにはパブリック フィールドが含まれていますが、これはわかりやすくするためです。  パブリック フィールドの使用は、推奨されるプログラミング手法ではありません。この場合、プログラム内のすべてのメソッドに、オブジェクトの内部処理への無制限で検証されないアクセスが許可されるからです。  通常、データ メンバーはプライベートにし、クラス メソッドとプロパティのみを介してアクセスする必要があります。  
  
 このインスタンス コンストラクターは、`CoOrds` クラスからオブジェクトを作成するときに呼び出されます。  引数を取らないこのようなコンストラクターを*既定のコンストラクター*と呼びます。  これは、コンストラクターを追加する場合に便利です。  たとえば、`CoOrds` クラスに、データ メンバーの初期値を指定できるコンストラクターを追加できます。  
  
 [!code-cs[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]  
  
 これにより、次のように、既定値や特定の初期値を使って `CoOrd` オブジェクトを作成できます。  
  
 [!code-cs[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]  
  
 クラスにコンストラクターがない場合は、既定のコンストラクターが自動的に生成され、既定値を使用してオブジェクト フィールドが初期化されます。  たとえば、[int](../../../csharp/language-reference/keywords/int.md) は 0 に初期化されます。  既定値の詳細については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。  したがって、`CoOrds` クラスの既定のコンストラクターはすべてのデータ メンバーをゼロに初期化するので、クラスの機能を変更せずに完全に削除できます。  下の「例 1」は複数のコンストラクターを使用する完全な例で、「例 2」は自動的に生成されるコンストラクターの例を示しています。  
  
 また、インスタンス コンストラクターを使用すると、基本クラスのインスタンス コンストラクターを呼び出すこともできます。  クラス コンストラクターは、初期化子を通じて基本クラスのコンストラクターを呼び出すことができます。次にその例を示します。  
  
 [!code-cs[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]  
  
 この例の `Circle` クラスは、`Circle` の派生元の `Shape` によって提供されるコンストラクターに、半径と高さを表す値を渡します。  下の「例 3」は、`Shape` と `Circle` を使用する完全な例を示しています。  
  
## 例 1  
 次の例は、クラス コンストラクターを 2 つ使用するクラスを示しています。1 つのコンストラクターには引数がなく、もう 1 つのコンストラクターには引数が 2 つあります。  
  
 [!code-cs[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]  
  
## 例 2  
 次の例の `Person` クラスにはコンストラクターがありません。この場合は、既定のコンストラクターが自動的に使用され、フィールドは既定値に初期化されます。  
  
 [!code-cs[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]  
  
 `age` の既定値は `0`、`name` の既定値は `null` です。  既定値の詳細については、「[既定値の一覧表](../../../csharp/language-reference/keywords/default-values-table.md)」を参照してください。  
  
## 例 3  
 次の例は、基本クラスの初期化子の使い方を示しています。  `Circle` クラスは一般的なクラス `Shape` から派生しており、`Cylinder` クラスは `Circle` クラスから派生しています。  どちらの派生クラスのコンストラクターも、基本クラスの初期化子を使用しています。  
  
 [!code-cs[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]  
  
 基本クラスのコンストラクターを呼び出すその他の例については、「[virtual](../../../csharp/language-reference/keywords/virtual.md)」、「[オーバーライド](../../../csharp/language-reference/keywords/override.md)」、および「[base](../../../csharp/language-reference/keywords/base.md)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [デストラクター](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [static](../../../csharp/language-reference/keywords/static.md)