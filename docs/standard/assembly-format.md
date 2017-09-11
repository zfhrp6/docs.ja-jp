---
title: ".NET アセンブリ ファイルの形式"
description: ".NET アプリおよびライブラリを記述する場合や含める場合に使用する .NET アセンブリ ファイル形式について説明します。"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.translationtype: HT
ms.sourcegitcommit: 934373d61407c8cc19b7d6424898a582880f9c21
ms.openlocfilehash: 47e895274f6d400639878e0bd5c700e04b554ce5
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---

# <a name="net-assembly-file-format"></a><span data-ttu-id="7530d-104">.NET アセンブリ ファイルの形式</span><span class="sxs-lookup"><span data-stu-id="7530d-104">.NET Assembly File Format</span></span>

<span data-ttu-id="7530d-105">.NET では、.NET プログラムの完全な記述と格納に使用するバイナリ ファイル形式として、"アセンブリ" が定義されています。</span><span class="sxs-lookup"><span data-stu-id="7530d-105">.NET defines a binary file format - "assembly" - that is used to fully-describe and contain .NET programs.</span></span> <span data-ttu-id="7530d-106">アセンブリは、プログラム自体と同様に従属ライブラリにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="7530d-106">Assemblies are used for the programs themselves as well as any dependent libraries.</span></span> <span data-ttu-id="7530d-107">.NET プログラムは、適切な .NET 実装以外の成果物を必要とせずに、1 つ以上のアセンブリとして実行できます。</span><span class="sxs-lookup"><span data-stu-id="7530d-107">A .NET program can be executed as one of more assemblies, with no other required artifacts, beyond the appropriate .NET implementation.</span></span> <span data-ttu-id="7530d-108">ネイティブの依存関係 (オペレーティング システム API を含む) は別の考慮事項であり、.NET アセンブリの形式には存在しません。ただし、この形式を使用して記述されることがあります (たとえば WinRT)。</span><span class="sxs-lookup"><span data-stu-id="7530d-108">Native dependencies, including operating system APIs, are a separate concern and are not contained within the .NET assembly format, although are sometimes described with this format (for example, WinRT).</span></span>

> <span data-ttu-id="7530d-109">各 CLI コンポーネントには、そのコンポーネントに固有の宣言、実装、参照のためのメタデータが含まれます。</span><span class="sxs-lookup"><span data-stu-id="7530d-109">Each CLI component carries the metadata for declarations, implementations, and references specific to that component.</span></span> <span data-ttu-id="7530d-110">そのため、コンポーネント固有のメタデータはコンポーネント メタデータと呼ばれ、結果として得られるコンポーネントは自己記述と呼ばれます (ECMA 335 I.9.1 のコンポーネントおよびアセンブリの仕様)。</span><span class="sxs-lookup"><span data-stu-id="7530d-110">Therefore, the component-specific metadata is referred to as component metadata, and the resulting component is said to be self-describing – from ECMA 335 I.9.1, Components and assemblies.</span></span>

<span data-ttu-id="7530d-111">この形式は ECMA 335 として仕様が完全に指定され、標準化されています。</span><span class="sxs-lookup"><span data-stu-id="7530d-111">The format is fully specified and standardized as ECMA 335.</span></span> <span data-ttu-id="7530d-112">すべての .NET コンパイラとランタイムが、この形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="7530d-112">All .NET compilers and runtimes use this format.</span></span> <span data-ttu-id="7530d-113">ドキュメント化された、更新が頻繁でないバイナリ形式の存在は、相互運用性の面で大きなメリットであり、ほぼ間違いなく必要条件になっています。</span><span class="sxs-lookup"><span data-stu-id="7530d-113">The presence of a documented and infrequently updated binary format has been a major benefit (arguably a requirement) for interoperatibility.</span></span> <span data-ttu-id="7530d-114">この形式が最後に実質的な方法で更新されたのは 2005 年 (.NET 2.0) で、ジェネリックやプロセッサ アーキテクチャに対応するための変更が行われました。</span><span class="sxs-lookup"><span data-stu-id="7530d-114">The format was last updated in a substantive way in 2005 (.NET 2.0) to accommodate generics and processor architecture.</span></span>

