---
title: "インポート宣言: open キーワード (F#)"
description: "完全修飾名を使用せずに参照できる要素を f# インポート宣言し、モジュールまたは名前空間を指定する方法について説明します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1e98e48c-52e9-4314-8954-85d5583125f0
ms.openlocfilehash: a6d79bed3dd202657d06956edf9499a9b21a5f03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="4ac30-104">インポート宣言:`open`キーワード</span><span class="sxs-lookup"><span data-stu-id="4ac30-104">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
<span data-ttu-id="4ac30-105">この記事の API リファレンスのリンクをクリックすると MSDN に移動します。</span><span class="sxs-lookup"><span data-stu-id="4ac30-105">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="4ac30-106">docs.microsoft.com API リファレンスは完全ではありません。</span><span class="sxs-lookup"><span data-stu-id="4ac30-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="4ac30-107">*インポート宣言*モジュールまたは完全修飾名を使用せずに参照できる要素の名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="4ac30-107">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>


## <a name="syntax"></a><span data-ttu-id="4ac30-108">構文</span><span class="sxs-lookup"><span data-stu-id="4ac30-108">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="4ac30-109">コメント</span><span class="sxs-lookup"><span data-stu-id="4ac30-109">Remarks</span></span>
<span data-ttu-id="4ac30-110">名前空間またはモジュールの完全修飾パスを使用してコードを参照するたびには、書き込み、読み取り、および管理することは困難コードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4ac30-110">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="4ac30-111">代わりに、使用することができます、`open`キーワードを頻繁に使用されるモジュールと名前空間モジュールまたは名前空間のメンバーを参照するときに、完全修飾名ではなく、名前の短縮形を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4ac30-111">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="4ac30-112">このキーワードがに似ていますが、 `using` 、C# の場合は、キーワード`using namespace`Visual c、および`Imports`Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="4ac30-112">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="4ac30-113">モジュールまたは名前空間は、同じプロジェクト内、または参照先プロジェクトまたはアセンブリ内にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ac30-113">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="4ac30-114">そうでない場合、プロジェクトへの参照を追加したり、使用、`-reference`コマンド`-`ライン オプション (またはその省略形`-r`)。</span><span class="sxs-lookup"><span data-stu-id="4ac30-114">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="4ac30-115">詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ac30-115">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="4ac30-116">インポート宣言は、その外側の名前空間、モジュール、またはファイルの末尾までの宣言を次のコードで使用できる名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="4ac30-116">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="4ac30-117">複数のインポート宣言を使用する場合は、別々 の行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="4ac30-117">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="4ac30-118">次のコードの使用を示しています、`open`コードを簡略化するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="4ac30-118">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="4ac30-119">F# コンパイラは生成されませんエラーまたは警告が 2 つ以上の開いているモジュールまたは名前空間に出現した場合、同じ名前のあいまいさが発生したとき。</span><span class="sxs-lookup"><span data-stu-id="4ac30-119">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="4ac30-120">あいまいさが発生すると、f# 優先直前に開かれた複数のモジュールまたは名前空間。</span><span class="sxs-lookup"><span data-stu-id="4ac30-120">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="4ac30-121">たとえば、次のコードで`empty`意味`Seq.empty`場合でも、`empty`両方にある、`List`と`Seq`モジュール。</span><span class="sxs-lookup"><span data-stu-id="4ac30-121">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="4ac30-122">そのため、注意を開くときのモジュールまたは名前空間など`List`または`Seq`同じ名前です。 代わりに、修飾名を使用するメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4ac30-122">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="4ac30-123">コードがインポート宣言の順序に依存しているすべての状況を避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ac30-123">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>


## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="4ac30-124">既定で開かれている名前空間</span><span class="sxs-lookup"><span data-stu-id="4ac30-124">Namespaces That Are Open by Default</span></span>
<span data-ttu-id="4ac30-125">一部の名前空間は、明示的なインポート宣言がなくても暗黙的に開かれたことの f# コードで頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="4ac30-125">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="4ac30-126">次の表は、既定で開かれている名前空間を示します。</span><span class="sxs-lookup"><span data-stu-id="4ac30-126">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="4ac30-127">名前空間</span><span class="sxs-lookup"><span data-stu-id="4ac30-127">Namespace</span></span>|<span data-ttu-id="4ac30-128">説明</span><span class="sxs-lookup"><span data-stu-id="4ac30-128">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="4ac30-129">基本的な f# 型の定義を含む組み込み型など`int`と`float`です。</span><span class="sxs-lookup"><span data-stu-id="4ac30-129">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="4ac30-130">基本的な算術演算子を含む`+`と`*`です。</span><span class="sxs-lookup"><span data-stu-id="4ac30-130">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="4ac30-131">変更できないコレクション クラスを含む`List`と`Array`です。</span><span class="sxs-lookup"><span data-stu-id="4ac30-131">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="4ac30-132">レイジー評価と非同期ワークフローなどのコントロール構成要素の型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4ac30-132">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="4ac30-133">書式設定された IO は、のように関数を含む、`printf`関数。</span><span class="sxs-lookup"><span data-stu-id="4ac30-133">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="4ac30-134">AutoOpen 属性</span><span class="sxs-lookup"><span data-stu-id="4ac30-134">AutoOpen Attribute</span></span>
<span data-ttu-id="4ac30-135">適用することができます、`AutoOpen`アセンブリに属性をアセンブリが参照されている場合に、名前空間またはモジュールを自動的に開きたい場合。</span><span class="sxs-lookup"><span data-stu-id="4ac30-135">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="4ac30-136">適用することも、`AutoOpen`属性の親モジュールまたは名前空間が開かれるときに、そのモジュールを自動的に開くモジュールにします。</span><span class="sxs-lookup"><span data-stu-id="4ac30-136">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="4ac30-137">詳細については、次を参照してください。 [Core.AutoOpenAttribute クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)です。</span><span class="sxs-lookup"><span data-stu-id="4ac30-137">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>


## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="4ac30-138">RequireQualifiedAccess 属性</span><span class="sxs-lookup"><span data-stu-id="4ac30-138">RequireQualifiedAccess Attribute</span></span>
<span data-ttu-id="4ac30-139">いくつかのモジュール、レコード、または共用体の型を指定することがあります、`RequireQualifiedAccess`属性。</span><span class="sxs-lookup"><span data-stu-id="4ac30-139">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="4ac30-140">これらのモジュール、レコード、または共用体の要素を参照する場合は、インポート宣言を含めるかどうかに関係なく、修飾名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ac30-140">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="4ac30-141">この属性を戦略的に使用する場合は、よくを定義する型名が使用されて、おけば名前の衝突を回避し、それによってコード回復力を高めるライブラリの変更にします。</span><span class="sxs-lookup"><span data-stu-id="4ac30-141">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="4ac30-142">詳細については、次を参照してください。 [Core.RequireQualifiedAccessAttribute クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)です。</span><span class="sxs-lookup"><span data-stu-id="4ac30-142">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>


## <a name="see-also"></a><span data-ttu-id="4ac30-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ac30-143">See Also</span></span>
[<span data-ttu-id="4ac30-144"># 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="4ac30-144"># Language Reference</span></span>](index.md)

[<span data-ttu-id="4ac30-145">名前空間</span><span class="sxs-lookup"><span data-stu-id="4ac30-145">Namespaces</span></span>](namespaces.md)

[<span data-ttu-id="4ac30-146">モジュール</span><span class="sxs-lookup"><span data-stu-id="4ac30-146">Modules</span></span>](modules.md)

