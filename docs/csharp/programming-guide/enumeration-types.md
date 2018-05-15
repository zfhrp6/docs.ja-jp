---
title: 列挙型 (C# プログラミング ガイド)
ms.date: 09/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cdaa609acfa34f3b0b3073d88f09fe735d48e9a2
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="bff8c-102">列挙型 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="bff8c-102">Enumeration types (C# Programming Guide)</span></span>

<span data-ttu-id="bff8c-103">列挙型 (列挙値または Enum とも呼ばれます) を利用すると、変数に割り当てる一連の名前付き整数定数を効率的に定義できます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="bff8c-104">たとえば、値が週の曜日を表す変数を定義するとします。</span><span class="sxs-lookup"><span data-stu-id="bff8c-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="bff8c-105">その変数が格納するのは 7 つの意味のある値だけです。</span><span class="sxs-lookup"><span data-stu-id="bff8c-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="bff8c-106">これらの値を定義するために、列挙型を利用できます。列挙型は [enum](../../csharp/language-reference/keywords/enum.md) キーワードで宣言されます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../../csharp/language-reference/keywords/enum.md) keyword.</span></span>

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

<span data-ttu-id="bff8c-107">既定では、列挙の各要素の基になる型は [int](../../csharp/language-reference/keywords/int.md) です。前の例のように、コロンを使用し、別の整数型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-107">By default the underlying type of each element in the enum is [int](../../csharp/language-reference/keywords/int.md). You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="bff8c-108">使用可能な型の一覧については、「[enum (C# リファレンス)](../../csharp/language-reference/keywords/enum.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bff8c-108">For a full list of possible types, see [enum (C# Reference)](../../csharp/language-reference/keywords/enum.md).</span></span>

<span data-ttu-id="bff8c-109">次の例のように、基になる型に型変換することで、基になる数値を確認できます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-109">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>

```csharp
Day today = Day.Monday;
int dayNumber =(int)today;
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);

Month thisMonth = Month.Dec;
byte monthNumber = (byte)thisMonth;
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);

// Output:
// Monday is day number #1.
// Dec is month number #11.
```

<span data-ttu-id="bff8c-110">数値型ではなく列挙型を使用する利点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-110">The following are advantages of using an enum instead of a numeric type:</span></span>

- <span data-ttu-id="bff8c-111">変数に対して有効な値をクライアント コードのために明確に指定します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-111">You clearly specify for client code which values are valid for the variable.</span></span>

- <span data-ttu-id="bff8c-112">Visual Studio の IntelliSense で、定義済みの値が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-112">In Visual Studio, IntelliSense lists the defined values.</span></span>

<span data-ttu-id="bff8c-113">列挙子一覧に要素の値を指定しないとき、値は自動的に 1 ずつ増えます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-113">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="bff8c-114">前の例では、`Day.Sunday` の値が 0 で、`Day.Monday` の値が 1 です。その後も同様に 1 ずつ増えます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-114">In the previous example, `Day.Sunday` has a value of 0, `Day.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="bff8c-115">新しい `Day` オブジェクトを作成するとき、明示的に値を割り当てない場合、`Day.Sunday` の既定値 (0) が与えられます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-115">When you create a new `Day` object, it will have a default value of `Day.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="bff8c-116">列挙を作成するときは、最も論理的な既定値を選択し、それにゼロの値を与えます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-116">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="bff8c-117">それにより、列挙を作成したときに明示的に値を割り当てない場合、すべての列挙にその既定値が与えられます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-117">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>

<span data-ttu-id="bff8c-118">変数 `meetingDay` の型が `Day` の場合、(明示的な型変換なしで) `Day` により定義される値の 1 つのみを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-118">If the variable `meetingDay` is of type `Day`, then (without an explicit cast) you can only assign it one of the values defined by `Day`.</span></span> <span data-ttu-id="bff8c-119">会議の日が変更されたら、`Day` から `meetingDay` に新しい値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-119">And if the meeting day changes, you can assign a new value from `Day` to `meetingDay`:</span></span>

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> <span data-ttu-id="bff8c-120">任意の整数値を `meetingDay` に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-120">It's possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="bff8c-121">たとえば、`meetingDay = (Day) 42` というコード行はエラーを生成しません。</span><span class="sxs-lookup"><span data-stu-id="bff8c-121">For example, this line of code does not produce an error: `meetingDay = (Day) 42`.</span></span> <span data-ttu-id="bff8c-122">ただし、これは行わないでください。列挙変数は列挙により定義される値の 1 つのみを保持すると暗黙的に予想されるためです。</span><span class="sxs-lookup"><span data-stu-id="bff8c-122">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="bff8c-123">列挙型の変数に任意の値を割り当てると、エラーが発生する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="bff8c-123">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>

<span data-ttu-id="bff8c-124">ある列挙型の列挙子一覧の要素に任意の値を割り当てることができます。また、計算された値を利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-124">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="bff8c-125">ビット フラグとしての列挙型</span><span class="sxs-lookup"><span data-stu-id="bff8c-125">Enumeration types as bit flags</span></span>

<span data-ttu-id="bff8c-126">列挙型を利用してビット フラグを定義できます。ビット フラグを定義すると、列挙型のインスタンスは列挙子一覧で定義されている値のあらゆる組み合わせを格納できます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-126">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="bff8c-127">(もちろん、意味のない組み合わせやプログラム コードで許可されない組み合わせもあります。)</span><span class="sxs-lookup"><span data-stu-id="bff8c-127">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>

<span data-ttu-id="bff8c-128">ビット フラグ列挙を作成するには、<xref:System.FlagsAttribute?displayProperty=nameWithType> 属性を適用し、ビット処理演算の `AND`、`OR`、`NOT`、`XOR` を実行できるように値を定義します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-128">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="bff8c-129">ビット フラグ列挙に、"フラグが設定されていない" という意味のゼロの値を持つ名前付き定数を追加します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-129">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="bff8c-130">"フラグが設定されていない" という意味ではない場合、ゼロの値をフラグに指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="bff8c-130">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>

<span data-ttu-id="bff8c-131">次の例では、`Day` 列挙の別のバージョンが定義されています。`Days` という名前が付いています。</span><span class="sxs-lookup"><span data-stu-id="bff8c-131">In the following example, another version of the `Day` enum, which is named `Days`, is defined.</span></span> <span data-ttu-id="bff8c-132">`Days` に `Flags` 属性が与えられており、各値に次の大きい 2 の累乗が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="bff8c-132">`Days` has the `Flags` attribute, and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="bff8c-133">これにより、値が `Days.Tuesday | Days.Thursday` になる `Days` 変数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-133">This enables you to create a `Days` variable whose value is `Days.Tuesday | Days.Thursday`.</span></span>

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

<span data-ttu-id="bff8c-134">列挙にフラグを設定するには、次の例のように、ビット処理演算子 `OR` を利用します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-134">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

<span data-ttu-id="bff8c-135">特定のフラグが設定されているかどうかを判断するには、次の例のように、ビット処理演算 `AND` を利用します。</span><span class="sxs-lookup"><span data-stu-id="bff8c-135">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<span data-ttu-id="bff8c-136"><xref:System.FlagsAttribute?displayProperty=nameWithType> 属性を使用して列挙型を定義する際の検討事項の詳細については、<xref:System.Enum?displayProperty=nameWithType> に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bff8c-136">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="bff8c-137">System.Enum メソッドを利用して列挙値を検出し、操作する</span><span class="sxs-lookup"><span data-stu-id="bff8c-137">Using the System.Enum methods to discover and manipulate enum values</span></span>

<span data-ttu-id="bff8c-138">列挙はすべて、<xref:System.Enum?displayProperty=nameWithType> 型のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="bff8c-138">All enums are instances of the <xref:System.Enum?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="bff8c-139"><xref:System.Enum?displayProperty=nameWithType> から新しいクラスを派生させることはできませんが、このメソッドを利用して列挙インスタンスの値に関する情報を検出し、操作できます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-139">You cannot derive new classes from <xref:System.Enum?displayProperty=nameWithType>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

<span data-ttu-id="bff8c-140">詳細については、「<xref:System.Enum?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bff8c-140">For more information, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="bff8c-141">拡張メソッドを利用して列挙に新しいメソッドを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="bff8c-141">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="bff8c-142">詳細については、「[方法 : 列挙型対応の新しいメソッドを作成する](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bff8c-142">For more information, see [How to: Create a New Method for an Enumeration](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bff8c-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="bff8c-143">See also</span></span>
 <xref:System.Enum?displayProperty=nameWithType>  
 [<span data-ttu-id="bff8c-144">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="bff8c-144">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bff8c-145">enum</span><span class="sxs-lookup"><span data-stu-id="bff8c-145">enum</span></span>](../../csharp/language-reference/keywords/enum.md)
