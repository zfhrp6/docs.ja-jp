---
title: F# でコンポーネントのデザイン ガイドライン
description: F# で他の呼び出し元で消費するためのコンポーネントを記述するためのガイドラインを説明します。
ms.date: 05/14/2018
ms.openlocfilehash: 7859baac76be01b2cfbdc8602b6cc417cfe5106f
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2018
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="ea14f-103">F# でコンポーネントのデザイン ガイドライン</span><span class="sxs-lookup"><span data-stu-id="ea14f-103">F# component design guidelines</span></span>

<span data-ttu-id="ea14f-104">このドキュメントは、一連の f# プログラミング、f# コンポーネントのデザインのガイドラインに基づいて、v14、Microsoft Research のコンポーネントのデザイン ガイドラインおよび[別のバージョン](https://fsharp.org/specs/component-design-guidelines/)最初 curated および f# Software Foundation によって維持されます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and [another version](https://fsharp.org/specs/component-design-guidelines/) originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="ea14f-105">このドキュメントでは、f# プログラミングに慣れていると仮定します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="ea14f-106">多く f# コミュニティ投稿と、このガイドのさまざまなバージョンに役立つフィードバックのご協力に感謝します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="ea14f-107">概要</span><span class="sxs-lookup"><span data-stu-id="ea14f-107">Overview</span></span>

<span data-ttu-id="ea14f-108">このドキュメントは、f# コンポーネントの設計とコーディングに関連する問題の一部を検索します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="ea14f-109">コンポーネントは、次のいずれかで意味があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="ea14f-110">プロジェクト内の外部のコンシューマーのある f# プロジェクト内のレイヤー。</span><span class="sxs-lookup"><span data-stu-id="ea14f-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="ea14f-111">アセンブリ境界を越えて、f# コードによる消費を意図してライブラリです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="ea14f-112">アセンブリ境界を越えて、任意の .NET 言語による消費を意図してライブラリです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="ea14f-113">ライブラリのパッケージ リポジトリを使用して配布など[NuGet](https://nuget.org)です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="ea14f-114">この記事で説明した方法に従って、[優れた f# コードの 5 つの原則](index.md#five-principles-of-good-f-code)とため両方の機能を利用し、適切なプログラミング オブジェクトします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="ea14f-115">方法には、タイミングに関係なくコンポーネントおよびライブラリのデザイナー接している実用的で prosaic の問題の数、開発者が最も簡単に使用できる API を作成しようとしています。</span><span class="sxs-lookup"><span data-stu-id="ea14f-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="ea14f-116">Conscientious アプリケーション、 [.NET ライブラリ デザイン ガイドライン](../../standard/design-guidelines/index.md)一貫性のある一連の消費を快適になり、Api の作成における導いたりするされます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="ea14f-117">一般的なガイドライン</span><span class="sxs-lookup"><span data-stu-id="ea14f-117">General guidelines</span></span>

<span data-ttu-id="ea14f-118">F# ライブラリ、ライブラリの対象読者に関係なく適用されるいくつかのユニバーサル ガイドラインがあります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="ea14f-119">.NET ライブラリのデザイン ガイドラインを説明します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="ea14f-120">F# でコーディングを行うように関係なくすることが重要知識のある、 [.NET ライブラリ デザイン ガイドライン](../../standard/design-guidelines/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="ea14f-121">ほとんどの他の f# および .NET プログラマはや理解しており次のガイドラインに準拠するように .NET コードを期待します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="ea14f-122">.NET ライブラリのデザイン ガイドラインでは、名前付け、クラス、インターフェイス、メンバーのデザイン (プロパティ、メソッド、イベントなど) およびの詳細は、設計に関する一般的なガイダンスを提供し、さまざまなデザイン ガイドの参照の最初のポイントを便利が。</span><span class="sxs-lookup"><span data-stu-id="ea14f-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="ea14f-123">XML ドキュメント コメントをコードに追加します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="ea14f-124">パブリック Api の XML ドキュメントでは、ライブラリのファイルをこれらの型とメンバー、および有効にする構成ドキュメントを使用するときに、優れたの Intellisense とクイック ヒントを取得できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-124">XML documentation on public APIs ensure that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="ea14f-125">参照してください、 [XML ドキュメント](../language-reference/xml-documentation.md)に関するその他のマークアップ内で、xmldoc コメントの使用できるさまざまな xml タグ。</span><span class="sxs-lookup"><span data-stu-id="ea14f-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

