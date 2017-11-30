---
title: "-refonly (C# コンパイラ オプション)"
ms.date: 07/08/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /refonly
helpviewer_keywords:
- /refonly compiler option [C#]
- -refonly compiler option [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4c745416bda56f5f1b1b4ab8267274d972a990d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="refonly-c-compiler-options"></a><span data-ttu-id="afc06-102">/refonly (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="afc06-102">/refonly (C# Compiler Options)</span></span>

<span data-ttu-id="afc06-103">**/Refonly**オプションは、参照アセンブリをプライマリ出力として、実装アセンブリではなく出力をすることを示します。</span><span class="sxs-lookup"><span data-stu-id="afc06-103">The **/refonly** option indicates that a reference assembly should be output instead of an implementation assembly, as the primary output.</span></span> <span data-ttu-id="afc06-104">`/refonly` パラメーターは、参照アセンブリを実行できない場合に、PDB の出力を暗黙的に無効にします。</span><span class="sxs-lookup"><span data-stu-id="afc06-104">The `/refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="afc06-105">構文</span><span class="sxs-lookup"><span data-stu-id="afc06-105">Syntax</span></span>

```console
/refonly
```

## <a name="remarks"></a><span data-ttu-id="afc06-106">コメント</span><span class="sxs-lookup"><span data-stu-id="afc06-106">Remarks</span></span>

<span data-ttu-id="afc06-107">メタデータのみアセンブリには、1 つの `throw null` 本体で置き換えられたメソッド本体がありますが、匿名型を除くすべてのメンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="afc06-107">Metadata-only assemblies have their method bodies replaced with a single `throw null` body, but include all members except anonymous types.</span></span> <span data-ttu-id="afc06-108">(本体なしではなく) `throw null` 本体を使用する理由は、PEVerify を実行して渡せるようにするためです (そのためにメタデータの完全性を検証します)。</span><span class="sxs-lookup"><span data-stu-id="afc06-108">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="afc06-109">参照アセンブリには、アセンブリ レベルの `ReferenceAssembly` 属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="afc06-109">Reference assemblies include an assembly-level `ReferenceAssembly` attribute.</span></span> <span data-ttu-id="afc06-110">この属性は、ソースで指定できます (指定すると、コンパイラではこれを合成する必要がなくなります)。</span><span class="sxs-lookup"><span data-stu-id="afc06-110">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="afc06-111">この属性により、ランタイムで実行のための参照アセンブリの読み込みが拒否されます (ただし、リフレクションのみモードでは読み込むことができます)。</span><span class="sxs-lookup"><span data-stu-id="afc06-111">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in reflection-only mode).</span></span> <span data-ttu-id="afc06-112">アセンブリにリフレクションするツールでは、参照アセンブリをリフレクションのみで読み込んでいることを確認する必要があります。そうでない場合、ランタイムから typeload エラーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="afc06-112">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only, otherwise they will receive a typeload error from the runtime.</span></span>

<span data-ttu-id="afc06-113">参照アセンブリは、メタデータのみアセンブリからさらにメタデータ (プライベート メンバー) を削除します。</span><span class="sxs-lookup"><span data-stu-id="afc06-113">Reference assemblies further remove metadata (private members) from metadata-only assemblies:</span></span>

- <span data-ttu-id="afc06-114">参照アセンブリには、API サーフェスでそれが必要とする参照のみがあります。</span><span class="sxs-lookup"><span data-stu-id="afc06-114">A reference assembly only has references for what it needs in the API surface.</span></span> <span data-ttu-id="afc06-115">実際のアセンブリには、特定の実装に関連するその他の参照がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="afc06-115">The real assembly may have additional references related to specific implementations.</span></span> <span data-ttu-id="afc06-116">たとえば、`class C { private void M() { dynamic d = 1; ... } }` の参照アセンブリは、`dynamic` に必要などの型も参照しません。</span><span class="sxs-lookup"><span data-stu-id="afc06-116">For instance, the reference assembly for `class C { private void M() { dynamic d = 1; ... } }` does not reference any types required for `dynamic`.</span></span>
- <span data-ttu-id="afc06-117">プライベート関数のメンバー (メソッド、プロパティ、およびイベント) は、それらの削除がコンパイルに著しい影響を与えない場合に削除されます。</span><span class="sxs-lookup"><span data-stu-id="afc06-117">Private function-members (methods, properties, and events) are removed in cases where their removal doesn't observably impact compilation.</span></span> <span data-ttu-id="afc06-118">`InternalsVisibleTo` 属性がない場合、内部関数メンバーに同じことを行います。</span><span class="sxs-lookup"><span data-stu-id="afc06-118">If there are no `InternalsVisibleTo` attributes, do the same for internal function-members.</span></span>
- <span data-ttu-id="afc06-119">ただし、すべての型 (プライベートまたは入れ子になった型を含む) は参照アセンブリで保持されます。</span><span class="sxs-lookup"><span data-stu-id="afc06-119">But all types (including private or nested types) are kept in reference assemblies.</span></span> <span data-ttu-id="afc06-120">すべての属性が (内部属性も) 保持されます。</span><span class="sxs-lookup"><span data-stu-id="afc06-120">All attributes are kept (even internal ones).</span></span>
- <span data-ttu-id="afc06-121">すべての仮想メソッドが保持されます。</span><span class="sxs-lookup"><span data-stu-id="afc06-121">All virtual methods are kept.</span></span> <span data-ttu-id="afc06-122">明示的なインターフェイスの実装が保持されます。</span><span class="sxs-lookup"><span data-stu-id="afc06-122">Explicit interface implementations are kept.</span></span> <span data-ttu-id="afc06-123">明示的に実装されたプロパティとイベントが保持されます (これらのアクセサーが仮想のため保持されます)。</span><span class="sxs-lookup"><span data-stu-id="afc06-123">Explicitly implemented properties and events are kept, as their accessors are virtual (and are therefore kept).</span></span>
- <span data-ttu-id="afc06-124">構造体のすべてのフィールドが保持されます </span><span class="sxs-lookup"><span data-stu-id="afc06-124">All fields of a struct are kept.</span></span> <span data-ttu-id="afc06-125">(これは、post-C#-7.1 絞り込みの候補です)。</span><span class="sxs-lookup"><span data-stu-id="afc06-125">(This is a candidate for post-C#-7.1 refinement)</span></span>

<span data-ttu-id="afc06-126">`/refonly` オプションと [`/refout`](refout-compiler-option.md) オプションは同時に指定できません。</span><span class="sxs-lookup"><span data-stu-id="afc06-126">The `/refonly` and [`/refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="afc06-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="afc06-127">See also</span></span>
 [<span data-ttu-id="afc06-128">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="afc06-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="afc06-129">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="afc06-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
