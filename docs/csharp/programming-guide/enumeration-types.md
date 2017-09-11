---
title: "列挙型 (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 677de7c6e0c0f72b600ce8ee5a8bad265725f6d3
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="5eb84-102">列挙型 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="5eb84-102">Enumeration Types (C# Programming Guide)</span></span>
<span data-ttu-id="5eb84-103">列挙型 (列挙値または Enum とも呼ばれます) を利用すると、変数に割り当てる一連の名前付き整数定数を効率的に定義できます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="5eb84-104">たとえば、値が週の曜日を表す変数を定義するとします。</span><span class="sxs-lookup"><span data-stu-id="5eb84-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="5eb84-105">その変数が格納するのは 7 つの意味のある値だけです。</span><span class="sxs-lookup"><span data-stu-id="5eb84-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="5eb84-106">これらの値を定義するために、列挙型を利用できます。列挙型は [enum](../../csharp/language-reference/keywords/enum.md) キーワードで宣言されます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../../csharp/language-reference/keywords/enum.md) keyword.</span></span>  
  
 <span data-ttu-id="5eb84-107">[!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="5eb84-107">[!code-cs[csProgGuideEnums#1](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_1.cs)]</span></span>  
  
 <span data-ttu-id="5eb84-108">既定では、列挙の各要素の基になる型は [int](../../csharp/language-reference/keywords/int.md) です。</span><span class="sxs-lookup"><span data-stu-id="5eb84-108">By default the underlying type of each element in the enum is [int](../../csharp/language-reference/keywords/int.md).</span></span> <span data-ttu-id="5eb84-109">前の例のように、コロンを使用し、別の整数型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-109">You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="5eb84-110">使用可能な型の一覧については、「[enum (C# リファレンス)](../../csharp/language-reference/keywords/enum.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eb84-110">For a full list of possible types, see [enum (C# Reference)](../../csharp/language-reference/keywords/enum.md).</span></span>  
  
 <span data-ttu-id="5eb84-111">次の例のように、基になる型に型変換することで、基になる数値を確認できます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-111">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>  
  
```csharp  
Days today = Days.Monday;  
int dayNumber =(int)today;  
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);  
  
Months thisMonth = Months.Dec;  
byte monthNumber = (byte)thisMonth;  
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);  
  
// Output:  
// Monday is day number #1.  
// Dec is month number #11.  
```  
  
 <span data-ttu-id="5eb84-112">数値型ではなく列挙型を使用する利点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5eb84-112">The following are advantages of using an enum instead of a numeric type:</span></span>  
  
-   <span data-ttu-id="5eb84-113">変数に対して有効な値をクライアント コードのために明確に指定します。</span><span class="sxs-lookup"><span data-stu-id="5eb84-113">You clearly specify for client code which values are valid for the variable.</span></span>  
  
-   <span data-ttu-id="5eb84-114">[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] の IntelliSense で、定義済みの値が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-114">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], IntelliSense lists the defined values.</span></span>  
  
 <span data-ttu-id="5eb84-115">列挙子一覧に要素の値を指定しないとき、値は自動的に 1 ずつ増えます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-115">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="5eb84-116">前の例では、`Days.Sunday` の値が 0 で、`Days.Monday` の値が 1 です。その後も同様に 1 ずつ増えます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-116">In the previous example, `Days.Sunday` has a value of 0, `Days.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="5eb84-117">新しい `Days` オブジェクトを作成するとき、明示的に値を割り当てない場合、`Days.Sunday` の既定値 (0) が与えられます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-117">When you create a new `Days` object, it will have a default value of `Days.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="5eb84-118">列挙を作成するときは、最も論理的な既定値を選択し、それにゼロの値を与えます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-118">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="5eb84-119">それにより、列挙を作成したときに明示的に値を割り当てない場合、すべての列挙にその既定値が与えられます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-119">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>  
  
 <span data-ttu-id="5eb84-120">変数 `meetingDay` の型が `Days` の場合、(明示的な型変換なしで) `Days` により定義される値の 1 つのみを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-120">If the variable `meetingDay` is of type `Days`, then (without an explicit cast) you can only assign it one of the values defined by `Days`.</span></span> <span data-ttu-id="5eb84-121">会議の日が変更されたら、`Days` から `meetingDay` に新しい値を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-121">And if the meeting day changes, you can assign a new value from `Days` to `meetingDay`:</span></span>  
  
 <span data-ttu-id="5eb84-122">[!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="5eb84-122">[!code-cs[csProgGuideEnums#4](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5eb84-123">任意の整数値を `meetingDay` に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-123">It is possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="5eb84-124">たとえば、`meetingDay = (Days) 42` というコード行はエラーを生成しません。</span><span class="sxs-lookup"><span data-stu-id="5eb84-124">For example, this line of code does not produce an error: `meetingDay = (Days) 42`.</span></span> <span data-ttu-id="5eb84-125">ただし、これは行わないでください。列挙変数は列挙により定義される値の 1 つのみを保持すると暗黙的に予想されるためです。</span><span class="sxs-lookup"><span data-stu-id="5eb84-125">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="5eb84-126">列挙型の変数に任意の値を割り当てると、エラーが発生する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="5eb84-126">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>  
  
 <span data-ttu-id="5eb84-127">ある列挙型の列挙子一覧の要素に任意の値を割り当てることができます。また、計算された値を利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-127">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>  
  
 <span data-ttu-id="5eb84-128">[!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="5eb84-128">[!code-cs[csProgGuideEnums#3](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_3.cs)]</span></span>  
  
## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="5eb84-129">ビット フラグとしての列挙型</span><span class="sxs-lookup"><span data-stu-id="5eb84-129">Enumeration Types as Bit Flags</span></span>  
 <span data-ttu-id="5eb84-130">列挙型を利用してビット フラグを定義できます。ビット フラグを定義すると、列挙型のインスタンスは列挙子一覧で定義されている値のあらゆる組み合わせを格納できます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-130">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="5eb84-131">(もちろん、意味のない組み合わせやプログラム コードで許可されない組み合わせもあります。)</span><span class="sxs-lookup"><span data-stu-id="5eb84-131">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>  
  
 <span data-ttu-id="5eb84-132">ビット フラグ列挙を作成するには、<xref:System.FlagsAttribute?displayProperty=fullName> 属性を適用し、ビット処理演算の `AND`、`OR`、`NOT`、`XOR` を実行できるように値を定義します。</span><span class="sxs-lookup"><span data-stu-id="5eb84-132">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=fullName> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="5eb84-133">ビット フラグ列挙に、"フラグが設定されていない" という意味のゼロの値を持つ名前付き定数を追加します。</span><span class="sxs-lookup"><span data-stu-id="5eb84-133">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="5eb84-134">"フラグが設定されていない" という意味ではない場合、ゼロの値をフラグに指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="5eb84-134">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>  
  
 <span data-ttu-id="5eb84-135">次の例では、`Days` 列挙の別のバージョンが定義されています。`Days2` という名前が付いています。</span><span class="sxs-lookup"><span data-stu-id="5eb84-135">In the following example, another version of the `Days` enum, which is named `Days2`, is defined.</span></span> <span data-ttu-id="5eb84-136">`Days2` に `Flags` 属性が与えられており、各値に次の大きい 2 の累乗が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="5eb84-136">`Days2` has the `Flags` attribute and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="5eb84-137">これにより、値が `Days2.Tuesday` と `Days2.Thursday` になる `Days2` 変数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-137">This enables you to create a `Days2` variable whose value is `Days2.Tuesday` and `Days2.Thursday`.</span></span>  
  
 <span data-ttu-id="5eb84-138">[!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="5eb84-138">[!code-cs[csProgGuideEnums#2](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_4.cs)]</span></span>  
  
 <span data-ttu-id="5eb84-139">列挙にフラグを設定するには、次の例のように、ビット処理演算子 `OR` を利用します。</span><span class="sxs-lookup"><span data-stu-id="5eb84-139">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>  
  
 <span data-ttu-id="5eb84-140">[!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="5eb84-140">[!code-cs[csProgGuideEnums#6](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_5.cs)]</span></span>  
  
 <span data-ttu-id="5eb84-141">特定のフラグが設定されているかどうかを判断するには、次の例のように、ビット処理演算 `AND` を利用します。</span><span class="sxs-lookup"><span data-stu-id="5eb84-141">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>  
  
 <span data-ttu-id="5eb84-142">[!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="5eb84-142">[!code-cs[csProgGuideEnums#7](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_6.cs)]</span></span>  
  
 <span data-ttu-id="5eb84-143"><xref:System.FlagsAttribute?displayProperty=fullName> 属性を使用して列挙型を定義する際の検討事項の詳細については、<xref:System.Enum?displayProperty=fullName> に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eb84-143">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=fullName> attribute, see <xref:System.Enum?displayProperty=fullName>.</span></span>  
  
## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="5eb84-144">System.Enum メソッドを利用して列挙値を検出し、操作する</span><span class="sxs-lookup"><span data-stu-id="5eb84-144">Using the System.Enum Methods to Discover and Manipulate Enum Values</span></span>  
 <span data-ttu-id="5eb84-145">列挙はすべて、<xref:System.Enum?displayProperty=fullName> 型のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="5eb84-145">All enums are instances of the <xref:System.Enum?displayProperty=fullName> type.</span></span> <span data-ttu-id="5eb84-146"><xref:System.Enum?displayProperty=fullName> から新しいクラスを派生させることはできませんが、このメソッドを利用して列挙インスタンスの値に関する情報を検出し、操作できます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-146">You cannot derive new classes from <xref:System.Enum?displayProperty=fullName>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>  
  
 <span data-ttu-id="5eb84-147">[!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="5eb84-147">[!code-cs[csProgGuideEnums#5](../../csharp/programming-guide/codesnippet/CSharp/enumeration-types_7.cs)]</span></span>  
  
 <span data-ttu-id="5eb84-148">詳細については、「<xref:System.Enum?displayProperty=fullName>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eb84-148">For more information, see <xref:System.Enum?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="5eb84-149">拡張メソッドを利用して列挙に新しいメソッドを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="5eb84-149">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="5eb84-150">詳細については、「[方法 : 列挙型対応の新しいメソッドを作成する](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5eb84-150">For more information, see [How to: Create a New Method for an Enumeration](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>  

## <a name="see-also"></a><span data-ttu-id="5eb84-151">関連項目</span><span class="sxs-lookup"><span data-stu-id="5eb84-151">See Also</span></span>  
 <span data-ttu-id="5eb84-152"><xref:System.Enum?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5eb84-152"><xref:System.Enum?displayProperty=fullName></span></span>   
 <span data-ttu-id="5eb84-153">[C# プログラミング ガイド](../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5eb84-153">[C# Programming Guide](../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="5eb84-154">enum</span><span class="sxs-lookup"><span data-stu-id="5eb84-154">enum</span></span>](../../csharp/language-reference/keywords/enum.md)

