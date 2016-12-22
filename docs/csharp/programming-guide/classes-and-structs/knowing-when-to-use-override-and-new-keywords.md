---
title: "Override キーワードと New キーワードを使用する場合について (C# プログラミング ガイド) | Microsoft Docs"
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
  - "new キーワード [C#]"
  - "override キーワード [C#]"
  - "ポリモーフィズム [C#], 使用 (override と new を) [C#]"
ms.assetid: 323db184-b136-46fc-8839-007886e7e8b0
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Override キーワードと New キーワードを使用する場合について (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# では、派生クラスのメソッドを基本クラスのメソッドと同じ名前にできます。  両者のメソッドの関係は、[new](../../../csharp/language-reference/keywords/new.md) キーワードおよび [override](../../../csharp/language-reference/keywords/override.md) キーワードを使用して指定できます。  `override` 修飾子は基本クラスのメソッドを*拡張*し、`new` 修飾子は基本クラスのメッソドを*隠ぺい*します。  この違いについて、このトピックの例で示します。  
  
 コンソール アプリケーションで、`BaseClass` と `DerivedClass` という 2 つのクラスを宣言します。  `DerivedClass` は `BaseClass` から継承されます。  
  
```c#  
class BaseClass  
{  
    public void Method1()  
    {  
        Console.WriteLine("Base - Method1");  
    }  
}  
  
class DerivedClass : BaseClass  
{  
    public void Method2()  
    {  
        Console.WriteLine("Derived - Method2");  
    }  
}  
  
```  
  
 `Main` メソッドで、変数 `bc`、`dc`、および `bcdc` を宣言します。  
  
-   `bc` は `BaseClass` 型で、その値は `BaseClass` 型です。  
  
-   `dc` は `DerivedClass` 型で、その値は `DerivedClass` 型です。  
  
-   `bcdc` は `BaseClass` 型で、その値は `DerivedClass` 型です。  この変数に注目してください。  
  
 `bc` と `bcdc` は `BaseClass` 型であるため、キャストを使用しない限り、直接アクセスできるのは `Method1` に限られます。  変数 `dc` は、`Method1` と `Method2` の両方にアクセスできます。  これらの関係を次にコードに示します。  
  
```c#  
class Program  
{  
    static void Main(string[] args)  
    {  
        BaseClass bc = new BaseClass();  
        DerivedClass dc = new DerivedClass();  
        BaseClass bcdc = new DerivedClass();  
  
        bc.Method1();  
        dc.Method1();  
        dc.Method2();  
        bcdc.Method1();  
    }  
    // Output:  
    // Base - Method1  
    // Base - Method1  
    // Derived - Method2  
    // Base - Method1  
}  
  
```  
  
 次に、`BaseClass` に以下の `Method2` メソッドを追加します。  このメソッドのシグネチャは、`DerivedClass` の `Method2` メソッドのシグネチャと一致します。  
  
```c#  
public void Method2()  
{  
    Console.WriteLine("Base - Method2");  
}  
  
```  
  
 `BaseClass` に `Method2` メソッドが追加されたため、次のコードに示すように、`BaseClass` の変数である `bc` と `bcdc` に対して 2 つ目の呼び出しステートメントを追加できます。  
  
```c#  
bc.Method1();  
bc.Method2();  
dc.Method1();  
dc.Method2();  
bcdc.Method1();  
bcdc.Method2();  
  
```  
  
 プロジェクトのビルド時に、`BaseClass` に `Method2` メソッドを追加したことに対して警告が生成されます。  警告の内容は、`DerivedClass` の `Method2` メソッドによって `BaseClass` の `Method2` メソッドが隠ぺいされるというものです。  このような結果になることを意図している場合には、`Method2` の定義で、`new` キーワードを使用することをお勧めします。  また、警告を解消するには、どちらかの `Method2` メソッドの名前を変更することもできますが、この手段はいつも実用的であるとは限りません。  
  
 `new` を追加する前に、プログラムを実行して、追加した呼び出しステートメントによって生成される出力を確認してください。  次のような結果が表示されます。  
  
```c#  
// Output:  
// Base - Method1  
// Base - Method2  
// Base - Method1  
// Derived - Method2  
// Base - Method1  
// Base - Method2  
  
```  
  
 `new` キーワードを使用すると、同じ出力を得るための関係は保持されますが、警告が発生しなくなります。  `BaseClass` 型の変数は、`BaseClass` のメンバーに引き続きアクセスします。`DerivedClass` 型の変数は、まず `DerivedClass` のメンバーに引き続きアクセスしてから、`BaseClass` から継承されたメンバーについてアクセスできないか検討されます。  
  
 警告を抑制するには、次のコードに示すように、`DerivedClass` の `Method2` の定義に `new` 修飾子を追加します。  修飾子は、`public` の前または後に追加できます。  
  
```c#  
public new void Method2()  
{  
    Console.WriteLine("Derived - Method2");  
}  
  
```  
  
 プログラムを再度実行して、出力に変更がないことを確認します。  また、警告が表示されないことも確認します。  `new` 修飾子を使用すると、これによって修飾されるメンバーは、基本クラスから継承したメンバーを隠ぺいすることを承知していると表明することになります。  継承を介した名前の隠ぺいの詳細については、「[new 修飾子](../../../csharp/language-reference/keywords/new-modifier.md)」を参照してください。  
  
 この動作を、`override` を使用したときの効果と対比させるために、次のメソッドを `DerivedClass` に追加します。  `override` 修飾子は、`public` の前または後に追加できます。  
  
```c#  
public override void Method1()  
{  
    Console.WriteLine("Derived - Method1");  
}  
  
```  
  
 `BaseClass` の `Method1` の定義には、`virtual` 修飾子を追加します。  `virtual` 修飾子は、`public` の前または後に追加できます。  
  
```c#  
public virtual void Method1()  
{  
    Console.WriteLine("Base - Method1");  
}  
  
```  
  
 プロジェクトを再度実行します。  次の出力の、特に最後の 2 行に注目してください。  
  
```c#  
// Output:  
// Base - Method1  
// Base - Method2  
// Derived - Method1  
// Derived - Method2  
// Derived - Method1  
// Base - Method2  
  
```  
  
 `override` 修飾子を使用することによって、`bcdc` は、`DerivedClass` で定義された `Method1` メソッドにアクセスできます。  通常、継承階層における動作として、これは望ましいものです。  派生クラスから作成された値を持つオブジェクトでは、派生クラスで定義されたメソッドを使用する必要があるためです。  `override` を使用して基本クラスのメソッドを拡張することで、この動作を実現できます。  
  
 ここまでの例をすべて含んだコードを次に示します。  
  
```c#  
using System;  
using System.Text;  
  
namespace OverrideAndNew  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            BaseClass bc = new BaseClass();  
            DerivedClass dc = new DerivedClass();  
            BaseClass bcdc = new DerivedClass();  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in BaseClass.  
            bc.Method1();  
            bc.Method2();  
            // Output:  
            // Base - Method1  
            // Base - Method2  
  
            // The following two calls do what you would expect. They call  
            // the methods that are defined in DerivedClass.  
            dc.Method1();  
            dc.Method2();  
            // Output:  
            // Derived - Method1  
            // Derived - Method2  
  
            // The following two calls produce different results, depending   
            // on whether override (Method1) or new (Method2) is used.  
            bcdc.Method1();  
            bcdc.Method2();  
            // Output:  
            // Derived - Method1  
            // Base - Method2  
        }  
    }  
  
    class BaseClass  
    {  
        public virtual void Method1()  
        {  
            Console.WriteLine("Base - Method1");  
        }  
  
        public virtual void Method2()  
        {  
            Console.WriteLine("Base - Method2");  
        }  
    }  
  
    class DerivedClass : BaseClass  
    {  
        public override void Method1()  
        {  
            Console.WriteLine("Derived - Method1");  
        }  
  
        public new void Method2()  
        {  
            Console.WriteLine("Derived - Method2");  
        }  
    }  
}  
  
```  
  
 次の例では、別のコンテキストで同様の動作を示します。  この例では、`Car` という名前の基本クラスと、この基本クラスから派生した `ConvertibleCar` と `Minivan` という 2 つのクラスの、合わせて 3 つのクラスを定義しています。  基本クラスには、`DescribeCar` メソッドが含まれます。  このメソッドは自動車の基本的な説明を表示してから、詳細な情報を表示するために `ShowDetails` を呼び出します。  3 つのクラスには、それぞれ `ShowDetails` メソッドが定義されています。  `ConvertibleCar` クラスの `ShowDetails` の定義には、`new` 修飾子が使用されています。  `Minivan` クラスの `ShowDetails` の定義には、`override` 修飾子が使用されています。  
  
```c#  
// Define the base class, Car. The class defines two methods,  
// DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
// class also defines a ShowDetails method. The example tests which version of  
// ShowDetails is selected, the base class method or the derived class method.  
class Car  
{  
    public void DescribeCar()  
    {  
        System.Console.WriteLine("Four wheels and an engine.");  
        ShowDetails();  
    }  
  
    public virtual void ShowDetails()  
    {  
        System.Console.WriteLine("Standard transportation.");  
    }  
}  
  
// Define the derived classes.  
  
// Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
// hides the base class method.  
class ConvertibleCar : Car  
{  
    public new void ShowDetails()  
    {  
        System.Console.WriteLine("A roof that opens up.");  
    }  
}  
  
// Class Minivan uses the override modifier to specify that ShowDetails  
// extends the base class method.  
class Minivan : Car  
{  
    public override void ShowDetails()  
    {  
        System.Console.WriteLine("Carries seven people.");  
    }  
}  
  
```  
  
 この例では、どのバージョンの `ShowDetails` が呼び出されるかをテストします。  次に示す `TestCars1` メソッドでは、各クラスのインスタンスを宣言し、そのすべてのインスタンスで `DescribeCar` を呼び出します。  
  
```c#  
public static void TestCars1()  
{  
    System.Console.WriteLine("\nTestCars1");  
    System.Console.WriteLine("----------");  
  
    Car car1 = new Car();  
    car1.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    // Notice the output from this test case. The new modifier is  
    // used in the definition of ShowDetails in the ConvertibleCar  
    // class.    
  
    ConvertibleCar car2 = new ConvertibleCar();  
    car2.DescribeCar();  
    System.Console.WriteLine("----------");  
  
    Minivan car3 = new Minivan();  
    car3.DescribeCar();  
    System.Console.WriteLine("----------");  
}  
  
```  
  
 `TestCars1` による出力は次のようになります。  `car2` による結果に特に注意してください。予想した出力とは異なっているのではないでしょうか。  オブジェクトの型は `ConvertibleCar` であるのに、`DescribeCar` は、`ConvertibleCar` クラスで定義されているバージョンの `ShowDetails` にはアクセスしません。このメソッドが `override` 修飾子ではなく、`new` 修飾子を使用して宣言されているためです。  その結果、`ConvertibleCar` オブジェクトは、`Car` オブジェクトと同じ説明を表示します。  `car3` の結果 \(`Minivan` オブジェクト\) と対比してください。  この場合、`Minivan` クラスで宣言されている `ShowDetails` メソッドによって、`Car` クラスで宣言されている `ShowDetails` メソッドはオーバーライドされ、ミニバンについての説明が表示されます。  
  
```c#  
  
// TestCars1  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
  
```  
  
 `TestCars2` は、`Car` 型のオブジェクトのリストを作成します。  オブジェクトの値は、`Car`、`ConvertibleCar`、および `Minivan` の各クラスからインスタンス化されます。  `DescribeCar` は、リストの各要素で呼び出されます。  `TestCars2` の定義を次のコードに示します。  
  
```c#  
public static void TestCars2()  
{  
    System.Console.WriteLine("\nTestCars2");  
    System.Console.WriteLine("----------");  
  
    var cars = new List<Car> { new Car(), new ConvertibleCar(),   
        new Minivan() };  
  
    foreach (var car in cars)  
    {  
        car.DescribeCar();  
        System.Console.WriteLine("----------");  
    }  
}  
  
```  
  
 次の出力が表示されます。  この出力は、`TestCars1` で表示された出力と同じものである点に注意してください。  `ConvertibleCar` クラスの `ShowDetails` メソッドは、オブジェクトの型が `TestCars1` のように `ConvertibleCar` であっても、または `TestCars2` のように `Car` であっても、呼び出されません。  これとは逆に、`car3` では、`Minivan` 型または `Car` 型の両方の場合において、`Minivan` クラスの `ShowDetails` メソッドが呼び出されます。  
  
```c#  
// TestCars2  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Standard transportation.  
// ----------  
// Four wheels and an engine.  
// Carries seven people.  
// ----------  
  
```  
  
 `TestCars3` メソッドと `TestCars4` メソッドで、例全体が完成します。  これらのメソッドは、最初に `ConvertibleCar` 型および `Minivan` 型を持つように宣言されたオブジェクトから \(`TestCars3`\)、次に `Car` 型を持つように宣言されたオブジェクトから \(`TestCars4`\)、`ShowDetails` を直接呼び出します。  次のコードに、これら 2 つのメソッドの定義を示します。  
  
```c#  
  
public static void TestCars3()  
{  
    System.Console.WriteLine("\nTestCars3");  
    System.Console.WriteLine("----------");  
    ConvertibleCar car2 = new ConvertibleCar();  
    Minivan car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
public static void TestCars4()  
{  
    System.Console.WriteLine("\nTestCars4");  
    System.Console.WriteLine("----------");  
    Car car2 = new ConvertibleCar();  
    Car car3 = new Minivan();  
    car2.ShowDetails();  
    car3.ShowDetails();  
}  
  
```  
  
 メソッドからは次の出力が生成されます。この出力はこのトピックの最初の例の結果と対応しています。  
  
```c#  
// TestCars3  
// ----------  
// A roof that opens up.  
// Carries seven people.  
  
// TestCars4  
// ----------  
// Standard transportation.  
// Carries seven people.  
  
```  
  
 次のコードは、プロジェクトの全体とその出力とを示します。  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
namespace OverrideAndNew2  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Declare objects of the derived classes and test which version  
            // of ShowDetails is run, base or derived.  
            TestCars1();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars2();  
  
            // Declare objects of the derived classes and call ShowDetails  
            // directly.  
            TestCars3();  
  
            // Declare objects of the base class, instantiated with the  
            // derived classes, and repeat the tests.  
            TestCars4();  
        }  
  
        public static void TestCars1()  
        {  
            System.Console.WriteLine("\nTestCars1");  
            System.Console.WriteLine("----------");  
  
            Car car1 = new Car();  
            car1.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            // Notice the output from this test case. The new modifier is  
            // used in the definition of ShowDetails in the ConvertibleCar  
            // class.    
            ConvertibleCar car2 = new ConvertibleCar();  
            car2.DescribeCar();  
            System.Console.WriteLine("----------");  
  
            Minivan car3 = new Minivan();  
            car3.DescribeCar();  
            System.Console.WriteLine("----------");  
        }  
        // Output:  
        // TestCars1  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars2()  
        {  
            System.Console.WriteLine("\nTestCars2");  
            System.Console.WriteLine("----------");  
  
            var cars = new List<Car> { new Car(), new ConvertibleCar(),   
                new Minivan() };  
  
            foreach (var car in cars)  
            {  
                car.DescribeCar();  
                System.Console.WriteLine("----------");  
            }  
        }  
        // Output:  
        // TestCars2  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Standard transportation.  
        // ----------  
        // Four wheels and an engine.  
        // Carries seven people.  
        // ----------  
  
        public static void TestCars3()  
        {  
            System.Console.WriteLine("\nTestCars3");  
            System.Console.WriteLine("----------");  
            ConvertibleCar car2 = new ConvertibleCar();  
            Minivan car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars3  
        // ----------  
        // A roof that opens up.  
        // Carries seven people.  
  
        public static void TestCars4()  
        {  
            System.Console.WriteLine("\nTestCars4");  
            System.Console.WriteLine("----------");  
            Car car2 = new ConvertibleCar();  
            Car car3 = new Minivan();  
            car2.ShowDetails();  
            car3.ShowDetails();  
        }  
        // Output:  
        // TestCars4  
        // ----------  
        // Standard transportation.  
        // Carries seven people.  
    }  
  
    // Define the base class, Car. The class defines two virtual methods,  
    // DescribeCar and ShowDetails. DescribeCar calls ShowDetails, and each derived  
    // class also defines a ShowDetails method. The example tests which version of  
    // ShowDetails is used, the base class method or the derived class method.  
    class Car  
    {  
        public virtual void DescribeCar()  
        {  
            System.Console.WriteLine("Four wheels and an engine.");  
            ShowDetails();  
        }  
  
        public virtual void ShowDetails()  
        {  
            System.Console.WriteLine("Standard transportation.");  
        }  
    }  
  
    // Define the derived classes.  
  
    // Class ConvertibleCar uses the new modifier to acknowledge that ShowDetails  
    // hides the base class method.  
    class ConvertibleCar : Car  
    {  
        public new void ShowDetails()  
        {  
            System.Console.WriteLine("A roof that opens up.");  
        }  
    }  
  
    // Class Minivan uses the override modifier to specify that ShowDetails  
    // extends the base class method.  
    class Minivan : Car  
    {  
        public override void ShowDetails()  
        {  
            System.Console.WriteLine("Carries seven people.");  
        }  
    }  
  
}  
  
```  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [クラスと構造体](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Override キーワードと New キーワードによるバージョン管理](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)   
 [base](../../../csharp/language-reference/keywords/base.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)