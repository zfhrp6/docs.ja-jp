---
title: "Override キーワードと New キーワードによるバージョン管理 (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, override と new"
  - "C# 言語, バージョン管理"
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Override キーワードと New キーワードによるバージョン管理 (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# 言語は、異なるライブラリの[基本](../../../csharp/language-reference/keywords/base.md)クラスと派生クラスの間でも、下位互換性を維持して改良できるようにバージョン管理がデザインされています。  たとえば、C\# では、派生[クラス](../../../csharp/language-reference/keywords/class.md)のメンバーと同じ名前の新しいメンバーを基本クラスに導入することが完全にサポートされているため、予期しない動作が起こることはありません。  また、メソッドが継承メソッドをオーバーライドするかどうか、またはメソッドが同じ名前の継承メソッドを隠す新しいメソッドかどうかをクラスに明示的に記述する必要があります。  
  
 C\# では、基本クラスのメソッドと同じ名前のメソッドを派生クラスに含めることができます。  
  
-   基本クラスのメソッドは、[仮想](../../../csharp/language-reference/keywords/virtual.md)と定義する必要があります。  
  
-   派生クラスのメソッドの前に [new](../../../csharp/language-reference/keywords/new.md) キーワードや [override](../../../csharp/language-reference/keywords/override.md) キーワードが記述されていない場合、コンパイラは警告メッセージを表示し、そのメソッドは `new` キーワードが存在するように動作します。  
  
-   派生クラスのメソッドの前に `new` キーワードが記述されている場合、そのメソッドは、基本クラスのメソッドから独立したものとして定義されます。  
  
-   派生クラスのメソッドの前に `override` キーワードが記述されている場合、派生クラスのオブジェクトは、基本クラスのメソッドではなく、派生クラスのメソッドを呼び出します。  
  
-   `base` キーワードを使用すると、派生クラスの中から基本クラスのメソッドを呼び出すことができます。  
  
-   `override`、`virtual`、および `new` の各キーワードは、プロパティ、インデクサー、およびイベントにも適用できます。  
  
 C\# のメソッドは、既定で非仮想メソッドです。  メソッドが仮想と宣言されている場合、そのメソッドを継承するクラスでは、固有のバージョンを実装できます。  メソッドを仮想メソッドにするには、`virtual` 修飾子を基本クラスのメソッド宣言で使用します。  その場合、派生クラスでは、`override` キーワードを使用して基本クラスの仮想メソッドをオーバーライドすることも、`new` キーワードを使用して基本クラスの仮想メソッドを隠すこともできます。  `override` キーワードも `new` キーワードも指定しない場合、コンパイラは警告メッセージを表示し、派生クラスのメソッドは基本クラスのメソッドを隠します。  
  
 このことを実際に例を挙げて説明します。`GraphicsClass` という名前のクラスを A 社で作成しており、このクラスを自分のプログラムで使用するとします。  `GraphicsClass` を次に示します。  
  
 [!code-cs[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]  
  
 会社でこのクラスを使用しているので、このクラスから次のように独自のクラスを派生し、新しいメソッドを追加します。  
  
 [!code-cs[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]  
  
 作成したアプリケーションは、A 社が次のコードに示すような `GraphicsClass` の新バージョンをリリースするまで、問題なく使用できます。  
  
 [!code-cs[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]  
  
 `GraphicsClass` の新バージョンには、`DrawRectangle` という名前のメソッドが含まれています。  最初は、何の問題も発生しません。  新しいバージョンは、古いバージョンとバイナリ互換性があります。  新しいクラスがコンピューター システムにインストールされても、配置済みのソフトウェアは引き続き正常に動作します。  `DrawRectangle` メソッドへの既存の呼び出しは、派生クラスのバージョンを参照し続けます。  
  
 ただし、`GraphicsClass` の新バージョンを使ってアプリケーションを再コンパイルすると、コンパイラが警告メッセージを表示します \(CS0108\)。  この警告の内容は、`DrawRectangle` メソッドをアプリケーションでどのように動作させるかを検討する必要があるというものです。  
  
 自分のメソッドで新しい基本クラスのメソッドをオーバーライドする場合は、次のように `override` キーワードを使用します。  
  
 [!code-cs[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]  
  
 `override` キーワードにより、`YourDerivedGraphicsClass` から派生したオブジェクトは、確実に `DrawRectangle` の派生クラス バージョンを使用します。  `YourDerivedGraphicsClass` から派生したオブジェクトは、次のように base キーワードを使用して、`DrawRectangle` の基本クラス バージョンに引き続きアクセスできます。  
  
 [!code-cs[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]  
  
 自分のメソッドが新しい基本クラスのメソッドをオーバーライドしないようにする場合は、次の点に注意する必要があります。  2 つのメソッドを混同しないようにするために、自分のメソッドの名前を変更します。  この作業には時間がかかり、エラーが発生しやすいので、場合によっては適切でないことがあります。  プロジェクトが比較的小規模である場合は、Visual Studio のリファクタリング オプションを使用して、メソッドの名前を変更できます。  詳細については、「[Refactoring Classes and Types \(Class Designer\)](/visual-studio/ide/refactoring-classes-and-types-class-designer)」を参照してください。  
  
 または、次のように派生クラスの定義で `new` キーワードを使用して警告を表示させないようにすることもできます。  
  
 [!code-cs[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]  
  
 `new` キーワードを使用すると、基本クラスに含まれている定義が派生クラスの定義によって隠されることがコンパイラに通知されます。  これが既定の動作です。  
  
## オーバーライドとメソッドの選択  
 クラスでメソッドに名前を付けると、名前が同じで、渡されるパラメーターと互換のパラメーターを持つ 2 つのメソッドが存在する場合など、複数のメソッドが呼び出しに対応する場合に、呼び出すのに最適なメソッドを C\# コンパイラが選択します。  次の 2 つのメソッドは互換です。  
  
 [!code-cs[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]  
  
 `Derived` のインスタンスで `DoWork` が呼び出されると、C\# コンパイラは最初に、`Derived` で当初宣言された `DoWork` のバージョンと互換性のある呼び出しを実行します。  オーバーライド メソッドは、クラスで宣言されたものと見なされません。これらは、基本クラスで宣言されたメソッドの新しい実装です。  C\# コンパイラは、`Derived` の元のメソッドにメソッド呼び出しを一致させることができない場合に限り、名前が同じで互換のパラメーターを持つ、オーバーライドされたメソッドに呼び出しを一致させようとします。  次に例を示します。  
  
 [!code-cs[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]  
  
 変数 `val` は、暗黙的に double に変換できるので、C\# コンパイラは、`DoWork(int)` の代わりに `DoWork(double)` を呼び出します。  これを回避する方法は 2 つあります。  1 つは、仮想メソッドと同じ名前を付けて新しいメソッドを宣言することを避ける方法です。  もう 1 つは、`Derived` のインスタンスを `Base` にキャストすることにより、C\# コンパイラに対して、基本クラスのメソッド リストを検索して、仮想メソッドを呼び出すように指示する方法です。  メソッドが仮想であるため、`Derived` の `DoWork(int)` の実装が呼び出されます。  次に例を示します。  
  
 [!code-cs[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]  
  
 `new` と `override`の例については、 " " を参照してください [Override キーワードと New キーワードを使用する場合について](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [メソッド](../../../fsharp/language-reference/members/methods.md)   
 [継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)