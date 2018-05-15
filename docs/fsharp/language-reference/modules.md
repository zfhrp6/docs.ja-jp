---
title: モジュール (F#)
description: F# モジュールは、f# コード、値、型、および f# プログラムでは、関数の値などのグループ化方法について説明します。
ms.date: 04/24/2017
ms.openlocfilehash: ddb6a0762171f8acc94f0ba0cf29c4b6b3e4990e
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="modules"></a><span data-ttu-id="7b070-103">モジュール</span><span class="sxs-lookup"><span data-stu-id="7b070-103">Modules</span></span>

<span data-ttu-id="7b070-104">F# 言語のコンテキストで、*モジュール*f# コード、値、型、および f# プログラムでは、関数の値などのグループです。</span><span class="sxs-lookup"><span data-stu-id="7b070-104">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="7b070-105">モジュールのコードをグループ化すると、関連するコードをまとめることができ、プログラム内で名前の競合を回避するのに役立ちます</span><span class="sxs-lookup"><span data-stu-id="7b070-105">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="7b070-106">構文</span><span class="sxs-lookup"><span data-stu-id="7b070-106">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="7b070-107">コメント</span><span class="sxs-lookup"><span data-stu-id="7b070-107">Remarks</span></span>
<span data-ttu-id="7b070-108">F# モジュールは、f# コードの構成要素の種類、値、関数の値、および内のコードなどのグループ化`do`バインドします。</span><span class="sxs-lookup"><span data-stu-id="7b070-108">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="7b070-109">静的メンバーのみを持つ共通言語ランタイム (CLR) クラスとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="7b070-109">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="7b070-110">モジュールにファイル全体が含まれているかどうかによって、モジュール宣言の 2 種類があります: 最上位レベルのモジュールの宣言とローカル モジュール宣言します。</span><span class="sxs-lookup"><span data-stu-id="7b070-110">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="7b070-111">最上位レベルのモジュールの宣言には、モジュールには中にファイル全体が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7b070-111">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="7b070-112">最上位レベルのモジュールの宣言は、ファイル内の最初の宣言としてのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="7b070-112">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="7b070-113">省略可能な最上位モジュール宣言の構文で*修飾名前空間*モジュールを含む入れ子になった名前空間の名前のシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="7b070-113">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="7b070-114">修飾名前空間を事前に宣言する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7b070-114">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="7b070-115">最上位のモジュールの宣言をインデントする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7b070-115">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="7b070-116">ローカル モジュールのすべての宣言にインデントを設定する必要は。</span><span class="sxs-lookup"><span data-stu-id="7b070-116">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="7b070-117">ローカル モジュール宣言では、そのモジュール宣言の下にインデント宣言だけは、モジュールの一部です。</span><span class="sxs-lookup"><span data-stu-id="7b070-117">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="7b070-118">すべてのローカル モジュールを含むファイルの内容全体を拡張子を付けずにファイルと同じ名前を持つ暗黙的に作成された最上位モジュールの一部となるコード ファイルが最上位レベルのモジュールの宣言または名前空間の宣言で始まっていない場合最初の文字を大文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="7b070-118">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="7b070-119">たとえば、次のファイルがあるとします。</span><span class="sxs-lookup"><span data-stu-id="7b070-119">For example, consider the following file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="7b070-120">このファイルは、この方法で記述されている場合、コンパイルは。</span><span class="sxs-lookup"><span data-stu-id="7b070-120">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="7b070-121">をファイルに複数のモジュールがある場合は、モジュールごとにローカル モジュールの宣言を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b070-121">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="7b070-122">外側の名前空間が宣言されている場合、これらのモジュールは、外側の名前空間の一部になります。</span><span class="sxs-lookup"><span data-stu-id="7b070-122">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="7b070-123">外側の名前空間が宣言されていない場合、モジュールは、暗黙的に作成された最上位モジュールの一部になります。</span><span class="sxs-lookup"><span data-stu-id="7b070-123">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="7b070-124">次のコード例では、複数のモジュールを含むコード ファイルを示します。</span><span class="sxs-lookup"><span data-stu-id="7b070-124">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="7b070-125">コンパイラが暗黙的にという名前の最上位モジュールを作成`Multiplemodules`、および`MyModule1`と`MyModule2`その最上位レベルのモジュールで入れ子にします。</span><span class="sxs-lookup"><span data-stu-id="7b070-125">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="7b070-126">プロジェクトまたは 1 つのコンパイルで複数のファイルが存在する場合、またはライブラリを構築する場合は、名前空間の宣言またはファイルの上部にあるモジュールを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b070-126">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="7b070-127">のみ、f# コンパイラは暗黙的にモジュール名を決定し、プロジェクトまたはコンパイルのコマンド ラインでは、1 つのファイルが存在し、アプリケーションを作成するときにします。</span><span class="sxs-lookup"><span data-stu-id="7b070-127">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="7b070-128">*アクセシビリティ修飾子*、次のいずれかになります: `public`、 `private`、`internal`です。</span><span class="sxs-lookup"><span data-stu-id="7b070-128">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="7b070-129">詳細については、「[Access Control](access-control.md)」(アクセス制御) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b070-129">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="7b070-130">既定値はパブリックです。</span><span class="sxs-lookup"><span data-stu-id="7b070-130">The default is public.</span></span>


## <a name="referencing-code-in-modules"></a><span data-ttu-id="7b070-131">モジュール内のコードを参照します。</span><span class="sxs-lookup"><span data-stu-id="7b070-131">Referencing Code in Modules</span></span>
<span data-ttu-id="7b070-132">別のモジュールから関数、型、および値を参照するときにする必要がありますを使用する修飾名かモジュールを開きます。</span><span class="sxs-lookup"><span data-stu-id="7b070-132">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="7b070-133">修飾名を使用する場合は、名前空間、モジュール、および対象のプログラム要素の識別子を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b070-133">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="7b070-134">次のようには、ピリオド (.)、修飾パスの各部分を分離します。</span><span class="sxs-lookup"><span data-stu-id="7b070-134">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="7b070-135">モジュールまたは 1 つ以上のコードを簡略化する名前空間を開くことができます。</span><span class="sxs-lookup"><span data-stu-id="7b070-135">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="7b070-136">開く名前空間とモジュールの詳細については、次を参照してください。[インポート宣言:、`open`キーワード](import-declarations-the-open-keyword.md)です。</span><span class="sxs-lookup"><span data-stu-id="7b070-136">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="7b070-137">次のコード例では、ファイルの末尾までのすべてのコードを含む最上位レベルのモジュールを示します。</span><span class="sxs-lookup"><span data-stu-id="7b070-137">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="7b070-138">同じプロジェクト内の別のファイルからこのコードを使用するには、修飾名を使用するか、または開く、モジュール、関数を使用する前に、次の例に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="7b070-138">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="7b070-139">入れ子になったモジュール</span><span class="sxs-lookup"><span data-stu-id="7b070-139">Nested Modules</span></span>
<span data-ttu-id="7b070-140">モジュールは、入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="7b070-140">Modules can be nested.</span></span> <span data-ttu-id="7b070-141">内部のモジュールは、いない新しいモジュール、内側のモジュールがあることを示すために外部モジュール宣言枝葉と同じインデントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b070-141">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="7b070-142">たとえば、次の 2 つの例を比較します。</span><span class="sxs-lookup"><span data-stu-id="7b070-142">For example, compare the following two examples.</span></span> <span data-ttu-id="7b070-143">モジュール`Z`次のコードの内部のモジュールです。</span><span class="sxs-lookup"><span data-stu-id="7b070-143">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="7b070-144">モジュールが、`Z`モジュールに兄弟`Y`次のコードにします。</span><span class="sxs-lookup"><span data-stu-id="7b070-144">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="7b070-145">モジュール`Z`モジュールで他の宣言枝葉と同じインデントしないために、次のコードでは、兄弟モジュールも`Y`します。</span><span class="sxs-lookup"><span data-stu-id="7b070-145">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="7b070-146">最後に、外側のモジュールの宣言を持たず、その直後に別のモジュール宣言によって、新しいモジュール宣言は、内部のモジュールと見なされますが、コンパイラが警告が表示するかどうかは、2 番目のモジュールの定義は遠くよりインデントされません、まずは。</span><span class="sxs-lookup"><span data-stu-id="7b070-146">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="7b070-147">警告を回避するのには、内部のモジュールをインデントします。</span><span class="sxs-lookup"><span data-stu-id="7b070-147">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="7b070-148">1 つの外部モジュール内にあるファイル内のすべてのコードが必要な内部モジュールをする場合は、外側のモジュールには、等号 (=) は不要し、インデントを設定するのには、外側のモジュールである任意の内部モジュールを宣言を含む、宣言することはありません。</span><span class="sxs-lookup"><span data-stu-id="7b070-148">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="7b070-149">内部モジュール宣言内の宣言は、インデントする必要はします。</span><span class="sxs-lookup"><span data-stu-id="7b070-149">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="7b070-150">次のコードでは、この例を示します。</span><span class="sxs-lookup"><span data-stu-id="7b070-150">The following code shows this case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a><span data-ttu-id="7b070-151">再帰的なモジュール</span><span class="sxs-lookup"><span data-stu-id="7b070-151">Recursive modules</span></span>

<span data-ttu-id="7b070-152">F# 4.1 には、再帰的に相互に含まれているすべてのコードでは、モジュールの概念が導入されています。</span><span class="sxs-lookup"><span data-stu-id="7b070-152">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="7b070-153">使用してこれを行う`module rec`です。</span><span class="sxs-lookup"><span data-stu-id="7b070-153">This is done via `module rec`.</span></span>  <span data-ttu-id="7b070-154">使用`module rec`タイプやモジュール間で相互に参照のコードを記述することはできませんに痛みがあるいくつかを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="7b070-154">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="7b070-155">この例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7b070-155">The following is an example of this:</span></span>

```fsharp
module rec RecursiveModule =
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
        let peel (b: Banana) =
            let flip (banana: Banana) =
                match banana.Orientation with
                | Up -> 
                    banana.Orientation <- Down
                    banana
                | Down -> banana

            let peelSides (banana: Banana) =
                banana.Sides
                |> List.map (function
                             | Unpeeled -> Peeled
                             | Peeled -> Peeled)

            match b.Orientation with
            | Up ->   b |> flip |> peelSides
            | Down -> b |> peelSides
```

<span data-ttu-id="7b070-156">なお例外`DontSqueezeTheBananaException`とクラス`Banana`両方には、互いを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b070-156">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="7b070-157">さらに、モジュール`BananaHelpers`とクラス`Banana`も互いを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b070-157">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="7b070-158">これを削除した場合、f# で表現できないが、`rec`からキーワード、`RecursiveModule`モジュール。</span><span class="sxs-lookup"><span data-stu-id="7b070-158">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="7b070-159">この機能ではも使用[名前空間](namespaces.md)f# 4.1 にします。</span><span class="sxs-lookup"><span data-stu-id="7b070-159">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b070-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b070-160">See Also</span></span>

<span data-ttu-id="7b070-161">[F# 言語リファレンス](index.md)
[名前空間](namespaces.md)
[f# RFC FS 1009 - ファイル内でより大きなスコープを相互に参照型とモジュールを許可します。](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)</span><span class="sxs-lookup"><span data-stu-id="7b070-161">[F# Language Reference](index.md)
[Namespaces](namespaces.md)
[F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)</span></span>
