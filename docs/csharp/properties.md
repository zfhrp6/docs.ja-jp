---
title: "プロパティ"
description: "C# のプロパティについて説明します。C# のプロパティには、検証、計算値、遅延評価、プロパティ変更通知の機能があります。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 04/03/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 6950d25a-bba1-4744-b7c7-a3cc90438c55
ms.openlocfilehash: 1ffacd52df89a955ebfa72dc58836211c7a58640
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2017
---
# <a name="properties"></a><span data-ttu-id="58672-104">プロパティ</span><span class="sxs-lookup"><span data-stu-id="58672-104">Properties</span></span>

<span data-ttu-id="58672-105">C# のプロパティは、非常に優れた機能です。</span><span class="sxs-lookup"><span data-stu-id="58672-105">Properties are first class citizens in C#.</span></span> <span data-ttu-id="58672-106">開発者は C# で定義されている構文を使用して、設計の意図を正確に表すコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="58672-106">The language defines syntax that enables developers to write code that accurately expresses their design intent.</span></span>

<span data-ttu-id="58672-107">プロパティは、アクセスされたときにはフィールドのように振る舞います。</span><span class="sxs-lookup"><span data-stu-id="58672-107">Properties behave like fields when they are accessed.</span></span>
<span data-ttu-id="58672-108">ただし、フィールドとは異なり、プロパティの実装ではアクセサーを使用します。プロパティがアクセスされたときや値を割り当てられたときに実行されるステートメントをアクセサーで定義します。</span><span class="sxs-lookup"><span data-stu-id="58672-108">However, unlike fields, properties are implemented with accessors that define the statements executed when a property is accessed or assigned.</span></span>

## <a name="property-syntax"></a><span data-ttu-id="58672-109">プロパティの構文</span><span class="sxs-lookup"><span data-stu-id="58672-109">Property Syntax</span></span>

<span data-ttu-id="58672-110">プロパティの構文は、フィールドを自然に拡張したものです。</span><span class="sxs-lookup"><span data-stu-id="58672-110">The syntax for properties is a natural extension to fields.</span></span> <span data-ttu-id="58672-111">フィールドで格納場所を定義します。</span><span class="sxs-lookup"><span data-stu-id="58672-111">A field defines a storage location:</span></span>

```csharp
public class Person
{
    public string FirstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="58672-112">プロパティの定義には、プロパティの値を取得する `get` アクセサーとプロパティに値を割り当てる `set` アクセサーの宣言が含まれます。</span><span class="sxs-lookup"><span data-stu-id="58672-112">A property definition contains declarations for a `get` and `set` accessor that retrieves and assigns the value of that property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="58672-113">上記の構文は "*自動プロパティ*" の構文です。</span><span class="sxs-lookup"><span data-stu-id="58672-113">The syntax shown above is the *auto property* syntax.</span></span> <span data-ttu-id="58672-114">コンパイラによって、プロパティをバックアップするフィールドの格納場所が生成されます。</span><span class="sxs-lookup"><span data-stu-id="58672-114">The compiler generates the storage location for the field that backs up the property.</span></span> <span data-ttu-id="58672-115">また、`get` アクセサーと `set` アクセサーの本体もコンパイラによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="58672-115">The compiler also implements the body of the `get` and `set` accessors.</span></span>

<span data-ttu-id="58672-116">場合によっては、その型の既定以外の値にプロパティを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58672-116">Sometimes, you need to initialize a property to a value other than the default for its type.</span></span>  <span data-ttu-id="58672-117">C# では、プロパティの右中かっこの後で値を設定することにより可能です。</span><span class="sxs-lookup"><span data-stu-id="58672-117">C# enables that by setting a value after the closing brace for the property.</span></span> <span data-ttu-id="58672-118">`FirstName` プロパティの初期値は `null` より空の文字列の方がよい場合があります。</span><span class="sxs-lookup"><span data-stu-id="58672-118">You may prefer the initial value for the `FirstName` property to be the empty string rather than `null`.</span></span> <span data-ttu-id="58672-119">その場合は次に示すように指定します。</span><span class="sxs-lookup"><span data-stu-id="58672-119">You would specify that as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; } = string.Empty;

    // remaining implementation removed from listing
}
```

