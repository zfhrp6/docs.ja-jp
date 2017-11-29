---
title: "演算子のオーバーロード (F#)"
description: "クラスまたはレコードの種類と、グローバル レベルで f# での算術演算子をオーバー ロードする方法を説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 019277ed-f649-4fa5-ad43-097865f449d9
ms.openlocfilehash: 76ddab5339e11d71bb326b60d727017eb838ccf4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="operator-overloading"></a><span data-ttu-id="e8895-104">演算子のオーバーロード</span><span class="sxs-lookup"><span data-stu-id="e8895-104">Operator Overloading</span></span>

<span data-ttu-id="e8895-105">このトピックでは、クラス型またはレコード型の算術演算子をオーバーロードする方法と、グローバル レベルで算術演算子をオーバーロードする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e8895-105">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>


## <a name="syntax"></a><span data-ttu-id="e8895-106">構文</span><span class="sxs-lookup"><span data-stu-id="e8895-106">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="e8895-107">コメント</span><span class="sxs-lookup"><span data-stu-id="e8895-107">Remarks</span></span>
<span data-ttu-id="e8895-108">前の構文では、*演算子記号*の 1 つ`+`、 `-`、 `*`、 `/`、`=`のようにします。</span><span class="sxs-lookup"><span data-stu-id="e8895-108">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="e8895-109">*パラメーター リスト*その演算子の通常の構文で記述する順序でオペランドを指定します。</span><span class="sxs-lookup"><span data-stu-id="e8895-109">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="e8895-110">*メソッド本体*結果の値を構築します。</span><span class="sxs-lookup"><span data-stu-id="e8895-110">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="e8895-111">演算子のオーバーロードには、static を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e8895-111">Operator overloads for operators must be static.</span></span> <span data-ttu-id="e8895-112">演算子がなどの単項演算子のオーバー ロード`+`と`-`、チルダを使用する必要があります (`~`) で、*演算子記号*いることを示す演算子は、単項演算子および二項演算子ではないのように、次の宣言。</span><span class="sxs-lookup"><span data-stu-id="e8895-112">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="e8895-113">次のコードは、演算子を 2 つだけ含むベクター クラスを示しています。その 1 つは単項マイナス演算子で、もう 1 つはスカラーによる乗算演算子です。</span><span class="sxs-lookup"><span data-stu-id="e8895-113">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="e8895-114">この例では、ベクターとスカラーの記述順序とは無関係に演算子が機能する必要があるため、必要となるスカラー乗算のオーバーロードは 2 つです。</span><span class="sxs-lookup"><span data-stu-id="e8895-114">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="e8895-115">新しい演算子の作成</span><span class="sxs-lookup"><span data-stu-id="e8895-115">Creating New Operators</span></span>
<span data-ttu-id="e8895-116">標準演算子はすべてオーバーロードすることができますが、特定の文字を並べて新しい演算子を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="e8895-116">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="e8895-117">使用できる演算子文字は`!`、 `%`、 `&`、 `*`、 `+`、 `-`、 `.`、 `/`、 `<`、 `=`、 `>`、 `?`、 `@`、 `^`、 `|`、および`~`です。</span><span class="sxs-lookup"><span data-stu-id="e8895-117">Allowed operator characters are `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="e8895-118">`~` には、演算子を単項演算子にするという特別な意味があるため、演算子の文字シーケンスに含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="e8895-118">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="e8895-119">すべての演算子には、単項を作成できます。</span><span class="sxs-lookup"><span data-stu-id="e8895-119">Not all operators can be made unary.</span></span>

<span data-ttu-id="e8895-120">作成した演算子は、使用した厳密な文字シーケンスに従って、特定の優先順位と結合規則を持つようになります。</span><span class="sxs-lookup"><span data-stu-id="e8895-120">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="e8895-121">結合規則を使用する方向は、左から右にすることも、右から左にすることもできます。シーケンスの中で同じレベルの優先順位を持つ演算子を、かっこを使用せずに記述する場合は、必ず結合規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="e8895-121">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="e8895-122">演算子文字の `.` は、優先順位に影響しません。そのため、通常の乗算演算子と同じ優先順位と結合規則を持つ独自の形式の乗算演算子を定義する場合などに、`.*` のような演算子を作成できます。</span><span class="sxs-lookup"><span data-stu-id="e8895-122">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="e8895-123">演算子のみ`?`と`?<-`で始めることは`?`します。</span><span class="sxs-lookup"><span data-stu-id="e8895-123">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="e8895-124">F# でのすべての演算子の優先順位を示すテーブルは含まれて[シンボルと演算子のリファレンス](symbol-and-operator-reference/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="e8895-124">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](symbol-and-operator-reference/index.md).</span></span>


## <a name="overloaded-operator-names"></a><span data-ttu-id="e8895-125">オーバーロードされた演算子の名前</span><span class="sxs-lookup"><span data-stu-id="e8895-125">Overloaded Operator Names</span></span>
<span data-ttu-id="e8895-126">F# コンパイラが演算子の式をコンパイルするときに、その演算子のメソッドが生成されます。このメソッドには、コンパイラにより生成された名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="e8895-126">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="e8895-127">これは、このメソッドの Microsoft Intermediate Language (MSIL) で使用される名前です。また、リフレクションと IntelliSense でも使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8895-127">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="e8895-128">通常、この名前を F# コードで使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e8895-128">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="e8895-129">次の表に、標準演算子と生成される名前を示します。</span><span class="sxs-lookup"><span data-stu-id="e8895-129">The following table shows the standard operators and their corresponding generated names.</span></span>



|<span data-ttu-id="e8895-130">演算子</span><span class="sxs-lookup"><span data-stu-id="e8895-130">Operator</span></span>|<span data-ttu-id="e8895-131">生成された名前</span><span class="sxs-lookup"><span data-stu-id="e8895-131">Generated name</span></span>|
|--------|--------------|
|`[]`|`op_Nil`|
|`::`|`op_Cons`|
|`+`|`op_Addition`|
|`-`|`op_Subtraction`|
|`*`|`op_Multiply`|
|`/`|`op_Division`|
|`@`|`op_Append`|
|`^`|`op_Concatenate`|
|`%`|`op_Modulus`|
|`&&&`|`op_BitwiseAnd`|
|<code>&#124;&#124;&#124;</code>|`op_BitwiseOr`|
|`^^^`|`op_ExclusiveOr`|
|`<<<`|`op_LeftShift`|
|`~~~`|`op_LogicalNot`|
|`>>>`|`op_RightShift`|
|`~+`|`op_UnaryPlus`|
|`~-`|`op_UnaryNegation`|
|`=`|`op_Equality`|
|`<=`|`op_LessThanOrEqual`|
|`>=`|`op_GreaterThanOrEqual`|
|`<`|`op_LessThan`|
|`>`|`op_GreaterThan`|
|`?`|`op_Dynamic`|
|`?<-`|`op_DynamicAssignment`|
|<code>&#124;></code>|`op_PipeRight`|
|<code><&#124;</code>|`op_PipeLeft`|
|`!`|`op_Dereference`|
|`>>`|`op_ComposeRight`|
|`<<`|`op_ComposeLeft`|
|`<@ @>`|`op_Quotation`|
|`<@@ @@>`|`op_QuotationUntyped`|
|`+=`|`op_AdditionAssignment`|
|`-=`|`op_SubtractionAssignment`|
|`*=`|`op_MultiplyAssignment`|
|`/=`|`op_DivisionAssignment`|
|`..`|`op_Range`|
|`.. ..`|`op_RangeStep`|
<span data-ttu-id="e8895-132">ここに記載されていないその他の演算子文字の組み合わせも演算子として使用できます。その場合の名前は、次の表の各文字の名前を連結して生成されます。</span><span class="sxs-lookup"><span data-stu-id="e8895-132">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="e8895-133">たとえば、+!</span><span class="sxs-lookup"><span data-stu-id="e8895-133">For example, +!</span></span> <span data-ttu-id="e8895-134">なります`op_PlusBang`です。</span><span class="sxs-lookup"><span data-stu-id="e8895-134">becomes `op_PlusBang`.</span></span>



|<span data-ttu-id="e8895-135">演算子文字</span><span class="sxs-lookup"><span data-stu-id="e8895-135">Operator character</span></span>|<span data-ttu-id="e8895-136">名前</span><span class="sxs-lookup"><span data-stu-id="e8895-136">Name</span></span>|
|------------------|----|
|`>`|`Greater`|
|`<`|`Less`|
|`+`|`Plus`|
|`-`|`Minus`|
|`*`|`Multiply`|
|`/`|`Divide`|
|`=`|`Equals`|
|`~`|`Twiddle`|
|`%`|`Percent`|
|`.`|`Dot`|
|`&`|`Amp`|
|<code>&#124;</code>|`Bar`|
|`@`|`At`|
|`^`|`Hat`|
|`!`|`Bang`|
|`?`|`Qmark`|
|`(`|`LParen`|
|`,`|`Comma`|
|`)`|`RParen`|
|`[`|`LBrack`|
|`]`|`RBrack`|

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="e8895-137">前置演算子と挿入演算子</span><span class="sxs-lookup"><span data-stu-id="e8895-137">Prefix and Infix Operators</span></span>
<span data-ttu-id="e8895-138">*プレフィックス*オペランドまたは関数と同様に、オペランドの前に配置する演算子は想定されています。</span><span class="sxs-lookup"><span data-stu-id="e8895-138">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="e8895-139">*挿入辞*演算子の 2 つのオペランドの間には想定されています。</span><span class="sxs-lookup"><span data-stu-id="e8895-139">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="e8895-140">前置演算子として使用できるのは特定の演算子だけです。</span><span class="sxs-lookup"><span data-stu-id="e8895-140">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="e8895-141">演算子は、常に前置演算子であるもの、挿入演算子にも前置演算子にもなるもの、および常に挿入演算子であるものに分けられます。</span><span class="sxs-lookup"><span data-stu-id="e8895-141">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="e8895-142">`!` で始まる演算子 (`!=` を除く) と `~` 演算子、または `~` の繰り返しシーケンスは、常に前置演算子です。</span><span class="sxs-lookup"><span data-stu-id="e8895-142">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="e8895-143">演算子 `+`、`-`、`+.`、`-.`、`&`、`&&`、`%`、および `%%` は、前置演算子にも挿入演算子にもなります。</span><span class="sxs-lookup"><span data-stu-id="e8895-143">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="e8895-144">これらの演算子の前置バージョンを挿入バージョンと区別するには、定義時に前置演算子の先頭に `~` を追加します。</span><span class="sxs-lookup"><span data-stu-id="e8895-144">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="e8895-145">`~` は、演算子の使用時には使用されず、定義時にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="e8895-145">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="e8895-146">例</span><span class="sxs-lookup"><span data-stu-id="e8895-146">Example</span></span>

<span data-ttu-id="e8895-147">次のコードは、分数型を実装する際の演算子のオーバーロードの使用例です。</span><span class="sxs-lookup"><span data-stu-id="e8895-147">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="e8895-148">分数は、分子と分母で表されます。</span><span class="sxs-lookup"><span data-stu-id="e8895-148">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="e8895-149">`hcf` 関数を使用して最大公約数を求め、その公約数を使用して約分します。</span><span class="sxs-lookup"><span data-stu-id="e8895-149">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="e8895-150">**出力:**</span><span class="sxs-lookup"><span data-stu-id="e8895-150">**Output:**</span></span>

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="e8895-151">グローバル レベルの演算子</span><span class="sxs-lookup"><span data-stu-id="e8895-151">Operators at the Global Level</span></span>
<span data-ttu-id="e8895-152">演算子は、グローバル レベルで定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="e8895-152">You can also define operators at the global level.</span></span> <span data-ttu-id="e8895-153">次のコードは、演算子を定義`+?`です。</span><span class="sxs-lookup"><span data-stu-id="e8895-153">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="e8895-154">上記のコードの出力は `12` になります。</span><span class="sxs-lookup"><span data-stu-id="e8895-154">The output of the above code is `12`.</span></span>

<span data-ttu-id="e8895-155">F# のスコープ規則では、新しく定義された演算子が組み込み演算子よりも優先されるため、このようにして、通常の算術演算子を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="e8895-155">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="e8895-156">キーワード `inline` は、グローバル演算子と共に使用されることがよくあります。グローバル演算子は、通常、呼び出し元のコードに適宜組み込まれる小規模関数にします。</span><span class="sxs-lookup"><span data-stu-id="e8895-156">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="e8895-157">演算子関数をインライン化することにより、その関数を静的に解決された型パラメーターと共に使用して、静的に解決されたジェネリック コードを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="e8895-157">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="e8895-158">詳細については、次を参照してください。[インライン関数](functions/inline-functions.md)と[型パラメーターを静的に解決](generics/statically-resolved-type-parameters.md)です。</span><span class="sxs-lookup"><span data-stu-id="e8895-158">For more information, see [Inline Functions](functions/inline-functions.md) and [Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8895-159">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8895-159">See Also</span></span>
[<span data-ttu-id="e8895-160">メンバー</span><span class="sxs-lookup"><span data-stu-id="e8895-160">Members</span></span>](members/index.md)
