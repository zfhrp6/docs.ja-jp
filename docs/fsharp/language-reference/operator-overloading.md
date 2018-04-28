---
title: 演算子のオーバーロード (F#)
description: クラスまたはレコードの種類と、グローバル レベルで f# での算術演算子をオーバー ロードする方法を説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 45fcb4d2acce29caa6b38d08ae4f166884f20147
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="operator-overloading"></a><span data-ttu-id="fb7da-103">演算子のオーバーロード</span><span class="sxs-lookup"><span data-stu-id="fb7da-103">Operator Overloading</span></span>

<span data-ttu-id="fb7da-104">このトピックでは、クラス型またはレコード型の算術演算子をオーバーロードする方法と、グローバル レベルで算術演算子をオーバーロードする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb7da-104">This topic describes how to overload arithmetic operators in a class or record type, and at the global level.</span></span>


## <a name="syntax"></a><span data-ttu-id="fb7da-105">構文</span><span class="sxs-lookup"><span data-stu-id="fb7da-105">Syntax</span></span>

```fsharp
// Overloading an operator as a class or record member.
static member (operator-symbols) (parameter-list) =
    method-body
// Overloading an operator at the global level
let [inline] (operator-symbols) parameter-list = function-body
```

## <a name="remarks"></a><span data-ttu-id="fb7da-106">コメント</span><span class="sxs-lookup"><span data-stu-id="fb7da-106">Remarks</span></span>
<span data-ttu-id="fb7da-107">前の構文では、*演算子記号*の 1 つ`+`、 `-`、 `*`、 `/`、`=`のようにします。</span><span class="sxs-lookup"><span data-stu-id="fb7da-107">In the previous syntax, the *operator-symbol* is one of `+`, `-`, `*`, `/`, `=`, and so on.</span></span> <span data-ttu-id="fb7da-108">*パラメーター リスト*その演算子の通常の構文で記述する順序でオペランドを指定します。</span><span class="sxs-lookup"><span data-stu-id="fb7da-108">The *parameter-list* specifies the operands in the order they appear in the usual syntax for that operator.</span></span> <span data-ttu-id="fb7da-109">*メソッド本体*結果の値を構築します。</span><span class="sxs-lookup"><span data-stu-id="fb7da-109">The *method-body* constructs the resulting value.</span></span>

<span data-ttu-id="fb7da-110">演算子のオーバーロードには、static を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb7da-110">Operator overloads for operators must be static.</span></span> <span data-ttu-id="fb7da-111">演算子がなどの単項演算子のオーバー ロード`+`と`-`、チルダを使用する必要があります (`~`) で、*演算子記号*いることを示す演算子は、単項演算子および二項演算子ではないのように、次の宣言。</span><span class="sxs-lookup"><span data-stu-id="fb7da-111">Operator overloads for unary operators, such as `+` and `-`, must use a tilde (`~`) in the *operator-symbol* to indicate that the operator is a unary operator and not a binary operator, as shown in the following declaration.</span></span>

```fsharp
static member (~-) (v : Vector)
```

<span data-ttu-id="fb7da-112">次のコードは、演算子を 2 つだけ含むベクター クラスを示しています。その 1 つは単項マイナス演算子で、もう 1 つはスカラーによる乗算演算子です。</span><span class="sxs-lookup"><span data-stu-id="fb7da-112">The following code illustrates a vector class that has just two operators, one for unary minus and one for multiplication by a scalar.</span></span> <span data-ttu-id="fb7da-113">この例では、ベクターとスカラーの記述順序とは無関係に演算子が機能する必要があるため、必要となるスカラー乗算のオーバーロードは 2 つです。</span><span class="sxs-lookup"><span data-stu-id="fb7da-113">In the example, two overloads for scalar multiplication are needed because the operator must work regardless of the order in which the vector and scalar appear.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4001.fs)]

