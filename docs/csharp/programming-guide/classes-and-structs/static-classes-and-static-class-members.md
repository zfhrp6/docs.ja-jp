---
title: "静的クラスと静的クラス メンバー (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "C# 言語, 静的クラス"
  - "C# 言語, 静的メンバー"
  - "静的クラス メンバー [C#]"
  - "静的クラス [C#]"
  - "静的メンバー [C#]"
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
caps.latest.revision: 49
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 49
---
# 静的クラスと静的クラス メンバー (C# プログラミング ガイド)
[静的](../../../csharp/language-reference/keywords/static.md)クラスは、基本的には非静的クラスと同じですが、静的クラスはインスタンス化できないという点が異なります。  言い換えると、[new](../../../csharp/language-reference/keywords/new.md) キーワードを使用して、そのクラス型の変数を作成することはできません。  インスタンス変数がないため、静的クラスのメンバーにアクセスするには、クラス名そのものを使用します。  たとえば、`UtilityClass` という静的クラスがあり、`MethodA` というパブリック メソッドが定義されている場合、このメソッドを呼び出すには次の例のようにします。  
  
```c#  
UtilityClass.MethodA();  
```  
  
 静的クラスは、入力パラメーターに対してのみ処理を行い、内部のインスタンス フィールドを取得したり設定したりする必要のない一連のメソッドを格納する、便利なコンテナーとして使用できます。  たとえば、.NET Framework クラス ライブラリでは、静的クラス <xref:System.Math?displayProperty=fullName> に、数値演算を実行するメソッドが含まれています。これらのメソッドでは、<xref:System.Math> クラスの特定のインスタンスに固有のデータを格納または取得する必要は生じません。  つまり、次の例に示すように、クラス名とメソッド名を指定することで、クラスのメンバーを適用します。  
  
```  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
  
```  
  
 すべてのクラス型と同様に、静的クラスの型情報は、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] の共通言語ランタイム \(CLR: Common Language Runtime\) によって、そのクラスを参照しているプログラムが読み込まれるときに読み込まれます。プログラムでは、クラスが読み込まれるタイミングを正確に指定することはできません。  ただし、クラスがプログラム内で最初に参照される前に、そのクラスが読み込まれ、そのフィールドが初期化され、その静的コンストラクターが呼び出されることが保証されます。  静的コンストラクターは一度だけ呼び出され、静的クラスは、プログラムが存在するアプリケーション ドメインの有効期間にわたってメモリに保持されます。  
  
> [!NOTE]
>  インスタンスの作成を 1 つしか許さない非静的クラスを作成する方法については、「[C\# でのシングルトンの実装](http://go.microsoft.com/fwlink/?LinkID=100567)」を参照してください。  
  
 静的クラスの主な特徴を次の一覧に示します。  
  
-   静的メンバーのみが含まれます。  
  
-   インスタンス化できません。  
  
-   シールされています。  
  
-   [インスタンス コンストラクター](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)を含めることはできません。  
  
 したがって、静的クラスを作成することと、静的メンバーとプライベート コンストラクターのみを含むクラスを作成することは、基本的に同じです。  プライベート コンストラクターは、クラスのインスタンス化を防止します。  静的クラスを使用する利点は、インスタンス メンバーが誤って追加されないことをコンパイラで確認できるという点です。  コンパイラによって、このクラスのインスタンスを作成できないことが保証されます。  
  
 静的クラスはシールされるため、継承できません。  <xref:System.Object> 以外のクラスから継承することはできません。  静的クラスにインスタンス コンストラクターを含めることはできませんが、静的コンストラクターを含めることは可能です。  特別な初期化を必要とする静的メンバーがクラスに含まれている場合は、非静的クラスであっても静的コンストラクターを定義する必要があります。  詳細については、「[静的コンストラクター](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)」を参照してください。  
  
## 使用例  
 次に、摂氏と華氏の間で温度を変換する 2 つのメソッドを含む静的クラスのコード例を示します。  
  
 [!code-cs[csProgGuideObjects#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_1.cs)]  
  
## 静的メンバー  
 非静的クラスには、静的メソッド、フィールド、プロパティ、イベントを含めることができます。  静的メンバーは、クラスのインスタンスが作成されていない場合でもクラスで呼び出すことができます。  静的メンバーには、必ずインスタンス名ではなくクラス名でアクセスします。  クラスのインスタンスがいくつ作成されていても、静的メンバーのコピーは 1 つしか存在しません。  静的メソッドと静的プロパティは、それを含んでいる型の非静的フィールドや非静的イベントにはアクセスできません。また、メソッド パラメーターに明示的に渡されない限り、どのオブジェクトのインスタンス変数にもアクセスできません。  
  
 クラス全体を静的として宣言するよりも、非静的クラスを宣言して、いくつかの静的メンバーを含める方が一般的です。  静的フィールドの一般的な用途として、インスタンス化されたオブジェクトの数を保持することと、すべてのインスタンスで共有する必要のある値を格納することの 2 つがあります。  
  
 静的メソッドのオーバーロードはできますが、オーバーライドはできません。これは、静的メソッドがクラスのインスタンスではなくクラスに属しているためです。  
  
 フィールドを `static const` として宣言することはできませんが、[const](../../../csharp/language-reference/keywords/const.md) フィールドは、その動作において本質的に静的です。  const フィールドは、型のインスタンスではなく型に属します。  そのため、const フィールドにアクセスするには、静的フィールドに対して使用するのと同じ `ClassName.MemberName` 表記法を使用します。  オブジェクト インスタンスは必要ありません。  
  
 C\# では、静的なローカル変数 \(メソッドのスコープで宣言された変数\) はサポートされません。  
  
 静的クラスのメンバーを宣言するには、次の例に示すように、メンバーの戻り値の型の前で `static` キーワードを使用します。  
  
 [!code-cs[csProgGuideObjects#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_2.cs)]  
  
 静的メンバーは初めてアクセスされる前に初期化されます。また、静的コンストラクターがある場合は、それが呼び出される前に初期化されます。  静的クラスのメンバーにアクセスするには、次の例に示すように、変数名の代わりにクラス名を使用してメンバーの位置を指定します。  
  
 [!code-cs[csProgGuideObjects#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_3.cs)]  
  
 クラスに静的フィールドが含まれている場合は、クラスが読み込まれたときに静的フィールドを初期化する静的コンストラクターを用意します。  
  
 静的メソッドの呼び出しでは、Microsoft Intermediate Language \(MSIL\) の call 命令が生成されます。これに対して、インスタンス メソッドの呼び出しでは `callvirt` 命令が生成され、null オブジェクト参照もチェックされます。  ただし、ほとんどの場合、2 つの間にパフォーマンス上の違いはそれほどありません。  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [static](../../../csharp/language-reference/keywords/static.md)   
 [クラス](../../../csharp/programming-guide/classes-and-structs/classes.md)   
 [クラス](../../../csharp/language-reference/keywords/class.md)   
 [静的コンストラクター](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)   
 [インスタンス コンストラクター](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)