<span data-ttu-id="ea14f-126">短い形式として XML のコメントを使用することができます (`/// comment`)、または標準の XML コメント (`///<summary>comment</summary>`)。</span><span class="sxs-lookup"><span data-stu-id="ea14f-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="ea14f-127">安定したライブラリとコンポーネントの Api の明示的なシグネチャ ファイル (.fsi) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="ea14f-128">パブリック API を両方こと、ライブラリの完全パブリック サーフェスを把握できるだけでなくする内部し、パブリックのドキュメント間を明確に分離を提供することができますの簡潔な概要を説明する f# ライブラリで明示的なシグネチャ ファイルの使用実装の詳細。</span><span class="sxs-lookup"><span data-stu-id="ea14f-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which both helps to ensure that you know the full public surface of your library, as well as provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="ea14f-129">シグネチャ ファイルが実装と署名の両方のファイルに対する変更を要求することによって、パブリック API の変化に摩擦を追加することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-129">Note that signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="ea14f-130">その結果、署名ファイルは通常のみ際に挿入される API 確立しましたになるし、大幅に変更が不要になった想定します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="ea14f-131">常に文字列を .NET で使用するためのベスト プラクティスに従う</span><span class="sxs-lookup"><span data-stu-id="ea14f-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="ea14f-132">次の[.NET での文字列を使用するためのベスト プラクティス](../../standard/base-types/best-practices-strings.md)ガイダンス。</span><span class="sxs-lookup"><span data-stu-id="ea14f-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="ea14f-133">具体的には、常に明示的に記述*カルチャ インテント*変換と文字列の比較で (該当する場合)。</span><span class="sxs-lookup"><span data-stu-id="ea14f-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="ea14f-134">F# に関するガイドラインのライブラリが直面しています。</span><span class="sxs-lookup"><span data-stu-id="ea14f-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="ea14f-135">ここでは、パブリック f# の開発に関する推奨事項のライブラリが直面しています。f# の開発者によって使用するためのパブリック Api を公開するライブラリは、します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="ea14f-136">F# を具体的には適用可能なライブラリ デザインの推奨事項のさまざまな。</span><span class="sxs-lookup"><span data-stu-id="ea14f-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="ea14f-137">具体的な推奨事項に従うがない場合は、.NET ライブラリ デザイン ガイドラインは、フォールバックのガイダンスです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="ea14f-138">名前付け規則</span><span class="sxs-lookup"><span data-stu-id="ea14f-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="ea14f-139">.NET の名前付けおよび大文字と小文字の規則を使用します</span><span class="sxs-lookup"><span data-stu-id="ea14f-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="ea14f-140">次の表では、.NET の名前付けおよび大文字と小文字の規則に従います。</span><span class="sxs-lookup"><span data-stu-id="ea14f-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="ea14f-141">F# の構成要素を含める小さな追加があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="ea14f-142">構成体</span><span class="sxs-lookup"><span data-stu-id="ea14f-142">Construct</span></span> | <span data-ttu-id="ea14f-143">Case</span><span class="sxs-lookup"><span data-stu-id="ea14f-143">Case</span></span> | <span data-ttu-id="ea14f-144">パーツ</span><span class="sxs-lookup"><span data-stu-id="ea14f-144">Part</span></span> | <span data-ttu-id="ea14f-145">使用例</span><span class="sxs-lookup"><span data-stu-id="ea14f-145">Examples</span></span> | <span data-ttu-id="ea14f-146">メモ</span><span class="sxs-lookup"><span data-stu-id="ea14f-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="ea14f-147">具象型</span><span class="sxs-lookup"><span data-stu-id="ea14f-147">Concrete types</span></span> | <span data-ttu-id="ea14f-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ea14f-148">PascalCase</span></span> | <span data-ttu-id="ea14f-149">名詞または形容詞</span><span class="sxs-lookup"><span data-stu-id="ea14f-149">Noun/ adjective</span></span> | <span data-ttu-id="ea14f-150">一覧で、Double、複雑な</span><span class="sxs-lookup"><span data-stu-id="ea14f-150">List, Double, Complex</span></span> | <span data-ttu-id="ea14f-151">具象型は、構造体、クラス、列挙体、デリゲート、レコード、および共用体です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="ea14f-152">OCaml で小文字従来型の名前ですが、F# で採用しています型の .NET 名前付けスキーム。</span><span class="sxs-lookup"><span data-stu-id="ea14f-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="ea14f-153">DLL</span><span class="sxs-lookup"><span data-stu-id="ea14f-153">DLLs</span></span>           | <span data-ttu-id="ea14f-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ea14f-154">PascalCase</span></span> |                 | <span data-ttu-id="ea14f-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="ea14f-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="ea14f-156">共用体タグ</span><span class="sxs-lookup"><span data-stu-id="ea14f-156">Union tags</span></span>     | <span data-ttu-id="ea14f-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ea14f-157">PascalCase</span></span> | <span data-ttu-id="ea14f-158">名詞</span><span class="sxs-lookup"><span data-stu-id="ea14f-158">Noun</span></span> | <span data-ttu-id="ea14f-159">いくつかの追加、成功</span><span class="sxs-lookup"><span data-stu-id="ea14f-159">Some, Add, Success</span></span> | <span data-ttu-id="ea14f-160">パブリック Api では、プレフィックスを使わないでください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="ea14f-161">必要に応じてなどの内部プレフィックスを使用して '' 入力チーム TAlpha を =</span><span class="sxs-lookup"><span data-stu-id="ea14f-161">Optionally use a prefix when internal, such as \`\`\`type Teams = TAlpha</span></span> | <span data-ttu-id="ea14f-162">TBeta</span><span class="sxs-lookup"><span data-stu-id="ea14f-162">TBeta</span></span> | <span data-ttu-id="ea14f-163">TDelta '' '。</span><span class="sxs-lookup"><span data-stu-id="ea14f-163">TDelta.\`\`\`</span></span> |
| <span data-ttu-id="ea14f-164">event</span><span class="sxs-lookup"><span data-stu-id="ea14f-164">Event</span></span>          | <span data-ttu-id="ea14f-165">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ea14f-165">PascalCase</span></span> | <span data-ttu-id="ea14f-166">動詞</span><span class="sxs-lookup"><span data-stu-id="ea14f-166">Verb</span></span> | <span data-ttu-id="ea14f-167">ValueChanged/ValueChanging</span><span class="sxs-lookup"><span data-stu-id="ea14f-167">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="ea14f-168">例外</span><span class="sxs-lookup"><span data-stu-id="ea14f-168">Exceptions</span></span>     | <span data-ttu-id="ea14f-169">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ea14f-169">PascalCase</span></span> |      | <span data-ttu-id="ea14f-170">WebException</span><span class="sxs-lookup"><span data-stu-id="ea14f-170">WebException</span></span> | <span data-ttu-id="ea14f-171">名前は、"Exception"で終わる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-171">Name should end with “Exception”.</span></span> |
| <span data-ttu-id="ea14f-172">フィールド</span><span class="sxs-lookup"><span data-stu-id="ea14f-172">Field</span></span>          | <span data-ttu-id="ea14f-173">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ea14f-173">PascalCase</span></span> | <span data-ttu-id="ea14f-174">名詞</span><span class="sxs-lookup"><span data-stu-id="ea14f-174">Noun</span></span> | <span data-ttu-id="ea14f-175">CurrentName</span><span class="sxs-lookup"><span data-stu-id="ea14f-175">CurrentName</span></span>  | |
| <span data-ttu-id="ea14f-176">インターフェイス型</span><span class="sxs-lookup"><span data-stu-id="ea14f-176">Interface types</span></span> |  <span data-ttu-id="ea14f-177">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ea14f-177">PascalCase</span></span> | <span data-ttu-id="ea14f-178">名詞または形容詞</span><span class="sxs-lookup"><span data-stu-id="ea14f-178">Noun/ adjective</span></span> | <span data-ttu-id="ea14f-179">IDisposable</span><span class="sxs-lookup"><span data-stu-id="ea14f-179">IDisposable</span></span> | <span data-ttu-id="ea14f-180">名前は、"I"で始まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-180">Name should start with “I”.</span></span> |
| <span data-ttu-id="ea14f-181">メソッド</span><span class="sxs-lookup"><span data-stu-id="ea14f-181">Method</span></span> |  <span data-ttu-id="ea14f-182">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ea14f-182">PascalCase</span></span> |  <span data-ttu-id="ea14f-183">動詞</span><span class="sxs-lookup"><span data-stu-id="ea14f-183">Verb</span></span> | <span data-ttu-id="ea14f-184">ToString</span><span class="sxs-lookup"><span data-stu-id="ea14f-184">ToString</span></span> | |
| <span data-ttu-id="ea14f-185">名前空間</span><span class="sxs-lookup"><span data-stu-id="ea14f-185">Namespace</span></span> | <span data-ttu-id="ea14f-186">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ea14f-186">PascalCase</span></span> | | <span data-ttu-id="ea14f-187">Microsoft.FSharp.Core</span><span class="sxs-lookup"><span data-stu-id="ea14f-187">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="ea14f-188">一般に使用`<Organization>.<Technology>[.<Subnamespace>]`、ただしテクノロジが組織に依存しない場合は、組織をドロップします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-188">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="ea14f-189">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea14f-189">Parameters</span></span> | <span data-ttu-id="ea14f-190">キャメル ケース</span><span class="sxs-lookup"><span data-stu-id="ea14f-190">camelCase</span></span> | <span data-ttu-id="ea14f-191">名詞</span><span class="sxs-lookup"><span data-stu-id="ea14f-191">Noun</span></span> |  <span data-ttu-id="ea14f-192">typeName、変換、範囲</span><span class="sxs-lookup"><span data-stu-id="ea14f-192">typeName, transform, range</span></span> | |
| <span data-ttu-id="ea14f-193">(内部) の値を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-193">let values (internal)</span></span> | <span data-ttu-id="ea14f-194">キャメル ケースまたは PascalCase</span><span class="sxs-lookup"><span data-stu-id="ea14f-194">camelCase or PascalCase</span></span> | <span data-ttu-id="ea14f-195">名詞と動詞</span><span class="sxs-lookup"><span data-stu-id="ea14f-195">Noun/ verb</span></span> |  <span data-ttu-id="ea14f-196">getValue、myTable</span><span class="sxs-lookup"><span data-stu-id="ea14f-196">getValue, myTable</span></span> |
| <span data-ttu-id="ea14f-197">値 (外部) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-197">let values (external)</span></span> | <span data-ttu-id="ea14f-198">キャメル ケースまたは PascalCase</span><span class="sxs-lookup"><span data-stu-id="ea14f-198">camelCase or PascalCase</span></span> | <span data-ttu-id="ea14f-199">名詞と動詞</span><span class="sxs-lookup"><span data-stu-id="ea14f-199">Noun/verb</span></span>  | <span data-ttu-id="ea14f-200">List.map、Dates.Today</span><span class="sxs-lookup"><span data-stu-id="ea14f-200">List.map, Dates.Today</span></span> | <span data-ttu-id="ea14f-201">let バインドされた値は、従来の機能のデザイン パターンに従うときに多くの場合、パブリック。</span><span class="sxs-lookup"><span data-stu-id="ea14f-201">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="ea14f-202">ただし、通常使用 PascalCase 識別子を他の .NET 言語から使用するとき。</span><span class="sxs-lookup"><span data-stu-id="ea14f-202">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="ea14f-203">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ea14f-203">Property</span></span>  | <span data-ttu-id="ea14f-204">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ea14f-204">PascalCase</span></span>  | <span data-ttu-id="ea14f-205">名詞または形容詞</span><span class="sxs-lookup"><span data-stu-id="ea14f-205">Noun/ adjective</span></span>  | <span data-ttu-id="ea14f-206">IsEndOfFile、背景色</span><span class="sxs-lookup"><span data-stu-id="ea14f-206">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="ea14f-207">ブール型プロパティ、通常は使用して、ことができ、IsEndOfFile、いない IsNotEndOfFile と同様に、肯定的である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-207">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="ea14f-208">省略形を回避します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-208">Avoid abbreviations</span></span>

