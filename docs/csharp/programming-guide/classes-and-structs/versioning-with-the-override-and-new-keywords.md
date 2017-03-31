---
title: "Override キーワードと New キーワードによるバージョン管理 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
caps.latest.revision: 25
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b464b4c395af093bb9124bb671c5c212c750f497
ms.lasthandoff: 03/13/2017

---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a>Override キーワードと New キーワードによるバージョン管理 (C# プログラミング ガイド)
C# 言語は、異なるライブラリ内の[基底](../../../csharp/language-reference/keywords/base.md)クラスと派生クラス間でのバージョン管理を進化させると同時に、下位互換性も維持されるよう設計されています。 そのため、たとえば、派生クラスのメンバーと同じ名前を使用して基底[クラス](../../../csharp/language-reference/keywords/class.md)の新規メンバーが導入されても、C# では完全にサポートされ、予期しない動作は発生しません。 ただしこのことは、メソッドが派生メソッドをオーバーライドするためのものなのか、それとも同じ名前の派生メソッドを非表示にする新規メソッドなのかを、クラスで明示的に記述しなければならないということでもあります。  
  
 C# では、派生クラスに基底クラスと同じ名前のメソッドを含めることができます。  
  
-   基底クラスのメソッドは、[virtual](../../../csharp/language-reference/keywords/virtual.md) で定義する必要があります。  
  
-   派生クラスのメソッドの前に [new](../../../csharp/language-reference/keywords/new.md) または [override](../../../csharp/language-reference/keywords/override.md) キーワードがない場合、コンパイラは警告を発し、メソッドは `new` キーワードが存在する場合と同様に動作します。  
  
-   派生クラスのメソッドの前に `new` キーワードがある場合、そのメソッドは基底クラスのメソッドに依存しないメソッドとして定義されます。  
  
-   派生クラスのメソッドの前に `override` キーワードがある場合、派生クラスのオブジェクトは、基底クラスのメソッドの代わりにそのメソッドを呼び出します。  
  
-   基底クラスのメソッドは、`base` キーワードを使用して派生クラス内から呼び出すことができます。  
  
-   `override`、 `virtual`、および `new` キーワードは、プロパティ、インデクサー、およびイベントにも適用できます。  
  
 既定では、C# のメソッドは仮想ではありません。 メソッドが仮想として宣言されている場合、そのメソッドを継承しているすべてのクラスは、独自のバージョンを実装できます。 仮想メソッドを仮想にするには、基底クラスのメソッド宣言で `virtual` 修飾子を使用します。 その後、派生クラスは `override` キーワードを使用して基底の仮想メソッドをオーバーライドするか、または `new` キーワードを使用して基底クラスの仮想メソッドを非表示にできます。 `override` と `new` のいずれのキーワードも指定されていない場合、コンパイラは警告を発し、派生クラスのメソッドは基底クラスのメソッドを非表示にします。  
  
 実演的な例として、会社 A が `GraphicsClass` というクラスを作成し、プログラムで使用する場合について説明します。 次のコードは `GraphicsClass` です。  
  
 [!code-cs[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]  
  
 この会社では、このクラスを使用して独自のクラスを派生させ、新しいメソッドを追加しました。  
  
 [!code-cs[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]  
  
 このアプリケーションは、会社 A が `GraphicsClass` の新しいバージョン (次のようなコード) をリリースするまでは、問題なく使用できていました。  
  
 [!code-cs[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]  
  
 `GraphicsClass` の新バージョンに、`DrawRectangle` というメソッドが含まれていますが、 当初は何も起こりませんでした。 新バージョンでは、旧バージョンとのバイナリ互換性が維持されています。 配置したソフトウェアは、それらのコンピューター システムに新しいクラスがインストールされても、機能し続けます。 `DrawRectangle` メソッドへの既存の呼び出しは、派生クラス内のバージョンを引き続き参照します。  
  
 しかし、`GraphicsClass` の新バージョンを使用してアプリケーションを再コンパイルした途端、コンパイラから警告 (CS0108) が発せられます。 この警告は、アプリケーション内での `DrawRectangle` メソッドの動作方法を検討する必要があることを示しています。  
  
 このメソッドで新しい基底クラスをオーバーライドする場合は、`override` キーワードを使用します。  
  
 [!code-cs[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]  
  
 `override` キーワードを使用すると、`YourDerivedGraphicsClass` から派生したすべてのオブジェクトは、派生クラス バージョンの `DrawRectangle` を使用するようになります。 `YourDerivedGraphicsClass` から派生したオブジェクトは、base キーワードを使用することで基底クラス バージョンの `DrawRectangle` にもアクセスできます。  
  
 [!code-cs[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]  
  
 このメソッドで新しい基底クラス メソッドをオーバーライドしない場合には、次の考慮事項が適用されます。 2 つのメソッド間の混乱を避けるために、メソッドの名前を変更できます。 これは時間がかかるうえにエラーが起こりやすいため、場合によっては実用的でない可能性があります。 ただし、プロジェクトが比較的小さい場合は、Visual Studio のリファクタリング オプションを使用して、メソッドの名前を変更することができます。 詳しくは、「[クラスおよび型のリファクタリング (クラス デザイナー)](https://docs.microsoft.com/visualstudio/ide/refactoring-classes-and-types-class-designer)」をご覧ください。  
  
 なお、派生クラスの定義内で `new` キーワードを使用することで、警告を回避することもできます。  
  
 [!code-cs[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]  
  
 `new` キーワードを使用すると、その定義によって基底クラス内の定義が非表示にされることがコンパイラに伝えられます。 これが既定の動作です。  
  
## <a name="override-and-method-selection"></a>オーバーライドとメソッド選択  
 クラスでメソッドを指定したときに、その呼び出しと互換性のあるメソッドが 2 つ以上ある場合、C# コンパイラはどのメソッドを呼び出すのが最適かを選択します (たとえば、同じ名前のメソッドが 2 つあり、そのパラメーターと、渡されたパラメーターとの間に互換性がある場合)。 たとえば、次の各メソッドには互換性があります。  
  
 [!code-cs[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]  
  
 `Derived` のインスタンスで `DoWork` が呼び出されると、C# コンパイラはまず、`Derived` で最初に宣言された `DoWork` のバージョンと互換性がある呼び出しを実行しようとします。 オーバーライド メソッドは、クラスで宣言されたものとは見なされません。これらは、基底クラスで宣言されたメソッドの新しい実装です。 C# コンパイラは、メソッドの呼び出しを `Derived` にある元のメソッドと対応付けできない場合にのみ、その呼び出しを、同じ名前と互換パラメーターを持つオーバーライド メソッドに対応付けます。 例:  
  
 [!code-cs[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]  
  
 変数 `val` は double 型に暗黙的に変換できるので、C# コンパイラは `DoWork(int)` の代わりに `DoWork(double)` を呼び出します。 この問題を回避する方法は 2 つあります。 1 つ目は、仮想メソッドと同じ名前の新しいメソッドを宣言しないようにすることです。 2 つ目は、`Derived` のインスタンスを `Base` にキャストすることで、C# コンパイラに基底クラス メソッドのリストを検索させ、仮想メソッドを呼び出すようにすることです。 メソッドが仮想なので、`Derived` にある `DoWork(int)` の実装が呼び出されます。 例:  
  
 [!code-cs[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]  
  
 `new` と `override` の例について詳しくは、「[Override キーワードと New キーワードを使用する場合について](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