## <a name="creating-new-operators"></a><span data-ttu-id="fb7da-114">新しい演算子の作成</span><span class="sxs-lookup"><span data-stu-id="fb7da-114">Creating New Operators</span></span>
<span data-ttu-id="fb7da-115">標準演算子はすべてオーバーロードすることができますが、特定の文字を並べて新しい演算子を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="fb7da-115">You can overload all the standard operators, but you can also create new operators out of sequences of certain characters.</span></span> <span data-ttu-id="fb7da-116">使用できる演算子文字は`!`、 `%`、 `&`、 `*`、 `+`、 `-`、 `.`、 `/`、 `<`、 `=`、 `>`、 `?`、 `@`、 `^`、 `|`、および`~`です。</span><span class="sxs-lookup"><span data-stu-id="fb7da-116">Allowed operator characters are `!`, `%`, `&`, `*`, `+`, `-`, `.`, `/`, `<`, `=`, `>`, `?`, `@`, `^`, `|`, and `~`.</span></span> <span data-ttu-id="fb7da-117">`~` には、演算子を単項演算子にするという特別な意味があるため、演算子の文字シーケンスに含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="fb7da-117">The `~` character has the special meaning of making an operator unary, and is not part of the operator character sequence.</span></span> <span data-ttu-id="fb7da-118">すべての演算子には、単項を作成できます。</span><span class="sxs-lookup"><span data-stu-id="fb7da-118">Not all operators can be made unary.</span></span>

<span data-ttu-id="fb7da-119">作成した演算子は、使用した厳密な文字シーケンスに従って、特定の優先順位と結合規則を持つようになります。</span><span class="sxs-lookup"><span data-stu-id="fb7da-119">Depending on the exact character sequence you use, your operator will have a certain precedence and associativity.</span></span> <span data-ttu-id="fb7da-120">結合規則を使用する方向は、左から右にすることも、右から左にすることもできます。シーケンスの中で同じレベルの優先順位を持つ演算子を、かっこを使用せずに記述する場合は、必ず結合規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="fb7da-120">Associativity can be either left to right or right to left and is used whenever operators of the same level of precedence appear in sequence without parentheses.</span></span>

<span data-ttu-id="fb7da-121">演算子文字の `.` は、優先順位に影響しません。そのため、通常の乗算演算子と同じ優先順位と結合規則を持つ独自の形式の乗算演算子を定義する場合などに、`.*` のような演算子を作成できます。</span><span class="sxs-lookup"><span data-stu-id="fb7da-121">The operator character `.` does not affect precedence, so that, for example, if you want to define your own version of multiplication that has the same precedence and associativity as ordinary multiplication, you could create operators such as `.*`.</span></span>

<span data-ttu-id="fb7da-122">演算子のみ`?`と`?<-`で始めることは`?`します。</span><span class="sxs-lookup"><span data-stu-id="fb7da-122">Only the operators `?` and `?<-` may start with `?`.</span></span>

<span data-ttu-id="fb7da-123">F# でのすべての演算子の優先順位を示すテーブルは含まれて[シンボルと演算子のリファレンス](symbol-and-operator-reference/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="fb7da-123">A table that shows the precedence of all operators in F# can be found in [Symbol and Operator Reference](symbol-and-operator-reference/index.md).</span></span>


## <a name="overloaded-operator-names"></a><span data-ttu-id="fb7da-124">オーバーロードされた演算子の名前</span><span class="sxs-lookup"><span data-stu-id="fb7da-124">Overloaded Operator Names</span></span>
<span data-ttu-id="fb7da-125">F# コンパイラが演算子の式をコンパイルするときに、その演算子のメソッドが生成されます。このメソッドには、コンパイラにより生成された名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="fb7da-125">When the F# compiler compiles an operator expression, it generates a method that has a compiler-generated name for that operator.</span></span> <span data-ttu-id="fb7da-126">これは、このメソッドの Microsoft Intermediate Language (MSIL) で使用される名前です。また、リフレクションと IntelliSense でも使用されます。</span><span class="sxs-lookup"><span data-stu-id="fb7da-126">This is the name that appears in the Microsoft intermediate language (MSIL) for the method, and also in reflection and IntelliSense.</span></span> <span data-ttu-id="fb7da-127">通常、この名前を F# コードで使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fb7da-127">You do not normally need to use these names in F# code.</span></span>