<span data-ttu-id="58672-120">これは、このトピックで後述するように、読み取り専用プロパティに最も役立ちます。</span><span class="sxs-lookup"><span data-stu-id="58672-120">This is most useful for read-only properties, as you'll see later in this topic.</span></span>

<span data-ttu-id="58672-121">格納場所は、下に示すように、開発者が定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="58672-121">You can also define the storage yourself, as shown below:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get { return firstName; }
        set { firstName = value; }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="58672-122">プロパティの実装が 1 つの式の場合は、*式形式のメンバー*を get アクセス操作子または set アクセス操作子に使用できます。</span><span class="sxs-lookup"><span data-stu-id="58672-122">When a property implementation is a single expression, you can use *expression bodied members* for the getter or setter:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set => firstName = value;
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="58672-123">このトピックでは、該当する箇所ではこの簡単な構文を使います。</span><span class="sxs-lookup"><span data-stu-id="58672-123">This simplified syntax will be used where applicable throughout this topic.</span></span>

<span data-ttu-id="58672-124">上に示したプロパティの定義は、読み取り/書き込みプロパティです。</span><span class="sxs-lookup"><span data-stu-id="58672-124">The property definition shown above is a read-write property.</span></span> <span data-ttu-id="58672-125">set アクセサーの `value` に注目してください。</span><span class="sxs-lookup"><span data-stu-id="58672-125">Notice the keyword `value` in the set accessor.</span></span> <span data-ttu-id="58672-126">`set` アクセサーには常に、`value` という名前のパラメーターが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="58672-126">The `set` accessor always has a single parameter named `value`.</span></span> <span data-ttu-id="58672-127">`get` アクセサーは、プロパティの型に変換可能な値を返す必要があります (この例では `string`)。</span><span class="sxs-lookup"><span data-stu-id="58672-127">The `get` accessor must return a value that is convertible to the type of the property (`string` in this example).</span></span>
 
<span data-ttu-id="58672-128">これが構文の基本です。</span><span class="sxs-lookup"><span data-stu-id="58672-128">That's the basics of the syntax.</span></span> <span data-ttu-id="58672-129">さまざまな設計手法をサポートするバリエーションが多数あります。</span><span class="sxs-lookup"><span data-stu-id="58672-129">There are many different variations that support a variety of different design idioms.</span></span> <span data-ttu-id="58672-130">これらを詳しく確認しながら、各種シナリオに応じた構文の選択肢を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="58672-130">Let's explore those, and learn the syntax options for each.</span></span>

## <a name="scenarios"></a><span data-ttu-id="58672-131">シナリオ</span><span class="sxs-lookup"><span data-stu-id="58672-131">Scenarios</span></span>

<span data-ttu-id="58672-132">ここまでに示した例は、検証が行われない読み取り/書き込みプロパティという、プロパティ定義の中でも単純なものでした。</span><span class="sxs-lookup"><span data-stu-id="58672-132">The examples above showed one of the simplest cases of property definition: a read-write property with no validation.</span></span> <span data-ttu-id="58672-133">目的のコードを `get` アクセサーと `set` アクセサーで記述することで、さまざまなシナリオに対応できます。</span><span class="sxs-lookup"><span data-stu-id="58672-133">By writing the code you want in the `get` and `set` accessors, you can create many different scenarios.</span></span>

### <a name="validation"></a><span data-ttu-id="58672-134">検証</span><span class="sxs-lookup"><span data-stu-id="58672-134">Validation</span></span>

<span data-ttu-id="58672-135">`set` アクセサーにコードを記述すると、プロパティが表す値を常に有効な値にすることができます。</span><span class="sxs-lookup"><span data-stu-id="58672-135">You can write code in the `set` accessor to ensure that the values represented by a property are always valid.</span></span> <span data-ttu-id="58672-136">たとえば、`Person` クラスに設定されているルールの 1 つに、名前は空白にできないというものがあるとします。</span><span class="sxs-lookup"><span data-stu-id="58672-136">For example, suppose one rule for the `Person` class is that the name cannot be blank, or whitespace.</span></span> <span data-ttu-id="58672-137">これは次のように記述できます。</span><span class="sxs-lookup"><span data-stu-id="58672-137">You would write that as follows:</span></span>

