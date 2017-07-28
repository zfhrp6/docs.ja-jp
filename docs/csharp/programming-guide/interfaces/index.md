---
title: "インターフェイス (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- interfaces [C#]
- C# language, interfaces
ms.assetid: 2feda177-ce11-432d-81b4-d50f5f35fd37
caps.latest.revision: 45
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0552cea71f66ba8c299b1706cab6778c9e3367c9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="interfaces-c-programming-guide"></a>インターフェイス (C# プログラミング ガイド)
インターフェイスには、[クラス](../../../csharp/language-reference/keywords/class.md)または[構造体](../../../csharp/language-reference/keywords/struct.md)で実装できる関連機能のグループの定義が含まれます。  
  
 インターフェイスを使用すると、たとえば、クラス内の複数のソースからの動作を含めることができます。 C# ではクラスの複数の継承がサポートされないため、この機能は重要です。 また、構造体の継承をシミュレートする場合はインターフェイスを使用する必要があります。これは、実際に別の構造体またはクラスから継承することができないためです。  
  
 インターフェイスを定義するには、次の例に示すように、[interface](../../../csharp/language-reference/keywords/interface.md) キーワードを使用します。  
  
 [!code-cs[csProgGuideInheritance#47](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_1.cs)]  
  
 <xref:System.IEquatable%601> インターフェイスを実装するすべてのクラスまたは構造体は、インターフェイスで指定された署名に一致する <xref:System.IEquatable%601.Equals%2A> メソッドの定義を含む必要があります。 したがって、`IEquatable<T>` を実装するクラスが `Equals` メソッドを含むと想定したうえで、これを使用してクラスの 1 つのインスタンスが同じクラスの別のインスタンスと等しいかどうかを判定できます。  
  
 `IEquatable<T>` の定義は `Equals` の実装を提供しません。 インターフェイスは、署名のみを定義します。 つまり、C# のインターフェイスは、すべてのメソッドが抽象的である抽象クラスに似ています。 クラスまたは構造体は複数のインターフェイスを実装できます。ただし、クラスが継承できるのは、抽象的かどうかに関係なく、1 つのクラスのみです。 したがって、インターフェイスを使用することにより、クラス内の複数のソースの動作を含めることができます。  
  
 抽象クラスの詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。  
  
 インターフェイスには、メソッド、プロパティ、イベント、インデクサー、またはこれらの 4 種類のメンバーの任意の組み合わせを含めることができます。 例へのリンクについては、「[関連項目](../../../csharp/programming-guide/interfaces/index.md#BKMK_RelatedSections)」を参照してください。 インターフェイスには、定数、フィールド、演算子、インスタンス コンストラクター、ファイナライザー、または型を含めることはできません。 インターフェイスのメンバーは、自動的にパブリックに設定され、アクセス修飾子を含むことはできません。 メンバーを [static](../../../csharp/language-reference/keywords/static.md) として宣言することもできません。  
  
 インターフェイスのメンバーを実装するには、実装するクラスの対応するメンバーがパブリックかつ非静的であり、インターフェイスのメンバーと同じ名前および署名を持つ必要があります。  
  
 クラスまたは構造体でインターフェイスを実装するときは、インターフェイスで定義されているすべてのメンバーの実装を提供する必要があります。 インターフェイス自体は、基本クラスの機能を継承できるようにクラスまたは構造体が継承できる機能を提供しません。 ただし、基本クラスでインターフェイスが実装される場合、その基本クラスから派生するすべてのクラスはその実装を継承します。  
  
 IEquatable<T\> インターフェイスの実装例を次に示します。 実装するクラスの `Car` は、<xref:System.IEquatable%601.Equals%2A> メソッドの実装を提供する必要があります。  
  
 [!code-cs[csProgGuideInheritance#48](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interfaces_2.cs)]  
  
 クラスのプロパティとインデクサーでは、インターフェイスに定義されているプロパティまたはインデクサーの追加のアクセサーを定義できます。 たとえば、インターフェイスで [get](../../../csharp/language-reference/keywords/get.md) アクセサーを持つプロパティを宣言するとします。 このインターフェイスを実装するクラスでは、`get` アクセサーと [set](../../../csharp/language-reference/keywords/set.md) アクセサーの両方を持つ同じプロパティを宣言できます。 ただし、プロパティまたはインデクサーで明示的な実装を使用する場合は、これらのアクセサーが一致する必要があります。 明示的な実装の詳細については、「[明示的なインターフェイス実装](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)」および「[インターフェイスのプロパティ](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)」を参照してください。  
  
 インターフェイスは、他のインターフェイスを実装できます。 クラスは、継承する基底クラスまたは他のインターフェイスが実装するインターフェイスを介して、インターフェイスを複数回含めることができます。 ただし、クラスでインターフェイスの実装を提供できるのは 1 回のみであり、それもクラスでクラスの定義の一部としてインターフェイスを宣言する場合 (`class ClassName : InterfaceName`) に限られます。 インターフェイスを実装する基本クラスを継承することによってインターフェイスを継承する場合、基本クラスは、そのインターフェイスのメンバーの実装を提供します。 ただし、派生クラスでは、継承された実装を使用する代わりに、インターフェイスのメンバーを再実装できます。  
  
 また、基本クラスでは、仮想メンバーを使用して、インターフェイスのメンバーを実装することもできます。 その場合、派生クラスでは、仮想メンバーをオーバーライドすることでインターフェイスの動作を変更できます。 仮想メンバーの詳細については、「[ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)」を参照してください。  
  
## <a name="interfaces-summary"></a>インターフェイスの概要  
 インターフェイスは、次の特性を持ちます。  
  
-   インターフェイスは、抽象基本クラスに似ています。 インターフェイスを実装するすべてのクラスまたは構造体では、そのすべてのメンバーを実装する必要があります。  
  
-   インターフェイスを直接インスタンス化することはできません。 そのメンバーは、インターフェイスを実装する任意のクラスまたは構造体によって実装されます。  
  
-   インターフェイスには、イベント、インデクサー、メソッド、およびプロパティを含めることができます。  
  
-   インターフェイスには、メソッドの実装は含まれません。  
  
-   クラスまたは構造体は、複数のインターフェイスを実装できます。 クラスは、基本クラスを継承する一方で、1 つまたは複数のインターフェイスを実装できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [明示的なインターフェイスの実装](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md)  
 インターフェイスに固有のクラス メンバーを作成する方法について説明します。  
  
 [方法: インターフェイス メンバーを明示的に実装する](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-interface-members.md)  
 インターフェイスのメンバーを明示的に実装する方法の例を示します。  
  
 [方法: 2 つのインターフェイスのメンバーを明示的に実装する](../../../csharp/programming-guide/interfaces/how-to-explicitly-implement-members-of-two-interfaces.md)  
 継承を持つインターフェイスのメンバーを明示的に実装する方法の例を示します。  
  
##  <a name="BKMK_RelatedSections"></a>関連項目  
  
-   [インターフェイスのプロパティ](../../../csharp/programming-guide/classes-and-structs/interface-properties.md)  
  
-   [インターフェイスのインデクサー](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [方法: インターフェイス イベントを実装する](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)  
  
-   [継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
  
-   [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [ポリモーフィズム](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
  
-   [抽象クラスとシール クラス、およびクラス メンバー](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
  
-   [プロパティ](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [イベント](../../../csharp/programming-guide/events/index.md)  
  
-   [インデクサー](../../../csharp/programming-guide/indexers/index.md)  
  
## <a name="featured-book-chapter"></a>参考書籍の該当する章  
 「[Learning C# 3.0: Master the Fundamentals of C# 3.0 (C# 3.0 の学習: C# 3.0 の基礎を習得)](http://msdn.microsoft.com/library/orm-9780596521066-01.aspx)」の「[Interfaces (インターフェイス)](http://msdn.microsoft.com/library/orm-9780596521066-01-13.aspx)」  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)

