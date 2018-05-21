---
title: 静的クラスと静的クラス メンバー (C# プログラミング ガイド)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, static members
- static members [C#]
- static classes [C#]
- C# language, static classes
- static class members [C#]
ms.assetid: 235614b5-1371-4dbd-9abd-b406a8b0298b
ms.openlocfilehash: f3e64d975d2845d8317b37f43c3811af6be03b55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="static-classes-and-static-class-members-c-programming-guide"></a><span data-ttu-id="f25a8-102">静的クラスと静的クラス メンバー (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="f25a8-102">Static Classes and Static Class Members (C# Programming Guide)</span></span>
<span data-ttu-id="f25a8-103">[静的](../../../csharp/language-reference/keywords/static.md)クラスは基本的には非静的クラスと同じですが、静的クラスはインスタンス化できないという点が異なります。</span><span class="sxs-lookup"><span data-stu-id="f25a8-103">A [static](../../../csharp/language-reference/keywords/static.md) class is basically the same as a non-static class, but there is one difference: a static class cannot be instantiated.</span></span> <span data-ttu-id="f25a8-104">つまり、[new](../../../csharp/language-reference/keywords/new.md) キーワードを使用して、そのクラス型の変数を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="f25a8-104">In other words, you cannot use the [new](../../../csharp/language-reference/keywords/new.md) keyword to create a variable of the class type.</span></span> <span data-ttu-id="f25a8-105">インスタンス変数がないため、静的クラスのメンバーにアクセスするには、クラス名自体を使用します。</span><span class="sxs-lookup"><span data-stu-id="f25a8-105">Because there is no instance variable, you access the members of a static class by using the class name itself.</span></span> <span data-ttu-id="f25a8-106">たとえば、`UtilityClass` という静的クラスがあり、`MethodA` というパブリック メソッドが定義されている場合、このメソッドを呼び出すには次の例のようにします。</span><span class="sxs-lookup"><span data-stu-id="f25a8-106">For example, if you have a static class that is named `UtilityClass` that has a public method named `MethodA`, you call the method as shown in the following example:</span></span>  
  
```csharp  
UtilityClass.MethodA();  
```  
  
 <span data-ttu-id="f25a8-107">静的クラスは、入力パラメーターに対してのみ処理を行い、内部のインスタンス フィールドを取得したり設定したりする必要のない一連のメソッドを格納する、便利なコンテナーとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="f25a8-107">A static class can be used as a convenient container for sets of methods that just operate on input parameters and do not have to get or set any internal instance fields.</span></span> <span data-ttu-id="f25a8-108">たとえば、.NET Framework クラス ライブラリでは、静的クラス <xref:System.Math?displayProperty=nameWithType> に、数値演算を実行するメソッドが含まれており、<xref:System.Math> クラスの特定のインスタンスに固有のデータを格納または取得する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f25a8-108">For example, in the .NET Framework Class Library, the static <xref:System.Math?displayProperty=nameWithType> class contains methods that perform mathematical operations, without any requirement to store or retrieve data that is unique to a particular instance of the <xref:System.Math> class.</span></span> <span data-ttu-id="f25a8-109">つまり、次の例に示すように、クラス名とメソッド名を指定して、クラスのメンバーを適用します。</span><span class="sxs-lookup"><span data-stu-id="f25a8-109">That is, you apply the members of the class by specifying the class name and the method name, as shown in the following example.</span></span>  
  
```csharp  
double dub = -3.14;  
Console.WriteLine(Math.Abs(dub));  
Console.WriteLine(Math.Floor(dub));  
Console.WriteLine(Math.Round(Math.Abs(dub)));  
  
// Output:  
// 3.14  
// -4  
// 3  
```  
  
 <span data-ttu-id="f25a8-110">すべてのクラス型の場合と同様に、静的クラスの型情報は、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] の共通言語ランタイム (CLR) によって、そのクラスを参照しているプログラムが読み込まれるときに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="f25a8-110">As is the case with all class types, the type information for a static class is loaded by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] common language runtime (CLR) when the program that references the class is loaded.</span></span> <span data-ttu-id="f25a8-111">プログラムでは、クラスが読み込まれるタイミングを正確に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="f25a8-111">The program cannot specify exactly when the class is loaded.</span></span> <span data-ttu-id="f25a8-112">ただし、クラスがプログラム内で最初に参照される前に、そのクラスが読み込まれ、そのフィールドが初期化され、その静的コンストラクターが呼び出されることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="f25a8-112">However, it is guaranteed to be loaded and to have its fields initialized and its static constructor called before the class is referenced for the first time in your program.</span></span> <span data-ttu-id="f25a8-113">静的コンストラクターは一度だけ呼び出され、静的クラスは、プログラムが存在するアプリケーション ドメインの有効期間にわたってメモリに保持されます。</span><span class="sxs-lookup"><span data-stu-id="f25a8-113">A static constructor is only called one time, and a static class remains in memory for the lifetime of the application domain in which your program resides.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f25a8-114">インスタンスの作成を 1 つしか許可しない非静的クラスを作成する場合は、「[C# でのシングルトンの実装](https://msdn.microsoft.com/library/ms998558.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f25a8-114">To create a non-static class that allows only one instance of itself to be created, see [Implementing Singleton in C#](https://msdn.microsoft.com/library/ms998558.aspx).</span></span>  
  
 <span data-ttu-id="f25a8-115">静的クラスの主な特徴を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="f25a8-115">The following list provides the main features of a static class:</span></span>  
  
-   <span data-ttu-id="f25a8-116">静的メンバーだけが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f25a8-116">Contains only static members.</span></span>  
  
-   <span data-ttu-id="f25a8-117">インスタンス化できません。</span><span class="sxs-lookup"><span data-stu-id="f25a8-117">Cannot be instantiated.</span></span>  
  
-   <span data-ttu-id="f25a8-118">シールされています。</span><span class="sxs-lookup"><span data-stu-id="f25a8-118">Is sealed.</span></span>  
  
-   <span data-ttu-id="f25a8-119">[インスタンス コンストラクター](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="f25a8-119">Cannot contain [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  
  
 <span data-ttu-id="f25a8-120">したがって、静的クラスを作成することと、静的メンバーとプライベート コンストラクターのみを含むクラスを作成することは、基本的に同じです。</span><span class="sxs-lookup"><span data-stu-id="f25a8-120">Creating a static class is therefore basically the same as creating a class that contains only static members and a private constructor.</span></span> <span data-ttu-id="f25a8-121">プライベート コンストラクターは、クラスのインスタンス化を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="f25a8-121">A private constructor prevents the class from being instantiated.</span></span> <span data-ttu-id="f25a8-122">静的クラスを使用する利点は、インスタンス メンバーが誤って追加されないことをコンパイラで確認できるという点です。</span><span class="sxs-lookup"><span data-stu-id="f25a8-122">The advantage of using a static class is that the compiler can check to make sure that no instance members are accidentally added.</span></span> <span data-ttu-id="f25a8-123">コンパイラによって、このクラスのインスタンスを作成できないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="f25a8-123">The compiler will guarantee that instances of this class cannot be created.</span></span>  
  
 <span data-ttu-id="f25a8-124">静的クラスはシールされるため、継承できません。</span><span class="sxs-lookup"><span data-stu-id="f25a8-124">Static classes are sealed and therefore cannot be inherited.</span></span> <span data-ttu-id="f25a8-125"><xref:System.Object> 以外のクラスから継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="f25a8-125">They cannot inherit from any class except <xref:System.Object>.</span></span> <span data-ttu-id="f25a8-126">静的クラスにインスタンス コンストラクターを含めることはできませんが、静的コンストラクターを含めることはできます。</span><span class="sxs-lookup"><span data-stu-id="f25a8-126">Static classes cannot contain an instance constructor; however, they can contain a static constructor.</span></span> <span data-ttu-id="f25a8-127">特別な初期化を必要とする静的メンバーがクラスに含まれている場合は、非静的クラスであっても静的コンストラクターを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f25a8-127">Non-static classes should also define a static constructor if the class contains static members that require non-trivial initialization.</span></span> <span data-ttu-id="f25a8-128">詳細については、「[静的コンストラクター](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f25a8-128">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f25a8-129">例</span><span class="sxs-lookup"><span data-stu-id="f25a8-129">Example</span></span>  
 <span data-ttu-id="f25a8-130">次に、摂氏と華氏の間で温度を変換する 2 つのメソッドを含む静的クラスの例を示します。</span><span class="sxs-lookup"><span data-stu-id="f25a8-130">Here is an example of a static class that contains two methods that convert temperature from Celsius to Fahrenheit and from Fahrenheit to Celsius:</span></span>  
  
 [!code-csharp[csProgGuideObjects#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_1.cs)]  
  
## <a name="static-members"></a><span data-ttu-id="f25a8-131">静的メンバー</span><span class="sxs-lookup"><span data-stu-id="f25a8-131">Static Members</span></span>  
 <span data-ttu-id="f25a8-132">非静的クラスには、静的メソッド、フィールド、プロパティ、またはイベントを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="f25a8-132">A non-static class can contain static methods, fields, properties, or events.</span></span> <span data-ttu-id="f25a8-133">静的メンバーは、クラスのインスタンスが作成されていない場合でも、クラスで呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="f25a8-133">The static member is callable on a class even when no instance of the class has been created.</span></span> <span data-ttu-id="f25a8-134">静的メンバーには、必ずインスタンス名ではなくクラス名でアクセスします。</span><span class="sxs-lookup"><span data-stu-id="f25a8-134">The static member is always accessed by the class name, not the instance name.</span></span> <span data-ttu-id="f25a8-135">クラスのインスタンスの作成数に関係なく、静的メンバーのコピーは 1 つしか存在しません。</span><span class="sxs-lookup"><span data-stu-id="f25a8-135">Only one copy of a static member exists, regardless of how many instances of the class are created.</span></span> <span data-ttu-id="f25a8-136">静的メソッドと静的プロパティは、それを含んでいる型の非静的フィールドや非静的イベントにはアクセスできません。また、メソッド パラメーターに明示的に渡されない限り、どのオブジェクトのインスタンス変数にもアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="f25a8-136">Static methods and properties cannot access non-static fields and events in their containing type, and they cannot access an instance variable of any object unless it is explicitly passed in a method parameter.</span></span>  
  
 <span data-ttu-id="f25a8-137">クラス全体を静的として宣言するよりも、非静的クラスを宣言して、いくつかの静的メンバーを含める方が一般的です。</span><span class="sxs-lookup"><span data-stu-id="f25a8-137">It is more typical to declare a non-static class with some static members, than to declare an entire class as static.</span></span> <span data-ttu-id="f25a8-138">静的フィールドの一般的な用途として、インスタンス化されたオブジェクトの数を保持することと、すべてのインスタンスで共有する必要のある値を格納することの 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="f25a8-138">Two common uses of static fields are to keep a count of the number of objects that have been instantiated, or to store a value that must be shared among all instances.</span></span>  
  
 <span data-ttu-id="f25a8-139">静的メソッドのオーバーロードはできますが、オーバーライドはできません。これは、静的メソッドがクラスのインスタンスではなくクラスに属しているためです。</span><span class="sxs-lookup"><span data-stu-id="f25a8-139">Static methods can be overloaded but not overridden, because they belong to the class, and not to any instance of the class.</span></span>  
  
 <span data-ttu-id="f25a8-140">フィールドを `static const` として宣言することはできませんが、[const](../../../csharp/language-reference/keywords/const.md) フィールドは、その動作において本質的に静的です。</span><span class="sxs-lookup"><span data-stu-id="f25a8-140">Although a field cannot be declared as `static const`, a [const](../../../csharp/language-reference/keywords/const.md) field is essentially static in its behavior.</span></span> <span data-ttu-id="f25a8-141">これは、型のインスタンスではなく、型に属します。</span><span class="sxs-lookup"><span data-stu-id="f25a8-141">It belongs to the type, not to instances of the type.</span></span> <span data-ttu-id="f25a8-142">そのため、const フィールドにアクセスするには、静的フィールドに対して使用するのと同じ `ClassName.MemberName` 表記法を使用します。</span><span class="sxs-lookup"><span data-stu-id="f25a8-142">Therefore, const fields can be accessed by using the same `ClassName.MemberName` notation that is used for static fields.</span></span> <span data-ttu-id="f25a8-143">オブジェクト インスタンスは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="f25a8-143">No object instance is required.</span></span>  
  
 <span data-ttu-id="f25a8-144">C# では、静的なローカル変数 (メソッドのスコープで宣言された変数) はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="f25a8-144">C# does not support static local variables (variables that are declared in method scope).</span></span>  
  
 <span data-ttu-id="f25a8-145">静的クラスのメンバーを宣言するには、次の例に示すように、メンバーの戻り値の型の前で `static` キーワードを使用します。</span><span class="sxs-lookup"><span data-stu-id="f25a8-145">You declare static class members by using the `static` keyword before the return type of the member, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_2.cs)]  
  
 <span data-ttu-id="f25a8-146">静的メンバーは初めてアクセスされる前に初期化されます。また、静的コンストラクターがある場合は、それが呼び出される前に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="f25a8-146">Static members are initialized before the static member is accessed for the first time and before the static constructor, if there is one, is called.</span></span> <span data-ttu-id="f25a8-147">静的クラスのメンバーにアクセスするには、次の例に示すように、変数名の代わりにクラス名を使用してメンバーの位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="f25a8-147">To access a static class member, use the name of the class instead of a variable name to specify the location of the member, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-classes-and-static-class-members_3.cs)]  
  
 <span data-ttu-id="f25a8-148">クラスに静的フィールドが含まれている場合は、クラスが読み込まれたときに静的フィールドを初期化する静的コンストラクターを用意します。</span><span class="sxs-lookup"><span data-stu-id="f25a8-148">If your class contains static fields, provide a static constructor that initializes them when the class is loaded.</span></span>  
  
 <span data-ttu-id="f25a8-149">静的メソッドの呼び出しでは、Microsoft Intermediate Language (MSIL) の call 命令が生成されます。これに対して、インスタンス メソッドの呼び出しでは `callvirt` 命令が生成され、null オブジェクト参照もチェックされます。</span><span class="sxs-lookup"><span data-stu-id="f25a8-149">A call to a static method generates a call instruction in Microsoft intermediate language (MSIL), whereas a call to an instance method generates a `callvirt` instruction, which also checks for a null object references.</span></span> <span data-ttu-id="f25a8-150">ただし、ほとんどの場合、2 つの間にパフォーマンス上の違いはそれほどありません。</span><span class="sxs-lookup"><span data-stu-id="f25a8-150">However, most of the time the performance difference between the two is not significant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f25a8-151">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f25a8-151">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f25a8-152">参照</span><span class="sxs-lookup"><span data-stu-id="f25a8-152">See Also</span></span>  
 [<span data-ttu-id="f25a8-153">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f25a8-153">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f25a8-154">static</span><span class="sxs-lookup"><span data-stu-id="f25a8-154">static</span></span>](../../../csharp/language-reference/keywords/static.md)  
 [<span data-ttu-id="f25a8-155">クラス</span><span class="sxs-lookup"><span data-stu-id="f25a8-155">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [<span data-ttu-id="f25a8-156">class</span><span class="sxs-lookup"><span data-stu-id="f25a8-156">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="f25a8-157">静的コンストラクター</span><span class="sxs-lookup"><span data-stu-id="f25a8-157">Static Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
 [<span data-ttu-id="f25a8-158">インスタンス コンストラクター</span><span class="sxs-lookup"><span data-stu-id="f25a8-158">Instance Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)