<span data-ttu-id="ea14f-209">.NET ガイドラインの省略形の使用を防ぐため (たとえば、"使用`OnButtonClick`なく`OnBtnClick`") です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-209">The .NET guidelines discourage the use of abbreviations (for example, “use `OnButtonClick` rather than `OnBtnClick`”).</span></span> <span data-ttu-id="ea14f-210">一般的な省略形など`Async`「非同期」の場合は、許容されます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-210">Common abbreviations, such as `Async` for “Asynchronous”, are tolerated.</span></span> <span data-ttu-id="ea14f-211">、関数型プログラミングでは、このガイドラインは無視される場合がありますたとえば、 `List.iter` 「反復処理する」の省略形を使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-211">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for “iterate”.</span></span> <span data-ttu-id="ea14f-212">このため、略語を使用して f# ではある程度の大きい値を許容する傾向があります-を-f# プログラミングでは、引き続き通常パブリック コンポーネントのデザインに避ける必要がありますが、します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-212">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="ea14f-213">大文字小文字の区別の名前の衝突を避ける</span><span class="sxs-lookup"><span data-stu-id="ea14f-213">Avoid casing name collisions</span></span>

<span data-ttu-id="ea14f-214">.NET のガイドラインでは、一部のクライアント言語 (たとえば、Visual Basic) 小文字は区別されませんので、名の競合を区別するために単独で大文字と小文字を使用できないことを言います。</span><span class="sxs-lookup"><span data-stu-id="ea14f-214">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="ea14f-215">頭字語を使用して適切な場所</span><span class="sxs-lookup"><span data-stu-id="ea14f-215">Use acronyms where appropriate</span></span>

<span data-ttu-id="ea14f-216">XML などの頭字語は、省略形ではないや、uncapitalized 形式 (Xml) での .NET ライブラリで広く使用されます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-216">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="ea14f-217">のみよく知られている、広く認識されているの頭字語を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-217">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="ea14f-218">PascalCase 名を使用するジェネリック パラメーター</span><span class="sxs-lookup"><span data-stu-id="ea14f-218">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="ea14f-219">PascalCase 名を使用するジェネリック パラメーターの f# などのパブリック Api でのライブラリが直面しています。</span><span class="sxs-lookup"><span data-stu-id="ea14f-219">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="ea14f-220">具体的には、ような名前を使用して`T`、 `U`、 `T1`、`T2`の任意のジェネリック パラメーターを使用して特定の名前をなしませんし、f# に直接つながっているライブラリのような名前を使用して`Key`、 `Value`、 `Arg`(がないなど、 `TKey`)。</span><span class="sxs-lookup"><span data-stu-id="ea14f-220">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="ea14f-221">パブリックの関数と f# モジュール内の値に PascalCase またはキャメル ケースのいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-221">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="ea14f-222">キャメル ケースが使用するよう設計されているパブリック関数の使用修飾されていない (たとえば、 `invalidArg`)、(たとえば、List.map)「標準的なコレクション関数」にします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-222">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the “standard collection functions” (for example, List.map).</span></span> <span data-ttu-id="ea14f-223">どちらの場合も、関数名機能は言語のキーワードと同様にします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-223">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="ea14f-224">オブジェクト、型、およびモジュールのデザイン</span><span class="sxs-lookup"><span data-stu-id="ea14f-224">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="ea14f-225">名前空間またはモジュールを使用してタイプやモジュールを含める</span><span class="sxs-lookup"><span data-stu-id="ea14f-225">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="ea14f-226">コンポーネントのそれぞれの f# ファイルは、名前空間の宣言またはモジュールの宣言で始まる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-226">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="ea14f-227">または</span><span class="sxs-lookup"><span data-stu-id="ea14f-227">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="ea14f-228">モジュールと名前空間を使用して、最上位レベルのコードを整理する間の相違点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-228">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="ea14f-229">名前空間が複数のファイルにまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-229">Namespaces can span multiple files</span></span>
* <span data-ttu-id="ea14f-230">名前空間は内部のモジュール内にある場合を除き、f# の関数を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="ea14f-230">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="ea14f-231">指定されたモジュールのコードは、1 つのファイル内に含まれる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-231">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="ea14f-232">最上位レベルのモジュールは、内部のモジュールのなしの f# 関数を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-232">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="ea14f-233">最上位レベルの名前空間またはモジュール間の選択は、コードのコンパイルした形式に影響し、したがってが影響他の .NET 言語から、ビューは、API 最終的に利用できる f# コードの外部で。</span><span class="sxs-lookup"><span data-stu-id="ea14f-233">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="ea14f-234">オブジェクトの種類に固有の操作のためのメソッドとプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-234">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="ea14f-235">オブジェクトを使用する場合は、メソッドおよびその型のプロパティとして利用できる機能が実装されていることを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-235">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="ea14f-236">そのメンバーに特定のメンバーが持つ機能の一括必要があるとは限りません実装はありませんが、その機能の利用できる部分の有効期限があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-236">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="ea14f-237">クラスを使用して、変更可能な状態をカプセル化</span><span class="sxs-lookup"><span data-stu-id="ea14f-237">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="ea14f-238">F# でこれのみ行う必要があります、いる状態は既にカプセル化されていないクロージャ、シーケンス式、または非同期計算などの別の言語コンストラクトでします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-238">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="ea14f-239">インターフェイスを使用してグループ化に関連する操作</span><span class="sxs-lookup"><span data-stu-id="ea14f-239">Use interfaces to group related operations</span></span>

<span data-ttu-id="ea14f-240">インターフェイス型を使用して、一連の操作を表します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-240">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="ea14f-241">これは、関数の組または関数のレコードなど、その他のオプションをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-241">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="ea14f-242">優先します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-242">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

