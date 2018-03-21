---
title: "反復子 (C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 48b09368ed0a84dc84793091b819ba7b4b6183f1
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="iterators-c"></a><span data-ttu-id="5921f-102">反復子 (C#)</span><span class="sxs-lookup"><span data-stu-id="5921f-102">Iterators (C#)</span></span>
<span data-ttu-id="5921f-103">*反復子*を使用して、リストや配列などのコレクションをステップ実行することができます。</span><span class="sxs-lookup"><span data-stu-id="5921f-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>  
  
 <span data-ttu-id="5921f-104">iterator メソッドまたは `get` アクセサーは、コレクションに対するカスタム イテレーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="5921f-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="5921f-105">反復子メソッドは、[yield return](../../../csharp/language-reference/keywords/yield.md) ステートメントを使用して、各要素を 1 回に 1 つ返します。</span><span class="sxs-lookup"><span data-stu-id="5921f-105">An iterator method uses the [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="5921f-106">`yield return` ステートメントに達すると、コードの現在の場所が記憶されます。</span><span class="sxs-lookup"><span data-stu-id="5921f-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="5921f-107">次回、iterator 関数が呼び出されると、この位置から実行が再開されます。</span><span class="sxs-lookup"><span data-stu-id="5921f-107">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="5921f-108">[foreach](../../../csharp/language-reference/keywords/foreach-in.md) ステートメントまたは LINQ クエリを使用して、クライアント コードから反復子を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5921f-108">You consume an iterator from client code by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>  
  
 <span data-ttu-id="5921f-109">次の例では、`foreach` ループの最初の反復子により、最初の `yield return` ステートメントに達するまで `SomeNumbers` iterator メソッドで実行が続行されます。</span><span class="sxs-lookup"><span data-stu-id="5921f-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="5921f-110">このイテレーションは 3 の値を返し、iterator メソッドの現在の場所が保持されます。</span><span class="sxs-lookup"><span data-stu-id="5921f-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="5921f-111">ループの次のイテレーションでは、iterator メソッドの実行が中断した場所から続行し、`yield return` ステートメントに達したときに再度停止します。</span><span class="sxs-lookup"><span data-stu-id="5921f-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="5921f-112">このイテレーションは 5 の値を返し、ここでも iterator メソッドの現在の場所が保持されます。</span><span class="sxs-lookup"><span data-stu-id="5921f-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="5921f-113">iterator メソッドの最後に達すると、ループが完了します。</span><span class="sxs-lookup"><span data-stu-id="5921f-113">The loop completes when the end of the iterator method is reached.</span></span>  
  
```csharp  
static void Main()  
{  
    foreach (int number in SomeNumbers())  
    {  
        Console.Write(number.ToString() + " ");  
    }  
    // Output: 3 5 8  
    Console.ReadKey();  
}  
  
public static System.Collections.IEnumerable SomeNumbers()  
{  
    yield return 3;  
    yield return 5;  
    yield return 8;  
}  
```  
  
 <span data-ttu-id="5921f-114">Iterator メソッドまたは `get` アクセサーの戻り値の型は、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601> となります。</span><span class="sxs-lookup"><span data-stu-id="5921f-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="5921f-115">`yield break` ステートメントを使用すると、反復を終了できます。</span><span class="sxs-lookup"><span data-stu-id="5921f-115">You can use a `yield break` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="5921f-116">反復子は、Visual Studio 2005 の C# で導入されました。</span><span class="sxs-lookup"><span data-stu-id="5921f-116">Iterators were introduced in C# in Visual Studio 2005.</span></span>  
  
 <span data-ttu-id="5921f-117">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="5921f-117">**In this topic**</span></span>  
  
-   [<span data-ttu-id="5921f-118">単純な反復子</span><span class="sxs-lookup"><span data-stu-id="5921f-118">Simple Iterator</span></span>](#BKMK_SimpleIterator)  
  
-   [<span data-ttu-id="5921f-119">コレクション クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="5921f-119">Creating a Collection Class</span></span>](#BKMK_CollectionClass)  
  
-   [<span data-ttu-id="5921f-120">ジェネリック リストと共に反復子を使用する</span><span class="sxs-lookup"><span data-stu-id="5921f-120">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)  
  
-   [<span data-ttu-id="5921f-121">構文情報</span><span class="sxs-lookup"><span data-stu-id="5921f-121">Syntax Information</span></span>](#BKMK_SyntaxInformation)  
  
-   [<span data-ttu-id="5921f-122">技術的な実装</span><span class="sxs-lookup"><span data-stu-id="5921f-122">Technical Implementation</span></span>](#BKMK_Technical)  
  
-   [<span data-ttu-id="5921f-123">反復子の使用</span><span class="sxs-lookup"><span data-stu-id="5921f-123">Use of Iterators</span></span>](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  <span data-ttu-id="5921f-124">このトピックの単純な反復子の例を除くすべての例には、`System.Collections` および `System.Collections.Generic` 名前空間の [using](../../../csharp/language-reference/keywords/using-directive.md) ディレクティブが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5921f-124">For all examples in this topic except the Simple Iterator example, include [using](../../../csharp/language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>  
  
##  <a name="BKMK_SimpleIterator"></a> <span data-ttu-id="5921f-125">単純な反復子</span><span class="sxs-lookup"><span data-stu-id="5921f-125">Simple Iterator</span></span>  
 <span data-ttu-id="5921f-126">次の例では、[for](../../../csharp/language-reference/keywords/for.md) ループ内に 1 つの `yield return` ステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5921f-126">The following example has a single `yield return` statement that is inside a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="5921f-127">`Main` では、`foreach` ステートメント本文の各イテレーションで iterator 関数が呼び出され、これが次の `yield return` ステートメントに続行されます。</span><span class="sxs-lookup"><span data-stu-id="5921f-127">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>  
  
```csharp  
static void Main()  
{  
    foreach (int number in EvenSequence(5, 18))  
    {  
        Console.Write(number.ToString() + " ");  
    }  
    // Output: 6 8 10 12 14 16 18  
    Console.ReadKey();  
}  
  
public static System.Collections.Generic.IEnumerable<int>  
    EvenSequence(int firstNumber, int lastNumber)  
{  
    // Yield even numbers in the range.  
    for (int number = firstNumber; number <= lastNumber; number++)  
    {  
        if (number % 2 == 0)  
        {  
            yield return number;  
        }  
    }  
}  
```  
  
##  <a name="BKMK_CollectionClass"></a> <span data-ttu-id="5921f-128">コレクション クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="5921f-128">Creating a Collection Class</span></span>  
 <span data-ttu-id="5921f-129">次の例の `DaysOfTheWeek` クラスは、<xref:System.Collections.IEnumerable.GetEnumerator%2A> メソッドを必要とする <xref:System.Collections.IEnumerable> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="5921f-129">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="5921f-130">コンパイラは、<xref:System.Collections.IEnumerator> を返す `GetEnumerator` メソッドを暗黙的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="5921f-130">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>  
  
 <span data-ttu-id="5921f-131">`GetEnumerator` メソッドは、`yield return` ステートメントを使用して、各文字列を一度に 1 つ返します。</span><span class="sxs-lookup"><span data-stu-id="5921f-131">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>  
  
```csharp  
static void Main()  
{  
    DaysOfTheWeek days = new DaysOfTheWeek();  
  
    foreach (string day in days)  
    {  
        Console.Write(day + " ");  
    }  
    // Output: Sun Mon Tue Wed Thu Fri Sat  
    Console.ReadKey();  
}  
  
public class DaysOfTheWeek : IEnumerable  
{  
    private string[] days = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };  
  
    public IEnumerator GetEnumerator()  
    {  
        for (int index = 0; index < days.Length; index++)  
        {  
            // Yield each day of the week.  
            yield return days[index];  
        }  
    }  
}  
```  
  
 <span data-ttu-id="5921f-132">次の例では、動物のコレクションを含む `Zoo` クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="5921f-132">The following example creates a `Zoo` class that contains a collection of animals.</span></span>  
  
 <span data-ttu-id="5921f-133">クラス インスタンス (`theZoo`) を参照する `foreach` ステートメントでは、`GetEnumerator` メソッドが暗黙的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5921f-133">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="5921f-134">`Birds` および `Mammals` プロパティを参照する `foreach` ステートメントでは、`AnimalsForType` という名前の iterator メソッドが使用されます。</span><span class="sxs-lookup"><span data-stu-id="5921f-134">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>  
  
```csharp  
static void Main()  
{  
    Zoo theZoo = new Zoo();  
  
    theZoo.AddMammal("Whale");  
    theZoo.AddMammal("Rhinoceros");  
    theZoo.AddBird("Penguin");  
    theZoo.AddBird("Warbler");  
  
    foreach (string name in theZoo)  
    {  
        Console.Write(name + " ");  
    }  
    Console.WriteLine();  
    // Output: Whale Rhinoceros Penguin Warbler  
  
    foreach (string name in theZoo.Birds)  
    {  
        Console.Write(name + " ");  
    }  
    Console.WriteLine();  
    // Output: Penguin Warbler  
  
    foreach (string name in theZoo.Mammals)  
    {  
        Console.Write(name + " ");  
    }  
    Console.WriteLine();  
    // Output: Whale Rhinoceros  
  
    Console.ReadKey();  
}  
  
public class Zoo : IEnumerable  
{  
    // Private members.  
    private List<Animal> animals = new List<Animal>();  
  
    // Public methods.  
    public void AddMammal(string name)  
    {  
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Mammal });  
    }  
  
    public void AddBird(string name)  
    {  
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Bird });  
    }  
  
    public IEnumerator GetEnumerator()  
    {  
        foreach (Animal theAnimal in animals)  
        {  
            yield return theAnimal.Name;  
        }  
    }  
  
    // Public members.  
    public IEnumerable Mammals  
    {  
        get { return AnimalsForType(Animal.TypeEnum.Mammal); }  
    }  
  
    public IEnumerable Birds  
    {  
        get { return AnimalsForType(Animal.TypeEnum.Bird); }  
    }  
  
    // Private methods.  
    private IEnumerable AnimalsForType(Animal.TypeEnum type)  
    {  
        foreach (Animal theAnimal in animals)  
        {  
            if (theAnimal.Type == type)  
            {  
                yield return theAnimal.Name;  
            }  
        }  
    }  
  
    // Private class.  
    private class Animal  
    {  
        public enum TypeEnum { Bird, Mammal }  
  
        public string Name { get; set; }  
        public TypeEnum Type { get; set; }  
    }  
}  
```  
  
##  <a name="BKMK_GenericList"></a> <span data-ttu-id="5921f-135">ジェネリック リストと共に反復子を使用する</span><span class="sxs-lookup"><span data-stu-id="5921f-135">Using Iterators with a Generic List</span></span>  
 <span data-ttu-id="5921f-136">次の例の `Stack(Of T)` ジェネリック クラスは、<xref:System.Collections.Generic.IEnumerable%601> ジェネリック インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="5921f-136">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="5921f-137">`Push` メソッドでは、`T` 型の配列に値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="5921f-137">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="5921f-138"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> メソッドは、`yield return` ステートメントを使って配列値を返します。</span><span class="sxs-lookup"><span data-stu-id="5921f-138">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>  
  
 <span data-ttu-id="5921f-139">ジェネリック メソッド <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> だけでなく、非ジェネリック メソッド <xref:System.Collections.IEnumerable.GetEnumerator%2A> も実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5921f-139">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="5921f-140">これは、<xref:System.Collections.Generic.IEnumerable%601> が <xref:System.Collections.IEnumerable> から継承するためです。</span><span class="sxs-lookup"><span data-stu-id="5921f-140">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="5921f-141">非ジェネリック実装は、ジェネリック実装に従います。</span><span class="sxs-lookup"><span data-stu-id="5921f-141">The non-generic implementation defers to the generic implementation.</span></span>  
  
 <span data-ttu-id="5921f-142">例では名前付き反復子を使用して、同じデータ コレクションでのさまざまな反復処理をサポートします。</span><span class="sxs-lookup"><span data-stu-id="5921f-142">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="5921f-143">この場合の名前付き反復子は、`TopToBottom` プロパティと `BottomToTop` プロパティ、および `TopN` メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5921f-143">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>  
  
 <span data-ttu-id="5921f-144">`BottomToTop` プロパティは `get` アクセサーで反復子を使用します。</span><span class="sxs-lookup"><span data-stu-id="5921f-144">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>  
  
```csharp  
static void Main()  
{  
    Stack<int> theStack = new Stack<int>();  
  
    //  Add items to the stack.  
    for (int number = 0; number <= 9; number++)  
    {  
        theStack.Push(number);  
    }  
  
    // Retrieve items from the stack.  
    // foreach is allowed because theStack implements  
    // IEnumerable<int>.  
    foreach (int number in theStack)  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 9 8 7 6 5 4 3 2 1 0  
  
    // foreach is allowed, because theStack.TopToBottom  
    // returns IEnumerable(Of Integer).  
    foreach (int number in theStack.TopToBottom)  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 9 8 7 6 5 4 3 2 1 0  
  
    foreach (int number in theStack.BottomToTop)  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 0 1 2 3 4 5 6 7 8 9  
  
    foreach (int number in theStack.TopN(7))  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 9 8 7 6 5 4 3  
  
    Console.ReadKey();  
}  
  
public class Stack<T> : IEnumerable<T>  
{  
    private T[] values = new T[100];  
    private int top = 0;  
  
    public void Push(T t)  
    {  
        values[top] = t;  
        top++;  
    }  
    public T Pop()  
    {  
        top--;  
        return values[top];  
    }  
  
    // This method implements the GetEnumerator method. It allows  
    // an instance of the class to be used in a foreach statement.  
    public IEnumerator<T> GetEnumerator()  
    {  
        for (int index = top - 1; index >= 0; index--)  
        {  
            yield return values[index];  
        }  
    }  
  
    IEnumerator IEnumerable.GetEnumerator()  
    {  
        return GetEnumerator();  
    }  
  
    public IEnumerable<T> TopToBottom  
    {  
        get { return this; }  
    }  
  
    public IEnumerable<T> BottomToTop  
    {  
        get  
        {  
            for (int index = 0; index <= top - 1; index++)  
            {  
                yield return values[index];  
            }  
        }  
    }  
  
    public IEnumerable<T> TopN(int itemsFromTop)  
    {  
        // Return less than itemsFromTop if necessary.  
        int startIndex = itemsFromTop >= top ? 0 : top - itemsFromTop;  
  
        for (int index = top - 1; index >= startIndex; index--)  
        {  
            yield return values[index];  
        }  
    }  
  
}  
```  
  
##  <a name="BKMK_SyntaxInformation"></a> <span data-ttu-id="5921f-145">構文情報</span><span class="sxs-lookup"><span data-stu-id="5921f-145">Syntax Information</span></span>  
 <span data-ttu-id="5921f-146">反復子は、メソッドまたは `get` アクセサーとして指定できます。</span><span class="sxs-lookup"><span data-stu-id="5921f-146">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="5921f-147">反復子を、イベント、インスタンス コンストラクター、静的コンストラクター、静的ファイナライザーで指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="5921f-147">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>  
  
 <span data-ttu-id="5921f-148">`yield return` ステートメント内の式の型から反復子の戻り値の型への暗黙的な変換が存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5921f-148">An implicit conversion must exist from the expression type in the `yield return` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="5921f-149">C# の場合、反復子メソッドで `in`、`ref`、`out` パラメーターを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="5921f-149">In C#, an iterator method cannot have any `in`, `ref`, or `out` parameters.</span></span>  
  
 <span data-ttu-id="5921f-150">C# の場合、"yield" は予約語ではなく、`return` または `break` キーワードの前に使用される場合にのみ、特別な意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="5921f-150">In C#, "yield" is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>  
  
##  <a name="BKMK_Technical"></a> <span data-ttu-id="5921f-151">技術的な実装</span><span class="sxs-lookup"><span data-stu-id="5921f-151">Technical Implementation</span></span>  
 <span data-ttu-id="5921f-152">メソッドとして反復子を記述しても、コンパイラが入れ子のクラス (つまり、事実上、ステート マシン) に変換します。</span><span class="sxs-lookup"><span data-stu-id="5921f-152">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="5921f-153">このクラスは、クライアント コードで `foreach` ループが続く限り、反復子の位置を追跡します。</span><span class="sxs-lookup"><span data-stu-id="5921f-153">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>  
  
 <span data-ttu-id="5921f-154">コンパイラの動作を確認するには、Ildasm.exe ツールを使用して、iterator メソッドに対して生成される Microsoft 中間言語コードを表示します。</span><span class="sxs-lookup"><span data-stu-id="5921f-154">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>  
  
 <span data-ttu-id="5921f-155">[クラス](../../../csharp/language-reference/keywords/class.md)または[構造体](../../../csharp/language-reference/keywords/struct.md)用の反復子を作成する場合、<xref:System.Collections.IEnumerator> インターフェイス全体を実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5921f-155">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="5921f-156">コンパイラは、反復子を検出すると、<xref:System.Collections.IEnumerator> または <xref:System.Collections.Generic.IEnumerator%601> インターフェイスの `Current`、`MoveNext`、および `Dispose` メソッドを自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="5921f-156">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>  
  
 <span data-ttu-id="5921f-157">`foreach` ループの連続する反復ごとに (または `IEnumerator.MoveNext` を直接呼び出すと)、前の `yield return` ステートメントの後で次の反復子コード本体が再開されます。</span><span class="sxs-lookup"><span data-stu-id="5921f-157">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="5921f-158">その後、反復子本体の最後に到達するか、`yield break` ステートメントが検出されるまで、次の `yield return` ステートメントに続行されます。</span><span class="sxs-lookup"><span data-stu-id="5921f-158">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>  
  
 <span data-ttu-id="5921f-159">反復子は、<xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> メソッドをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="5921f-159">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5921f-160">反復処理を最初から再度行う場合は、新しい反復子を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5921f-160">To re-iterate from the start, you must obtain a new iterator.</span></span>  
  
 <span data-ttu-id="5921f-161">詳細については、「[C# 言語の仕様](../../../csharp/language-reference/language-specification/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5921f-161">For additional information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
##  <a name="BKMK_UseOfIterators"></a> <span data-ttu-id="5921f-162">反復子の使用</span><span class="sxs-lookup"><span data-stu-id="5921f-162">Use of Iterators</span></span>  
 <span data-ttu-id="5921f-163">反復子を使用すると、複雑なコードを使用して一覧シーケンスを設定する必要がある場合に、`foreach` ループの単純さを維持することができます。</span><span class="sxs-lookup"><span data-stu-id="5921f-163">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="5921f-164">これは次のような場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5921f-164">This can be useful when you want to do the following:</span></span>  
  
-   <span data-ttu-id="5921f-165">最初の `foreach` ループ イテレーションの後に一覧シーケンスを変更する。</span><span class="sxs-lookup"><span data-stu-id="5921f-165">Modify the list sequence after the first `foreach` loop iteration.</span></span>  
  
-   <span data-ttu-id="5921f-166">最初の `foreach` ループ イテレーションの前に大きい一覧が完全に読み込まれないようにする。</span><span class="sxs-lookup"><span data-stu-id="5921f-166">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="5921f-167">例として、ページ フェッチでのテーブル行のバッチの読み込みなどがあります。</span><span class="sxs-lookup"><span data-stu-id="5921f-167">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="5921f-168">また、別の例として、<xref:System.IO.DirectoryInfo.EnumerateFiles%2A> メソッドでの .NET Framework 内の反復子の実装があります。</span><span class="sxs-lookup"><span data-stu-id="5921f-168">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>  
  
-   <span data-ttu-id="5921f-169">反復子に一覧の作成をカプセル化する。</span><span class="sxs-lookup"><span data-stu-id="5921f-169">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="5921f-170">iterator メソッドでは、一覧を作成してから、ループで各結果を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="5921f-170">In the iterator method, you can build the list and then yield each result in a loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5921f-171">参照</span><span class="sxs-lookup"><span data-stu-id="5921f-171">See Also</span></span>  
 <xref:System.Collections.Generic>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="5921f-172">foreach、in</span><span class="sxs-lookup"><span data-stu-id="5921f-172">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="5921f-173">yield</span><span class="sxs-lookup"><span data-stu-id="5921f-173">yield</span></span>](../../../csharp/language-reference/keywords/yield.md)  
 [<span data-ttu-id="5921f-174">配列での foreach の使用</span><span class="sxs-lookup"><span data-stu-id="5921f-174">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
 [<span data-ttu-id="5921f-175">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="5921f-175">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
