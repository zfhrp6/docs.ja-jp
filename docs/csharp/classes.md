---
title: "クラス - C# ガイド"
description: "クラスの型と、クラスを作成する方法について説明します"
keywords: .NET, .NET Core, C#
author: BillWagner
ms.author: wiwagn
ms.date: 10/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.translationtype: HT
ms.sourcegitcommit: b041fbec3ff22157d00af2447e76a7ce242007fc
ms.openlocfilehash: 13cbd3a5b53ea9b0f1acb22684b6a28639d00751
ms.contentlocale: ja-jp
ms.lasthandoff: 09/14/2017

---

# <a name="classes"></a>クラス
*クラス*とは、他の型、メソッド、およびイベントの変数をまとめてグループ化することで独自のカスタム型を作成できる構成要素です。 クラスは設計図に似ています。 型の動作とデータを定義します。 クラスが静的として宣言されていない場合、クライアント コードでは、*オブジェクト*または*インスタンス*を作成して変数に割り当てることでクラスを使用できます。 変数は、その変数への参照がすべてスコープ外になるまで、メモリ内に保持されます。 すべてスコープ外になったとき、CLR により、ガベージ コレクションの対象となるようにマークされます。 クラスが[静的](language-reference/keywords/static.md)として宣言されている場合、メモリ内には 1 つのコピーだけが存在し、クライアント コードは*インスタンス変数*ではなくクラス自体を介してそのコピーにアクセスします。 詳細については、「[静的クラスと静的クラス メンバー](programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  

## <a name="reference-types"></a>参照型  
[class](language-reference/keywords/class.md) として定義された型は、*参照型*です。 参照型の変数を宣言した場合、実行時には、[new](language-reference/keywords/new.md) 演算子によってオブジェクトのインスタンスが明示的に作成されるまで、この変数には [null](language-reference/keywords/null.md) が格納されます。または、次の例に示すように、[new](language-reference/keywords/new.md) を使用して、どこか別の場所で作成されたオブジェクトを割り当てることもできます。  

[!code-csharp[Reference Types](../../samples/snippets/csharp/concepts/classes/reference-type.cs)]
  
オブジェクトが作成されると、マネージ ヒープ上でメモリが割り当てられ、変数にはそのオブジェクトの場所への参照のみが格納されます。 マネージ ヒープを使用する型では、メモリの割り当て時と、CLR の自動メモリ管理機能 (*ガベージ コレクション*) による再要求時の両方についてオーバーヘッドが発生します。 しかし、ガベージ コレクションも高度に最適化されるため、ほとんどのシナリオでは、パフォーマンス上の問題が発生することはありません。 ガベージ コレクションの詳細については、「[自動メモリ管理とガベージ コレクション](../standard/garbage-collection/gc.md)」を参照してください。  
  
参照型は、オブジェクト指向プログラミングの基本的な特性である*継承*を完全にサポートします。 クラスの作成時には、[シール](language-reference/keywords/sealed.md) クラスとして定義されているものを除く、他のすべてのインターフェイスまたはクラスから継承できます。また、作成したクラスから他のクラスを継承し、仮想メソッドをオーバーライドすることもできます。 詳細については、「[継承](programming-guide/classes-and-structs/inheritance.md)」を参照してください。

## <a name="declaring-classes"></a>クラスの宣言  
クラスは、次の例に示すように、[class](language-reference/keywords/class.md) キーワードを使用して宣言します。  
  
[!code-csharp[Declaring Classes](../../samples/snippets/csharp/concepts/classes/declaring-classes.cs)]  
  
**class** キーワードは、アクセス修飾子の後に配置します。 この例では、[public](language-reference/keywords/public.md) が使用されているため、だれもがこのクラスからオブジェクトを作成できます。 **class** キーワードの後にクラスの名前を記述します。 定義の残りの部分がクラス本体で、そこで動作とデータを定義します。 クラスのフィールド、プロパティ、メソッド、およびイベントは*クラス メンバー*と総称されます。  
  
## <a name="creating-objects"></a>オブジェクトの作成  
クラスはオブジェクトの型を定義しますが、オブジェクト自体ではありません。 オブジェクトは、クラスに基づく具体的なエンティティであり、クラスのインスタンスと呼ばれることもあります。  
  
オブジェクトを作成するには、次のように、[new](language-reference/keywords/new.md) キーワードの後にオブジェクトの基になるクラスの名前を指定します。  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects.cs)]   
  