```csharp
public class Person
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            firstName = value;
        }
    }
    private string firstName;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="58672-138">上記の例では、名を空白にしてはいけないというルールが強制的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="58672-138">The example above enforces the rule that the first name must not be blank, or whitespace.</span></span> <span data-ttu-id="58672-139">もし開発者が下のように指定すると、</span><span class="sxs-lookup"><span data-stu-id="58672-139">If a developer writes</span></span>

```csharp
hero.FirstName = "";
```

<span data-ttu-id="58672-140">この割り当てに対して `ArgumentException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="58672-140">That assignment throws an `ArgumentException`.</span></span> <span data-ttu-id="58672-141">プロパティの set アクセサーの戻り値は void でなければならないため、例外をスローすることで set アクセサーにエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="58672-141">Because a property set accessor must have a void return type, you report errors in the set accessor by throwing an exception.</span></span>

<span data-ttu-id="58672-142">これが検証のシンプルな例です。</span><span class="sxs-lookup"><span data-stu-id="58672-142">That is a simple case of validation.</span></span> <span data-ttu-id="58672-143">この構文を拡張して、シナリオに必要なあらゆる要素に対応できます。</span><span class="sxs-lookup"><span data-stu-id="58672-143">You can extend this same syntax to anything needed in your scenario.</span></span> <span data-ttu-id="58672-144">たとえば、各種プロパティ間の関係をチェックしたり、外部条件に対して検証したりできます。</span><span class="sxs-lookup"><span data-stu-id="58672-144">You can check the relationships between different properties, or validate against any external conditions.</span></span> <span data-ttu-id="58672-145">C# で有効なステートメントは、すべてプロパティ アクセサーでも有効です。</span><span class="sxs-lookup"><span data-stu-id="58672-145">Any valid C# statements are valid in a property accessor.</span></span>

### <a name="read-only"></a><span data-ttu-id="58672-146">読み取り専用</span><span class="sxs-lookup"><span data-stu-id="58672-146">Read-only</span></span>

<span data-ttu-id="58672-147">ここまでのプロパティ定義はすべて、パブリック アクセサーを持つ読み取り/書き込みプロパティでした。</span><span class="sxs-lookup"><span data-stu-id="58672-147">Up to this point, all the property definitions you have seen are read/write properties with public accessors.</span></span> <span data-ttu-id="58672-148">これ以外にも、プロパティに有効なアクセシビリティがあります。</span><span class="sxs-lookup"><span data-stu-id="58672-148">That's not the only valid accessibility for properties.</span></span>
<span data-ttu-id="58672-149">たとえば、読み取り専用プロパティを作成したり、set アクセサーと get アクセサーに異なるアクセシビリティを設定したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="58672-149">You can create read-only properties, or give different accessibility to the set and get accessors.</span></span> <span data-ttu-id="58672-150">具体例として、`Person` クラスで、クラス内の他のメソッドからのみ `FirstName` プロパティの値を変更できるようにしたい場合は、</span><span class="sxs-lookup"><span data-stu-id="58672-150">Suppose that your `Person` class should only enable changing the value of the `FirstName` property from other methods in that class.</span></span> <span data-ttu-id="58672-151">set アクセサーのアクセシビリティを `public` ではなく `private` に設定します。</span><span class="sxs-lookup"><span data-stu-id="58672-151">You could give the set accessor `private` accessibility instead of `public`:</span></span>