<span data-ttu-id="7530d-115">この形式は CPU や OS に依存しません。</span><span class="sxs-lookup"><span data-stu-id="7530d-115">The format is CPU- and OS-agnostic.</span></span> <span data-ttu-id="7530d-116">多くのチップや CPU を対象にした .NET 実装の一部として使用されています。</span><span class="sxs-lookup"><span data-stu-id="7530d-116">It has been used as part of .NET implementations that target many chips and CPUs.</span></span> <span data-ttu-id="7530d-117">この形式自体は Windows で開発された経緯がありますが、任意のオペレーティング システムに実装できます。</span><span class="sxs-lookup"><span data-stu-id="7530d-117">While the format itself has Windows heritage, it is implementable on any operating system.</span></span> <span data-ttu-id="7530d-118">OS の相互運用性にかかわる、この形式の最も重要なオプションと言えるのは、ほとんどの値をリトル エンディアン形式で格納することです。</span><span class="sxs-lookup"><span data-stu-id="7530d-118">It’s arguably most significant choice for OS interoperability is that most values are stored in little-endian format.</span></span> <span data-ttu-id="7530d-119">コンピューターのポインター サイズ (32 ビット、64 ビットなど) に対する特定の関係はありません。</span><span class="sxs-lookup"><span data-stu-id="7530d-119">It doesn’t have a specific affinity to machine pointer size (for example, 32-bit, 64-bit).</span></span>

<span data-ttu-id="7530d-120">.NET アセンブリ形式は、特定のプログラムまたはライブラリの構造をとてもわかりやすく記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="7530d-120">The .NET assembly format is also very descriptive about the structure of a given program or library.</span></span> <span data-ttu-id="7530d-121">アセンブリの内部コンポーネント、具体的にはアセンブリ参照や定義済みの型とそれらの内部構造を記述します。</span><span class="sxs-lookup"><span data-stu-id="7530d-121">It describes the internal components of an assembly, specifically: assembly references and types defined and their internal structure.</span></span> <span data-ttu-id="7530d-122">ツールまたは API で表示のためにこの情報の読み取り、処理を行ったり、プログラムによる決定を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7530d-122">Tools or APIs can read and process this information for display or to make programmatic decisions.</span></span>

## <a name="format"></a><span data-ttu-id="7530d-123">形式</span><span class="sxs-lookup"><span data-stu-id="7530d-123">Format</span></span>

<span data-ttu-id="7530d-124">.NET バイナリ形式は、Windows [PE ファイル](http://en.wikipedia.org/wiki/Portable_Executable)形式に基づいています。</span><span class="sxs-lookup"><span data-stu-id="7530d-124">The .NET binary format is based on the Windows [PE file](http://en.wikipedia.org/wiki/Portable_Executable) format.</span></span> <span data-ttu-id="7530d-125">実際には、.NET クラス ライブラリは Windows PE に準拠し、Windows ダイナミック リンク ライブラリ (DLL) またはアプリケーション実行可能ファイル (EXE) のように見えます。</span><span class="sxs-lookup"><span data-stu-id="7530d-125">In fact, .NET class libraries are conformant Windows PEs, and appear on first glance to be Windows dynamic link libraries (DLLs) or application executables (EXEs).</span></span> <span data-ttu-id="7530d-126">これは Windows 上でとても便利な特性であり、ネイティブな実行可能バイナリのように偽装して、実行可能バイナリと同じように扱うことができます (OS ロード、PE ツールなど)。</span><span class="sxs-lookup"><span data-stu-id="7530d-126">This is a very useful characteristic on Windows, where they can masquerade as native executable binaries and get some of the same treatment (for example, OS load, PE tools).</span></span>

![アセンブリ ヘッダー](./media/assembly-format/assembly-headers.png)

<span data-ttu-id="7530d-128">ECMA 335 II.25.1 のランタイム ファイル形式の構造に基づくアセンブリ ヘッダー。</span><span class="sxs-lookup"><span data-stu-id="7530d-128">Assembly Headers from ECMA 335 II.25.1, Structure of the runtime file format.</span></span>

## <a name="processing-the-assemblies"></a><span data-ttu-id="7530d-129">アセンブリの処理</span><span class="sxs-lookup"><span data-stu-id="7530d-129">Processing the Assemblies</span></span>

<span data-ttu-id="7530d-130">アセンブリを処理するツールや API を記述することができます。</span><span class="sxs-lookup"><span data-stu-id="7530d-130">It is possible to write tools or APIs to process assemblies.</span></span> <span data-ttu-id="7530d-131">アセンブリ情報を使用して、実行時のプログラムによる決定、アセンブリの書き換え、エディターでの API IntelliSense の提供、ドキュメントの生成ができます。</span><span class="sxs-lookup"><span data-stu-id="7530d-131">Assembly information enables making programmatic decisions at runtime, re-writing assemblies, providing API IntelliSense in an editor and generating documentation.</span></span> <span data-ttu-id="7530d-132"><xref:System.Reflection?displayProperty=fullName> と [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) は、この目的によく使われるツールの好例です。</span><span class="sxs-lookup"><span data-stu-id="7530d-132"><xref:System.Reflection?displayProperty=fullName> and [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) are good examples of tools that are frequently used for this purpose.</span></span>