<span data-ttu-id="ea14f-243">インターフェイスは、.NET では、どのようなファンクター通常できるようになりますを実現するために使用できるファースト クラスの概念です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-243">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="ea14f-244">さらに、関数のレコードのことはできませんが、プログラムに存在: 型のエンコードに使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-244">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a><span data-ttu-id="ea14f-245">操作を実行するグループの機能をモジュールのコレクションを使用します</span><span class="sxs-lookup"><span data-stu-id="ea14f-245">Use a module to group functions which act on collections</span></span>

<span data-ttu-id="ea14f-246">コレクション型を定義するときなどの操作の標準セットを提供することを検討してください`CollectionType.map`と`CollectionType.iter`) の新しいコレクション型。</span><span class="sxs-lookup"><span data-stu-id="ea14f-246">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="ea14f-247">このようなモジュールを含める場合は FSharp.Core で見つかった関数の名前付け規則に従います。</span><span class="sxs-lookup"><span data-stu-id="ea14f-247">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="ea14f-248">数学関数や DSL ライブラリで特にの一般的な正規の関数グループ関数をモジュールを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-248">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="ea14f-249">たとえば、`Microsoft.FSharp.Core.Operators`されて自動的に開かれている最上位の関数のコレクション (と同様に`abs`と`sin`) FSharp.Core.dll によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-249">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="ea14f-250">同様に、統計のライブラリは関数を持つモジュールを含めることが`erf`と`erfc`に明示的にまたは自動的に開かれるこのモジュールは設計されています。</span><span class="sxs-lookup"><span data-stu-id="ea14f-250">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="ea14f-251">RequireQualifiedAccess の使用を検討し、慎重に AutoOpen 属性を適用</span><span class="sxs-lookup"><span data-stu-id="ea14f-251">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="ea14f-252">追加する、`[<RequireQualifiedAccess>]`属性をモジュールにことを示し、モジュールが開かれていませんアクセスを修飾するモジュールの要素への参照が明示的に必要なことです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-252">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="ea14f-253">たとえば、`Microsoft.FSharp.Collections.List`モジュールは、この属性を持ちます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-253">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="ea14f-254">これは、機能は、関数と、モジュール内の値は、他のモジュールの名前と競合する可能性のある名前を持つ場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-254">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="ea14f-255">修飾のアクセスを必要とすると、長期的な保守容易性とライブラリの発展性が大幅に増やすできます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-255">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="ea14f-256">追加する、`[<AutoOpen>]`をモジュールに属性を含む名前空間が開かれたときに、モジュールが開かれることを意味します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-256">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="ea14f-257">`[<AutoOpen>]`属性は、アセンブリが参照されている場合に自動的に開かれているモジュールを示すためにアセンブリにも適用できます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-257">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="ea14f-258">統計ライブラリなど、 **MathsHeaven.Statistics**場合があります、`module MathsHeaven.Statistics.Operators`関数を含む`erf`と`erfc`です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-258">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="ea14f-259">このモジュールとして指定することは正当`[<AutoOpen>]`です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-259">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="ea14f-260">つまり、`open MathsHeaven.Statistics`もこのモジュールを開き、名前を`erf`と`erfc`スコープにします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-260">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="ea14f-261">別なを使用して`[<AutoOpen>]`拡張メソッドが含まれるモジュールです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-261">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="ea14f-262">使いすぎ`[<AutoOpen>]`汚染名前空間と属性に潜在顧客は、注意を払って使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-262">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="ea14f-263">特定のドメインを賢く利用で特定のライブラリの`[<AutoOpen>]`使いやすさにつながることができます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-263">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="ea14f-264">ここで、よく知られている演算子の使用は適切なクラスで演算子メンバーの定義を検討してください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-264">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="ea14f-265">場合によってベクトルなどの数学的な構造をモデル化するクラスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-265">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="ea14f-266">モデル化されているドメインがよく知られている演算子を持つクラスに固有のメンバーとして定義することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-266">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="ea14f-267">このガイドは、これらの型の .NET の一般的なガイダンスに対応します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-267">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="ea14f-268">ただし、f# コーディングこれにより、これらの型の f# 関数と組み合わせておよび List.sumBy など、メンバーの制約のメソッドで使用するようにさらに重要なことができます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-268">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="ea14f-269">提供する CompiledName の使用を検討します。他の .NET 言語コンシューマー NET のフレンドリ名</span><span class="sxs-lookup"><span data-stu-id="ea14f-269">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="ea14f-270">F# のコンシューマーの名前を 1 つのスタイルで何かにすることも (小文字のみに表示されるように静的メンバーなどモジュール バインド関数の場合と同様) がアセンブリにコンパイルすると、名前の別のスタイルがします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-270">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="ea14f-271">使用することができます、`[<CompiledName>]`属性とは異なるスタイル コードを提供する非 f# アセンブリを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-271">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="ea14f-272">使用して`[<CompiledName>]`、非 f# アセンブリのコンシューマーの .NET 名前付け規則を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-272">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="ea14f-273">メンバー関数の場合は、メソッドのオーバー ロードを使用するため、これにより、シンプルな API 場合</span><span class="sxs-lookup"><span data-stu-id="ea14f-273">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="ea14f-274">メソッドのオーバー ロードは、さまざまなオプションと引数が、同様の機能を実行する必要がある API を簡略化するための強力なツールです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-274">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="ea14f-275">F# では、引数の型ではなく引数の数のオーバー ロードする方が一般的です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-275">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="ea14f-276">これらの型のデザインが発展する可能性がある場合、レコード、共用体の型の表現を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-276">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="ea14f-277">オブジェクトの具体的な表現を公開することを回避します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-277">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="ea14f-278">たとえば、具象の形式を<xref:System.DateTime>値が .NET ライブラリ デザインの外部のパブリック API によって公開されていません。</span><span class="sxs-lookup"><span data-stu-id="ea14f-278">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="ea14f-279">実行時に、共通言語ランタイムは、実行全体で使用されるコミットの実装を認識します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-279">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="ea14f-280">ただし、コンパイルされたコードはしない自体、具体的な表現への依存関係を取得します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-280">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="ea14f-281">機能拡張の実装の継承は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-281">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="ea14f-282">F# では、実装の継承がほとんど使用されません。</span><span class="sxs-lookup"><span data-stu-id="ea14f-282">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="ea14f-283">さらに、継承階層は多くの場合、複雑で、新しい必要条件は到着したときに変更するが困難にします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-283">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="ea14f-284">継承の実装は、互換性とは、問題に最適なソリューションは、インターフェイスの実装など、ポリモーフィズムの設計時に、f# プログラム内で代替手法を取得する必要がありますが、まれなケースの f# では引き続き存在します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-284">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="ea14f-285">関数とメンバーのシグネチャ</span><span class="sxs-lookup"><span data-stu-id="ea14f-285">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="ea14f-286">少数の関連のない複数の値を返すときに、戻り値の組を使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-286">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="ea14f-287">戻り値の型、タプルを使用しての良い例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-287">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="ea14f-288">多くのコンポーネントを含む型を返すか、コンポーネントは、特定の単一のエンティティに関連する、場所は、組ではなく名前付きの型を使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-288">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="ea14f-289">使用して`Async<T>`f# API の境界での非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="ea14f-289">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="ea14f-290">という名前の対応する同期操作があるかどうかは`Operation`を返す、 `T`、このという名前を付けると、非同期処理する必要があります`AsyncOperation`を返す場合`Async<T>`または`OperationAsync`を返す場合`Task<T>`です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-290">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="ea14f-291">Begin/end メソッドを公開する、よく使用される .NET 型の使用を検討の`Async.FromBeginEnd`拡張メソッドを特定の .NET Api を F# で非同期プログラミング モデルを提供するファサードとして書き込みます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-291">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int) : int =
        ...
    member this.AsyncCompute(x:int) : Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="ea14f-292">例外</span><span class="sxs-lookup"><span data-stu-id="ea14f-292">Exceptions</span></span>

