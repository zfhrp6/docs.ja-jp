---
title: "オブジェクト指向プログラミング (C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: de06921840f06f36d8600b9567986644f58c6ad5
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="1d780-102">オブジェクト指向プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="1d780-102">Object-Oriented Programming (C#)</span></span>
<span data-ttu-id="1d780-103">C# は、カプセル化、継承、ポリモーフィズムなど、オブジェクト指向プログラミングを完全にサポートします。</span><span class="sxs-lookup"><span data-stu-id="1d780-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>  
  
 <span data-ttu-id="1d780-104">"*カプセル化*" とは、関連するプロパティ、メソッド、およびその他のメンバーのグループが 1 つの単位またはオブジェクトとして扱われることを意味します。</span><span class="sxs-lookup"><span data-stu-id="1d780-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>  
  
 <span data-ttu-id="1d780-105">"*継承*" は、既存のクラスに基づいて新しいクラスを作成する機能です。</span><span class="sxs-lookup"><span data-stu-id="1d780-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>  
  
 <span data-ttu-id="1d780-106">"*ポリモーフィズム*" とは、同じプロパティまたはメソッドを異なる方法で実装している複数のクラスを、交換して使用できることです。</span><span class="sxs-lookup"><span data-stu-id="1d780-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>  
  
 <span data-ttu-id="1d780-107">このセクションでは、次の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="1d780-107">This section describes the following concepts:</span></span>  
  
-   [<span data-ttu-id="1d780-108">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="1d780-108">Classes and Objects</span></span>](#Classes)  
  
    -   [<span data-ttu-id="1d780-109">クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="1d780-109">Class Members</span></span>](#Members)  
  
         [<span data-ttu-id="1d780-110">プロパティとフィールド</span><span class="sxs-lookup"><span data-stu-id="1d780-110">Properties and Fields</span></span>](#Properties)  
  
         [<span data-ttu-id="1d780-111">メソッド</span><span class="sxs-lookup"><span data-stu-id="1d780-111">Methods</span></span>](#Methods)  
  
         [<span data-ttu-id="1d780-112">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="1d780-112">Constructors</span></span>](#Constructors)  
  
         [<span data-ttu-id="1d780-113">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="1d780-113">Finalizers</span></span>](#Finalizers)  
  
         [<span data-ttu-id="1d780-114">イベント</span><span class="sxs-lookup"><span data-stu-id="1d780-114">Events</span></span>](#Events)  
  
         [<span data-ttu-id="1d780-115">入れ子になったクラス</span><span class="sxs-lookup"><span data-stu-id="1d780-115">Nested Classes</span></span>](#NestedClasses)  
  
    -   [<span data-ttu-id="1d780-116">アクセス修飾子とアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="1d780-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)  
  
    -   [<span data-ttu-id="1d780-117">クラスのインスタンス化</span><span class="sxs-lookup"><span data-stu-id="1d780-117">Instantiating Classes</span></span>](#InstantiatingClasses)  
  
    -   [<span data-ttu-id="1d780-118">静的クラスとメンバー</span><span class="sxs-lookup"><span data-stu-id="1d780-118">Static Classes and Members</span></span>](#Static)  
  
    -   [<span data-ttu-id="1d780-119">匿名型</span><span class="sxs-lookup"><span data-stu-id="1d780-119">Anonymous Types</span></span>](#AnonymousTypes)  
  
-   [<span data-ttu-id="1d780-120">継承</span><span class="sxs-lookup"><span data-stu-id="1d780-120">Inheritance</span></span>](#Inheritance)  
  
    -   [<span data-ttu-id="1d780-121">メンバーのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="1d780-121">Overriding Members</span></span>](#Overriding)  
  
-   [<span data-ttu-id="1d780-122">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d780-122">Interfaces</span></span>](#Interfaces)  
  
-   [<span data-ttu-id="1d780-123">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="1d780-123">Generics</span></span>](#Generics)  
  
-   [<span data-ttu-id="1d780-124">デリゲート</span><span class="sxs-lookup"><span data-stu-id="1d780-124">Delegates</span></span>](#Delegates)  
  
##  <span data-ttu-id="1d780-125"><a name="Classes"></a> クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="1d780-125"><a name="Classes"></a> Classes and Objects</span></span>  
 <span data-ttu-id="1d780-126">"*クラス*" という用語と "*オブジェクト*" という用語は同じ意味で使われる場合がありますが、実際には、クラスはオブジェクトの "*型*" を表すのに対し、オブジェクトはクラスの使用可能な "*インスタンス*" です。</span><span class="sxs-lookup"><span data-stu-id="1d780-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="1d780-127">そのため、オブジェクトを作成する操作は "*インスタンス化*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="1d780-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="1d780-128">設計図との対比を使って説明すると、クラスは設計図であり、オブジェクトはその設計図を基にした建築物です。</span><span class="sxs-lookup"><span data-stu-id="1d780-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>  
  
 <span data-ttu-id="1d780-129">クラスを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-129">To define a class:</span></span>  
  
```csharp  
class SampleClass  
{  
}  
```  
  
 <span data-ttu-id="1d780-130">C# には、"*構造体*" と呼ばれる軽量バージョンのクラスも用意されています。構造体は、大きいオブジェクト配列を作成する必要があり、その配列に使用されるメモリの量を抑えたい場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1d780-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>  
  
 <span data-ttu-id="1d780-131">構造体を定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-131">To define a structure:</span></span>  
  
```csharp  
struct SampleStruct  
{  
}  
```  
  
 <span data-ttu-id="1d780-132">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="1d780-132">For more information, see:</span></span>  
  
-   [<span data-ttu-id="1d780-133">class</span><span class="sxs-lookup"><span data-stu-id="1d780-133">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
  
-   [<span data-ttu-id="1d780-134">struct</span><span class="sxs-lookup"><span data-stu-id="1d780-134">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
###  <span data-ttu-id="1d780-135"><a name="Members"></a> クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="1d780-135"><a name="Members"></a> Class Members</span></span>  
 <span data-ttu-id="1d780-136">各クラスには、さまざまな "*クラス メンバー*" を含めることができます。クラス メンバーには、クラスのデータを記述するプロパティ、クラスの動作を定義するメソッド、異なるクラスやオブジェクト間で通信するためのイベントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1d780-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>  
  
####  <span data-ttu-id="1d780-137"><a name="Properties"></a> プロパティとフィールド</span><span class="sxs-lookup"><span data-stu-id="1d780-137"><a name="Properties"></a> Properties and Fields</span></span>  
 <span data-ttu-id="1d780-138">フィールドとプロパティは、オブジェクトに格納されている情報を表します。</span><span class="sxs-lookup"><span data-stu-id="1d780-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="1d780-139">フィールドは、直接読み取ったり設定したりできるので変数と似ています。</span><span class="sxs-lookup"><span data-stu-id="1d780-139">Fields are like variables because they can be read or set directly.</span></span>  
  
 <span data-ttu-id="1d780-140">フィールドを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-140">To define a field:</span></span>  
  
```csharp  
Class SampleClass  
{  
    public string sampleField;  
}  
```  
  
 <span data-ttu-id="1d780-141">プロパティには get プロシージャと set プロシージャがあり、これらを使用することで値の設定方法や戻り値をより細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="1d780-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>  
  
 <span data-ttu-id="1d780-142">C# では、プロパティ値を格納するプライベート フィールドを作成するか、または自動実装プロパティと呼ばれる手法を使用できます。自動実装プロパティでは、値を格納するフィールドが背後で自動的に作成され、プロパティ プロシージャの基本的なロジックが提供されます。</span><span class="sxs-lookup"><span data-stu-id="1d780-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>  
  
 <span data-ttu-id="1d780-143">自動実装プロパティを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-143">To define an auto-implemented property:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int SampleProperty { get; set; }  
}  
```  
  
 <span data-ttu-id="1d780-144">プロパティ値の読み取りと書き込みのために追加の操作を実行する必要がある場合は、プロパティ値を格納するフィールドを定義し、値を格納および取得する基本的なロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="1d780-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>  
  
```csharp  
class SampleClass  
{  
    private int _sample;  
    public int Sample  
    {  
        // Return the value stored in a field.  
        get { return _sample; }  
        // Store the value in the field.  
        set { _sample = value; }  
    }  
}  
```  
  
 <span data-ttu-id="1d780-145">ほとんどのプロパティには、プロパティ値の設定と取得を行うための両方のメソッドまたはプロシージャがあります。</span><span class="sxs-lookup"><span data-stu-id="1d780-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="1d780-146">ただし、読み取り専用または書き込み専用のプロパティを作成して、プロパティの変更や読み取りを制限することもできます。</span><span class="sxs-lookup"><span data-stu-id="1d780-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="1d780-147">C# では、`get` プロパティ メソッドまたは `set` プロパティ メソッドを省略します。</span><span class="sxs-lookup"><span data-stu-id="1d780-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="1d780-148">ただし、自動実装プロパティを読み取り専用または書き込み専用にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="1d780-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>  
  
 <span data-ttu-id="1d780-149">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="1d780-149">For more information, see:</span></span>  
  
-   [<span data-ttu-id="1d780-150">get</span><span class="sxs-lookup"><span data-stu-id="1d780-150">get</span></span>](../../../csharp/language-reference/keywords/get.md)  
  
-   [<span data-ttu-id="1d780-151">set</span><span class="sxs-lookup"><span data-stu-id="1d780-151">set</span></span>](../../../csharp/language-reference/keywords/set.md)  
  
####  <span data-ttu-id="1d780-152"><a name="Methods"></a> メソッド</span><span class="sxs-lookup"><span data-stu-id="1d780-152"><a name="Methods"></a> Methods</span></span>  
 <span data-ttu-id="1d780-153">"*メソッド*" は、オブジェクトが実行できる処理です。</span><span class="sxs-lookup"><span data-stu-id="1d780-153">A *method* is an action that an object can perform.</span></span>  
  
 <span data-ttu-id="1d780-154">クラスのメソッドを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-154">To define a method of a class:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int sampleMethod(string sampleParam)  
    {  
        // Insert code here  
    }  
}  
```  
  
 <span data-ttu-id="1d780-155">クラスには、同じメソッドに対して、パラメーターの数やパラメーターの型が異なる複数の実装 ("*オーバーロード*") を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="1d780-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>  
  
 <span data-ttu-id="1d780-156">メソッドをオーバーロードするコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-156">To overload a method:</span></span>  
  
```csharp  
public int sampleMethod(string sampleParam) {};  
public int sampleMethod(int sampleParam) {}  
```  
  
 <span data-ttu-id="1d780-157">ほとんどの場合、メソッドはクラス定義内で宣言します。</span><span class="sxs-lookup"><span data-stu-id="1d780-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="1d780-158">ただし、C# では、既存のクラスの実際の定義の外部にメソッドを追加できる "*拡張メソッド*" がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1d780-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>  
  
 <span data-ttu-id="1d780-159">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="1d780-159">For more information, see:</span></span>  
  
-   [<span data-ttu-id="1d780-160">メソッド</span><span class="sxs-lookup"><span data-stu-id="1d780-160">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="1d780-161">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="1d780-161">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
  
####  <span data-ttu-id="1d780-162"><a name="Constructors"></a> コンストラクター</span><span class="sxs-lookup"><span data-stu-id="1d780-162"><a name="Constructors"></a> Constructors</span></span>  
 <span data-ttu-id="1d780-163">コンストラクターは、特定の型のオブジェクトを作成するときに自動的に実行されるクラス メソッドです。</span><span class="sxs-lookup"><span data-stu-id="1d780-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="1d780-164">コンストラクターは、通常、新しいオブジェクトのデータ メンバーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="1d780-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="1d780-165">コンストラクターは、クラスの作成時に 1 回だけ実行できます。</span><span class="sxs-lookup"><span data-stu-id="1d780-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="1d780-166">また、コンストラクター内のコードは常に、クラス内の他のすべてのコードより先に実行されます。</span><span class="sxs-lookup"><span data-stu-id="1d780-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="1d780-167">他のメソッドと同じように、コンストラクターにも複数のオーバーロードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1d780-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>  
  
 <span data-ttu-id="1d780-168">クラスのコンストラクターを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-168">To define a constructor for a class:</span></span>  
  
```csharp  
public class SampleClass  
{  
    public SampleClass()  
    {  
        // Add code here  
    }  
}  
```  
  
 <span data-ttu-id="1d780-169">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="1d780-169">For more information, see:</span></span>  
  
 <span data-ttu-id="1d780-170">「[コンストラクター](../../../csharp/programming-guide/classes-and-structs/constructors.md)」。</span><span class="sxs-lookup"><span data-stu-id="1d780-170">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md).</span></span>  
  
####  <span data-ttu-id="1d780-171"><a name="Finalizers"></a> ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="1d780-171"><a name="Finalizers"></a> Finalizers</span></span>  
 <span data-ttu-id="1d780-172">ファイナライザーは、クラスのインスタンスを破棄するために使います。</span><span class="sxs-lookup"><span data-stu-id="1d780-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="1d780-173">.NET Framework では、アプリケーション内のマネージ オブジェクトのメモリの割り当てと解放は、ガベージ コレクターによって自動的に管理されます。</span><span class="sxs-lookup"><span data-stu-id="1d780-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="1d780-174">ただし、アプリケーションで作成されるアンマネージ リソースを適切にクリーンアップするために、ファイナライザーも必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="1d780-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="1d780-175">1 つのクラスに定義できるファイナライザーは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="1d780-175">There can be only one finalizers for a class.</span></span>  
  
 <span data-ttu-id="1d780-176">.NET Framework のファイナライザーおよびガベージ コレクションについて詳しくは、「[ガベージ コレクション](../../../standard/garbage-collection/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1d780-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
####  <span data-ttu-id="1d780-177"><a name="Events"></a> イベント</span><span class="sxs-lookup"><span data-stu-id="1d780-177"><a name="Events"></a> Events</span></span>  
 <span data-ttu-id="1d780-178">クラスやオブジェクトは、何か重要なことが起こった場合に、イベントを使用して他のクラスまたはオブジェクトに通知を送ります。</span><span class="sxs-lookup"><span data-stu-id="1d780-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="1d780-179">イベントを送信する (発生させる) クラスは "*パブリッシャー*" と呼ばれ、イベントを受信する (処理する) クラスは "*サブスクライバー*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="1d780-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="1d780-180">イベント、およびイベントの発生と処理の詳細については、「[イベント](../../../standard/events/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1d780-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>  
  
-   <span data-ttu-id="1d780-181">クラスでイベントを宣言するには、[event](../../../csharp/language-reference/keywords/event.md) キーワードを使います。</span><span class="sxs-lookup"><span data-stu-id="1d780-181">To declare an event in a class, use the [event](../../../csharp/language-reference/keywords/event.md) keyword.</span></span>  
  
-   <span data-ttu-id="1d780-182">イベントを発生させるには、イベント デリゲートを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1d780-182">To raise an event, invoke the event delegate.</span></span>  
  
-   <span data-ttu-id="1d780-183">イベントをサブスクライブするには、`+=` 演算子を使用します。イベント サブスクリプションを解除するには、`-=` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="1d780-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>  
  
####  <span data-ttu-id="1d780-184"><a name="NestedClasses"></a> 入れ子になったクラス</span><span class="sxs-lookup"><span data-stu-id="1d780-184"><a name="NestedClasses"></a> Nested Classes</span></span>  
 <span data-ttu-id="1d780-185">別のクラス内で定義されているクラスを "*入れ子になったクラス*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="1d780-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="1d780-186">既定では、入れ子になったクラスはプライベートです。</span><span class="sxs-lookup"><span data-stu-id="1d780-186">By default, the nested class is private.</span></span>  
  
```csharp  
class Container  
{  
    class Nested  
    {  
        // Add code here.  
    }  
}  
```  
  
 <span data-ttu-id="1d780-187">入れ子になったクラスのインスタンスを作成するには、コンテナー クラスの名前に続けて、ドットと入れ子になったクラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="1d780-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>  
  
```csharp  
Container.Nested nestedInstance = new Container.Nested()  
```  
  
###  <span data-ttu-id="1d780-188"><a name="AccessModifiers"></a> アクセス修飾子とアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="1d780-188"><a name="AccessModifiers"></a> Access Modifiers and Access Levels</span></span>  
 <span data-ttu-id="1d780-189">すべてのクラスおよびクラス メンバーでは、"*アクセス修飾子*" を使って、他のクラスに提供するアクセス レベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="1d780-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>  
  
 <span data-ttu-id="1d780-190">次のアクセス修飾子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="1d780-190">The following access modifiers are available:</span></span>  
  
|<span data-ttu-id="1d780-191">C# の修飾子</span><span class="sxs-lookup"><span data-stu-id="1d780-191">C# Modifier</span></span>|<span data-ttu-id="1d780-192">定義</span><span class="sxs-lookup"><span data-stu-id="1d780-192">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="1d780-193">public</span><span class="sxs-lookup"><span data-stu-id="1d780-193">public</span></span>](../../../csharp/language-reference/keywords/public.md)|<span data-ttu-id="1d780-194">この型またはメンバーには、同じアセンブリ内の他のコードや、そのアセンブリを参照する別のアセンブリ内の任意のコードからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1d780-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|  
|[<span data-ttu-id="1d780-195">private</span><span class="sxs-lookup"><span data-stu-id="1d780-195">private</span></span>](../../../csharp/language-reference/keywords/private.md)|<span data-ttu-id="1d780-196">この型またはメンバーには、同じクラスのコードのみがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1d780-196">The type or member can only be accessed by code in the same class.</span></span>|  
|[<span data-ttu-id="1d780-197">protected</span><span class="sxs-lookup"><span data-stu-id="1d780-197">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)|<span data-ttu-id="1d780-198">この型またはメンバーには、同じクラスまたは派生クラスのコードのみがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1d780-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|  
|[<span data-ttu-id="1d780-199">internal</span><span class="sxs-lookup"><span data-stu-id="1d780-199">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)|<span data-ttu-id="1d780-200">この型またはメンバーには、同じアセンブリ内の任意のコードからアクセスできますが、別のアセンブリからはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="1d780-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="1d780-201">この型またはメンバーには、同じアセンブリ内の任意のコード、または別のアセンブリ内の任意の派生クラスからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1d780-201">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|  
  
 <span data-ttu-id="1d780-202">詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1d780-202">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
###  <span data-ttu-id="1d780-203"><a name="InstantiatingClasses"></a> クラスのインスタンス化</span><span class="sxs-lookup"><span data-stu-id="1d780-203"><a name="InstantiatingClasses"></a> Instantiating Classes</span></span>  
 <span data-ttu-id="1d780-204">オブジェクトを作成するには、クラスをインスタンス化する (クラスのインスタンスを作成する) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d780-204">To create an object, you need to instantiate a class, or create a class instance.</span></span>  
  
```csharp  
SampleClass sampleObject = new SampleClass();  
```  
  
 <span data-ttu-id="1d780-205">クラスをインスタンス化した後は、インスタンスのプロパティやフィールドに値を割り当てたり、クラスのメソッドを呼び出したりできます。</span><span class="sxs-lookup"><span data-stu-id="1d780-205">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>  
  
```csharp  
// Set a property value.  
sampleObject.sampleProperty = "Sample String";  
// Call a method.  
sampleObject.sampleMethod();  
```  
  
 <span data-ttu-id="1d780-206">クラスのインスタンス化のプロセスでプロパティに値を割り当てるには、オブジェクト初期化子を使用します。</span><span class="sxs-lookup"><span data-stu-id="1d780-206">To assign values to properties during the class instantiation process, use object initializers:</span></span>  
  
```csharp  
// Set a property value.  
SampleClass sampleObject = new SampleClass   
    { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="1d780-207">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="1d780-207">For more information, see:</span></span>  
  
-   [<span data-ttu-id="1d780-208">new 演算子</span><span class="sxs-lookup"><span data-stu-id="1d780-208">new Operator</span></span>](../../../csharp/language-reference/keywords/new-operator.md)  
  
-   [<span data-ttu-id="1d780-209">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="1d780-209">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
  
###  <span data-ttu-id="1d780-210"><a name="Static"></a> 静的クラスとメンバー</span><span class="sxs-lookup"><span data-stu-id="1d780-210"><a name="Static"></a> Static Classes and Members</span></span>  
 <span data-ttu-id="1d780-211">クラスの静的メンバーは、クラスのすべてのインスタンスで共有されるプロパティ、プロシージャ、またはフィールドです。</span><span class="sxs-lookup"><span data-stu-id="1d780-211">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>  
  
 <span data-ttu-id="1d780-212">静的メンバーを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-212">To define a static member:</span></span>  
  
```csharp  
static class SampleClass  
{  
    public static string SampleString = "Sample String";  
}  
```  
  
 <span data-ttu-id="1d780-213">静的メンバーにアクセスするには、クラスのオブジェクトを作成せずにクラスの名前を使います。</span><span class="sxs-lookup"><span data-stu-id="1d780-213">To access the static member, use the name of the class without creating an object of this class:</span></span>  
  
```csharp  
Console.WriteLine(SampleClass.SampleString);  
```  
  
 <span data-ttu-id="1d780-214">C# の静的クラスには静的メンバーだけがあり、インスタンス化することはできません。</span><span class="sxs-lookup"><span data-stu-id="1d780-214">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="1d780-215">また、静的メンバーから、非静的のプロパティ、フィールド、またはメソッドにアクセスすることもできません。</span><span class="sxs-lookup"><span data-stu-id="1d780-215">Static members also cannot access non-static  properties, fields or methods</span></span>  
  
 <span data-ttu-id="1d780-216">詳しくは、「[static](../../../csharp/language-reference/keywords/static.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1d780-216">For more information, see: [static](../../../csharp/language-reference/keywords/static.md).</span></span>  
  
###  <span data-ttu-id="1d780-217"><a name="AnonymousTypes"></a> 匿名型</span><span class="sxs-lookup"><span data-stu-id="1d780-217"><a name="AnonymousTypes"></a> Anonymous Types</span></span>  
 <span data-ttu-id="1d780-218">匿名型を使用すると、データ型のクラス定義を記述せずにオブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1d780-218">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="1d780-219">クラスは、コンパイラによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="1d780-219">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="1d780-220">このクラスには使用可能な名前がなく、オブジェクトの宣言時に指定したプロパティが格納されます。</span><span class="sxs-lookup"><span data-stu-id="1d780-220">The class has no usable name and contains the properties you specify in declaring the object.</span></span>  
  
 <span data-ttu-id="1d780-221">匿名型のインスタンスを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-221">To create an instance of an anonymous type:</span></span>  
  
```csharp  
// sampleObject is an instance of a simple anonymous type.  
var sampleObject =   
    new { FirstProperty = "A", SecondProperty = "B" };  
```  
  
 <span data-ttu-id="1d780-222">詳しくは、「[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1d780-222">For more information, see: [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
##  <span data-ttu-id="1d780-223"><a name="Inheritance"></a> 継承</span><span class="sxs-lookup"><span data-stu-id="1d780-223"><a name="Inheritance"></a> Inheritance</span></span>  
 <span data-ttu-id="1d780-224">継承を使用すると、他のクラスで定義されている動作を再利用、拡張、および変更する新しいクラスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1d780-224">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="1d780-225">メンバーが継承される側のクラスを "*基底クラス*" と呼び、メンバーを継承する側のクラスを "*派生クラス*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="1d780-225">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="1d780-226">ただし、C# のすべてのクラスは、.NET のクラス階層構造をサポートしてすべてのクラスに下位レベルのサービスを提供する <xref:System.Object> クラスを暗黙的に継承します。</span><span class="sxs-lookup"><span data-stu-id="1d780-226">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d780-227">C# は多重継承をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1d780-227">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="1d780-228">つまり、派生クラスに対して指定できる基底クラスは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="1d780-228">That is, you can specify only one base class for a derived class.</span></span>  
  
 <span data-ttu-id="1d780-229">基底クラスを継承するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-229">To inherit from a base class:</span></span>  
  
```csharp  
class DerivedClass:BaseClass{}  
```  
  
 <span data-ttu-id="1d780-230">既定では、すべてのクラスが継承可能になります。</span><span class="sxs-lookup"><span data-stu-id="1d780-230">By default all classes can be inherited.</span></span> <span data-ttu-id="1d780-231">ただし、クラスを基底クラスとして使用できないように指定したり、基底クラスとしてのみ使用できるクラスを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="1d780-231">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>  
  
 <span data-ttu-id="1d780-232">クラスを基底クラスとして使用できないように指定する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-232">To specify that a class cannot be used as a base class:</span></span>  
  
```csharp  
public sealed class A { }  
```  
  
 <span data-ttu-id="1d780-233">クラスが基底クラスとしてのみ使用され、インスタンス化できないように指定する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-233">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>  
  
```csharp  
public abstract class B { }  
```  
  
 <span data-ttu-id="1d780-234">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="1d780-234">For more information, see:</span></span>  
  
-   [<span data-ttu-id="1d780-235">sealed</span><span class="sxs-lookup"><span data-stu-id="1d780-235">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)  
  
-   [<span data-ttu-id="1d780-236">abstract</span><span class="sxs-lookup"><span data-stu-id="1d780-236">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)  
  
###  <span data-ttu-id="1d780-237"><a name="Overriding"></a> メンバーのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="1d780-237"><a name="Overriding"></a> Overriding Members</span></span>  
 <span data-ttu-id="1d780-238">既定では、派生クラスは基底クラスのすべてのメンバーを継承します。</span><span class="sxs-lookup"><span data-stu-id="1d780-238">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="1d780-239">継承したメンバーの動作を変更する場合は、そのメンバーをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d780-239">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="1d780-240">つまり、派生クラスに、メソッド、プロパティ、またはイベントの新しい実装を定義できます。</span><span class="sxs-lookup"><span data-stu-id="1d780-240">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>  
  
 <span data-ttu-id="1d780-241">プロパティやメソッドのオーバーライド方法を制御するには、次の修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="1d780-241">The following modifiers are used to control how properties and methods are overridden:</span></span>  
  
|<span data-ttu-id="1d780-242">C# の修飾子</span><span class="sxs-lookup"><span data-stu-id="1d780-242">C# Modifier</span></span>|<span data-ttu-id="1d780-243">定義</span><span class="sxs-lookup"><span data-stu-id="1d780-243">Definition</span></span>|  
|------------------|----------------|  
|[<span data-ttu-id="1d780-244">virtual</span><span class="sxs-lookup"><span data-stu-id="1d780-244">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="1d780-245">派生クラスでのクラス メンバーのオーバーライドを許可します。</span><span class="sxs-lookup"><span data-stu-id="1d780-245">Allows a class member to be overridden in a derived class.</span></span>|  
|[<span data-ttu-id="1d780-246">override</span><span class="sxs-lookup"><span data-stu-id="1d780-246">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="1d780-247">基底クラスで定義されている仮想メンバー (オーバーライドできるメンバー) をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="1d780-247">Overrides a virtual (overridable) member defined in the base class.</span></span>|  
|[<span data-ttu-id="1d780-248">abstract</span><span class="sxs-lookup"><span data-stu-id="1d780-248">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="1d780-249">派生クラスでのクラス メンバーのオーバーライドを必須にします。</span><span class="sxs-lookup"><span data-stu-id="1d780-249">Requires that a class member to be overridden in the derived class.</span></span>|  
|[<span data-ttu-id="1d780-250">new 修飾子</span><span class="sxs-lookup"><span data-stu-id="1d780-250">new Modifier</span></span>](../../../csharp/language-reference/keywords/new-modifier.md)|<span data-ttu-id="1d780-251">基底クラスから継承されたメンバーを隠ぺいします。</span><span class="sxs-lookup"><span data-stu-id="1d780-251">Hides a member inherited from a base class</span></span>|  
  
##  <span data-ttu-id="1d780-252"><a name="Interfaces"></a> インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d780-252"><a name="Interfaces"></a> Interfaces</span></span>  
 <span data-ttu-id="1d780-253">インターフェイスは、クラスと同様にプロパティ、メソッド、およびイベントのセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="1d780-253">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="1d780-254">ただし、クラスとは異なり、インターフェイスは実装を提供しません。</span><span class="sxs-lookup"><span data-stu-id="1d780-254">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="1d780-255">インターフェイスはクラスによって実装され、クラスとは別のエンティティとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="1d780-255">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="1d780-256">インターフェイスを実装するクラスは、そのインターフェイスのあらゆる機能を定義に従って厳密に実装する必要があります。この点で、インターフェイスはコントラクトを表しています。</span><span class="sxs-lookup"><span data-stu-id="1d780-256">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>  
  
 <span data-ttu-id="1d780-257">インターフェイスを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-257">To define an interface:</span></span>  
  
```csharp  
interface ISampleInterface  
{  
    void doSomething();  
}  
```  
  
 <span data-ttu-id="1d780-258">クラスにインターフェイスを実装するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-258">To implement an interface in a class:</span></span>  
  
```csharp  
class SampleClass : ISampleInterface  
{  
    void ISampleInterface.doSomething()  
    {  
        // Method implementation.  
    }  
}  
```  
  
 <span data-ttu-id="1d780-259">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="1d780-259">For more information, see:</span></span>  
  
 [<span data-ttu-id="1d780-260">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1d780-260">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
  
 [<span data-ttu-id="1d780-261">interface</span><span class="sxs-lookup"><span data-stu-id="1d780-261">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
  
##  <span data-ttu-id="1d780-262"><a name="Generics"></a> ジェネリック</span><span class="sxs-lookup"><span data-stu-id="1d780-262"><a name="Generics"></a> Generics</span></span>  
 <span data-ttu-id="1d780-263">.NET Framework のクラス、構造体、インターフェイス、およびメソッドは、格納または使用できるオブジェクトの型を定義する "*型パラメーター*" を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="1d780-263">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="1d780-264">ジェネリックの最も一般的な例として、コレクションがあります。コレクションには、その中に格納されるオブジェクトの型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="1d780-264">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>  
  
 <span data-ttu-id="1d780-265">ジェネリック クラスを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-265">To define a generic class:</span></span>  
  
```csharp  
Public class SampleGeneric<T>   
{  
    public T Field;  
}  
```  
  
 <span data-ttu-id="1d780-266">ジェネリック クラスのインスタンスを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-266">To create an instance of a generic class:</span></span>  
  
```csharp  
SampleGeneric<string> sampleObject = new SampleGeneric<string>();  
sampleObject.Field = "Sample string";  
```  
  
 <span data-ttu-id="1d780-267">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="1d780-267">For more information, see:</span></span>  
  
-   [<span data-ttu-id="1d780-268">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="1d780-268">Generics</span></span>](~/docs/standard/generics/index.md)  
  
-   [<span data-ttu-id="1d780-269">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="1d780-269">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
  
##  <span data-ttu-id="1d780-270"><a name="Delegates"></a> デリゲート</span><span class="sxs-lookup"><span data-stu-id="1d780-270"><a name="Delegates"></a> Delegates</span></span>  
 <span data-ttu-id="1d780-271">"*デリゲート*" は、メソッド シグネチャを定義する型であり、互換性のあるシグネチャを持つ任意のメソッドへの参照を提供できます。</span><span class="sxs-lookup"><span data-stu-id="1d780-271">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="1d780-272">メソッドは、デリゲートを使用して起動する (呼び出す) ことができます。</span><span class="sxs-lookup"><span data-stu-id="1d780-272">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="1d780-273">デリゲートは、他のメソッドへの引数としてメソッドを渡すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="1d780-273">Delegates are used to pass methods as arguments to other methods.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d780-274">イベント ハンドラーは、デリゲートを介して呼び出されるメソッドにすぎません。</span><span class="sxs-lookup"><span data-stu-id="1d780-274">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="1d780-275">デリゲートを使用したイベント処理について詳しくは、「[イベント](../../../standard/events/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1d780-275">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>  
  
 <span data-ttu-id="1d780-276">デリゲートを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-276">To create a delegate:</span></span>  
  
```csharp  
public delegate void SampleDelegate(string str);  
```  
  
 <span data-ttu-id="1d780-277">デリゲートで指定されたシグネチャに一致するメソッドへの参照を作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1d780-277">To create a reference to a method that matches the signature specified by the delegate:</span></span>  
  
```csharp  
class SampleClass  
{  
    // Method that matches the SampleDelegate signature.  
    public static void sampleMethod(string message)  
    {  
        // Add code here.  
    }  
    // Method that instantiates the delegate.  
    void SampleDelegate()  
    {  
        SampleDelegate sd = sampleMethod;  
        sd("Sample string");  
    }  
}  
```  
  
 <span data-ttu-id="1d780-278">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="1d780-278">For more information, see:</span></span>  
  
-   [<span data-ttu-id="1d780-279">デリゲート</span><span class="sxs-lookup"><span data-stu-id="1d780-279">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
  
-   [<span data-ttu-id="1d780-280">delegate</span><span class="sxs-lookup"><span data-stu-id="1d780-280">delegate</span></span>](../../../csharp/language-reference/keywords/delegate.md)  
  
## <a name="see-also"></a><span data-ttu-id="1d780-281">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d780-281">See Also</span></span>  
 [<span data-ttu-id="1d780-282">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="1d780-282">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)

