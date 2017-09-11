---
title: ".NET でのその他の文字列の解析"
description: ".NET でのその他の文字列の解析"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/29/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 67670b10-3df4-45ea-8908-5ba3f056887c
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: db80cc5f37e814f224ff76b14a906bb4d41064fb
ms.contentlocale: ja-jp
ms.lasthandoff: 03/02/2017

---

# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="73cb4-104">.NET でのその他の文字列の解析</span><span class="sxs-lookup"><span data-stu-id="73cb4-104">Parsing other strings in .NET</span></span>

<span data-ttu-id="73cb4-105">数値および [DateTime](xref:System.DateTime) 文字列だけでなく、[Char](xref:System.Char)、[Boolean](xref:System.Boolean)、および [Enum](xref:System.Enum) 型を表す文字列をデータ型に解析することもできます。</span><span class="sxs-lookup"><span data-stu-id="73cb4-105">In addition to numeric and [DateTime](xref:System.DateTime) strings, you can also parse strings that represent the types [Char](xref:System.Char), [Boolean](xref:System.Boolean), and [Enum](xref:System.Enum) into data types.</span></span>

## <a name="char"></a><span data-ttu-id="73cb4-106">Char</span><span class="sxs-lookup"><span data-stu-id="73cb4-106">Char</span></span>

<span data-ttu-id="73cb4-107">[Char](xref:System.Char) データ型に関連付けられている静的解析メソッドは、1 つの文字を含む文字列をUnicode 値に変換するのに便利です。</span><span class="sxs-lookup"><span data-stu-id="73cb4-107">The static parse method associated with the [Char](xref:System.Char) data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="73cb4-108">次のコードの例では、文字列を Unicode 文字に解析します。</span><span class="sxs-lookup"><span data-stu-id="73cb4-108">The following code example parses a string into a Unicode character.</span></span>

```csharp
string MyString1 = "A";
char MyChar = Char.Parse(MyString1);
// MyChar now contains a Unicode "A" character.
```

```vb
Dim MyString1 As String = "A"
Dim MyChar As Char = Char.Parse(MyString1)
' MyChar now contains a Unicode "A" character.
```

## <a name="boolean"></a><span data-ttu-id="73cb4-109">ブール型</span><span class="sxs-lookup"><span data-stu-id="73cb4-109">Boolean</span></span>

<span data-ttu-id="73cb4-110">[Boolean](xref:System.Boolean) データ型には、[Parse](xref:System.Boolean.Parse(System.String)) メソッドが含まれ、`Boolean` 値を示す文字列を実際の `Boolean` 型に変換するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="73cb4-110">The [Boolean](xref:System.Boolean) data type contains a [Parse](xref:System.Boolean.Parse(System.String)) method that you can use to convert a string that represents a `Boolean` value into an actual `Boolean` type.</span></span> <span data-ttu-id="73cb4-111">このメソッドは大文字と小文字を区別しません。また、"True" または "False" を含む文字列を正常に解析することができます。</span><span class="sxs-lookup"><span data-stu-id="73cb4-111">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="73cb4-112">`Boolean` 型に関連付けられる `Parse` メソッドは、空白で囲まれた文字列を解析することもできます。</span><span class="sxs-lookup"><span data-stu-id="73cb4-112">The `Parse` method associated with the `Boolean` type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="73cb4-113">その他の文字列が渡された場合、[FormatException](xref:System.FormatException) がスローされます。</span><span class="sxs-lookup"><span data-stu-id="73cb4-113">If any other string is passed, a [FormatException](xref:System.FormatException) is thrown.</span></span>

<span data-ttu-id="73cb4-114">次のコードの例では、`Parse` メソッドを使用して、文字列を `Boolean` 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="73cb4-114">The following code example uses the `Parse` method to convert a string into a `Boolean` value.</span></span>

```csharp
string MyString2 = "True";
bool MyBool = bool.Parse(MyString2);
// MyBool now contains a True Boolean value.
```

```vb
Dim MyString1 As String = "A"
Dim MyChar As Char = Char.Parse(MyString1)
' MyChar now contains a Unicode "A" character.
```

## <a name="enumeration"></a><span data-ttu-id="73cb4-115">列挙</span><span class="sxs-lookup"><span data-stu-id="73cb4-115">Enumeration</span></span>

<span data-ttu-id="73cb4-116">静的 [Parse](xref:System.Enum.Parse(System.Type,System.String)) メソッドを使用して、列挙型を文字列の値に初期化できます。</span><span class="sxs-lookup"><span data-stu-id="73cb4-116">You can use the static [Parse](xref:System.Enum.Parse(System.Type,System.String)) method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="73cb4-117">このメソッドでは、解析している列挙型、解析する文字列、および解析が大文字小文字を区別するかどうかを示す省略可能な `Boolean` フラグを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="73cb4-117">This method accepts the enumeration type you are parsing, the string to parse, and an optional `Boolean` flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="73cb4-118">解析している文字列は、コンマで区切られた複数の値を含めることができます。これは、1 つ以上の空の領域 (空白とも呼ばれます) が前後にある場合があります。</span><span class="sxs-lookup"><span data-stu-id="73cb4-118">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="73cb4-119">文字列に複数の値がある場合、返されたオブジェクトの値は、ビット演算 OR 演算と組み合わされたすべての指定された値の値です。</span><span class="sxs-lookup"><span data-stu-id="73cb4-119">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>

<span data-ttu-id="73cb4-120">次の例では、`Parse` メソッドを使用して、文字列形式を列挙値に変換します。</span><span class="sxs-lookup"><span data-stu-id="73cb4-120">The following example uses the `Parse` method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="73cb4-121">[DayOfWeek](xref:System.DayOfWeek) 列挙体は、文字列から Thursday に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="73cb4-121">The [DayOfWeek](xref:System.DayOfWeek) enumeration is initialized to Thursday from a string.</span></span>

```csharp
string MyString3 = "Thursday";
DayOfWeek MyDays = (DayOfWeek)Enum.Parse(typeof(DayOfWeek), MyString3);
Console.WriteLine(MyDays);
// The result is Thursday.
```

```vb
Dim MyString3 As String = "Thursday"
Dim MyDays As DayOfWeek = CType([Enum].Parse(GetType(DayOfWeek), MyString3), DayOfWeek)
Console.WriteLine("{0:G}", MyDays)
' The result is Thursday.
```

## <a name="see-also"></a><span data-ttu-id="73cb4-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="73cb4-122">See Also</span></span>

[<span data-ttu-id="73cb4-123">.NET での文字列の解析</span><span class="sxs-lookup"><span data-stu-id="73cb4-123">Parsing strings in .NET</span></span>](parsing-strings.md)

[<span data-ttu-id="73cb4-124">.NET での型の書式設定</span><span class="sxs-lookup"><span data-stu-id="73cb4-124">Formatting types in .NET</span></span>](formatting-types.md)

[<span data-ttu-id="73cb4-125">.NET での型変換</span><span class="sxs-lookup"><span data-stu-id="73cb4-125">Type conversion in .NET</span></span>](type-conversion.md)


