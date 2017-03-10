---
title: "部分クラスと部分メソッド (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, 部分クラスおよびメソッド"
  - "部分クラス [C#]"
  - "部分メソッド [C#]"
ms.assetid: 804cecb7-62db-4f97-a99f-60975bd59fa1
caps.latest.revision: 35
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 35
---
# 部分クラスと部分メソッド (C# プログラミング ガイド)
[クラス](../../../csharp/language-reference/keywords/class.md)や[構造体](../../../csharp/language-reference/keywords/struct.md)、[インターフェイス](../../../csharp/language-reference/keywords/interface.md)やメソッドの定義を、複数のソース ファイルに分割できます。  各ソース ファイルには、型やメソッドの定義のセクションが含まれ、分割されたすべての部分はアプリケーションのコンパイル時に結合されます。  
  
## 部分クラス  
 クラス定義を分割するのが望ましいのは、次のような場合です。  
  
-   大型プロジェクトを開発する際に、クラスを別個のファイルに分割すると、複数のプログラマが同時にそのクラスの作業を行うことができます。  
  
-   自動生成ソースを使用する際に、ソース ファイルを再作成せずにコードをクラスに追加できます。  Visual Studio では、Windows フォームや Web サービス ラッパー コードなどを作成するときにこのアプローチを使用します。  Visual Studio によって作成されたファイルを変更せずに、これらのクラスを使用するコードを作成できます。  
  