<span data-ttu-id="ea14f-293">例外は、.NET の例外つまり、する必要がありますいない頻繁に発生実行時にします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-293">Exceptions are exceptional in .NET; that is, they should not occur frequently at runtime.</span></span> <span data-ttu-id="ea14f-294">場合に、含まれている情報は重要です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-294">When they do, the information they contain is valuable.</span></span> <span data-ttu-id="ea14f-295">例外は、コア .NET; のファースト クラスの概念次のように、例外のアプリケーションを適切なコンポーネントのインターフェイスの設計の一部として使用するため it です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-295">Exceptions are a core first class concept of .NET; it hence follows that appropriate application of the Exceptions should be used as part of the design of the interface of a component.</span></span>

#### <a name="follow-the-net-guidelines-for-exceptions"></a><span data-ttu-id="ea14f-296">例外、.NET のガイドラインに従う</span><span class="sxs-lookup"><span data-stu-id="ea14f-296">Follow the .NET guidelines for exceptions</span></span>

<span data-ttu-id="ea14f-297">[.NET ライブラリ デザイン ガイドライン](../../standard/design-guidelines/exceptions.md)のすべての .NET プログラミングのコンテキストでの例外の使用上のすばらしいアドバイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-297">The [.NET Library Design Guidelines](../../standard/design-guidelines/exceptions.md) give excellent advice on the use of exceptions in the context of all .NET programming.</span></span> <span data-ttu-id="ea14f-298">これらのガイドラインの一部としては。</span><span class="sxs-lookup"><span data-stu-id="ea14f-298">Some of these guidelines are as follows:</span></span>

* <span data-ttu-id="ea14f-299">通常の制御フローの例外を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-299">Do not use exceptions for normal flow of control.</span></span> <span data-ttu-id="ea14f-300">この手法は OCaml などの言語で使用される多くの場合、これはバグが発生しやすくし、.NET で効率的なことができます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-300">Although this technique is often used in languages such as OCaml, it is bug-prone and can be inefficient on .NET.</span></span> <span data-ttu-id="ea14f-301">代わりに、検討を返す、`None`オプションの失敗の原因、一般的なまたは予期される出現する位置を示す値。</span><span class="sxs-lookup"><span data-stu-id="ea14f-301">Instead, consider returning a `None` option value to indicate a failure that is a common or expected occurrence.</span></span>

* <span data-ttu-id="ea14f-302">関数が正しく使用されていないときに、コンポーネントによってスローされる例外を文書化します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-302">Document exceptions thrown by your components when a function is used incorrectly.</span></span>

* <span data-ttu-id="ea14f-303">可能であれば、システムの名前空間から既存の例外を使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-303">Where possible, employ existing exceptions from the System namespaces.</span></span> <span data-ttu-id="ea14f-304">回避<xref:System.ApplicationException>ことができます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-304">Avoid <xref:System.ApplicationException>, though.</span></span>

* <span data-ttu-id="ea14f-305">スローしないで<xref:System.Exception>ことをユーザー コードにはエスケープするときにします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-305">Do not throw <xref:System.Exception> when it will escape to user code.</span></span> <span data-ttu-id="ea14f-306">これは、使用しないが含まれています。 `failwith`、 `failwithf`、スクリプトで使用すると、開発中コード用の便利な関数は、より具体的な種類の例外がスローされることを優先するための f# ライブラリ コードから削除するかがいます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-306">This includes avoiding the use of `failwith`, `failwithf`, which are handy functions for use in scripting and for code under development, but should be removed from F# library code in favor of throwing a more specific exception type.</span></span>

* <span data-ttu-id="ea14f-307">使用して`nullArg`、 `invalidArg`、および`invalidOp`をスローするためのメカニズムとして<xref:System.ArgumentNullException>、 <xref:System.ArgumentException>、および<xref:System.InvalidOperationException>適切な場合です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-307">Use `nullArg`, `invalidArg`, and `invalidOp` as the mechanism to throw <xref:System.ArgumentNullException>, <xref:System.ArgumentException>, and <xref:System.InvalidOperationException> when appropriate.</span></span>

#### <a name="consider-using-option-values-for-return-types-when-failure-is-not-an-exceptional-scenario"></a><span data-ttu-id="ea14f-308">エラーが例外的なシナリオではない場合に戻り値の型のオプションの値を使用してください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-308">Consider using option values for return types when failure is not an exceptional scenario</span></span>

<span data-ttu-id="ea14f-309">例外に .NET アプローチはことがあります「例外的な」です。つまり、それらを実行する頻度が比較的低い。</span><span class="sxs-lookup"><span data-stu-id="ea14f-309">The .NET approach to exceptions is that they should be “exceptional”; that is, they should occur relatively infrequently.</span></span> <span data-ttu-id="ea14f-310">ただし、一部の操作 (たとえば、テーブルを検索) が頻繁に失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-310">However, some operations (for example, searching a table) may fail frequently.</span></span> <span data-ttu-id="ea14f-311">F# のオプションの値は、これらの操作の戻り値の型を表すための優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-311">F# option values are an excellent way to represent the return types of these operations.</span></span> <span data-ttu-id="ea14f-312">これらの操作は、通常、名のプレフィックス"try"で開始します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-312">These operations conventionally start with the name prefix “try”:</span></span>

```fsharp
// bad: throws exception if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// bad: returns -1 if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// good: returns None if no element meets criteria
member this.TryFindFirstIndex(pred : 'T -> bool) : int option =
    ...
```