<span data-ttu-id="fb7da-128">次の表に、標準演算子と生成される名前を示します。</span><span class="sxs-lookup"><span data-stu-id="fb7da-128">The following table shows the standard operators and their corresponding generated names.</span></span>



|<span data-ttu-id="fb7da-129">演算子</span><span class="sxs-lookup"><span data-stu-id="fb7da-129">Operator</span></span>|<span data-ttu-id="fb7da-130">生成された名前</span><span class="sxs-lookup"><span data-stu-id="fb7da-130">Generated name</span></span>|
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
<span data-ttu-id="fb7da-131">ここに記載されていないその他の演算子文字の組み合わせも演算子として使用できます。その場合の名前は、次の表の各文字の名前を連結して生成されます。</span><span class="sxs-lookup"><span data-stu-id="fb7da-131">Other combinations of operator characters that are not listed here can be used as operators and have names that are made up by concatenating names for the individual characters from the following table.</span></span> <span data-ttu-id="fb7da-132">たとえば、+!</span><span class="sxs-lookup"><span data-stu-id="fb7da-132">For example, +!</span></span> <span data-ttu-id="fb7da-133">なります`op_PlusBang`です。</span><span class="sxs-lookup"><span data-stu-id="fb7da-133">becomes `op_PlusBang`.</span></span>



|<span data-ttu-id="fb7da-134">演算子文字</span><span class="sxs-lookup"><span data-stu-id="fb7da-134">Operator character</span></span>|<span data-ttu-id="fb7da-135">名前</span><span class="sxs-lookup"><span data-stu-id="fb7da-135">Name</span></span>|
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

## <a name="prefix-and-infix-operators"></a><span data-ttu-id="fb7da-136">前置演算子と挿入演算子</span><span class="sxs-lookup"><span data-stu-id="fb7da-136">Prefix and Infix Operators</span></span>
<span data-ttu-id="fb7da-137">*プレフィックス*オペランドまたは関数と同様に、オペランドの前に配置する演算子は想定されています。</span><span class="sxs-lookup"><span data-stu-id="fb7da-137">*Prefix* operators are expected to be placed in front of an operand or operands, much like a function.</span></span> <span data-ttu-id="fb7da-138">*挿入辞*演算子の 2 つのオペランドの間には想定されています。</span><span class="sxs-lookup"><span data-stu-id="fb7da-138">*Infix* operators are expected to be placed between the two operands.</span></span>

<span data-ttu-id="fb7da-139">前置演算子として使用できるのは特定の演算子だけです。</span><span class="sxs-lookup"><span data-stu-id="fb7da-139">Only certain operators can be used as prefix operators.</span></span> <span data-ttu-id="fb7da-140">演算子は、常に前置演算子であるもの、挿入演算子にも前置演算子にもなるもの、および常に挿入演算子であるものに分けられます。</span><span class="sxs-lookup"><span data-stu-id="fb7da-140">Some operators are always prefix operators, others can be infix or prefix, and the rest are always infix operators.</span></span> <span data-ttu-id="fb7da-141">`!` で始まる演算子 (`!=` を除く) と `~` 演算子、または `~` の繰り返しシーケンスは、常に前置演算子です。</span><span class="sxs-lookup"><span data-stu-id="fb7da-141">Operators that begin with `!`, except `!=`, and the operator `~`, or repeated sequences of`~`, are always prefix operators.</span></span> <span data-ttu-id="fb7da-142">演算子 `+`、`-`、`+.`、`-.`、`&`、`&&`、`%`、および `%%` は、前置演算子にも挿入演算子にもなります。</span><span class="sxs-lookup"><span data-stu-id="fb7da-142">The operators `+`, `-`, `+.`, `-.`, `&`, `&&`, `%`, and `%%` can be prefix operators or infix operators.</span></span> <span data-ttu-id="fb7da-143">これらの演算子の前置バージョンを挿入バージョンと区別するには、定義時に前置演算子の先頭に `~` を追加します。</span><span class="sxs-lookup"><span data-stu-id="fb7da-143">You distinguish the prefix version of these operators from the infix version by adding a `~` at the beginning of a prefix operator when it is defined.</span></span> <span data-ttu-id="fb7da-144">`~` は、演算子の使用時には使用されず、定義時にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="fb7da-144">The `~` is not used when you use the operator, only when it is defined.</span></span>