-   クラス定義を分割するには、次のように [partial](../../../csharp/language-reference/keywords/partial-type.md) キーワード修飾子を使用します。  
  
 [!code-cs[csProgGuideObjects#26](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/partial-classes-and-meth_1.cs)]  
  
 `partial` キーワードは、クラス、構造体、またはインターフェイスの他の部分を名前空間内で定義できることを示します。  `partial` キーワードは、すべての部分で使用する必要があります。  最終的な型を形成するためには、コンパイル時にすべての部分が用意できている必要があります。  また、すべての部分で同じアクセシビリティ \(`public` や `private` など\) を使用する必要があります。  
  
 抽象と宣言された部分がある場合、型全体が抽象と見なされます。  シールと宣言された部分がある場合、型全体がシールと見なされます。  また、基本型を宣言する部分がある場合は、型全体が該当するクラスを継承します。  
  
 基本クラスを指定する部分はすべて一致する必要がありますが、基本クラスを省略する部分も基本型を継承します。  部分は別の基本インターフェイスを指定でき、すべての部分宣言で示されたすべてのインターフェイスが最終的な型によって実装されます。  部分定義で宣言されたクラス、構造体、インターフェイスの各メンバーは、他のすべての部分で利用できます。  最終的な型は、コンパイル時にすべての部分を結合して形成されます。  
  
> [!NOTE]
>  `partial` 識別子は、デリゲートや列挙宣言では使用できません。  
  
 次の例は、入れ子にされた型は、それを包含する型自体が partial でない場合でも、partial にできることを示しています。  
  
 [!code-cs[csProgGuideObjects#25](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/partial-classes-and-meth_2.cs)]  
  
 部分型定義の属性は、コンパイル時に結合されます。  たとえば、次の宣言について考えてみます。  
  
 [!code-cs[csProgGuideObjects#23](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/partial-classes-and-meth_3.cs)]  
  
 これらは、次の宣言と等価です。  
  
 [!code-cs[csProgGuideObjects#24](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/partial-classes-and-meth_4.cs)]  
  
 各部分型定義に含まれる次の要素は、すべて結合されます。  
  
-   XML コメント  
  
-   インターフェイス  
  
-   ジェネリック型パラメーター属性  
  
-   クラス属性  
  
-   メンバー  
  
 たとえば、次の宣言について考えてみます。  
  
 [!code-cs[csProgGuideObjects#21](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/partial-classes-and-meth_5.cs)]  
  
 これらは、次の宣言と等価です。  
  
 [!code-cs[csProgGuideObjects#22](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/partial-classes-and-meth_6.cs)]  
  
### 制約  
 部分クラス定義の使用時には、以下の規則が適用されます。  
  
-   同じ型の部分である部分型定義はすべて `partial` で修飾する必要があります。  たとえば、次のクラス宣言はエラーになります。  
  
     [!code-cs[csProgGuideObjects#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/partial-classes-and-meth_7.cs)]  
  
-   `partial` 修飾子は、`class`、`struct`、または `interface` キーワードの直前にのみ配置できます。  
  
-   入れ子にされた部分型は、次の例で示すように、部分型定義で宣言できます。  
  
     [!code-cs[csProgGuideObjects#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/partial-classes-and-meth_8.cs)]  
  
-   同じ型の部分である部分型定義はすべて同じアセンブリまたは同じモジュール \(.exe ファイルまたは .dll ファイル\) 内で定義する必要があります。  部分定義は、複数のモジュールにまたがることができません。  
  
-   クラス名とジェネリック型パラメーターはすべての部分型定義で一致する必要があります。  ジェネリック型は partial にできます。  部分宣言では、それぞれ同じパラメーター名を同じ順序で使用する必要があります。  
  
-   以下のキーワードは、部分型定義では省略できますが、ある 1 つの部分型定義に存在する場合は、同じ型の別の部分定義で指定されているキーワードと競合できません。  
  
    -   [public](../../../csharp/language-reference/keywords/public.md)  
  
    -   [private](../../../csharp/language-reference/keywords/private.md)  
  
    -   [protected](../../../csharp/language-reference/keywords/protected.md)  
  
    -   [internal](../../../csharp/language-reference/keywords/internal.md)  
  
    -   [abstract](../../../csharp/language-reference/keywords/abstract.md)  
  
    -   [sealed](../../../csharp/language-reference/keywords/sealed.md)  
  
    -   基本クラス  
  
    -   [new](../../../csharp/language-reference/keywords/new.md) 修飾子 \(入れ子にされた部分\)  
  
    -   ジェネリック制約  
  
         詳細については、「[型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)」を参照してください。  
  
## 例 1  
  
### Description  
 次の例では、クラス `CoOrds` のフィールドとコンストラクターを 1 つの部分クラス定義で宣言し、メンバー `PrintCoOrds` を別の部分クラス定義で宣言しています。  
  
### コード  
 [!code-cs[csProgGuideObjects#17](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/partial-classes-and-meth_9.cs)]  
  
## 例 2  
  
### Description  
 次の例は、部分構造体と部分インターフェイスも開発できることを示しています。  
  
### コード  
 [!code-cs[csProgGuideObjects#18](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/partial-classes-and-meth_10.cs)]  
  
## 部分メソッド  
 部分クラスまたは構造体に部分メソッドを含めることができます。  クラスのある部分にメソッドのシグネチャが含まれます。  同じ部分または別の部分に、オプションの実装を定義できます。  実装を備えていない場合、メソッドとメソッドに対するすべての呼び出しは、コンパイル時に削除されます。  
  
 部分メソッドを使用すると、クラスのある部分の実装者はイベントに似た方法でメソッドの定義を行うことができます。  クラスの別の部分の実装者は、メソッドを実装するかどうかを決定できます。  メソッドを実装しないと、コンパイラはメソッド シグネチャとメソッドに対するすべての呼び出しを削除します。  メソッドへの呼び出しは、呼び出しでの引数の評価により発生するすべての結果を含め、ランタイムには影響を与えません。  したがって、部分クラス内のコードは、実装を備えていない部分メソッドでも自由に使用できます。  呼び出されるメソッドが実装されていなくても、コンパイル時のエラーやランタイム エラーにはなりません。  
  
 部分メソッドは、生成されるコードをカスタマイズする方法として特に便利です。  メソッドの名前とシグネチャを予約できるので、生成されるコードはメソッドを呼び出すことができ、メソッドを実装するかどうかは開発者が決定できます。  部分クラスと同じように部分メソッドでも、コード ジェネレーターが作成したコードと開発者である人間が作成したコードがランタイム コストなしで連携できます。  
  
 部分メソッドの宣言は、定義と実装の 2 つの部分から成ります。  これらは部分クラスの別々の部分にあっても同じ部分にあってもかまいません。  実装宣言がない場合は、定義宣言とメソッドに対するすべての呼び出しの両方が、コンパイラでの最適化によって除外されます。  
  
```  
// Definition in file1.cs  
partial void onNameChanged();  
  
// Implementation in file2.cs  
partial void onNameChanged()  
{  
  // method body  
}  
```  
  
-   部分メソッドの宣言はコンテキスト キーワード [partial](../../../csharp/language-reference/keywords/partial-type.md) で始まる必要があり、メソッドは [void](../../../csharp/language-reference/keywords/void.md) を返す必要があります。  
  
-   部分メソッドには [ref](../../../csharp/language-reference/keywords/ref.md) パラメーターを使用できますが、[out](../../../csharp/language-reference/keywords/out.md) パラメーターは使用できません。  
  
-   部分メソッドは暗黙的に [private](../../../csharp/language-reference/keywords/private.md) です。したがって部分メソッドを [virtual](../../../csharp/language-reference/keywords/virtual.md) にすることはできません。  
  
-   部分メソッドを [extern](../../../csharp/language-reference/keywords/extern.md) にすることはできません。部分メソッドの定義なのか実装なのかは、本体の存在で決まるためです。  
  
-   部分メソッドには [static](../../../csharp/language-reference/keywords/static.md) 修飾子と [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 修飾子を使用できます。  
  
-   部分メソッドをジェネリックにできます。  制約は部分メソッドの定義宣言に置き、必要に応じて実装宣言で繰り返すことができます。  パラメーター名と型パラメーター名は、定義宣言と実装宣言で同じである必要はありません。  
  
-   [デリゲート](../../../csharp/language-reference/keywords/delegate.md)は、定義および実装されている部分メソッドには使用できますが、定義されているのみの部分メソッドには使用できません。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラス](../../../csharp/programming-guide/classes-and-structs/classes.md)   
 [構造体](../../../csharp/programming-guide/classes-and-structs/structs.md)   
 [インターフェイス](../../../csharp/programming-guide/interfaces/index.md)   
 [partial \(型\)](../../../csharp/language-reference/keywords/partial-type.md)