クラスのインスタンスを作成すると、そのオブジェクトへの参照が返されます。 前の例の `object1` は、`Customer` に基づくオブジェクトへの参照です。 この参照は、新しいオブジェクトを参照しますが、オブジェクト データ自体を含みません。 実際、オブジェクト参照は、オブジェクトを作成しなくても作成できます。  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects2.cs)]  
  
上のような、オブジェクトを参照しないオブジェクト参照を作成するのはお勧めしません。実行時にこのような参照を通じてオブジェクトへのアクセスを試みると失敗するからです。 ただし、新しいオブジェクトを作成するか、既存のオブジェクトに割り当てると、このような参照でオブジェクトを参照できるようになります。次に例を示します。  
  
[!code-csharp[Creating Objects](../../samples/snippets/csharp/concepts/classes/creating-objects3.cs)]  
  
上のコードでは、同じオブジェクトを参照する 2 つのオブジェクト参照が作成されます。 そのため、`object3` を通じて行われたオブジェクトの変更は、その後、`object4`を使用する際にも反映されます。 これは、クラスに基づくオブジェクトが参照によって参照されるからです。このためクラスは参照型と呼ばれています。  
  
## <a name="class-inheritance"></a>クラスの継承  
継承は、*派生*を使用して行われます。派生とは、データの動作の継承元である*基底クラス*を使用してクラスを宣言することを意味します。 基底クラスは、派生クラス名の後に、コロンと基底クラス名を追加して指定します。次に例を示します。  
  
[!code-csharp[Inheritance](../../samples/snippets/csharp/concepts/classes/inheritance.cs)]  
  
クラスで基底クラスを宣言している場合、基底クラスのすべてのメンバー (コンストラクター以外) が継承されます。  
  
C++ と異なり、C# のクラスは 1 つの基底クラスから直接継承することしかできません。 ただし、基底クラス自体が別のクラスを継承している場合があるため、1 つのクラスに複数の基底クラスが間接的に継承されることもあります。 さらに、クラスは複数のインターフェイスを直接実装できます。 詳細については、「[インターフェイス](programming-guide/interfaces/index.md)」を参照してください。  
  
クラスは[抽象](language-reference/keywords/abstract.md)としても宣言できます。 抽象クラスには、シグネチャ定義が存在し、実装は存在しない抽象メソッドが含まれています。 抽象クラスはインスタンス化できません。 抽象クラスを使用するには、抽象メソッドを実装する派生クラスを介する必要があります。 これとは対照的に、[シール](language-reference/keywords/sealed.md) クラスは、他のクラスに派生させることはできません。 詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。  
  
クラス定義は、別々のソース ファイルに分割できます。 詳細については、「[部分クラス定義](programming-guide/classes-and-structs/partial-classes-and-methods.md)」を参照してください。  
  
 
## <a name="example"></a>例
次の例では、フィールド、メソッド、およびコンストラクターという特殊なメソッドをそれぞれ 1 つずつ含むパブリック クラスを定義しています。 詳細については、「[コンストラクター](programming-guide/classes-and-structs/constructors.md)」を参照してください。 **new** キーワードによってクラスがインスタンス化されます。

[!code-csharp[Class Example](../../samples/snippets/csharp/concepts/classes/class-example.cs)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
詳細については、「[C# 言語の仕様](language-reference/language-specification/index.md)」を参照してください。 言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。
  
## <a name="see-also"></a>関連項目  
[C# プログラミング ガイド](programming-guide/index.md)   
[ポリモーフィズム](programming-guide/classes-and-structs/polymorphism.md)   
[クラスと構造体のメンバー](programming-guide/classes-and-structs/members.md)   
[クラスと構造体のメソッド](programming-guide/classes-and-structs/methods.md)   
[コンストラクター](programming-guide/classes-and-structs/constructors.md)   
[ファイナライザー](programming-guide/classes-and-structs/destructors.md)   
[オブジェクト](programming-guide/classes-and-structs/objects.md)