### <a name="extension-members"></a><span data-ttu-id="ea14f-313">拡張メンバー</span><span class="sxs-lookup"><span data-stu-id="ea14f-313">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="ea14f-314">F# で f# 拡張メンバーを慎重に適用にする-f# コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ea14f-314">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="ea14f-315">F# の拡張メンバー一般にのみ使用してくださいのほとんどでは、そのモードの使用の種類に関連付けられた組み込みの操作のクロージャに含まれる操作。</span><span class="sxs-lookup"><span data-stu-id="ea14f-315">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="ea14f-316">1 つの一般的な用途は、さまざまな .NET 型の f# 慣用は Api を提供します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-316">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="ea14f-317">共用体の型</span><span class="sxs-lookup"><span data-stu-id="ea14f-317">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="ea14f-318">クラスの階層構造ではなくツリー構造のデータの判別共用体を使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-318">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="ea14f-319">ツリーのような構造体は、再帰的に定義されています。</span><span class="sxs-lookup"><span data-stu-id="ea14f-319">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="ea14f-320">これは、継承を使用して不適切な判別共用体で洗練されたです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-320">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="ea14f-321">判別共用体のツリーのようなデータを表すも使用するパターン マッチで exhaustiveness メリットを享受できます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-321">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="ea14f-322">使用して`[<RequireQualifiedAccess>]`に名前を持つケースが十分に一意ではない共用体の型</span><span class="sxs-lookup"><span data-stu-id="ea14f-322">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="ea14f-323">判別共用体ケースなどの別の意味のわかりやすい名前を同じ名前がここでは、ドメインで気づいたら可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-323">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="ea14f-324">使用することができます`[<RequireQualifiedAccess>]`トリガーの順序に依存してにシャドウによる混乱を招くエラーを回避するために、ケースの名前を区別するために`open`ステートメント</span><span class="sxs-lookup"><span data-stu-id="ea14f-324">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="ea14f-325">これらの型のデザインが発展する可能性がある場合、バイナリの互換性のある Api の判別共用体の表現を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-325">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="ea14f-326">共用体の型は、f# パターン マッチ フォームの簡潔なプログラミング モデルに依存します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-326">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="ea14f-327">前述のように、これらの型のデザインが発展する可能性がある場合は、具体的なデータ表現を漏洩を避ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-327">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="ea14f-328">たとえば、判別共用体の形式を非表示にできるプライベートまたは内部の宣言を使用してまたは署名ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-328">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="ea14f-329">無秩序判別共用体を表示する場合があります、バージョンにハード ライブラリ ユーザー コードを分断することがなく。</span><span class="sxs-lookup"><span data-stu-id="ea14f-329">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="ea14f-330">代わりに、型の値に一致するパターンを許可するように 1 つまたは複数のアクティブなパターンを公開することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-330">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="ea14f-331">アクティブ パターンでは、f# 共用体の型を直接公開することを回避しながらに一致するパターンを F# でコンシューマーに提供する別の方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-331">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="ea14f-332">インライン関数とメンバーの制約</span><span class="sxs-lookup"><span data-stu-id="ea14f-332">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="ea14f-333">暗黙的なメンバー制約と静的に解決されたジェネリック型とインライン関数を使用して、ジェネリックな数値アルゴリズムを定義します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-333">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="ea14f-334">算術メンバー制約と f# 比較制約は、f# のプログラミング用の標準はします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-334">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="ea14f-335">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-335">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="ea14f-336">この関数の型は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-336">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="ea14f-337">これは、数値演算ライブラリ内のパブリック API の適切な関数です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-337">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="ea14f-338">型のクラスとダック」と入力をシミュレートするためにメンバー制約は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-338">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="ea14f-339">「入力ダック」をシミュレートすることは f# メンバー制約を使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-339">It is possible to simulate “duck typing” using F# member constraints.</span></span> <span data-ttu-id="ea14f-340">ただし、構成するメンバーを使用してこのではなく一般的なを f# で使用する必要があります-に、f# ライブラリ デザインします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-340">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="ea14f-341">これは、未知または標準の暗黙的な制約に基づいてライブラリ デザインになり強い特定のフレームワークを 1 つのパターンに関連付けられたユーザー コードが発生する傾向があるためです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-341">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="ea14f-342">さらに、この方法でメンバー制約が多用は非常に長いコンパイル時間につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-342">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="ea14f-343">演算子の定義</span><span class="sxs-lookup"><span data-stu-id="ea14f-343">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="ea14f-344">シンボリック カスタムの演算子を定義しないように</span><span class="sxs-lookup"><span data-stu-id="ea14f-344">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="ea14f-345">カスタム演算子は、一部の状況で不可欠な機能および実装コードの本文内で表記デバイスが非常に有用です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-345">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="ea14f-346">ライブラリの新規ユーザーの名前付き関数でを使いやすくする多くの場合です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-346">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="ea14f-347">さらに、カスタム シンボリック演算子は、ドキュメント、しにくいことができ、ユーザーでは検索され、検索エンジンの既存の制限のための演算子に関するヘルプを検索することが難しくします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-347">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="ea14f-348">その結果、という名前の関数、およびメンバーとして、機能を公開し、さらに、ドキュメントとすることのコストの認知表記の利点を上回る場合する場合にのみにこの機能のための演算子を公開することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-348">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="ea14f-349">測定単位</span><span class="sxs-lookup"><span data-stu-id="ea14f-349">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="ea14f-350">F# コードで追加した型の安全性の単位を慎重に使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-350">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="ea14f-351">他の .NET 言語で表示したときに、メジャーの単位の追加入力情報が消去されます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-351">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="ea14f-352">.NET コンポーネント、ツール、およびリフレクションが単位数 san の種類が表示される注意してください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-352">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="ea14f-353">たとえば、c# コンシューマーは参照`float`なく`float<kg>`です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-353">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="ea14f-354">型略称</span><span class="sxs-lookup"><span data-stu-id="ea14f-354">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="ea14f-355">型の省略形を使用して慎重に f# コードを簡略化</span><span class="sxs-lookup"><span data-stu-id="ea14f-355">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="ea14f-356">.NET コンポーネント、ツール、およびリフレクション型の省略名は表示されません。</span><span class="sxs-lookup"><span data-stu-id="ea14f-356">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="ea14f-357">型の省略形の重要な使用法には、ドメインが表示されるより複雑実際にが、コンシューマーが混乱することもできます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-357">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="ea14f-358">メンバーとプロパティが省略されている型で使用するものは本質的に異なる必要がありますのパブリック型の型の省略形を回避します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-358">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="ea14f-359">この場合、省略されている型は、定義されている実際の型の表現についてあまりが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-359">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="ea14f-360">代わりに、クラス型または単一ケースの判別共用体での省略形の折り返しを検討してください (または、パフォーマンスが重要な場合は、構造体の型を使用して、省略形をラップすることを検討してください)。</span><span class="sxs-lookup"><span data-stu-id="ea14f-360">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="ea14f-361">たとえば、することは避けてなど、F# でマップの特殊なケースとして、複数のマップを定義します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-361">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="ea14f-362">ただし、この型でドット付き表記の論理操作は、マップでは、操作と同じではありません: などが妥当 lookup 操作にマップします。[キー] 例外が発生するのではなく、辞書にキーがない場合は、空のリストを返します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-362">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="ea14f-363">他の .NET 言語から使用するためのライブラリに関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="ea14f-363">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="ea14f-364">他の .NET 言語から使用するためのライブラリをデザインする場合に従う必要が、 [.NET ライブラリ デザイン ガイドライン](../../standard/design-guidelines/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-364">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="ea14f-365">このドキュメントでこれらのライブラリは f# ではなく、標準の .NET ライブラリとしてというラベルが付いた-制限なし構築 f# を使用するライブラリが直面しています。</span><span class="sxs-lookup"><span data-stu-id="ea14f-365">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="ea14f-366">標準の .NET ライブラリのデザインには、f# の使用を最小限に抑えることによって、.NET Framework の残りの部分と一貫性のある使い慣れたと慣用 Api を提供することを意味のパブリック API で特定のコンス トラクターです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-366">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="ea14f-367">ルールは、次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-367">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-sesign-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="ea14f-368">Namespace と型の sesign (の他の .NET 言語から使用するライブラリ)</span><span class="sxs-lookup"><span data-stu-id="ea14f-368">Namespace and Type sesign (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="ea14f-369">コンポーネントのパブリック API への .NET の名前付け規則を適用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-369">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="ea14f-370">省略名および .NET の大文字と小文字のガイドラインを使用する特別な注意してください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-370">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="ea14f-371">名前空間、型、およびメンバーをコンポーネントの主要な組織構造として使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-371">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="ea14f-372">パブリックな機能を含むすべてのファイルの先頭でなければなりません、`namespace`宣言、および名前空間で公開されたエンティティだけに、型を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-372">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="ea14f-373">F# モジュールを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-373">Do not use F# modules.</span></span>

