---
title: "名前空間 (F#)"
description: "F# で名前空間を使用できるプログラム要素のグループに名前をアタッチするようにすることによって関連する機能の領域にコードを整理する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea42156f-e1b9-4535-9383-b45f46f3f7ca
ms.openlocfilehash: f3f73c4fe2197f1f3f2babbe6691ef6662d8f581
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/27/2018
---
# <a name="namespaces"></a><span data-ttu-id="dae10-104">名前空間</span><span class="sxs-lookup"><span data-stu-id="dae10-104">Namespaces</span></span>

<span data-ttu-id="dae10-105">名前空間を使用すると、プログラム要素のグループに名前を割り当てて、関連する機能の区分にコードを編成することができます。</span><span class="sxs-lookup"><span data-stu-id="dae10-105">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of program elements.</span></span>


## <a name="syntax"></a><span data-ttu-id="dae10-106">構文</span><span class="sxs-lookup"><span data-stu-id="dae10-106">Syntax</span></span>

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="dae10-107">コメント</span><span class="sxs-lookup"><span data-stu-id="dae10-107">Remarks</span></span>
<span data-ttu-id="dae10-108">名前空間にコードを配置する場合は、ファイル内の最初の宣言は名前空間を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dae10-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="dae10-109">ファイル全体の内容は、名前空間の一部になります。</span><span class="sxs-lookup"><span data-stu-id="dae10-109">The contents of the entire file then become part of the namespace.</span></span>

<span data-ttu-id="dae10-110">名前空間には、値と関数直接を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="dae10-110">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="dae10-111">代わりに、モジュール内では、値と関数を含める必要があるし、モジュールの名前空間に含まれます。</span><span class="sxs-lookup"><span data-stu-id="dae10-111">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="dae10-112">名前空間には、型、モジュールを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="dae10-112">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="dae10-113">名前空間を宣言できます明示的に名前空間キーワードを使用して、または暗黙的にモジュールを宣言するとき。</span><span class="sxs-lookup"><span data-stu-id="dae10-113">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="dae10-114">名前空間を明示的に宣言するには、名前空間キーワードの後に名前空間の名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="dae10-114">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="dae10-115">次の例では、型とその名前空間に含まれるモジュールのウィジェットの名前空間を宣言するコード ファイルを示します。</span><span class="sxs-lookup"><span data-stu-id="dae10-115">The following example shows a code file that declares a namespace Widgets with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="dae10-116">ファイルの内容全体が 1 つのモジュールである場合は、宣言することも名前空間に暗黙的を使用して、`module`キーワードとモジュールの完全修飾名で新しい名前空間名を指定します。</span><span class="sxs-lookup"><span data-stu-id="dae10-116">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="dae10-117">次の例は、名前空間を宣言するコード ファイル`Widgets`とモジュール`WidgetsModule`関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dae10-117">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="dae10-118">次のコードは同等上記のコードが、モジュールがローカル モジュール宣言します。</span><span class="sxs-lookup"><span data-stu-id="dae10-118">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="dae10-119">その場合は、名前空間は、独自の行に表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dae10-119">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="dae10-120">1 つ以上のモジュールが 1 つまたは複数の名前空間の同じファイルに必要な場合は、ローカル モジュール宣言を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dae10-120">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="dae10-121">ローカル モジュール宣言を使用する場合は、モジュールの宣言で修飾名前空間を使用できません。</span><span class="sxs-lookup"><span data-stu-id="dae10-121">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="dae10-122">次のコードでは、名前空間の宣言と 2 つのローカル モジュール宣言を持つファイルを示します。</span><span class="sxs-lookup"><span data-stu-id="dae10-122">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="dae10-123">名前空間で直接、モジュールが含まれるこのケースでは、ファイルと同じ名前を持つ暗黙的に作成されたモジュールはありません。</span><span class="sxs-lookup"><span data-stu-id="dae10-123">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="dae10-124">他のコードで、ファイルなど、`do`モジュール メンバーを修飾する必要があります、内部のモジュールではなく、名前空間には、バインディング、`widgetFunction`モジュール名を使用しています。</span><span class="sxs-lookup"><span data-stu-id="dae10-124">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="dae10-125">この例の出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="dae10-125">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="dae10-126">詳細については、次を参照してください。[モジュール](modules.md)です。</span><span class="sxs-lookup"><span data-stu-id="dae10-126">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="dae10-127">入れ子になった名前空間</span><span class="sxs-lookup"><span data-stu-id="dae10-127">Nested Namespaces</span></span>
<span data-ttu-id="dae10-128">入れ子になった名前空間を作成するときに、完全修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dae10-128">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="dae10-129">それ以外の場合、新しい最上位レベルの名前空間を作成します。</span><span class="sxs-lookup"><span data-stu-id="dae10-129">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="dae10-130">インデントは、名前空間の宣言で無視されます。</span><span class="sxs-lookup"><span data-stu-id="dae10-130">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="dae10-131">次の例では、入れ子になった名前空間を宣言する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dae10-131">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="dae10-132">ファイルとアセンブリの名前空間</span><span class="sxs-lookup"><span data-stu-id="dae10-132">Namespaces in Files and Assemblies</span></span>
<span data-ttu-id="dae10-133">名前空間は、1 つのプロジェクトまたはコンパイルで複数のファイルにまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="dae10-133">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="dae10-134">用語*名前空間のフラグメント*1 つのファイルに含まれている名前空間の部分について説明します。</span><span class="sxs-lookup"><span data-stu-id="dae10-134">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="dae10-135">名前空間には、複数のアセンブリもまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="dae10-135">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="dae10-136">たとえば、`System`名前空間には、多くのアセンブリに拡張されていて、入れ子になった名前空間多くにはが含まれていますが、全体の .NET Framework が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dae10-136">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>


