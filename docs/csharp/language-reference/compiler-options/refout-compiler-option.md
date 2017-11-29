---
title: "/refout (C# コンパイラ オプション)"
ms.date: 08/08/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /refout
helpviewer_keywords:
- refout compiler option [C#]
- /refout compiler option [C#]
- -refout compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc78165fc8f273948111c174ae0bf0af6591a8ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="refout-c-compiler-options"></a><span data-ttu-id="13e44-102">/refout (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="13e44-102">/refout (C# Compiler Options)</span></span>

<span data-ttu-id="13e44-103">**/refout** オプションは、参照アセンブリを出力するファイル パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="13e44-103">The **/refout** option specifies a file path where the reference assembly should be output.</span></span> <span data-ttu-id="13e44-104">Emit API では、これを `metadataPeStream` に変換します。</span><span class="sxs-lookup"><span data-stu-id="13e44-104">This translates to `metadataPeStream` in the Emit API.</span></span>

## <a name="syntax"></a><span data-ttu-id="13e44-105">構文</span><span class="sxs-lookup"><span data-stu-id="13e44-105">Syntax</span></span>

```console
/refout:filepath
```

## <a name="arguments"></a><span data-ttu-id="13e44-106">引数</span><span class="sxs-lookup"><span data-stu-id="13e44-106">Arguments</span></span>

 <span data-ttu-id="13e44-107">`filepath` 参照アセンブリのファイル パス。</span><span class="sxs-lookup"><span data-stu-id="13e44-107">`filepath` The filepath for the reference assembly.</span></span> <span data-ttu-id="13e44-108">通常はプライマリ アセンブリのファイルパスと一致します。</span><span class="sxs-lookup"><span data-stu-id="13e44-108">It should generally match that of the primary assembly.</span></span> <span data-ttu-id="13e44-109">(MSBuild で使用される) 推奨規則は、プライマリ アセンブリに相対する "ref/" サブ フォルダー内に参照アセンブリを配置することです。</span><span class="sxs-lookup"><span data-stu-id="13e44-109">The recommended convention (used by MSBuild) is to place the reference assembly in a "ref/" sub-folder relative to the primary assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="13e44-110">コメント</span><span class="sxs-lookup"><span data-stu-id="13e44-110">Remarks</span></span>

<span data-ttu-id="13e44-111">メタデータのみアセンブリには、1 つの `throw null` 本体で置き換えられたメソッド本体がありますが、匿名型を除くすべてのメンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="13e44-111">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="13e44-112">(本体なしではなく) `throw null` 本体を使用する理由は、PEVerify を実行して渡せるようにするためです (そのためにメタデータの完全性を検証します)。</span><span class="sxs-lookup"><span data-stu-id="13e44-112">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="13e44-113">参照アセンブリには、アセンブリ レベルの `ReferenceAssembly` 属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="13e44-113">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="13e44-114">この属性は、ソースで指定できます (指定すると、コンパイラではこれを合成する必要がなくなります)。</span><span class="sxs-lookup"><span data-stu-id="13e44-114">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="13e44-115">この属性により、ランタイムで実行のための参照アセンブリの読み込みが拒否されます (ただし、リフレクションのみモードでは読み込むことができます)。</span><span class="sxs-lookup"><span data-stu-id="13e44-115">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="13e44-116">アセンブリにリフレクションするツールでは、参照アセンブリをリフレクションのみで読み込んでいることを確認する必要があります。そうでない場合、ランタイムから typeload エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="13e44-116">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="13e44-117">参照アセンブリは、メタデータのみアセンブリからさらにメタデータ (プライベート メンバー) を削除します。</span><span class="sxs-lookup"><span data-stu-id="13e44-117">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="13e44-118">参照アセンブリには、API サーフェスでそれが必要とする参照のみがあります。</span><span class="sxs-lookup"><span data-stu-id="13e44-118">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="13e44-119">実際のアセンブリには、特定の実装に関連するその他の参照がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="13e44-119">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="13e44-120">たとえば、`class C { private void M() { dynamic d = 1; ... } }` の参照アセンブリは、`dynamic` に必要などの型も参照しません。</span><span class="sxs-lookup"><span data-stu-id="13e44-120">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="13e44-121">プライベート関数のメンバー (メソッド、プロパティ、およびイベント) は、それらの削除がコンパイルに著しい影響を与えない場合に削除されます。</span><span class="sxs-lookup"><span data-stu-id="13e44-121">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="13e44-122">`InternalsVisibleTo` 属性がない場合、内部関数メンバーに同じことを行います。</span><span class="sxs-lookup"><span data-stu-id="13e44-122">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="13e44-123">ただし、すべての型 (プライベートまたは入れ子になった型を含む) は参照アセンブリで保持されます。</span><span class="sxs-lookup"><span data-stu-id="13e44-123">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="13e44-124">すべての属性が (内部属性も) 保持されます。</span><span class="sxs-lookup"><span data-stu-id="13e44-124">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="13e44-125">すべての仮想メソッドが保持されます。</span><span class="sxs-lookup"><span data-stu-id="13e44-125">All virtual methods are kept.</span></span> <span data-ttu-id="13e44-126">明示的なインターフェイスの実装が保持されます。</span><span class="sxs-lookup"><span data-stu-id="13e44-126">Explicit interface implementations are kept.</span></span> <span data-ttu-id="13e44-127">明示的に実装されたプロパティとイベントが保持されます (これらのアクセサーが仮想のため保持されます)。</span><span class="sxs-lookup"><span data-stu-id="13e44-127">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="13e44-128">構造体のすべてのフィールドが保持されます </span><span class="sxs-lookup"><span data-stu-id="13e44-128">All fields of a struct are kept.</span></span> <span data-ttu-id="13e44-129">(これは、post-C#-7.1 絞り込みの候補です)。</span><span class="sxs-lookup"><span data-stu-id="13e44-129">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="13e44-130">`/refout` オプションと [`/refonly`](refonly-compiler-option.md) オプションは同時に指定できません。</span><span class="sxs-lookup"><span data-stu-id="13e44-130">The `/refout` and [`/refonly`](refonly-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="13e44-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="13e44-131">See Also</span></span>
 [<span data-ttu-id="13e44-132">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="13e44-132">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="13e44-133">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="13e44-133">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
