---
title: "enum (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords: enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
caps.latest.revision: "36"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 00ae9b555ae73db445fe4a4facf00753bf8c759a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="enum-c-reference"></a><span data-ttu-id="525d4-102">enum (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="525d4-102">enum (C# Reference)</span></span>
<span data-ttu-id="525d4-103">`enum` キーワードは、列挙型を宣言するために使用されます。列挙型は、列挙子リストと呼ばれる名前付き定数の集まりで構成される固有の型です。</span><span class="sxs-lookup"><span data-stu-id="525d4-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>  
  
 <span data-ttu-id="525d4-104">通常、列挙型は名前空間内に直接定義して、名前空間内のすべてのクラスが共通の利便性でアクセスできるようにするのが最も適切です。</span><span class="sxs-lookup"><span data-stu-id="525d4-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="525d4-105">ただし、列挙型はクラスまたは構造体内に入れ子にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="525d4-105">However, an enum can also be nested within a class or struct.</span></span>  
  
 <span data-ttu-id="525d4-106">既定では、最初の列挙子の値は 0 で、後続の列挙子の値は 1 ずつ増加していきます。</span><span class="sxs-lookup"><span data-stu-id="525d4-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="525d4-107">たとえば、次の列挙型では、 `Sat` は `0`、 `Sun` は `1`、 `Mon` は `2`などとなります。</span><span class="sxs-lookup"><span data-stu-id="525d4-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>  
  
```  
enum Days {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="525d4-108">列挙型では、次の例に示すように、初期化子を使用して既定値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="525d4-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>  
  
```  
enum Days {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="525d4-109">この列挙型では、要素の並びは `1` からではなく、 `0`から開始します。</span><span class="sxs-lookup"><span data-stu-id="525d4-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="525d4-110">ただし、列挙型には値が 0 となる定数を含めておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="525d4-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="525d4-111">詳細については、[列挙型](../../../csharp/programming-guide/enumeration-types.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="525d4-111">For more information, see [Enumeration Types](../../../csharp/programming-guide/enumeration-types.md).</span></span>  
  
 <span data-ttu-id="525d4-112">すべての列挙型には基になる型があり、基になる型には [char](../../../csharp/language-reference/keywords/char.md) 以外の任意の整数型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="525d4-112">Every enumeration type has an underlying type, which can be any integral type except [char](../../../csharp/language-reference/keywords/char.md).</span></span> <span data-ttu-id="525d4-113">列挙要素の基になる既定の型は [int](../../../csharp/language-reference/keywords/int.md)です。[byte](../../../csharp/language-reference/keywords/byte.md)など、他の整数型の列挙型を宣言するには、次の例に示すように、識別子に続けてコロンを使用し、その後に型を記述します。</span><span class="sxs-lookup"><span data-stu-id="525d4-113">The default underlying type of enumeration elements is [int](../../../csharp/language-reference/keywords/int.md). To declare an enum of another integral type, such as [byte](../../../csharp/language-reference/keywords/byte.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>  
  
```  
enum Days : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="525d4-114">列挙型で許容される型は、 `byte`、 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、 [short](../../../csharp/language-reference/keywords/short.md)、 [ushort](../../../csharp/language-reference/keywords/ushort.md)、 [int](../../../csharp/language-reference/keywords/int.md)、 [uint](../../../csharp/language-reference/keywords/uint.md)、 [long](../../../csharp/language-reference/keywords/long.md)、または [ulong](../../../csharp/language-reference/keywords/ulong.md)です。</span><span class="sxs-lookup"><span data-stu-id="525d4-114">The approved types for an enum are `byte`, [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="525d4-115">型 `Days` の変数には、基になる型の範囲内の任意の値を割り当てることができます。値は名前付き定数に限定されません。</span><span class="sxs-lookup"><span data-stu-id="525d4-115">A variable of type `Days` can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>  
  
 <span data-ttu-id="525d4-116">`enum E` の既定値は、式 `(E)0`によって算出された値です。</span><span class="sxs-lookup"><span data-stu-id="525d4-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="525d4-117">列挙子の名前に空白を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="525d4-117">An enumerator cannot contain white space in its name.</span></span>  
  
 <span data-ttu-id="525d4-118">基になる型は、列挙子ごとに割り当てるストレージの大きさを指定します。</span><span class="sxs-lookup"><span data-stu-id="525d4-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="525d4-119">ただし、 `enum` 型を整数型に変換するには、明示的なキャストが必要です。</span><span class="sxs-lookup"><span data-stu-id="525d4-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="525d4-120">たとえば、次のステートメントではキャストを使用して `Sun` から [に変換することで、列挙子](../../../csharp/language-reference/keywords/int.md) を `enum` int `int`型の変数に代入します。</span><span class="sxs-lookup"><span data-stu-id="525d4-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../../../csharp/language-reference/keywords/int.md) by using a cast to convert from `enum` to `int`.</span></span>  
  
```  
int x = (int)Days.Sun;  
```  
  
 <span data-ttu-id="525d4-121">列挙型に <xref:System.FlagsAttribute?displayProperty=nameWithType> を適用し、その要素をビットごとの `OR` 演算と組み合わせると、一部のツールを使用したときに、 `enum` の動作に属性が反映されます。</span><span class="sxs-lookup"><span data-stu-id="525d4-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="525d4-122">このような変更は、 <xref:System.Console> クラス メソッドや式エバリュエーターなどのツールを使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="525d4-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="525d4-123">(3 番目の使用例をご参照ください。)</span><span class="sxs-lookup"><span data-stu-id="525d4-123">(See the third example.)</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="525d4-124">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="525d4-124">Robust Programming</span></span>  
 <span data-ttu-id="525d4-125">定数の場合と同様に、列挙型の個々の値へのすべての参照はコンパイル時に数値リテラルに変換されます。</span><span class="sxs-lookup"><span data-stu-id="525d4-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="525d4-126">これにより、「[定数](../../../csharp/programming-guide/classes-and-structs/constants.md)」で説明しているように、バージョン管理の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="525d4-126">This can create potential versioning issues as described in [Constants](../../../csharp/programming-guide/classes-and-structs/constants.md).</span></span>  
  
 <span data-ttu-id="525d4-127">新しいバージョンの列挙型に追加の値を割り当てるか、新しいバージョンの列挙型メンバーの値を変更すると、依存関係のあるソース コードに問題が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="525d4-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="525d4-128">列挙値は、 [switch](../../../csharp/language-reference/keywords/switch.md) ステートメントでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="525d4-128">Enum values often are used in [switch](../../../csharp/language-reference/keywords/switch.md) statements.</span></span> <span data-ttu-id="525d4-129">`enum` 型に追加要素が追加されている場合、switch ステートメントの default セクションが予期せずに選択される場合があります。</span><span class="sxs-lookup"><span data-stu-id="525d4-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>  
  
 <span data-ttu-id="525d4-130">作成したコードが他の開発者によって使用される場合は、新しい要素を `enum` 型に追加したときのコードの反応を規定するガイドラインを用意しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="525d4-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="525d4-131">例</span><span class="sxs-lookup"><span data-stu-id="525d4-131">Example</span></span>  
 <span data-ttu-id="525d4-132">次の例では、列挙型 `Days`を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="525d4-132">In the following example, an enumeration, `Days`, is declared.</span></span> <span data-ttu-id="525d4-133">2 つの列挙子は明示的に整数に変換され、整数変数に代入されます。</span><span class="sxs-lookup"><span data-stu-id="525d4-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="525d4-134">例</span><span class="sxs-lookup"><span data-stu-id="525d4-134">Example</span></span>  
 <span data-ttu-id="525d4-135">次の例では、基本型オプションを使用して `enum` 型をメンバーに持つ `long`を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="525d4-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="525d4-136">列挙型の基になる型が `long`であっても、列挙型メンバーはキャストを使用して `long` 型に明示的に変換する必要があることにご注意ください。</span><span class="sxs-lookup"><span data-stu-id="525d4-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="525d4-137">例</span><span class="sxs-lookup"><span data-stu-id="525d4-137">Example</span></span>  
 <span data-ttu-id="525d4-138">次のコード例では、 <xref:System.FlagsAttribute?displayProperty=nameWithType> 宣言での `enum` 属性の使用とその効果を示します。</span><span class="sxs-lookup"><span data-stu-id="525d4-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]  
  
## <a name="comments"></a><span data-ttu-id="525d4-139">コメント</span><span class="sxs-lookup"><span data-stu-id="525d4-139">Comments</span></span>  
 <span data-ttu-id="525d4-140">この例では、 `Flags`を削除すると次の値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="525d4-140">If you remove `Flags`, the example displays the following values:</span></span>  
  
 `5`  
  
 `5`  
  
## <a name="c-language-specification"></a><span data-ttu-id="525d4-141">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="525d4-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="525d4-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="525d4-142">See Also</span></span>  
 [<span data-ttu-id="525d4-143">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="525d4-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="525d4-144">列挙型</span><span class="sxs-lookup"><span data-stu-id="525d4-144">Enumeration Types</span></span>](../../../csharp/programming-guide/enumeration-types.md)  
 [<span data-ttu-id="525d4-145">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="525d4-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="525d4-146">整数型の一覧表</span><span class="sxs-lookup"><span data-stu-id="525d4-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="525d4-147">組み込み型の一覧表</span><span class="sxs-lookup"><span data-stu-id="525d4-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="525d4-148">暗黙的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="525d4-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="525d4-149">明示的な数値変換の一覧表</span><span class="sxs-lookup"><span data-stu-id="525d4-149">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