<span data-ttu-id="ea14f-374">実装コードは、ユーティリティ型、およびユーティリティ関数を保持するためにパブリックでないモジュールを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-374">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="ea14f-375">静的な型必要がありますよりも優先される、モジュール API の将来の展開のオーバー ロードおよびその他の .NET API の設計概念 f# モジュール内では使用できませんの使用を許可するようにします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-375">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="ea14f-376">たとえば、次のパブリック API: の代わりに</span><span class="sxs-lookup"><span data-stu-id="ea14f-376">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="ea14f-377">代わりに検討してください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-377">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="ea14f-378">型のデザインが変化しない場合は、バニラ .NET Api で f# レコード型を使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-378">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="ea14f-379">F# のレコードの種類は、単純な .NET クラスにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-379">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="ea14f-380">これらは、一部の単純で安定した種類の Api に適しています。</span><span class="sxs-lookup"><span data-stu-id="ea14f-380">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="ea14f-381">使用を検討する必要があります、`[<NoEquality>]`と`[<NoComparison>]`属性のインターフェイスの自動生成を抑制します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-381">You should consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="ea14f-382">また、パブリック フィールドとしてこれらの公開バニラ .NET Api で変更可能なレコードのフィールドは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-382">Also avoid using mutable record fields in vanilla .NET APIs as these exposes a public field.</span></span> <span data-ttu-id="ea14f-383">常にクラスが、API の将来の進化をより柔軟なオプションを提供するかどうかを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-383">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="ea14f-384">たとえば、次の f# コードは、c# コンシューマーにパブリック API を公開します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-384">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="ea14f-385">F# の場合:</span><span class="sxs-lookup"><span data-stu-id="ea14f-385">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
```

<span data-ttu-id="ea14f-386">C#: </span><span class="sxs-lookup"><span data-stu-id="ea14f-386">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="ea14f-387">F# の共用体型バニラ .NET Api の形式を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-387">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="ea14f-388">F# 共用体型一般的に使用されないコンポーネントの境界を越えて f# であってに-f# コーディングします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-388">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="ea14f-389">これらは、コンポーネント、およびライブラリ内で内部的に使用するときに、優れた実装デバイスです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-389">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="ea14f-390">バニラ .NET API をデザインする場合は、プライベート宣言または署名ファイルを使用して、union 型の表現を非表示にすることを検討します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-390">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="ea14f-391">目的を提供する、メンバーを持つ共用体の表現を内部的に使用する型を追加することも可能性があります。ネットワークに接続された API です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-391">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="ea14f-392">GUI の設計やフレームワークのデザイン パターンを使用して他のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="ea14f-392">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="ea14f-393">多くのさまざまなフレームワークは WinForms、WPF では、ASP.NET などの .NET 内で使用できます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-393">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="ea14f-394">これらのフレームワークで使用するためのコンポーネントをデザインする場合は、それぞれの名前付けと設計の規則を使用してください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-394">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="ea14f-395">たとえば、WPF のプログラミングでは、WPF のパターンのデザインをデザインするクラスを採用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-395">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="ea14f-396">ユーザー インターフェイスのプログラミング モデルでは、イベントなどのデザイン パターンを使用しておりなどのコレクションの通知に基づく<xref:System.Collections.ObjectModel>です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-396">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="ea14f-397">オブジェクトとメンバーのデザイン (の他の .NET 言語から使用するライブラリ)</span><span class="sxs-lookup"><span data-stu-id="ea14f-397">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="ea14f-398">CLIEvent 属性を使用して、.NET イベントを公開するには</span><span class="sxs-lookup"><span data-stu-id="ea14f-398">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="ea14f-399">構築、`DelegateEvent`で特定の .NET デリゲート オブジェクトを取得する型と`EventArgs`(ではなく、 `Event`、使用する、`FSharpHandler`既定では型) を他の .NET 言語の使い慣れた方法でイベントが発行するためです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-399">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x:int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a><span data-ttu-id="ea14f-400">.NET のタスクを返すメソッドとしての非同期操作を公開します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-400">Expose asynchronous operations as methods which return .NET tasks</span></span>

<span data-ttu-id="ea14f-401">タスクは、アクティブな非同期計算を表す .NET で使用されます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-401">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="ea14f-402">タスクは、一般的な f# より小さいアレンジ`Async<T>`オブジェクト、タスクの「は既に実行中」を表すされ、並列の構成を実行するか、キャンセルの信号、およびその他の伝達を非表示にする方法で同時に構成することはできませんコンテキスト パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-402">Tasks are in general less compositional than F# `Async<T>` objects, since they represent “already executing” tasks and can’t be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="ea14f-403">ただし、この場合でもタスクを返すメソッドは .NET での非同期プログラミングの標準的な表現です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-403">However, despite this, methods which return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="ea14f-404">多くの場合も、明示的なキャンセル トークンをそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-404">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="ea14f-405">F# 関数型ではなく .NET 型のデリゲートを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-405">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="ea14f-406">ここで「f# 関数型」という意味では「矢印」型と同様に`int -> int`です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-406">Here “F# function types” mean “arrow” types like `int -> int`.</span></span>

<span data-ttu-id="ea14f-407">代わりにします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-407">Instead of this:</span></span>

```fsharp
member this.Transform(f:int->int) =
    ...
```

<span data-ttu-id="ea14f-408">方法 :</span><span class="sxs-lookup"><span data-stu-id="ea14f-408">Do this:</span></span>

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

<span data-ttu-id="ea14f-409">として f# 関数型が表示されます`class FSharpFunc<T,U>`他の .NET 言語にはデリゲート型を理解している言語機能とツールには適しています。</span><span class="sxs-lookup"><span data-stu-id="ea14f-409">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understand delegate types.</span></span> <span data-ttu-id="ea14f-410">.NET Framework 3.5 以降を対象とする上位のメソッドを作成するときに、`System.Func`と`System.Action`デリゲートは、低摩擦方法でこれらの Api を使用する .NET 開発者に公開する右の Api です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-410">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="ea14f-411">(.NET Framework 2.0 を対象とする場合、システム定義のデリゲート型は制限が多くなどの定義済みのデリゲート型の使用を検討`System.Converter<T,U>`または特定のデリゲート型を定義します)。</span><span class="sxs-lookup"><span data-stu-id="ea14f-411">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="ea14f-412">反対に、.NET のデリゲートが f# の自然な-ライブラリが直面している (f# で、次のセクションを参照してください-ライブラリが直面している)。</span><span class="sxs-lookup"><span data-stu-id="ea14f-412">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="ea14f-413">高階メソッドの標準の .NET ライブラリを開発するときに一般的な実装方法はすべて f# 関数型を使用して実装を作成し、実際の f# の最上部のシン ファサードとしてデリゲートを使用してパブリック API を作成、その結果、します。実装です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-413">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="ea14f-414">F# オプション値を返す代わりに、TryGetValue パターンを使用して、引数としての f# のオプション値を取得するメソッドのオーバー ロードを優先</span><span class="sxs-lookup"><span data-stu-id="ea14f-414">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="ea14f-415">Api で f# オプションの種類の使用の一般的なパターンの適切な標準の .NET を使用して .NET Api バニラに実装されている手法をデザインします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-415">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="ea14f-416">F# のオプションの値を返す代わりにブール型の戻り値の型と"TryGetValue"パターンと同様に out パラメーターを使用して検討してください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-416">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="ea14f-417">F# オプション値をパラメーターとして使用すると、代わりに、メソッドのオーバー ロードまたは省略可能な引数を使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-417">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal : byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x : int, y : int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x : int) = x

member this.ParamOverload(x : int, y : int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="ea14f-418">使用して、.NET コレクション インターフェイス型 IEnumerable\<T\>および IDictionary\<キー、値\>パラメーターと戻り値</span><span class="sxs-lookup"><span data-stu-id="ea14f-418">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="ea14f-419">.NET の配列などの具体的なコレクション型の使用を避ける`T[]`、f# の型`list<T>`、`Map<Key,Value>`と`Set<T>`などの .NET の具体的なコレクション型と`Dictionary<Key,Value>`です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-419">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="ea14f-420">.NET ライブラリのデザイン ガイドラインのようなさまざまなコレクション型を使用するに関する有益なアドバイスがある`IEnumerable<T>`です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-420">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="ea14f-421">配列の一部を使用して (`T[]`) は状況によっては、パフォーマンス grounds を許容します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-421">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="ea14f-422">特にことに注意してください`seq<T>`だけ、f# には別名が`IEnumerable<T>`、したがって seq は多くの場合、バニラ .NET API の適切な型とします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-422">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="ea14f-423">代わりに f# の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-423">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names : string list) =
    ...
```

