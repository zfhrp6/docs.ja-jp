---
title: .NET クラス ライブラリ
description: .NET クラス ライブラリを使用して、役に立つ機能をモジュールとしてコンポーネント化して、複数のアプリケーションで使用する方法について説明します。
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a67484c3-fe92-44d8-8fa3-36fa2071d880
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8f7c421d2490678f7122e78bc0b83ebf3a1aa9ea
ms.sourcegitcommit: 15316053918995cc1380163a7d7e7edd5c44e6d7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2018
---
# <a name="net-class-libraries"></a><span data-ttu-id="24212-104">.NET クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="24212-104">.NET Class Libraries</span></span>

<span data-ttu-id="24212-105">クラス ライブラリは、.NET の[共有ライブラリ](http://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries)の概念です。</span><span class="sxs-lookup"><span data-stu-id="24212-105">Class libraries are the [shared library](http://en.wikipedia.org/wiki/Library_%28computing%29#Shared_libraries) concept for .NET.</span></span> <span data-ttu-id="24212-106">クラス ライブラリを使用すると、役に立つ機能をモジュールとしてコンポーネント化して、複数のアプリケーションで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="24212-106">They enable you to componentize useful functionality into modules that can be used by multiple applications.</span></span> <span data-ttu-id="24212-107">また、アプリケーションの起動時には不要または認識されない機能を読み込むための手段としても使用できます。</span><span class="sxs-lookup"><span data-stu-id="24212-107">They can also be used as a means of loading functionality that is not needed or not known at application startup.</span></span> <span data-ttu-id="24212-108">クラス ライブラリは、[.NET アセンブリ ファイルの形式](assembly-format.md)を使用して記述されます。</span><span class="sxs-lookup"><span data-stu-id="24212-108">Class libraries are described using the [.NET Assembly file format](assembly-format.md).</span></span>

<span data-ttu-id="24212-109">次の 3 種類のクラス ライブラリを使用できます。</span><span class="sxs-lookup"><span data-stu-id="24212-109">There are three types of class libraries that you can use:</span></span>

*   <span data-ttu-id="24212-110">**プラットフォーム固有** クラス ライブラリは、特定のプラットフォーム (たとえば、.NET Framework、Xamarin iOS) のすべての API にアクセスできますが、そのプラットフォームを対象とするアプリケーションとライブラリでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="24212-110">**Platform-specific** class libraries have access to all the APIs in a given platform (for example, .NET Framework, Xamarin iOS), but can only be used by apps and libraries that target that platform.</span></span>
*   <span data-ttu-id="24212-111">**ポータブル** クラス ライブラリは、API のサブセットへのアクセスがあり、複数のプラットフォームを対象とするアプリケーションとライブラリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="24212-111">**Portable** class libraries have access to a subset of APIs, and can be used by apps and libraries that target multiple platforms.</span></span>
*   <span data-ttu-id="24212-112">**.NET Standard** クラス ライブラリは、プラットフォーム固有のライブラリとポータブル ライブラリの概念を両方の長所を持つ 1 つのモデルに統合しています。</span><span class="sxs-lookup"><span data-stu-id="24212-112">**.NET Standard** class libraries are a merger of the platform-specific and portable library concept into a single model that provides the best of both.</span></span>

## <a name="platform-specific-class-libraries"></a><span data-ttu-id="24212-113">プラットフォーム固有のクラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="24212-113">Platform-specific Class Libraries</span></span>

<span data-ttu-id="24212-114">プラットフォーム固有のライブラリは 1 つの .NET 実装 (たとえば、Windows 上の .NET Framework) にバインドされるため、既知の 1 つの実行環境に大きく依存する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="24212-114">Platform-specific libraries are bound to a single .NET implementation (for example, .NET Framework on Windows) and can therefore take significant dependencies on a known execution environment.</span></span> <span data-ttu-id="24212-115">そのような環境は既知の API のセット (.NET および OS API) を公開し、予想される状態 (Windows レジストリ) を維持および公開します。</span><span class="sxs-lookup"><span data-stu-id="24212-115">Such an environment will expose a known set of APIs (.NET and OS APIs) and will maintain and expose expected state (for example, Windows registry).</span></span>

<span data-ttu-id="24212-116">プラットフォーム固有のライブラリを作成する開発者は、基になるプラットフォームのすべての機能を利用できます。</span><span class="sxs-lookup"><span data-stu-id="24212-116">Developers who create platform specific libraries can fully exploit the underlying platform.</span></span> <span data-ttu-id="24212-117">このライブラリは特定のプラットフォーム上でのみ実行されるので、プラットフォームの確認や他の形式の条件付きコードの確認は必要ありません (複数プラットフォーム用のモジュール単一ソース コード)。</span><span class="sxs-lookup"><span data-stu-id="24212-117">The libraries will only ever run on that given platform, making platform checks or other forms of conditional code unnecessary (modulo single sourcing code for multiple platforms).</span></span>

<span data-ttu-id="24212-118">プラットフォーム固有のライブラリは、 .NET Framework のプライマリ クラス ライブラリの種類です。</span><span class="sxs-lookup"><span data-stu-id="24212-118">Platform-specific libraries have been the primary class library type for the .NET Framework.</span></span> <span data-ttu-id="24212-119">他の .NET 実装が登場しても、プラットフォーム固有のライブラリは、基準となるライブラリの種類として残っています。</span><span class="sxs-lookup"><span data-stu-id="24212-119">Even as other .NET implementations emerged, platform-specific libraries remained the dominant library type.</span></span>

## <a name="portable-class-libraries"></a><span data-ttu-id="24212-120">ポータブル クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="24212-120">Portable Class Libraries</span></span>

<span data-ttu-id="24212-121">ポータブル ライブラリは、複数の .NET 実装でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="24212-121">Portable libraries are supported on multiple .NET implementations.</span></span> <span data-ttu-id="24212-122">このライブラリは、既知の実行環境に依存することは同じですが、その環境は、完全な .NET 実装のセットの共通部分によって生成されます。</span><span class="sxs-lookup"><span data-stu-id="24212-122">They can still take dependencies on a known execution environment, however, the environment is a synthetic one that is generated by the intersection of a set of concrete .NET implementations.</span></span> <span data-ttu-id="24212-123">つまり、公開される API およびプラットフォームの前提は、プラットフォーム固有のライブラリで使用できる機能のサブセットです。</span><span class="sxs-lookup"><span data-stu-id="24212-123">This means that exposed APIs and platform assumptions are a subset of what would be available to a platform-specific library.</span></span>

<span data-ttu-id="24212-124">ポータブル ライブラリを作成するときに、プラットフォームの構成を選択します。</span><span class="sxs-lookup"><span data-stu-id="24212-124">You choose a platform configuration when you create a portable library.</span></span> <span data-ttu-id="24212-125">これらはサポートする必要があるプラットフォーム (たとえば、.NET Framework 4.5 以降、Windows Phone 8.0 以降) のセットです。</span><span class="sxs-lookup"><span data-stu-id="24212-125">These are the set of platforms that you need to support (for example, .NET Framework 4.5+, Windows Phone 8.0+).</span></span> <span data-ttu-id="24212-126">サポートするプラットフォームが増えるほど、想定可能な API とプラットフォームが減り、共通分母が最小になります。</span><span class="sxs-lookup"><span data-stu-id="24212-126">The more platforms you opt to support, the fewer APIs and fewer platform assumptions you can make, the lowest common denominator.</span></span> <span data-ttu-id="24212-127">このような特性は、最初は混乱を招くことがあります。ユーザーは多くの場合、「多いほどよい」と考えますが、結果はサポートするプラットフォームが増えるほど、使用可能な API は少なくなります。</span><span class="sxs-lookup"><span data-stu-id="24212-127">This characteristic can be confusing at first, since people often think "more is better", but find that more supported platforms results in fewer available APIs.</span></span>

<span data-ttu-id="24212-128">多くのライブラリ開発者は、1 つのソースから複数のプラットフォーム固有のライブラリを生成する方法 (条件付きコンパイル ディレクティブを使用) からポータブル ライブラリに切り替えています。</span><span class="sxs-lookup"><span data-stu-id="24212-128">Many library developers have switched from producing multiple platform-specific libraries from one source (using conditional compilation directives) to portable libraries.</span></span> <span data-ttu-id="24212-129">ポータブル ライブラリ内のプラットフォーム固有の機能にアクセスする[方法はいくつか](http://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html)あります。現時点で最も広く採用されている手法は、[bait-and-switch](http://log.paulbetts.org/the-bait-and-switch-pcl-trick/) です。</span><span class="sxs-lookup"><span data-stu-id="24212-129">There are [several approaches](http://blog.stephencleary.com/2012/11/portable-class-library-enlightenment.html) for accessing platform-specific functionality within portable libraries, with [bait-and-switch](http://log.paulbetts.org/the-bait-and-switch-pcl-trick/) being the most widely accepted technique at this point.</span></span>

### <a name="net-standard-class-libraries"></a><span data-ttu-id="24212-130">.NET Standard クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="24212-130">.NET Standard Class Libraries</span></span>

<span data-ttu-id="24212-131">.NET Standard ライブラリは、プラットフォームに固有のライブラリおよびポータブル ライブラリの概念に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="24212-131">.NET Standard libraries are a replacement of the platform-specific and portable libraries concepts.</span></span> <span data-ttu-id="24212-132">これらは、基になるプラットフォームのすべての機能を公開するという意味でプラットフォーム固有です (統合プラットフォームまたはプラットフォームの交差はありません)。</span><span class="sxs-lookup"><span data-stu-id="24212-132">They are platform-specific in the sense that they expose all functionality from the underlying platform (no synthetic platforms or platform intersections).</span></span> <span data-ttu-id="24212-133">これらは、すべてのサポートされるプラットフォーム上で機能するという意味でポータブルです。</span><span class="sxs-lookup"><span data-stu-id="24212-133">They are portable in the sense that they work on all supporting platforms.</span></span>

<span data-ttu-id="24212-134">.NET Standard は、ライブラリ _コントラクト_のセットを公開しています。</span><span class="sxs-lookup"><span data-stu-id="24212-134">The .NET Standard exposes a set of library _contracts_.</span></span> <span data-ttu-id="24212-135">.NET 実装は、各コントラクトを完全にサポートするか、またはまったくサポートしない必要があります。</span><span class="sxs-lookup"><span data-stu-id="24212-135">.NET implementations must support each contract fully or not at all.</span></span> <span data-ttu-id="24212-136">そのため、各実装は .NET Standard コントラクトのセットをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="24212-136">Each implementation, therefore, supports a set of .NET Standard contracts.</span></span> <span data-ttu-id="24212-137">当然の結果として、各 .NET Standard クラス ライブラリは、コントラクトの依存関係をサポートするプラットフォームでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="24212-137">The corollary is that each .NET Standard class library is supported on the platforms that support it’s contract dependencies.</span></span>

<span data-ttu-id="24212-138">.NET Standard は、.NET Framework のすべての機能を公開していません (それが目的でもありません)。ただし、ポータブル クラス ライブラリよりも多くの API を公開しています。</span><span class="sxs-lookup"><span data-stu-id="24212-138">The .NET Standard does not expose the entire functionality of the .NET Framework (nor is that a goal), however, they do expose many more APIs than Portable Class Libraries.</span></span> <span data-ttu-id="24212-139">時間の経過と共にさらに API が追加されます。</span><span class="sxs-lookup"><span data-stu-id="24212-139">More APIs will be added over time.</span></span>

<span data-ttu-id="24212-140">次のプラットフォームは、.NET Standard ライブラリをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="24212-140">The following platforms support .NET Standard libraries:</span></span>

* <span data-ttu-id="24212-141">.NET Core</span><span class="sxs-lookup"><span data-stu-id="24212-141">.NET Core</span></span>
* <span data-ttu-id="24212-142">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="24212-142">.NET Framework</span></span>
* <span data-ttu-id="24212-143">Mono</span><span class="sxs-lookup"><span data-stu-id="24212-143">Mono</span></span>
* <span data-ttu-id="24212-144">Xamarin.iOS、Xamarin.Mac、Xamarin.Android</span><span class="sxs-lookup"><span data-stu-id="24212-144">Xamarin.iOS, Xamarin.Mac, Xamarin.Android</span></span>
* <span data-ttu-id="24212-145">ユニバーサル Windows プラットフォーム (UWP)</span><span class="sxs-lookup"><span data-stu-id="24212-145">Universal Windows Platform (UWP)</span></span>
* <span data-ttu-id="24212-146">Windows</span><span class="sxs-lookup"><span data-stu-id="24212-146">Windows</span></span>
* <span data-ttu-id="24212-147">Windows Phone</span><span class="sxs-lookup"><span data-stu-id="24212-147">Windows Phone</span></span>
* <span data-ttu-id="24212-148">Windows Phone Silverlight</span><span class="sxs-lookup"><span data-stu-id="24212-148">Windows Phone Silverlight</span></span>

<span data-ttu-id="24212-149">詳細については、「[.NET Standard](net-standard.md)」トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="24212-149">For more information, see the [.NET Standard](net-standard.md) topic.</span></span>

### <a name="mono-class-libraries"></a><span data-ttu-id="24212-150">Mono クラス ライブラリ</span><span class="sxs-lookup"><span data-stu-id="24212-150">Mono Class Libraries</span></span>

<span data-ttu-id="24212-151">クラス ライブラリは、上記の 3 種類のライブラリを含む Mono 上でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="24212-151">Class libraries are supported on Mono, including the three types of libraries described above.</span></span> <span data-ttu-id="24212-152">多くの場合、Mono は、Microsoft .NET Framework のクロスプラット フォームの実装として (正しく) 確認されています。</span><span class="sxs-lookup"><span data-stu-id="24212-152">Mono has often been seen (correctly) as a cross-platform implementation of the Microsoft .NET Framework.</span></span> <span data-ttu-id="24212-153">これは、部分的には、プラットフォーム固有の .NET Framework ライブラリを変更や再コンパイルせずに Mono ランタイム上で実行できたためです。</span><span class="sxs-lookup"><span data-stu-id="24212-153">In part, this was because platform-specific .NET Framework libraries could run on the Mono runtime without modification or recompilation.</span></span> <span data-ttu-id="24212-154">このような特徴は、ポータブル クラス ライブラリの作成前に見られたので、NET Framework と Mono の間でバイナリを移植できるようにすることが当然の選択肢でした。</span><span class="sxs-lookup"><span data-stu-id="24212-154">This characteristic was in place before the creation of portable class libraries, so was an obvious choice to enable binary portability between the .NET Framework and Mono (although it only worked in one direction).</span></span>