## <a name="example"></a><span data-ttu-id="fb7da-145">例</span><span class="sxs-lookup"><span data-stu-id="fb7da-145">Example</span></span>

<span data-ttu-id="fb7da-146">次のコードは、分数型を実装する際の演算子のオーバーロードの使用例です。</span><span class="sxs-lookup"><span data-stu-id="fb7da-146">The following code illustrates the use of operator overloading to implement a fraction type.</span></span> <span data-ttu-id="fb7da-147">分数は、分子と分母で表されます。</span><span class="sxs-lookup"><span data-stu-id="fb7da-147">A fraction is represented by a numerator and a denominator.</span></span> <span data-ttu-id="fb7da-148">`hcf` 関数を使用して最大公約数を求め、その公約数を使用して約分します。</span><span class="sxs-lookup"><span data-stu-id="fb7da-148">The function `hcf` is used to determine the highest common factor, which is used to reduce fractions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4002.fs)]

<span data-ttu-id="fb7da-149">**出力:**</span><span class="sxs-lookup"><span data-stu-id="fb7da-149">**Output:**</span></span>

```
3/4 + 1/2 = 5/4
3/4 - 1/2 = 1/4
3/4 * 1/2 = 3/8
3/4 / 1/2 = 3/2
3/4 + 1 = 7/4
```

## <a name="operators-at-the-global-level"></a><span data-ttu-id="fb7da-150">グローバル レベルの演算子</span><span class="sxs-lookup"><span data-stu-id="fb7da-150">Operators at the Global Level</span></span>
<span data-ttu-id="fb7da-151">演算子は、グローバル レベルで定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="fb7da-151">You can also define operators at the global level.</span></span> <span data-ttu-id="fb7da-152">次のコードは、演算子を定義`+?`です。</span><span class="sxs-lookup"><span data-stu-id="fb7da-152">The following code defines an operator `+?`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4003.fs)]

<span data-ttu-id="fb7da-153">上記のコードの出力は `12` になります。</span><span class="sxs-lookup"><span data-stu-id="fb7da-153">The output of the above code is `12`.</span></span>

<span data-ttu-id="fb7da-154">F# のスコープ規則では、新しく定義された演算子が組み込み演算子よりも優先されるため、このようにして、通常の算術演算子を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="fb7da-154">You can redefine the regular arithmetic operators in this manner because the scoping rules for F# dictate that newly defined operators take precedence over the built-in operators.</span></span>

<span data-ttu-id="fb7da-155">キーワード `inline` は、グローバル演算子と共に使用されることがよくあります。グローバル演算子は、通常、呼び出し元のコードに適宜組み込まれる小規模関数にします。</span><span class="sxs-lookup"><span data-stu-id="fb7da-155">The keyword `inline` is often used with global operators, which are often small functions that are best integrated into the calling code.</span></span> <span data-ttu-id="fb7da-156">演算子関数をインライン化することにより、その関数を静的に解決された型パラメーターと共に使用して、静的に解決されたジェネリック コードを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="fb7da-156">Making operator functions inline also enables them to work with statically resolved type parameters to produce statically resolved generic code.</span></span> <span data-ttu-id="fb7da-157">詳細については、次を参照してください。[インライン関数](functions/inline-functions.md)と[型パラメーターを静的に解決](generics/statically-resolved-type-parameters.md)です。</span><span class="sxs-lookup"><span data-stu-id="fb7da-157">For more information, see [Inline Functions](functions/inline-functions.md) and [Statically Resolved Type Parameters](generics/statically-resolved-type-parameters.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fb7da-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="fb7da-158">See Also</span></span>
[<span data-ttu-id="fb7da-159">メンバー</span><span class="sxs-lookup"><span data-stu-id="fb7da-159">Members</span></span>](members/index.md)
