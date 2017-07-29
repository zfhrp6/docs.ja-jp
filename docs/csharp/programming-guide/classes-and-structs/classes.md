---
title: "クラス (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
caps.latest.revision: 40
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eedb087f177b1bff6f4d4177cd56ac4cca016490
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="classes-c-programming-guide"></a>クラス (C# プログラミング ガイド)
*クラス*とは、他の型、メソッド、およびイベントの変数をまとめてグループ化することで独自のカスタム型を作成できる構成要素です。 クラスは設計図に似ています。 型の動作とデータを定義します。 クラスが静的として宣言されていない場合、クライアント コードでは、*オブジェクト*または*インスタンス*を作成して変数に割り当てることでクラスを使用できます。 変数は、その変数への参照がすべてスコープ外になるまで、メモリ内に保持されます。 すべてスコープ外になったとき、CLR により、ガベージ コレクションの対象となるようにマークされます。 クラスが[静的](../../../csharp/language-reference/keywords/static.md)として宣言されている場合、メモリ内には 1 つのコピーだけが存在し、クライアント コードは*インスタンス変数*ではなくクラス自体を介してそのコピーにアクセスします。 詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
 構造体とは異なり、クラスは、オブジェクト指向プログラミングの基本的な特性である*継承*をサポートします。 詳細については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。  
  
## <a name="declaring-classes"></a>クラスの宣言  
 クラスは、次の例に示すように、[class](../../../csharp/language-reference/keywords/class.md) キーワードを使用して宣言します。  
  
 [!code-cs[csProgGuideObjects#79](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_1.cs)]  
  
 `class` キーワードは、アクセス レベルの後に配置します。 この例では、[public](../../../csharp/language-reference/keywords/public.md) が使用されているため、だれもがこのクラスからオブジェクトを作成できます。 `class` キーワードの後にクラスの名前を記述します。 定義の残りの部分がクラス本体で、そこで動作とデータを定義します。 クラスのフィールド、プロパティ、メソッド、およびイベントは*クラス メンバー*と総称されます。  
  
## <a name="creating-objects"></a>オブジェクトの作成  
 クラスとオブジェクトは、同義的に使用されることがありますが、これらは異なるものです。 クラスはオブジェクトの型を定義しますが、オブジェクト自体ではありません。 オブジェクトは、クラスに基づく具体的なエンティティであり、クラスのインスタンスと呼ばれることもあります。  
  
 オブジェクトを作成するには、次のように、[new](../../../csharp/language-reference/keywords/new.md) キーワードの後にオブジェクトの基になるクラスの名前を指定します。  
  
 [!code-cs[csProgGuideObjects#80](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_2.cs)]  
  
 クラスのインスタンスを作成すると、そのオブジェクトへの参照が返されます。 前の例の `object1` は、`Customer` に基づくオブジェクトへの参照です。 この参照は、新しいオブジェクトを参照しますが、オブジェクト データ自体を含みません。 実際、オブジェクト参照は、オブジェクトを作成しなくても作成できます。  
  
 [!code-cs[csProgGuideObjects#81](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_3.cs)]  
  
 上のような、オブジェクトを参照しないオブジェクト参照を作成するのはお勧めしません。実行時にこのような参照を通じてオブジェクトへのアクセスを試みると失敗するからです。 ただし、新しいオブジェクトを作成するか、既存のオブジェクトに割り当てると、このような参照でオブジェクトを参照できるようになります。次に例を示します。  
  
 [!code-cs[csProgGuideObjects#82](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_4.cs)]  
  
 上のコードでは、同じオブジェクトを参照する 2 つのオブジェクト参照が作成されます。 そのため、`object3` を通じて行われたオブジェクトの変更は、その後、`object4`を使用する際にも反映されます。 これは、クラスに基づくオブジェクトが参照によって参照されるからです。このためクラスは参照型と呼ばれています。  
  
## <a name="class-inheritance"></a>クラスの継承  
 継承は、*派生*を使用して行われます。派生とは、データの動作の継承元である*基底クラス*を使用してクラスを宣言することを意味します。 基底クラスは、派生クラス名の後に、コロンと基底クラス名を追加して指定します。次に例を示します。  
  
 [!code-cs[csProgGuideObjects#83](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_5.cs)]  
  
 クラスで基底クラスを宣言している場合、基底クラスのすべてのメンバー (コンストラクター以外) が継承されます。  
  
 C++ と異なり、C# のクラスは 1 つの基底クラスから直接継承することしかできません。 ただし、基底クラス自体が別のクラスを継承している場合があるため、1 つのクラスに複数の基底クラスが間接的に継承されることもあります。 さらに、クラスは複数のインターフェイスを直接実装できます。 詳細については、「[インターフェイス](../../../csharp/programming-guide/interfaces/index.md)」を参照してください。  
  
 クラスは[抽象](../../../csharp/language-reference/keywords/abstract.md)としても宣言できます。 抽象クラスには、シグネチャ定義が存在し、実装は存在しない抽象メソッドが含まれています。 抽象クラスはインスタンス化できません。 抽象クラスを使用するには、抽象メソッドを実装する派生クラスを介する必要があります。 これとは対照的に、[シール](../../../csharp/language-reference/keywords/sealed.md) クラスは、他のクラスに派生させることはできません。 詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。  
  
 クラス定義は、別々のソース ファイルに分割できます。 詳細については、「[部分クラスと部分メソッド](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。  
  
## <a name="description"></a>説明  
 次の例では、フィールド、メソッド、およびコンストラクターという特殊なメソッドをそれぞれ 1 つずつ含むパブリック クラスを定義しています。 詳細については、「[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)」を参照してください。 このクラスは、`new` キーワードによってインスタンス化されます。  
  
## <a name="example"></a>例  
 [!code-cs[csProgGuideObjects#84](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/classes_6.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [オブジェクト指向プログラミング](../concepts/object-oriented-programming.md)   
 [ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)   
 [メンバー](../../../csharp/programming-guide/classes-and-structs/members.md)   
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [ファイナライザー](../../../csharp/programming-guide/classes-and-structs/destructors.md)   
 [オブジェクト](../../../csharp/programming-guide/classes-and-structs/objects.md)

