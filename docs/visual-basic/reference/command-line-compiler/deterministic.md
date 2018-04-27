---
title: -決定論的
ms.date: 04/11/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 273abf8811f04cd7f58599ce3421ca1f17c740d9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="-deterministic"></a><span data-ttu-id="94458-102">-決定論的</span><span class="sxs-lookup"><span data-stu-id="94458-102">-deterministic</span></span>

<span data-ttu-id="94458-103">コンパイラで同じ入力に対してコンパイルの間でバイトの出力が同じアセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="94458-103">Causes the compiler to produce an assembly whose byte-for-byte output is identical across compilations for identical inputs.</span></span> 

## <a name="syntax"></a><span data-ttu-id="94458-104">構文</span><span class="sxs-lookup"><span data-stu-id="94458-104">Syntax</span></span>

```
-deterministic
```

## <a name="remarks"></a><span data-ttu-id="94458-105">コメント</span><span class="sxs-lookup"><span data-stu-id="94458-105">Remarks</span></span>

<span data-ttu-id="94458-106">既定では、コンパイラは、タイムスタンプおよびランダムな数値から生成される GUID を付加するための入力の特定のセットからコンパイラ出力が一意で。</span><span class="sxs-lookup"><span data-stu-id="94458-106">By default, compiler output from a given set of inputs is unique, since the compiler adds a timestamp and a GUID that is generated from random numbers.</span></span> <span data-ttu-id="94458-107">使用する、`-deterministic`を生成するオプション、*決定的アセンブリ*、1 つの入力が同じ限り、バイナリ コンテンツを持つはコンパイルの間で同じです。</span><span class="sxs-lookup"><span data-stu-id="94458-107">You use the `-deterministic` option to produce a *deterministic assembly*, one whose binary content is identical across compilations as long as the input remains the same.</span></span>

<span data-ttu-id="94458-108">コンパイラは、決定性のために、次の入力を検討します。</span><span class="sxs-lookup"><span data-stu-id="94458-108">The compiler considers the following inputs for the purpose of determinism:</span></span>

- <span data-ttu-id="94458-109">コマンド ライン パラメーターのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="94458-109">The sequence of command-line parameters.</span></span>
- <span data-ttu-id="94458-110">コンパイラの .rsp 応答ファイルの内容。</span><span class="sxs-lookup"><span data-stu-id="94458-110">The contents of the compiler's .rsp response file.</span></span>
- <span data-ttu-id="94458-111">これを使用すると、コンパイラの正確なバージョンとその参照先のアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="94458-111">The precise version of the compiler used, and its referenced assemblies.</span></span>
- <span data-ttu-id="94458-112">現在のディレクトリ パス。</span><span class="sxs-lookup"><span data-stu-id="94458-112">The current directory path.</span></span>
- <span data-ttu-id="94458-113">すべてのファイルのバイナリ コンテンツを明示的に渡すコンパイラに直接または間接的になど。</span><span class="sxs-lookup"><span data-stu-id="94458-113">The binary contents of all files explicitly passed to the compiler either directly or indirectly, including:</span></span> 
    - <span data-ttu-id="94458-114">ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="94458-114">Source files</span></span>
    - <span data-ttu-id="94458-115">参照アセンブリ</span><span class="sxs-lookup"><span data-stu-id="94458-115">Referenced assemblies</span></span>
    - <span data-ttu-id="94458-116">参照されるモジュール</span><span class="sxs-lookup"><span data-stu-id="94458-116">Referenced modules</span></span>
    - <span data-ttu-id="94458-117">リソース</span><span class="sxs-lookup"><span data-stu-id="94458-117">Resources</span></span>
    - <span data-ttu-id="94458-118">厳密な名前キー ファイル</span><span class="sxs-lookup"><span data-stu-id="94458-118">The strong name key file</span></span>
    - <span data-ttu-id="94458-119">応答ファイルの @</span><span class="sxs-lookup"><span data-stu-id="94458-119">@ response files</span></span>
    - <span data-ttu-id="94458-120">アナライザー</span><span class="sxs-lookup"><span data-stu-id="94458-120">Analyzers</span></span>
    - <span data-ttu-id="94458-121">Ruleset</span><span class="sxs-lookup"><span data-stu-id="94458-121">Rulesets</span></span>
    - <span data-ttu-id="94458-122">アナライザーが使用できる追加のファイル</span><span class="sxs-lookup"><span data-stu-id="94458-122">Additional files that may be used by analyzers</span></span>
- <span data-ttu-id="94458-123">(診断および例外のメッセージが生成される言語) の現在のカルチャ。</span><span class="sxs-lookup"><span data-stu-id="94458-123">The current culture (for the language in which diagnostics and exception messages are produced).</span></span>
- <span data-ttu-id="94458-124">既定のエンコーディングなど、現在のコード ページ エンコーディングが指定されていない場合。</span><span class="sxs-lookup"><span data-stu-id="94458-124">The default encoding (or the current code page) if the encoding is not specified.</span></span>
- <span data-ttu-id="94458-125">存在、非存在、およびコンパイラの検索パス上のファイルの内容 (などにより、指定した`/lib`または`/recurse`)。</span><span class="sxs-lookup"><span data-stu-id="94458-125">The existence, non-existence, and contents of files on the compiler's search paths (specified, for example, by `/lib` or `/recurse`).</span></span>
- <span data-ttu-id="94458-126">コンパイラを実行する CLR プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="94458-126">The CLR platform on which the compiler is run.</span></span>
- <span data-ttu-id="94458-127">値`%LIBPATH%`、アナライザー依存関係の読み込みに影響することができます。</span><span class="sxs-lookup"><span data-stu-id="94458-127">The value of `%LIBPATH%`, which can affect analyzer dependency loading.</span></span>

<span data-ttu-id="94458-128">ソースがパブリックに使用できる場合は、信頼できるソースからバイナリがコンパイルされたかどうかを確立するため決定論的コンパイルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="94458-128">When sources are publicly available, deterministic compilation can be used for establishing whether a binary is compiled from a trusted source.</span></span> <span data-ttu-id="94458-129">継続的なビルド システム バイナリへの変更に依存するビルド ステップを実行する必要があるかどうかを決定するために役立つことができます。</span><span class="sxs-lookup"><span data-stu-id="94458-129">It can also be useful in a continuous build system for determining whether build steps that are dependent on changes to a binary need to be executed.</span></span> 

## <a name="see-also"></a><span data-ttu-id="94458-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="94458-130">See Also</span></span>
[<span data-ttu-id="94458-131">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="94458-131">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
[<span data-ttu-id="94458-132">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="94458-132">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
