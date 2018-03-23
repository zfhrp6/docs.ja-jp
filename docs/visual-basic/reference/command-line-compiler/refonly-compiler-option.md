---
title: refonly (Visual Basic)
ms.date: 03/16/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5135ef4d33ddde27416e48c28425aa5b029237b
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/23/2018
---
# <a name="-refonly-visual-basic"></a><span data-ttu-id="cc63e-102">refonly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc63e-102">-refonly (Visual Basic)</span></span>

<span data-ttu-id="cc63e-103">**- Refonly**オプションは、コンパイル時のプライマリ出力が、実装のアセンブリではなく参照アセンブリであることを示します。</span><span class="sxs-lookup"><span data-stu-id="cc63e-103">The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly.</span></span> <span data-ttu-id="cc63e-104">`-refonly` パラメーターは、参照アセンブリを実行できない場合に、PDB の出力を暗黙的に無効にします。</span><span class="sxs-lookup"><span data-stu-id="cc63e-104">The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.</span></span>

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a><span data-ttu-id="cc63e-105">構文</span><span class="sxs-lookup"><span data-stu-id="cc63e-105">Syntax</span></span>

```console
-refonly
```

## <a name="remarks"></a><span data-ttu-id="cc63e-106">コメント</span><span class="sxs-lookup"><span data-stu-id="cc63e-106">Remarks</span></span>

<span data-ttu-id="cc63e-107">Visual Basic のサポート、`-refout`バージョン 15.3 と開始を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="cc63e-107">Visual Basic supports the `-refout` switch starting with version 15.3.</span></span>

<span data-ttu-id="cc63e-108">参照アセンブリはメタデータ コードではなく実装が含まれているメタデータのみのアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="cc63e-108">Reference assemblies are metadata-only assemblies that contain metadata but no implementation code.</span></span> <span data-ttu-id="cc63e-109">匿名型を除くすべての型およびメンバーの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc63e-109">They include type and member information for everything except anonymous types.</span></span> <span data-ttu-id="cc63e-110">(本体なしではなく) `throw null` 本体を使用する理由は、PEVerify を実行して渡せるようにするためです (そのためにメタデータの完全性を検証します)。</span><span class="sxs-lookup"><span data-stu-id="cc63e-110">The reason for using `throw null` bodies (as opposed to no bodies) is so that PEVerify could run and pass (thus validating the completeness of the metadata).</span></span>

<span data-ttu-id="cc63e-111">参照アセンブリは、アセンブリ レベル[ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute)属性。</span><span class="sxs-lookup"><span data-stu-id="cc63e-111">Reference assemblies include an assembly-level [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) attribute.</span></span> <span data-ttu-id="cc63e-112">この属性は、ソースで指定できます (指定すると、コンパイラではこれを合成する必要がなくなります)。</span><span class="sxs-lookup"><span data-stu-id="cc63e-112">This attribute may be specified in source (then the compiler won't need to synthesize it).</span></span> <span data-ttu-id="cc63e-113">この属性のためのランタイムが実行の参照アセンブリの読み込みが拒否されます (ただしリフレクション専用コンテキストに読み込まれていることができます)。</span><span class="sxs-lookup"><span data-stu-id="cc63e-113">Because of this attribute, runtimes will refuse to load reference assemblies for execution (but they can still be loaded in a reflection-only context).</span></span> <span data-ttu-id="cc63e-114">アセンブリに反映するためのツールは、リフレクション専用として参照アセンブリが読み込まれることを確認する必要があります。それ以外の場合、ランタイム、<xref:System.BadImageFormatException>です。</span><span class="sxs-lookup"><span data-stu-id="cc63e-114">Tools that reflect on assemblies need to ensure they load reference assemblies as reflection-only; otherwise, the runtime throws a <xref:System.BadImageFormatException>.</span></span>

<span data-ttu-id="cc63e-115">`-refonly` オプションと [`-refout`](refout-compiler-option.md) オプションは同時に指定できません。</span><span class="sxs-lookup"><span data-stu-id="cc63e-115">The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc63e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc63e-116">See also</span></span>
<span data-ttu-id="cc63e-117">[-refout](refout-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="cc63e-117">[-refout](refout-compiler-option.md) </span></span>  
[<span data-ttu-id="cc63e-118">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="cc63e-118">Visual Basic Command-Line Compiler</span></span>](index.md)  
[<span data-ttu-id="cc63e-119">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="cc63e-119">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)   