```csharp
public class Person
{
    public string FirstName { get; private set; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="58672-152">これで、`FirstName` プロパティにはどのコードからもアクセスできる一方で、値の割り当ては `Person` クラス内の他のコードからしかできなくなります。</span><span class="sxs-lookup"><span data-stu-id="58672-152">Now, the `FirstName` property can be accessed from any code, but it can only be assigned from other code in the `Person` class.</span></span>

<span data-ttu-id="58672-153">制限を設定するアクセス修飾子を set アクセサーと get アクセサーのどちらか 1 つに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="58672-153">You can add any restrictive access modifier to either the set or get accessors.</span></span> <span data-ttu-id="58672-154">個々のアクセサーには、プロパティ定義のアクセス修飾子よりも制限が強いアクセス修飾子を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58672-154">Any access modifier you place on the individual accessor must be more limited than the access modifier on the property definition.</span></span> <span data-ttu-id="58672-155">上記は、`FirstName` プロパティが `public` ですが set アクセサーが `private` であるため、有効です。</span><span class="sxs-lookup"><span data-stu-id="58672-155">The above is legal because the `FirstName` property is `public`, but the set accessor is `private`.</span></span> <span data-ttu-id="58672-156">`public` なアクセサーを持つ `private` なプロパティを宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="58672-156">You could not declare a `private` property with a `public` accessor.</span></span> <span data-ttu-id="58672-157">プロパティの宣言を宣言することも`protected`、 `internal`、 `protected internal`、`private protected`またはでも`private`です。</span><span class="sxs-lookup"><span data-stu-id="58672-157">Property declarations can also be declared `protected`, `internal`, `protected internal`, `private protected` or even `private`.</span></span>   

<span data-ttu-id="58672-158">`get` アクセサーに制限の高い修飾子を設定することも有効です。</span><span class="sxs-lookup"><span data-stu-id="58672-158">It is also legal to place the more restrictive modifier on the `get` accessor.</span></span> <span data-ttu-id="58672-159">たとえば、`public` なプロパティで、`get` アクセサーを `private` に制限できます。</span><span class="sxs-lookup"><span data-stu-id="58672-159">For example, you could have a `public` property, but restrict the `get` accessor to `private`.</span></span> <span data-ttu-id="58672-160">ただし、このようなシナリオは実際にはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="58672-160">That scenario is rarely done in practice.</span></span>

<span data-ttu-id="58672-161">また、コンストラクターやプロパティの初期化子でのみ設定できるように、プロパティに対する変更を制限することもできます。</span><span class="sxs-lookup"><span data-stu-id="58672-161">You can also restrict modifications to a property so that it can only be set in a constructor or a property initializer.</span></span> <span data-ttu-id="58672-162">`Person` クラスを次のように変更することができます。</span><span class="sxs-lookup"><span data-stu-id="58672-162">You can modify the `Person` class so as follows:</span></span>

```csharp
public class Person
{
    public Person(string firstName)
    {
        this.FirstName = firstName;
    }

    public string FirstName { get; }

    // remaining implementation removed from listing
}
```

<span data-ttu-id="58672-163">この機能は、読み取り専用プロパティとして公開されるコレクションを初期化する場合に最もよく使われます。</span><span class="sxs-lookup"><span data-stu-id="58672-163">This feature is most commonly used for initializing collections that are exposed as read-only properties:</span></span>

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a><span data-ttu-id="58672-164">計算されたプロパティ</span><span class="sxs-lookup"><span data-stu-id="58672-164">Computed Properties</span></span>

<span data-ttu-id="58672-165">プロパティが返す値は、メンバー フィールドの値でなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="58672-165">A property does not need to simply return the value of a member field.</span></span> <span data-ttu-id="58672-166">計算された値を返すプロパティを作成できます。</span><span class="sxs-lookup"><span data-stu-id="58672-166">You can create properties that return a computed value.</span></span> <span data-ttu-id="58672-167">姓と名を連結する計算をしてフルネームを返すように `Person` オブジェクトを拡張してみましょう。</span><span class="sxs-lookup"><span data-stu-id="58672-167">Let's expand the `Person` object to return the full name, computed by concatenating the first and last names:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName { get { return $"{FirstName} {LastName}"; } }
}
```

<span data-ttu-id="58672-168">上の例では、"*文字列補間*" 構文を使用して、フルネームを表す書式設定された文字列を作成しています。</span><span class="sxs-lookup"><span data-stu-id="58672-168">The example above uses the *String Interpolation* syntax to create the formatted string for the full name.</span></span>

<span data-ttu-id="58672-169">"*式形式のメンバー*" を使用することもできます。式形式のメンバーを使用すると、計算された `FullName` プロパティを簡潔な方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="58672-169">You can also use *Expression-bodied Members*, which provides a more succinct way to create the computed `FullName` property:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    public string FullName =>  $"{FirstName} {LastName}";
}
```
 
<span data-ttu-id="58672-170">"*式形式のメンバー*" では、式が 1 つだけ含まれたメソッドを定義する "*ラムダ式*" 構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="58672-170">*Expression-bodied Members* use the *lambda expression* syntax to define a method that contain a single expression.</span></span> <span data-ttu-id="58672-171">ここでは、その式が Person オブジェクトのフルネームを返しています。</span><span class="sxs-lookup"><span data-stu-id="58672-171">Here, that expression returns the full name for the person object.</span></span>

### <a name="lazy-evaluated-properties"></a><span data-ttu-id="58672-172">遅延評価されたプロパティ</span><span class="sxs-lookup"><span data-stu-id="58672-172">Lazy Evaluated Properties</span></span>

<span data-ttu-id="58672-173">計算されたプロパティの概念をストレージと組み合わせて、"*遅延評価されたプロパティ*" を作成できます。</span><span class="sxs-lookup"><span data-stu-id="58672-173">You can mix the concept of a computed property with storage and create a *lazy evaluated property*.</span></span>  <span data-ttu-id="58672-174">たとえば、`FullName` プロパティを更新して、プロパティが最初にアクセスされたときに文字列が書式設定されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="58672-174">For example, you could update the `FullName` property so that the string formatting only happened the first time it was accessed:</span></span>

```csharp
public class Person
{
    public string FirstName { get; set; }

