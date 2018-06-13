---
title: 'インポート宣言: open キーワード (F#)'
description: 完全修飾名を使用せずに参照できる要素を f# インポート宣言し、モジュールまたは名前空間を指定する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 29f09297993b347464f1572ac9ca24902c786f4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563533"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="6f364-103">インポート宣言:`open`キーワード</span><span class="sxs-lookup"><span data-stu-id="6f364-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
<span data-ttu-id="6f364-104">この記事の API リファレンスのリンクをクリックすると MSDN に移動します。</span><span class="sxs-lookup"><span data-stu-id="6f364-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="6f364-105">docs.microsoft.com API リファレンスは完全ではありません。</span><span class="sxs-lookup"><span data-stu-id="6f364-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="6f364-106">*インポート宣言*モジュールまたは完全修飾名を使用せずに参照できる要素の名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="6f364-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>


## <a name="syntax"></a><span data-ttu-id="6f364-107">構文</span><span class="sxs-lookup"><span data-stu-id="6f364-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="6f364-108">コメント</span><span class="sxs-lookup"><span data-stu-id="6f364-108">Remarks</span></span>
<span data-ttu-id="6f364-109">名前空間またはモジュールの完全修飾パスを使用してコードを参照するたびには、書き込み、読み取り、および管理することは困難コードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="6f364-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="6f364-110">代わりに、使用することができます、`open`キーワードを頻繁に使用されるモジュールと名前空間モジュールまたは名前空間のメンバーを参照するときに、完全修飾名ではなく、名前の短縮形を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6f364-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="6f364-111">このキーワードがに似ていますが、 `using` 、C# の場合は、キーワード`using namespace`Visual c、および`Imports`Visual Basic でします。</span><span class="sxs-lookup"><span data-stu-id="6f364-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="6f364-112">モジュールまたは名前空間は、同じプロジェクト内、または参照先プロジェクトまたはアセンブリ内にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f364-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="6f364-113">そうでない場合、プロジェクトへの参照を追加したり、使用、`-reference`コマンド`-`ライン オプション (またはその省略形`-r`)。</span><span class="sxs-lookup"><span data-stu-id="6f364-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="6f364-114">詳細については、「[コンパイラ オプション](compiler-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6f364-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="6f364-115">インポート宣言は、その外側の名前空間、モジュール、またはファイルの末尾までの宣言を次のコードで使用できる名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="6f364-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="6f364-116">複数のインポート宣言を使用する場合は、別々 の行に表示されます。</span><span class="sxs-lookup"><span data-stu-id="6f364-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="6f364-117">次のコードの使用を示しています、`open`コードを簡略化するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="6f364-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="6f364-118">F# コンパイラは生成されませんエラーまたは警告が 2 つ以上の開いているモジュールまたは名前空間に出現した場合、同じ名前のあいまいさが発生したとき。</span><span class="sxs-lookup"><span data-stu-id="6f364-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="6f364-119">あいまいさが発生すると、f# 優先直前に開かれた複数のモジュールまたは名前空間。</span><span class="sxs-lookup"><span data-stu-id="6f364-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="6f364-120">たとえば、次のコードで`empty`意味`Seq.empty`場合でも、`empty`両方にある、`List`と`Seq`モジュール。</span><span class="sxs-lookup"><span data-stu-id="6f364-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="6f364-121">そのため、注意を開くときのモジュールまたは名前空間など`List`または`Seq`同じ名前です。 代わりに、修飾名を使用するメンバーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6f364-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="6f364-122">コードがインポート宣言の順序に依存しているすべての状況を避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f364-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>


## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="6f364-123">既定で開かれている名前空間</span><span class="sxs-lookup"><span data-stu-id="6f364-123">Namespaces That Are Open by Default</span></span>
<span data-ttu-id="6f364-124">一部の名前空間は、明示的なインポート宣言がなくても暗黙的に開かれたことの f# コードで頻繁に使用されます。</span><span class="sxs-lookup"><span data-stu-id="6f364-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="6f364-125">次の表は、既定で開かれている名前空間を示します。</span><span class="sxs-lookup"><span data-stu-id="6f364-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="6f364-126">名前空間</span><span class="sxs-lookup"><span data-stu-id="6f364-126">Namespace</span></span>|<span data-ttu-id="6f364-127">説明</span><span class="sxs-lookup"><span data-stu-id="6f364-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="6f364-128">基本的な f# 型の定義を含む組み込み型など`int`と`float`です。</span><span class="sxs-lookup"><span data-stu-id="6f364-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="6f364-129">基本的な算術演算子を含む`+`と`*`です。</span><span class="sxs-lookup"><span data-stu-id="6f364-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="6f364-130">変更できないコレクション クラスを含む`List`と`Array`です。</span><span class="sxs-lookup"><span data-stu-id="6f364-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="6f364-131">レイジー評価と非同期ワークフローなどのコントロール構成要素の型が含まれています。</span><span class="sxs-lookup"><span data-stu-id="6f364-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="6f364-132">書式設定された IO は、のように関数を含む、`printf`関数。</span><span class="sxs-lookup"><span data-stu-id="6f364-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="6f364-133">AutoOpen 属性</span><span class="sxs-lookup"><span data-stu-id="6f364-133">AutoOpen Attribute</span></span>
<span data-ttu-id="6f364-134">適用することができます、`AutoOpen`アセンブリに属性をアセンブリが参照されている場合に、名前空間またはモジュールを自動的に開きたい場合。</span><span class="sxs-lookup"><span data-stu-id="6f364-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="6f364-135">適用することも、`AutoOpen`属性の親モジュールまたは名前空間が開かれるときに、そのモジュールを自動的に開くモジュールにします。</span><span class="sxs-lookup"><span data-stu-id="6f364-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="6f364-136">詳細については、次を参照してください。 [Core.AutoOpenAttribute クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)です。</span><span class="sxs-lookup"><span data-stu-id="6f364-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>


## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="6f364-137">RequireQualifiedAccess 属性</span><span class="sxs-lookup"><span data-stu-id="6f364-137">RequireQualifiedAccess Attribute</span></span>
<span data-ttu-id="6f364-138">いくつかのモジュール、レコード、または共用体の型を指定することがあります、`RequireQualifiedAccess`属性。</span><span class="sxs-lookup"><span data-stu-id="6f364-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="6f364-139">これらのモジュール、レコード、または共用体の要素を参照する場合は、インポート宣言を含めるかどうかに関係なく、修飾名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6f364-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="6f364-140">この属性を戦略的に使用する場合は、よくを定義する型名が使用されて、おけば名前の衝突を回避し、それによってコード回復力を高めるライブラリの変更にします。</span><span class="sxs-lookup"><span data-stu-id="6f364-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="6f364-141">詳細については、次を参照してください。 [Core.RequireQualifiedAccessAttribute クラス](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)です。</span><span class="sxs-lookup"><span data-stu-id="6f364-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>


## <a name="see-also"></a><span data-ttu-id="6f364-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="6f364-142">See Also</span></span>
[<span data-ttu-id="6f364-143"># 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="6f364-143"># Language Reference</span></span>](index.md)

[<span data-ttu-id="6f364-144">名前空間</span><span class="sxs-lookup"><span data-stu-id="6f364-144">Namespaces</span></span>](namespaces.md)

[<span data-ttu-id="6f364-145">モジュール</span><span class="sxs-lookup"><span data-stu-id="6f364-145">Modules</span></span>](modules.md)