<span data-ttu-id="ea14f-424">F# シーケンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-424">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="ea14f-425">引数を持たないメソッドを定義するメソッドの唯一の入力の型としてのユニットの種類を使用するか、唯一として void を返すメソッドを定義する型を返す</span><span class="sxs-lookup"><span data-stu-id="ea14f-425">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="ea14f-426">Unit 型の他の使用は避けてください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-426">Avoid other uses of the unit type.</span></span> <span data-ttu-id="ea14f-427">これらは、適切です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-427">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

<span data-ttu-id="ea14f-428">これは、正しくありません。</span><span class="sxs-lookup"><span data-stu-id="ea14f-428">This is bad:</span></span>

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="ea14f-429">標準の .NET API 境界での null 値を確認</span><span class="sxs-lookup"><span data-stu-id="ea14f-429">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="ea14f-430">F# 実装コードは、変更できないデザイン パターンと f# の型の null リテラルの使用上の制限のためより少ないの null 値を持つ傾向があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-430">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="ea14f-431">他の .NET 言語多くの場合、値として null より頻繁に使用します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-431">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="ea14f-432">このため、バニラ .NET API を公開する f# コードを API 境界で null のパラメーターをチェックし、これらの値が f# 実装コードをより深くをフローさせることを防止します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-432">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="ea14f-433">`isNull`関数またはパターンに一致する、`null`パターンを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-433">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="ea14f-434">戻り値としての組は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-434">Avoid using tuples as return values</span></span>

<span data-ttu-id="ea14f-435">代わりに、集計のデータを保持するか、out パラメーターを使用して複数の値を返す名前付きの型を返すことを好みます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-435">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="ea14f-436">組と構造体の組 .NET に存在して (c# の言語のサポート構造体の組を含む)、最もよくが用意されて理想的と予想される API .NET 開発者向けです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-436">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="ea14f-437">パラメーターのカリー化は使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="ea14f-437">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="ea14f-438">代わりに、呼び出し規約 .NET``Method(arg1,arg2,…,argN)``です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-438">Instead, use .NET calling conventions ``Method(arg1,arg2,…,argN)``.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="ea14f-439">ヒント: 任意の .NET 言語から使用するためのライブラリをデザインする場合はありません、実際にいくつか実験的な c# および Visual Basic プログラミングことを確認する「フィール右」これらの言語から、ライブラリの代用。</span><span class="sxs-lookup"><span data-stu-id="ea14f-439">Tip: If you’re designing libraries for use from any .NET language, then there’s no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="ea14f-440">また、ライブラリと、ドキュメントが開発者に期待どおりに表示されていることを確認するのに .NET Reflector や Visual Studio のオブジェクト ブラウザーなどのツールを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-440">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="ea14f-441">付録</span><span class="sxs-lookup"><span data-stu-id="ea14f-441">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="ea14f-442">他の .NET 言語で使用するために f# コードの設計のエンド ツー エンドの例</span><span class="sxs-lookup"><span data-stu-id="ea14f-442">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="ea14f-443">次のクラスを考えます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-443">Consider the following class:</span></span>

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

<span data-ttu-id="ea14f-444">このクラスの推定の f# 型は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-444">The inferred F# type of this class is as follows:</span></span>

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

<span data-ttu-id="ea14f-445">他の .NET 言語を使用するプログラマがこの f# 型の表示方法を見てをみましょう。</span><span class="sxs-lookup"><span data-stu-id="ea14f-445">Let’s take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="ea14f-446">たとえば、おおよそ c#「署名」とおりです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-446">For example, the approximate C# “signature” is as follows:</span></span>

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="ea14f-447">F# でどのように表すかコンストラクトをここで注目してくださいいくつかの重要な点があります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-447">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="ea14f-448">例えば:</span><span class="sxs-lookup"><span data-stu-id="ea14f-448">For example:</span></span>

* <span data-ttu-id="ea14f-449">引数の名前などのメタデータが保持されています。</span><span class="sxs-lookup"><span data-stu-id="ea14f-449">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="ea14f-450">2 つの引数を受け取る f# メソッドでは、c# のメソッドに 2 つの引数を受け取ることになります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-450">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="ea14f-451">関数および一覧は、対応する型が f# ライブラリへの参照になります。</span><span class="sxs-lookup"><span data-stu-id="ea14f-451">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="ea14f-452">次のコードでは、これらの点を考慮に入れるには、このコードを調整する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ea14f-452">The following code shows how to adjust this code to take these things into account.</span></span>

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

<span data-ttu-id="ea14f-453">コードの推定の f# 型は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-453">The inferred F# type of the code is as follows:</span></span>

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

<span data-ttu-id="ea14f-454">C# シグネチャを次に示しますようになりました。</span><span class="sxs-lookup"><span data-stu-id="ea14f-454">The C# signature is now as follows:</span></span>

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="ea14f-455">修正プログラムは、標準の .NET ライブラリの一部は、次のとおり、この型を使用する準備に対して行われます。</span><span class="sxs-lookup"><span data-stu-id="ea14f-455">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="ea14f-456">複数の名前を調整: `Point1`、 `n`、 `l`、および`f`になった`RadialPoint`、 `count`、 `factor`、および`transform`、それぞれします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-456">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="ea14f-457">戻り値の型を使用する`seq<RadialPoint>`の代わりに`RadialPoint list`一覧の構築を使用して、変更することによって`[ ... ]`を使用してシーケンスの構築に`IEnumerable<RadialPoint>`です。</span><span class="sxs-lookup"><span data-stu-id="ea14f-457">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="ea14f-458">.NET のデリゲート型を使用する`System.Func`f# 関数型の代わりにします。</span><span class="sxs-lookup"><span data-stu-id="ea14f-458">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="ea14f-459">これにより、c# コードで使用するより良いまでです。</span><span class="sxs-lookup"><span data-stu-id="ea14f-459">This makes it far nicer to consume in C# code.</span></span>
