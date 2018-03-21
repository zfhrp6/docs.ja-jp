---
title: "ラムダ式 (C# プログラミング ガイド)"
ms.date: 03/03/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 14bb60a5009f9a1ae59ed9846ebc868cfdcc05c6
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="12f47-102">ラムダ式 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="12f47-102">Lambda Expressions (C# Programming Guide)</span></span>
<span data-ttu-id="12f47-103">ラムダ式は、 [デリゲート](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) 型または [式ツリー](../../../csharp/programming-guide/delegates/using-delegates.md) 型を作成するために使用できる [匿名関数](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) です。</span><span class="sxs-lookup"><span data-stu-id="12f47-103">A lambda expression is an [anonymous function](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) that you can use to create [delegates](../../../csharp/programming-guide/delegates/using-delegates.md) or [expression tree](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b) types.</span></span> <span data-ttu-id="12f47-104">ラムダ式を使用すると、引数として渡したり関数呼び出しの結果値として返すことができるローカル関数を記述できます。</span><span class="sxs-lookup"><span data-stu-id="12f47-104">By using lambda expressions, you can write local functions that can be passed as arguments or returned as the value of function calls.</span></span> <span data-ttu-id="12f47-105">ラムダ式は、LINQ クエリ式を記述する場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="12f47-105">Lambda expressions are particularly helpful for writing LINQ query expressions.</span></span>  
  
 <span data-ttu-id="12f47-106">ラムダ式を作成するには、ラムダ演算子 ( [=>](../../../csharp/language-reference/operators/lambda-operator.md)) の左側に入力パラメーター (ある場合) を指定し、反対側に式またはステートメント ブロックを置きます。</span><span class="sxs-lookup"><span data-stu-id="12f47-106">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator [=>](../../../csharp/language-reference/operators/lambda-operator.md), and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="12f47-107">たとえば、ラムダ式 `x => x * x` は、 `x` という名前のパラメーターを指定し、 `x` を 2 乗した値を返します。</span><span class="sxs-lookup"><span data-stu-id="12f47-107">For example, the lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="12f47-108">次の例に示すように、この式をデリゲート型に割り当てることもできます。</span><span class="sxs-lookup"><span data-stu-id="12f47-108">You can assign this expression to a delegate type, as the following example shows:</span></span>  
  
```csharp  
delegate int del(int i);  
static void Main(string[] args)  
{  
    del myDelegate = x => x * x;  
    int j = myDelegate(5); //j = 25  
}  
```  
  
 <span data-ttu-id="12f47-109">式ツリー型を作成するには</span><span class="sxs-lookup"><span data-stu-id="12f47-109">To create an expression tree type:</span></span>  
  
```csharp  
using System.Linq.Expressions;  
  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Expression<del> myET = x => x * x;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="12f47-110">`=>` 演算子は、代入 (`=`) と同じ優先順位であり、[結合規則が右から左](../../../csharp/programming-guide/statements-expressions-operators/operators.md) です (演算子に関するドキュメントの「結合規則」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="12f47-110">The `=>` operator has the same precedence as assignment (`=`) and is [right associative](../../../csharp/programming-guide/statements-expressions-operators/operators.md) (see "Associativity" section of the Operators article).</span></span>  
  
 <span data-ttu-id="12f47-111">ラムダは、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] のメソッド ベースのクエリ内で標準クエリ演算子のメソッド (<xref:System.Linq.Enumerable.Where%2A> など) の引数として使用されます。</span><span class="sxs-lookup"><span data-stu-id="12f47-111">Lambdas are used in method-based [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries as arguments to standard query operator methods such as <xref:System.Linq.Enumerable.Where%2A>.</span></span>  
  
 <span data-ttu-id="12f47-112">メソッド ベースの構文を使用して ( <xref:System.Linq.Enumerable.Where%2A> to Objects および <xref:System.Linq.Enumerable> の場合と同様に) [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クラスの [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]メソッドを呼び出すと、パラメーターはデリゲート型 <xref:System.Func%602?displayProperty=nameWithType>になります。</span><span class="sxs-lookup"><span data-stu-id="12f47-112">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Where%2A> method in the <xref:System.Linq.Enumerable> class (as you do in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects and [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="12f47-113">ラムダ式はデリゲートを作成するための最も便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="12f47-113">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="12f47-114">たとえば (<xref:System.Linq.Queryable?displayProperty=nameWithType> の場合と同様に) [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] クラスの同じメソッドを呼び出すと、パラメーター型は <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Func\> になります。Func は最大 16 の入力パラメーターを持つ Func デリゲートです。</span><span class="sxs-lookup"><span data-stu-id="12f47-114">When you call the same method in, for example, the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]) then the parameter type is an <xref:System.Linq.Expressions.Expression?displayProperty=nameWithType><Func\> where Func is any of the Func delegates with up to sixteen input parameters.</span></span> <span data-ttu-id="12f47-115">ラムダ式は、こうした式ツリーを構築するための非常に簡潔な方法でもあります。</span><span class="sxs-lookup"><span data-stu-id="12f47-115">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="12f47-116">ラムダを使用すると `Where` 呼び出しの外観を似たものにできますが、ラムダから実際に作成されるオブジェクトの型は異なります。</span><span class="sxs-lookup"><span data-stu-id="12f47-116">The lambdas allow the `Where` calls to look similar although in fact the type of object created from the lambda is different.</span></span>  
  
 <span data-ttu-id="12f47-117">先ほどの例では、デリゲート シグネチャは暗黙的に型指定される `int`型の入力パラメーターを 1 つ持ち、 `int`を返します。</span><span class="sxs-lookup"><span data-stu-id="12f47-117">In the previous example, notice that the delegate signature has one implicitly-typed input parameter of type `int`, and returns an `int`.</span></span> <span data-ttu-id="12f47-118">このラムダ式を同じ型のデリゲートに変換することができます。デリゲートも 1 つの入力パラメーター (`x`) を持ち、コンパイラが暗黙的に `int` 型に変換できる値を返すからです </span><span class="sxs-lookup"><span data-stu-id="12f47-118">The lambda expression can be converted to a delegate of that type because it also has one input parameter (`x`) and a return value that the compiler can implicitly convert to type `int`.</span></span> <span data-ttu-id="12f47-119">(型の推論については後のセクションで詳しく説明します)。入力パラメーターとして 5 を使用してデリゲートを呼び出すと、デリゲートは 25 という結果を返します。</span><span class="sxs-lookup"><span data-stu-id="12f47-119">(Type inference is discussed in more detail in the following sections.) When the delegate is invoked by using an input parameter of 5, it returns a result of 25.</span></span>  
  
 <span data-ttu-id="12f47-120">[is](../../../csharp/language-reference/keywords/is.md) 演算子または [as](../../../csharp/language-reference/keywords/as.md) 演算子の左辺にラムダを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="12f47-120">Lambdas are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) or [as](../../../csharp/language-reference/keywords/as.md) operator.</span></span>  
  
 <span data-ttu-id="12f47-121">匿名メソッドに適用される制限は、すべてラムダ式にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="12f47-121">All restrictions that apply to anonymous methods also apply to lambda expressions.</span></span> <span data-ttu-id="12f47-122">詳細については、「[匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12f47-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
## <a name="expression-lambdas"></a><span data-ttu-id="12f47-123">式形式のラムダ</span><span class="sxs-lookup"><span data-stu-id="12f47-123">Expression Lambdas</span></span>  
 <span data-ttu-id="12f47-124">=> 演算子の右辺に式があるラムダ式を "*式形式のラムダ*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="12f47-124">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="12f47-125">式形式のラムダは、[式ツリー](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)の構築に幅広く使用されます。</span><span class="sxs-lookup"><span data-stu-id="12f47-125">Expression lambdas are used extensively in the construction of [Expression Trees](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).</span></span> <span data-ttu-id="12f47-126">式形式のラムダは式の結果を返します。基本的な形式は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="12f47-126">An expression lambda returns the result of the expression and takes the following basic form:</span></span>  
  
```csharp
(input-parameters) => expression
```

 <span data-ttu-id="12f47-127">かっこはラムダの入力パラメーターが 1 つの場合のみ省略可能で、それ以外の場合は必須です。</span><span class="sxs-lookup"><span data-stu-id="12f47-127">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="12f47-128">入力パラメーターが 2 つ以上ある場合は、かっこで囲んで各パラメーターをコンマで区切ります。</span><span class="sxs-lookup"><span data-stu-id="12f47-128">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>  
  
```csharp
(x, y) => x == y
```

 <span data-ttu-id="12f47-129">コンパイラが入力の型を推論するのが困難または不可能な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="12f47-129">Sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="12f47-130">このような場合は、次の例のように型を明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="12f47-130">When this occurs, you can specify the types explicitly as shown in the following example:</span></span>  
  
```csharp
(int x, string s) => s.Length > x
```

 <span data-ttu-id="12f47-131">入力パラメーターがないことを指定するには、次のように空のかっこを使用します。</span><span class="sxs-lookup"><span data-stu-id="12f47-131">Specify zero input parameters with empty parentheses:</span></span>  
  
```csharp
() => SomeMethod()
```

 <span data-ttu-id="12f47-132">この例では、式形式のラムダの本体をメソッド呼び出しで構成できることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="12f47-132">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="12f47-133">ただし、SQL Server など .NET Framework の外部で評価される式ツリーを作成する場合は、ラムダ式内でメソッド呼び出しを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="12f47-133">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="12f47-134">.NET 共通言語ランタイムのコンテキストの外部では、これらのメソッドは通用しません。</span><span class="sxs-lookup"><span data-stu-id="12f47-134">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>  
  
## <a name="statement-lambdas"></a><span data-ttu-id="12f47-135">ステートメント形式のラムダ</span><span class="sxs-lookup"><span data-stu-id="12f47-135">Statement Lambdas</span></span>  
 <span data-ttu-id="12f47-136">ステートメント形式のラムダは式形式のラムダに似ていますが、ステートメントが中かっこで囲まれる点が異なります。</span><span class="sxs-lookup"><span data-stu-id="12f47-136">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>  
  
<span data-ttu-id="12f47-137">(input-parameters) => { statement; }</span><span class="sxs-lookup"><span data-stu-id="12f47-137">(input-parameters) => { statement; }</span></span>

 <span data-ttu-id="12f47-138">ステートメント形式のラムダの本体は任意の数のステートメントで構成できますが、実際面では通常、2、3 個以下にします。</span><span class="sxs-lookup"><span data-stu-id="12f47-138">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>  
  
[!code-csharp[StatementLamba#1](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#1)]

[!code-csharp[StatementLamba#2](../../../../samples\snippets\csharp\programming-guide\lambda-expressions/statements.cs#2)]

 <span data-ttu-id="12f47-139">匿名メソッドと同様、ステートメント形式のラムダを使用して式ツリーを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="12f47-139">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="12f47-140">非同期ラムダ</span><span class="sxs-lookup"><span data-stu-id="12f47-140">Async Lambdas</span></span>  
 <span data-ttu-id="12f47-141">[async](../../../csharp/language-reference/keywords/async.md) キーワードと [await](../../../csharp/language-reference/keywords/await.md) キーワードを使用すると、非同期処理を組み込んだラムダ式およびステートメントを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="12f47-141">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../../csharp/language-reference/keywords/async.md) and [await](../../../csharp/language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="12f47-142">たとえば、次に示す Windows フォーム例には、非同期メソッド `ExampleMethodAsync`を呼び出して待機するイベント ハンドラーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="12f47-142">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```csharp
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
    }  
  
    private async void button1_Click(object sender, EventArgs e)  
    {  
        // ExampleMethodAsync returns a Task.  
        await ExampleMethodAsync();  
        textBox1.Text += "\r\nControl returned to Click event handler.\n";  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```

 <span data-ttu-id="12f47-143">非同期ラムダを使用して、同じイベント ハンドラーを追加できます。</span><span class="sxs-lookup"><span data-stu-id="12f47-143">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="12f47-144">次の例に示すように、このハンドラーを追加するには、ラムダ パラメーター リストの前に `async` 修飾子を追加します。</span><span class="sxs-lookup"><span data-stu-id="12f47-144">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```csharp  
public partial class Form1 : Form  
{  
    public Form1()  
    {  
        InitializeComponent();  
        button1.Click += async (sender, e) =>  
        {  
            // ExampleMethodAsync returns a Task.  
            await ExampleMethodAsync();  
            textBox1.Text += "\nControl returned to Click event handler.\n";  
        };  
    }  
  
    async Task ExampleMethodAsync()  
    {  
        // The following line simulates a task-returning asynchronous process.  
        await Task.Delay(1000);  
    }  
}  
```  

 <span data-ttu-id="12f47-145">非同期メソッドの作成および使用方法の詳細については、「[Async および Await を使用した非同期プログラミング](../../../csharp/programming-guide/concepts/async/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12f47-145">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="12f47-146">標準クエリ演算子でのラムダ</span><span class="sxs-lookup"><span data-stu-id="12f47-146">Lambdas with the Standard Query Operators</span></span>  
 <span data-ttu-id="12f47-147">標準クエリ演算子の多くが、汎用デリゲートの <xref:System.Func%602> ファミリに属する型の入力パラメーターを持ちます。</span><span class="sxs-lookup"><span data-stu-id="12f47-147">Many Standard query operators have an input parameter whose type is one of the <xref:System.Func%602> family of generic delegates.</span></span> <span data-ttu-id="12f47-148">これらのデリゲートは型パラメーターを使用して入力パラメーターの数と型、およびデリゲートの戻り値の型を定義します。</span><span class="sxs-lookup"><span data-stu-id="12f47-148">These delegates use type parameters to define the number and types of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="12f47-149">`Func` デリゲートは、ソース データのセット内の各要素に適用されるユーザー定義の式をカプセル化する場合に非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="12f47-149">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="12f47-150">たとえば、次のデリゲート型を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="12f47-150">For example, consider the following delegate type:</span></span>  
  
```csharp  
public delegate TResult Func<TArg0, TResult>(TArg0 arg0)  
```  
  
 <span data-ttu-id="12f47-151">このデリゲートを `Func<int,bool> myFunc` としてインスタンス化できます。 `int` は入力パラメーター、 `bool` は戻り値です。</span><span class="sxs-lookup"><span data-stu-id="12f47-151">The delegate can be instantiated as `Func<int,bool> myFunc` where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="12f47-152">戻り値は必ず最後の型パラメーターで指定されます。</span><span class="sxs-lookup"><span data-stu-id="12f47-152">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="12f47-153">`Func<int, string, bool>` は 2 つの入力パラメーター ( `int` と `string`) と戻り値の型 `bool`を持つデリゲートを定義しています。</span><span class="sxs-lookup"><span data-stu-id="12f47-153">`Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="12f47-154">次の `Func` デリゲートを呼び出すと、入力パラメーターが 5 に等しいかどうかを示す true または false が返されます。</span><span class="sxs-lookup"><span data-stu-id="12f47-154">The following `Func` delegate, when it is invoked, will return true or false to indicate whether the input parameter is equal to 5:</span></span>  
  
```csharp  
Func<int, bool> myFunc = x => x == 5;  
bool result = myFunc(4); // returns false of course  
```  
  
 <span data-ttu-id="12f47-155">たとえば System.Linq.Queryable で定義された標準クエリ演算子において、引数型が `Expression<Func>`の場合もラムダ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="12f47-155">You can also supply a lambda expression when the argument type is an `Expression<Func>`, for example in the standard query operators that are defined in System.Linq.Queryable.</span></span> <span data-ttu-id="12f47-156">`Expression<Func>` 引数を指定すると、ラムダは式ツリーにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="12f47-156">When you specify an `Expression<Func>` argument, the lambda will be compiled to an expression tree.</span></span>  
  
 <span data-ttu-id="12f47-157">標準クエリ演算子である <xref:System.Linq.Enumerable.Count%2A> メソッドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="12f47-157">A standard query operator, the <xref:System.Linq.Enumerable.Count%2A> method, is shown here:</span></span>  
  
```csharp  
int[] numbers = { 5, 4, 1, 3, 9, 8, 6, 7, 2, 0 };  
int oddNumbers = numbers.Count(n => n % 2 == 1);  
```  
  
 <span data-ttu-id="12f47-158">入力パラメーターの型はコンパイラが推論できますが、明示的に指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="12f47-158">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="12f47-159">この特定のラムダ式は、2 で除算したときに剰余が 1 になる整数 (`n`) をカウントします。</span><span class="sxs-lookup"><span data-stu-id="12f47-159">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>  
  
 <span data-ttu-id="12f47-160">次のメソッドは、配列 `numbers` 内で 9 より左側にある要素をすべて含むシーケンスを作成します。これは、9 がシーケンス内で条件を満たさない最初の数値であるためです。</span><span class="sxs-lookup"><span data-stu-id="12f47-160">The following line of code produces a sequence that contains all elements in the `numbers` array that are to the left side of the 9 because that's the first number in the sequence that doesn't meet the condition:</span></span>  
  
```csharp  
var firstNumbersLessThan6 = numbers.TakeWhile(n => n < 6);  
```  
  
 <span data-ttu-id="12f47-161">次の例は、複数の入力パラメーターをかっこで囲んで指定する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="12f47-161">This example shows how to specify multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="12f47-162">このメソッドは、値がその位置よりも小さい数値が出現するまで配列 numbers に含まれるすべての要素を返します。</span><span class="sxs-lookup"><span data-stu-id="12f47-162">The method returns all the elements in the numbers array until a number is encountered whose value is less than its position.</span></span> <span data-ttu-id="12f47-163">ラムダ演算子 (`=>`) と以上演算子 (`>=`) を混同しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="12f47-163">Do not confuse the lambda operator (`=>`) with the greater than or equal operator (`>=`).</span></span>  
  
```csharp  
var firstSmallNumbers = numbers.TakeWhile((n, index) => n >= index);  
```  
  
## <a name="type-inference-in-lambdas"></a><span data-ttu-id="12f47-164">ラムダにおける型の推論</span><span class="sxs-lookup"><span data-stu-id="12f47-164">Type Inference in Lambdas</span></span>  
 <span data-ttu-id="12f47-165">ラムダを記述する際、多くの場合は入力パラメーターの型を指定する必要はありません。これは、ラムダ本体やパラメーターのデリゲート型など C# 言語仕様に記述されている要素に基づいて、コンパイラが型を推論できるためです。</span><span class="sxs-lookup"><span data-stu-id="12f47-165">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter’s delegate type, and other factors as described in the C# Language Specification.</span></span> <span data-ttu-id="12f47-166">ほとんどの標準クエリ演算子では、最初の入力がソース シーケンス内の要素の型です。</span><span class="sxs-lookup"><span data-stu-id="12f47-166">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="12f47-167">したがって、 `IEnumerable<Customer>`を問い合わせると、入力変数は `Customer` オブジェクトであると推論されます。これは、そのメソッドとプロパティにアクセスできることを意味します。</span><span class="sxs-lookup"><span data-stu-id="12f47-167">So if you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  
  
```csharp  
customers.Where(c => c.City == "London");  
```  
  
 <span data-ttu-id="12f47-168">ラムダの一般規則は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="12f47-168">The general rules for lambdas are as follows:</span></span>  
  
-   <span data-ttu-id="12f47-169">ラムダにはデリゲート型と同じ数のパラメーターが含まれていなければなりません。</span><span class="sxs-lookup"><span data-stu-id="12f47-169">The lambda must contain the same number of parameters as the delegate type.</span></span>  
  
-   <span data-ttu-id="12f47-170">ラムダに含まれる各入力パラメーターは、対応するデリゲート パラメーターに暗黙的に変換できなければなりません。</span><span class="sxs-lookup"><span data-stu-id="12f47-170">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>  
  
-   <span data-ttu-id="12f47-171">ラムダの戻り値 (ある場合) は、デリゲートの戻り値の型に暗黙的に変換できなければなりません。</span><span class="sxs-lookup"><span data-stu-id="12f47-171">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>  
  
 <span data-ttu-id="12f47-172">共通型システムには "ラムダ式" の概念が組み込まれていないため、ラムダ式自体は型を持ちません。</span><span class="sxs-lookup"><span data-stu-id="12f47-172">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="12f47-173">しかし、変則的ではあってもラムダ式の "型" を表現できると都合が良い場合もあります。</span><span class="sxs-lookup"><span data-stu-id="12f47-173">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="12f47-174">このような場合の型は、ラムダ式の変換後のデリゲート型または <xref:System.Linq.Expressions.Expression> 型を指します。</span><span class="sxs-lookup"><span data-stu-id="12f47-174">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>  
  
## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="12f47-175">ラムダ式における変数のスコープ</span><span class="sxs-lookup"><span data-stu-id="12f47-175">Variable Scope in Lambda Expressions</span></span>  
 <span data-ttu-id="12f47-176">ラムダは、"*外部変数*" を参照できます (「[匿名メソッド](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)」を参照)。外部変数とは、ラムダ関数を定義するメソッド内のスコープ、またはラムダ式を含む型のスコープに存在する変数のことです。</span><span class="sxs-lookup"><span data-stu-id="12f47-176">Lambdas can refer to *outer variables* (see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="12f47-177">こうして取り込まれた変数は、ラムダ式で使用するために格納されます。これは、変数がスコープ外に出てガベージ コレクトされる場合でも変わりません。</span><span class="sxs-lookup"><span data-stu-id="12f47-177">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="12f47-178">外部変数は、ラムダ式で使用される前に明示的に代入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="12f47-178">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="12f47-179">次の例は、こうした規則を示しています。</span><span class="sxs-lookup"><span data-stu-id="12f47-179">The following example demonstrates these rules:</span></span>  
  
```csharp  
delegate bool D();  
delegate bool D2(int i);  
  
class Test  
{  
    D del;  
    D2 del2;  
    public void TestMethod(int input)  
    {  
        int j = 0;  
        // Initialize the delegates with lambda expressions.  
        // Note access to 2 outer variables.  
        // del will be invoked within this method.  
        del = () => { j = 10;  return j > input; };  
  
        // del2 will be invoked after TestMethod goes out of scope.  
        del2 = (x) => {return x == j; };  
  
        // Demonstrate value of j:  
        // Output: j = 0   
        // The delegate has not been invoked yet.  
        Console.WriteLine("j = {0}", j);        // Invoke the delegate.  
        bool boolResult = del();  
  
        // Output: j = 10 b = True  
        Console.WriteLine("j = {0}. b = {1}", j, boolResult);  
    }  
  
    static void Main()  
    {  
        Test test = new Test();  
        test.TestMethod(5);  
  
        // Prove that del2 still has a copy of  
        // local variable j from TestMethod.  
        bool result = test.del2(10);  
  
        // Output: True  
        Console.WriteLine(result);  
  
        Console.ReadKey();  
    }  
}  
```  
  
 <span data-ttu-id="12f47-180">ラムダ式における変数のスコープには、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="12f47-180">The following rules apply to variable scope in lambda expressions:</span></span>  
  
-   <span data-ttu-id="12f47-181">取り込まれた変数は、その変数を参照するデリゲートがガベージ コレクションの対象になるまでガベージ コレクトされません。</span><span class="sxs-lookup"><span data-stu-id="12f47-181">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>  
  
-   <span data-ttu-id="12f47-182">ラムダ式内に導入された変数は、外側のメソッドでは参照できません。</span><span class="sxs-lookup"><span data-stu-id="12f47-182">Variables introduced within a lambda expression are not visible in the outer method.</span></span>  
  
-   <span data-ttu-id="12f47-183">ラムダ式は、外側のメソッドの `in`、`ref`、`out` パラメーターを直接取り込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="12f47-183">A lambda expression cannot directly capture an `in`, `ref`, or `out` parameter from an enclosing method.</span></span>  
  
-   <span data-ttu-id="12f47-184">ラムダ式に含まれる return ステートメントで外側のメソッドを戻すことはありません。</span><span class="sxs-lookup"><span data-stu-id="12f47-184">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>  
  
-   <span data-ttu-id="12f47-185">ラムダ式には、 `goto` ステートメント、 `break` ステートメント、およびジャンプ ステートメントのジャンプ先がブロック外である場合はラムダ式の内部にある `continue` ステートメントを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="12f47-185">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="12f47-186">また、ジャンプ先がブロックの内部にある場合は、ラムダ式の外部でジャンプ ステートメントを使用するとエラーになります。</span><span class="sxs-lookup"><span data-stu-id="12f47-186">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="12f47-187">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="12f47-187">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapter"></a><span data-ttu-id="12f47-188">参考書籍の該当する章</span><span class="sxs-lookup"><span data-stu-id="12f47-188">Featured Book Chapter</span></span>  
 <span data-ttu-id="12f47-189">『[C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers (C# 3.0 クックブック (第 3 版): C# 3.0 プログラマ向けの 250 以上のソリューション)](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)』の「[Delegates, Events, and Lambda Expressions (デリゲート、イベント、およびラムダ式)](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx)」</span><span class="sxs-lookup"><span data-stu-id="12f47-189">[Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f47-190">参照</span><span class="sxs-lookup"><span data-stu-id="12f47-190">See Also</span></span>  
 [<span data-ttu-id="12f47-191">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="12f47-191">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="12f47-192">統合言語クエリ (LINQ)</span><span class="sxs-lookup"><span data-stu-id="12f47-192">LINQ (Language-Integrated Query)</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="12f47-193">匿名メソッド</span><span class="sxs-lookup"><span data-stu-id="12f47-193">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="12f47-194">is</span><span class="sxs-lookup"><span data-stu-id="12f47-194">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="12f47-195">式ツリー</span><span class="sxs-lookup"><span data-stu-id="12f47-195">Expression Trees</span></span>](../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="12f47-196">Visual Studio 2008 C# Samples (Visual Studio 2008 の C# サンプル) (LINQ サンプル クエリ ファイルと XQuery プログラムを参照してください)</span><span class="sxs-lookup"><span data-stu-id="12f47-196">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](http://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)  
 [<span data-ttu-id="12f47-197">Recursive lambda expressions (再帰的なラムダ式)</span><span class="sxs-lookup"><span data-stu-id="12f47-197">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
