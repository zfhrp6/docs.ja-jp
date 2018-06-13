---
title: -refonly (C# コンパイラ オプション)
ms.date: 07/08/2017
f1_keywords:
- /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
- refonly compiler option [C#]
ms.openlocfilehash: c380df1cb473fcd187e56bb0a338a909dd3ac894
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217348"
---
# <a name="-refonly-c-compiler-options"></a><span data-ttu-id="286b1-102">-refonly (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="286b1-102">-refonly (C# Compiler Options)</span></span>

<span data-ttu-id="286b1-103">**-refonly** オプションは、実装アセンブリではなく、参照アセンブリをプライマリ出力として出力することを示します。</span><span class="sxs-lookup"><span data-stu-id="286b1-103">The **-refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="286b1-104">`-refonly` パラメーターは、参照アセンブリを実行できない場合に、PDB の出力を暗黙的に無効にします。</span><span class="sxs-lookup"><span data-stu-id="286b1-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="286b1-105">構文</span><span class="sxs-lookup"><span data-stu-id="286b1-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="286b1-106">コメント</span><span class="sxs-lookup"><span data-stu-id="286b1-106">Remarks</span></span>

<span data-ttu-id="286b1-107">メタデータのみアセンブリには、1 つの `throw null` 本体で置き換えられたメソッド本体がありますが、匿名型を除くすべてのメンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="286b1-107">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="286b1-108">(本体なしではなく) `throw null` 本体を使用する理由は、PEVerify を実行して渡せるようにするためです (そのためにメタデータの完全性を検証します)。</span><span class="sxs-lookup"><span data-stu-id="286b1-108">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="286b1-109">参照アセンブリには、アセンブリ レベルの `ReferenceAssembly` 属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="286b1-109">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="286b1-110">この属性は、ソースで指定できます (指定すると、コンパイラではこれを合成する必要がなくなります)。</span><span class="sxs-lookup"><span data-stu-id="286b1-110">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="286b1-111">この属性により、ランタイムで実行のための参照アセンブリの読み込みが拒否されます (ただし、リフレクションのみモードでは読み込むことができます)。</span><span class="sxs-lookup"><span data-stu-id="286b1-111">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="286b1-112">アセンブリにリフレクションするツールでは、参照アセンブリをリフレクションのみで読み込んでいることを確認する必要があります。そうでない場合、ランタイムから typeload エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="286b1-112">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="286b1-113">参照アセンブリは、メタデータのみアセンブリからさらにメタデータ (プライベート メンバー) を削除します。</span><span class="sxs-lookup"><span data-stu-id="286b1-113">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="286b1-114">参照アセンブリには、API サーフェスでそれが必要とする参照のみがあります。</span><span class="sxs-lookup"><span data-stu-id="286b1-114">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="286b1-115">実際のアセンブリには、特定の実装に関連するその他の参照がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="286b1-115">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="286b1-116">たとえば、`class C { private void M() { dynamic d = 1; ... } }` の参照アセンブリは、`dynamic` に必要などの型も参照しません。</span><span class="sxs-lookup"><span data-stu-id="286b1-116">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="286b1-117">プライベート関数のメンバー (メソッド、プロパティ、およびイベント) は、それらの削除がコンパイルに著しい影響を与えない場合に削除されます。</span><span class="sxs-lookup"><span data-stu-id="286b1-117">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="286b1-118">`InternalsVisibleTo` 属性がない場合、内部関数メンバーに同じことを行います。</span><span class="sxs-lookup"><span data-stu-id="286b1-118">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="286b1-119">ただし、すべての型 (プライベートまたは入れ子になった型を含む) は参照アセンブリで保持されます。</span><span class="sxs-lookup"><span data-stu-id="286b1-119">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="286b1-120">すべての属性が (内部属性も) 保持されます。</span><span class="sxs-lookup"><span data-stu-id="286b1-120">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="286b1-121">すべての仮想メソッドが保持されます。</span><span class="sxs-lookup"><span data-stu-id="286b1-121">All virtual methods are kept.</span></span> <span data-ttu-id="286b1-122">明示的なインターフェイスの実装が保持されます。</span><span class="sxs-lookup"><span data-stu-id="286b1-122">Explicit interface implementations are kept.</span></span> <span data-ttu-id="286b1-123">明示的に実装されたプロパティとイベントが保持されます (これらのアクセサーが仮想のため保持されます)。</span><span class="sxs-lookup"><span data-stu-id="286b1-123">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="286b1-124">構造体のすべてのフィールドが保持されます </span><span class="sxs-lookup"><span data-stu-id="286b1-124">All fields of a struct are kept.</span></span> <span data-ttu-id="286b1-125">(これは、post-C#-7.1 絞り込みの候補です)。</span><span class="sxs-lookup"><span data-stu-id="286b1-125">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="286b1-126">`-refonly` オプションと [`-refout`](refout-compiler-option.md) オプションは同時に指定できません。</span><span class="sxs-lookup"><span data-stu-id="286b1-126">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="286b1-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="286b1-127">See also</span></span>
 [<span data-ttu-id="286b1-128">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="286b1-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="286b1-129">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="286b1-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