## <a name="global-namespace"></a><span data-ttu-id="dae10-137">グローバル Namespace</span><span class="sxs-lookup"><span data-stu-id="dae10-137">Global Namespace</span></span>
<span data-ttu-id="dae10-138">定義済みの名前空間を使用する`global`に最上位の .NET 名前空間名を格納します。</span><span class="sxs-lookup"><span data-stu-id="dae10-138">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="dae10-139">使用することできますもグローバル他の名前空間と名前が競合を解決するのには、たとえば、最上位の .NET 名前空間を参照します。</span><span class="sxs-lookup"><span data-stu-id="dae10-139">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="dae10-140">再帰的な名前空間</span><span class="sxs-lookup"><span data-stu-id="dae10-140">Recursive namespaces</span></span>

<span data-ttu-id="dae10-141">F# 4.1 には、再帰的に相互に含まれているすべてのコードでは、名前空間の概念が導入されています。</span><span class="sxs-lookup"><span data-stu-id="dae10-141">F# 4.1 introduces the notion of namespaces which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="dae10-142">使用してこれを行う`namespace rec`です。</span><span class="sxs-lookup"><span data-stu-id="dae10-142">This is done via `namespace rec`.</span></span>  <span data-ttu-id="dae10-143">使用`namespace rec`タイプやモジュール間で相互に参照のコードを記述することはできませんに痛みがあるいくつかを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="dae10-143">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="dae10-144">この例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="dae10-144">The following is an example of this:</span></span>

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set
    
    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b : Banana) =
        let flip banana =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides banana =
            for side in banana.Sides do
                if side = Unpeeled then
                    side <- Peeled

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

<span data-ttu-id="dae10-145">なお例外`DontSqueezeTheBananaException`とクラス`Banana`両方には、互いを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dae10-145">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="dae10-146">さらに、モジュール`BananaHelpers`とクラス`Banana`も互いを参照してください。</span><span class="sxs-lookup"><span data-stu-id="dae10-146">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="dae10-147">これを削除した場合、f# で表現できないが、`rec`からキーワード、`MutualReferences`名前空間。</span><span class="sxs-lookup"><span data-stu-id="dae10-147">This would not be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="dae10-148">この機能は使用できる最上位[モジュール](modules.md)f# 4.1 またはそれ以降。</span><span class="sxs-lookup"><span data-stu-id="dae10-148">This feature is also available for top-level [Modules](modules.md) in F# 4.1 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="dae10-149">参照</span><span class="sxs-lookup"><span data-stu-id="dae10-149">See Also</span></span>
[<span data-ttu-id="dae10-150">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="dae10-150">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="dae10-151">モジュール</span><span class="sxs-lookup"><span data-stu-id="dae10-151">Modules</span></span>](modules.md)

[<span data-ttu-id="dae10-152">F# RFC FS-1009 - ファイル内でより大きなスコープを相互に参照型とモジュールを許可します。</span><span class="sxs-lookup"><span data-stu-id="dae10-152">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