    public string LastName { get; set; }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="58672-175">ただし、上記のコードにはバグが含まれています。</span><span class="sxs-lookup"><span data-stu-id="58672-175">The above code contains a bug though.</span></span> <span data-ttu-id="58672-176">コードによって `FirstName` プロパティと `LastName` プロパティのいずれかの値が更新されると、以前に評価された `fullName` フィールドは無効になります。</span><span class="sxs-lookup"><span data-stu-id="58672-176">If code updates the value of either the `FirstName` or `LastName` property, the previously evaluated `fullName` field is invalid.</span></span> <span data-ttu-id="58672-177">`fullName` フィールドが再計算されるように、`FirstName` プロパティと `LastName` プロパティの `set` アクセサーを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58672-177">You need to update the `set` accessors of the `FirstName` and `LastName` property so that the `fullName` field is calculated again:</span></span>

```csharp
public class Person
{
    private string firstName;
    public string FirstName
    {
        get => firstName;
        set
        {
            firstName = value;
            fullName = null;
        }
    }

    private string lastName;
    public string LastName
    {
        get => lastName;
        set
        {
            lastName = value;
            fullName = null;
        }
    }

    private string fullName;
    public string FullName
    {
        get
        {
            if (fullName == null)
                fullName = $"{FirstName} {LastName}";
            return fullName;
        }
    }
}
```

<span data-ttu-id="58672-178">上の最終版では、必要になった場合にのみ `FullName` プロパティが評価されます。</span><span class="sxs-lookup"><span data-stu-id="58672-178">This final version evaluates the `FullName` property only when needed.</span></span>
<span data-ttu-id="58672-179">以前に計算されたものが有効であれば、それが使用されます。</span><span class="sxs-lookup"><span data-stu-id="58672-179">If the previously calculated version is valid, it's used.</span></span> <span data-ttu-id="58672-180">状態が変化したことで、以前に計算されたバージョンが無効になると、再計算が行われます。</span><span class="sxs-lookup"><span data-stu-id="58672-180">If another state change invalidates the previously calculated version, it will be recalculated.</span></span> <span data-ttu-id="58672-181">このクラスを使用するにあたって、開発者は実装の詳細を知っている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="58672-181">Developers that use this class do not need to know the details of the implementation.</span></span> <span data-ttu-id="58672-182">内部で変化があっても Person オブジェクトの使用には影響しません。</span><span class="sxs-lookup"><span data-stu-id="58672-182">None of these internal changes affect the use of the Person object.</span></span> <span data-ttu-id="58672-183">これが、プロパティを使用してオブジェクトのデータ メンバーを公開するする重要な利点です。</span><span class="sxs-lookup"><span data-stu-id="58672-183">That's the key reason for using Properties to expose data members of an object.</span></span>
 
### <a name="inotifypropertychanged"></a><span data-ttu-id="58672-184">INotifyPropertyChanged</span><span class="sxs-lookup"><span data-stu-id="58672-184">INotifyPropertyChanged</span></span>

<span data-ttu-id="58672-185">プロパティ アクセサーでコードを記述する必要があるシナリオとして、値が変更されたことをデータ バインディング クライアントに通知するための `INotifyPropertyChanged` インターフェイスのサポートというものもあります。</span><span class="sxs-lookup"><span data-stu-id="58672-185">A final scenario where you need to write code in a property accessor is to support the `INotifyPropertyChanged` interface used to notify data binding clients that a value has changed.</span></span> <span data-ttu-id="58672-186">プロパティの値が変更されると、オブジェクトはその変更を示す `PropertyChanged` イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="58672-186">When the value of a property changes, the object raises the `PropertyChanged` event to indicate the change.</span></span> <span data-ttu-id="58672-187">データ バインディング ライブラリは、その変更に基づいて表示要素を更新します。</span><span class="sxs-lookup"><span data-stu-id="58672-187">The data binding libraries, in turn, update display elements based on that change.</span></span> <span data-ttu-id="58672-188">下のコードは、この Person クラスの `FirstName` プロパティに `INotifyPropertyChanged` を実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="58672-188">The code below shows how you would implement `INotifyPropertyChanged` for the `FirstName` property of this person class.</span></span>

```csharp
public class Person : INotifyPropertyChanged
{
    public string FirstName
    {
        get => firstName;
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("First name must not be blank");
            if (value != firstName)
            {
                PropertyChanged?.Invoke(this, 
                    new PropertyChangedEventArgs(nameof(FirstName)));
            }
            firstName = value;
        }
    }
    private string firstName;

    public event PropertyChangedEventHandler PropertyChanged;
    // remaining implementation removed from listing
}
```

<span data-ttu-id="58672-189">`?.` は "*null 条件演算子*" と呼ばれる演算子です。</span><span class="sxs-lookup"><span data-stu-id="58672-189">The `?.` operator is called the *null conditional operator*.</span></span> <span data-ttu-id="58672-190">演算子の右側を評価する前に、null 参照がないかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="58672-190">It checks for a null reference before evaluating the right side of the operator.</span></span> <span data-ttu-id="58672-191">チェックの結果、`PropertyChanged` イベントに対するサブスクライバーがない場合は、イベントを発生させるコードは実行されません。</span><span class="sxs-lookup"><span data-stu-id="58672-191">The end result is that if there are no subscribers to the `PropertyChanged` event, the code to raise the event doesn't execute.</span></span> <span data-ttu-id="58672-192">その場合、評価は行われず `NullReferenceException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="58672-192">It would throw a `NullReferenceException` without this check in that case.</span></span> <span data-ttu-id="58672-193">詳細については、[`events`](delegates-events.md) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="58672-193">See the page on [`events`](delegates-events.md) for more details.</span></span> <span data-ttu-id="58672-194">上記の例では、新たに `nameof` という演算子を使用して、記号としてのプロパティ名を文字列に変換しています。</span><span class="sxs-lookup"><span data-stu-id="58672-194">This example also uses the new `nameof` operator to convert from the property name symbol to its text representation.</span></span>
<span data-ttu-id="58672-195">`nameof` を使用すると、プロパティ名にタイプミスが含まれるというエラーを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="58672-195">Using `nameof` can reduce errors where you have mistyped the name of the property.</span></span>

<span data-ttu-id="58672-196">これも、アクセサーでコードを記述することで目的のシナリオをサポートできるケースの一例です。</span><span class="sxs-lookup"><span data-stu-id="58672-196">Again, this is an example of a case where you can write code in your accessors to support the scenarios you need.</span></span>

## <a name="summing-up"></a><span data-ttu-id="58672-197">まとめ</span><span class="sxs-lookup"><span data-stu-id="58672-197">Summing up</span></span>

<span data-ttu-id="58672-198">プロパティは、クラスまたはオブジェクトに含まれた一種のスマート フィールドです。</span><span class="sxs-lookup"><span data-stu-id="58672-198">Properties are a form of smart fields in a class or object.</span></span> <span data-ttu-id="58672-199">オブジェクトの外部からは、オブジェクト内にあるフィールドのように見えます。</span><span class="sxs-lookup"><span data-stu-id="58672-199">From outside the object, they appear like fields in the object.</span></span> <span data-ttu-id="58672-200">一方、プロパティは、C# の機能をどれでも自由に使用して実装できます。</span><span class="sxs-lookup"><span data-stu-id="58672-200">However, properties can be implemented using the full palette of C# functionality.</span></span>
<span data-ttu-id="58672-201">検証、各種アクセシビリティ、遅延評価など、目的のシナリオで必要となる要素はすべて提供できます。</span><span class="sxs-lookup"><span data-stu-id="58672-201">You can provide validation, different accessibility, lazy evaluation, or any requirements your scenarios need.</span></span>
