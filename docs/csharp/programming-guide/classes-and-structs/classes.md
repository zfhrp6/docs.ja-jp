---
title: クラス (C# プログラミング ガイド)
description: クラスの型と、クラスの型を作成する方法について説明します
ms.date: 04/05/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 808e25315b0010fd55112f2ed237485c3d0c40d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="classes-c-programming-guide"></a>クラス (C# プログラミング ガイド)
*クラス*とは、他の型、メソッド、およびイベントの変数をまとめてグループ化することで独自のカスタム型を作成できる構成要素です。 クラスは設計図に似ています。 型の動作とデータを定義します。 クラスが static と宣言されていない場合、クライアント コードはそのクラスの "*インスタンス*" を作成できます。 これらのインスタンスは、変数に割り当てられる "*オブジェクト*" です。 クラスのインスタンスは、その変数への参照がすべてスコープ外になるまで、メモリ内に保持されます。 すべてスコープ外になったとき、CLR により、ガベージ コレクションの対象となるようにマークされます。 クラスが [static](../../../csharp/language-reference/keywords/static.md) として宣言されている場合は、インスタンスを作成できず、クライアント コードはクラス自体を介してのみクラスにアクセスできます。 詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  

## <a name="reference-types"></a>参照型  
[class](../../../csharp/language-reference/keywords/class.md) として定義された型は、*参照型*です。 実行時には、参照型の変数を宣言すると、[new](../../../csharp/language-reference/keywords/new.md) 演算子を使用してクラスのインスタンスを明示的に作成するまで、変数には値 [null](../../../csharp/language-reference/keywords/null.md) が格納されています。または、次の例に示すように、別の場所で作成されたオブジェクトを代入することもできます。

```csharp
MyClass mc = new MyClass();
MyClass mc2 = mc;
```

オブジェクトが作成されると、マネージ ヒープ上でメモリが割り当てられ、変数にはそのオブジェクトの場所への参照のみが格納されます。 マネージ ヒープを使用する型では、メモリの割り当て時と、CLR の自動メモリ管理機能 (*ガベージ コレクション*) による再要求時の両方についてオーバーヘッドが発生します。 しかし、ガベージ コレクションも高度に最適化されるため、ほとんどのシナリオでは、パフォーマンス上の問題が発生することはありません。 ガベージ コレクションの詳細については、「[自動メモリ管理とガベージ コレクション](../../../standard/garbage-collection/gc.md)」を参照してください。  
  
## <a name="declaring-classes"></a>クラスの宣言  
 クラスは、次の例に示すように、[class](../../../csharp/language-reference/keywords/class.md) キーワードを使用して宣言します。

 ```csharp
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 `class` キーワードは、アクセス レベルの後に配置します。 この例では、[public](../../../csharp/language-reference/keywords/public.md) が使用されているため、誰でもこのクラスのインスタンスを作成できます。 `class` キーワードの後にクラスの名前を記述します。 定義の残りの部分がクラス本体で、そこで動作とデータを定義します。 クラスのフィールド、プロパティ、メソッド、およびイベントは*クラス メンバー*と総称されます。  
  
## <a name="creating-objects"></a>オブジェクトの作成  
 クラスとオブジェクトは、同義的に使用されることがありますが、これらは異なるものです。 クラスはオブジェクトの型を定義しますが、オブジェクト自体ではありません。 オブジェクトは、クラスに基づく具体的なエンティティであり、クラスのインスタンスと呼ばれることもあります。  
  
 オブジェクトを作成するには、次のように、[new](../../../csharp/language-reference/keywords/new.md) キーワードの後にオブジェクトの基になるクラスの名前を指定します。  

 ```csharp
 Customer object1 = new Customer();
 ```
  
 クラスのインスタンスを作成すると、そのオブジェクトへの参照が返されます。 前の例の `object1` は、`Customer` に基づくオブジェクトへの参照です。 この参照は、新しいオブジェクトを参照しますが、オブジェクト データ自体を含みません。 実際、オブジェクト参照は、オブジェクトを作成しなくても作成できます。  
  
  ```csharp
  Customer object2;
  ```
  
 上のような、オブジェクトを参照しないオブジェクト参照を作成するのはお勧めしません。実行時にこのような参照を通じてオブジェクトへのアクセスを試みると失敗するからです。 ただし、新しいオブジェクトを作成するか、既存のオブジェクトに割り当てると、このような参照でオブジェクトを参照できるようになります。次に例を示します。  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
 ```
  
 上のコードでは、同じオブジェクトを参照する 2 つのオブジェクト参照が作成されます。 そのため、`object3` を通じて行われたオブジェクトの変更は、後で `object4` を使用するときに反映されます。 これは、クラスに基づくオブジェクトが参照によって参照されるからです。このためクラスは参照型と呼ばれています。  
  
## <a name="class-inheritance"></a>クラスの継承  

 クラスは、オブジェクト指向プログラミングの基本的な特性である "*継承*" を完全にサポートします。 クラスを作成するときは、[sealed](../../../csharp/language-reference/keywords/sealed.md) として定義されているものを除く、他のすべてのインターフェイスまたはクラスから継承できます。また、作成したクラスから他のクラスを継承し、クラスの仮想メソッドをオーバーライドすることもできます。

 継承は、*派生*を使用して行われます。派生とは、データの動作の継承元である*基底クラス*を使用してクラスを宣言することを意味します。 基底クラスは、派生クラス名の後に、コロンと基底クラス名を追加して指定します。次に例を示します。  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```
  
 クラスで基底クラスを宣言している場合、基底クラスのすべてのメンバー (コンストラクター以外) が継承されます。 詳細については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。
  
 C++ と異なり、C# のクラスは 1 つの基底クラスから直接継承することしかできません。 ただし、基底クラス自体が別のクラスを継承している場合があるため、1 つのクラスに複数の基底クラスが間接的に継承されることもあります。 さらに、クラスは複数のインターフェイスを直接実装できます。 詳細については、「[インターフェイス](../../../csharp/programming-guide/interfaces/index.md)」を参照してください。  
  
 クラスは[抽象](../../../csharp/language-reference/keywords/abstract.md)としても宣言できます。 抽象クラスには、シグネチャ定義が存在し、実装は存在しない抽象メソッドが含まれています。 抽象クラスはインスタンス化できません。 抽象クラスを使用するには、抽象メソッドを実装する派生クラスを介する必要があります。 これとは対照的に、[シール](../../../csharp/language-reference/keywords/sealed.md) クラスは、他のクラスに派生させることはできません。 詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。  
  
 クラス定義は、別々のソース ファイルに分割できます。 詳細については、「[部分クラスと部分メソッド](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。  
  
## <a name="description"></a>説明  
 次の例では、フィールド、メソッド、およびコンストラクターという特殊なメソッドをそれぞれ 1 つずつ含むパブリック クラスを定義しています。 詳細については、「[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)」を参照してください。 このクラスは、`new` キーワードによってインスタンス化されます。  
  
## <a name="example"></a>例  
 [!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)] 
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [オブジェクト指向プログラミング](../concepts/object-oriented-programming.md)  
 [ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [メンバー](../../../csharp/programming-guide/classes-and-structs/members.md)  
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [ファイナライザー](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [オブジェクト](../../../csharp/programming-guide/classes-and-structs/objects.md)
