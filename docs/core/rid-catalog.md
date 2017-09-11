---
title: ".NET Core のランタイム識別子 (RID) のカタログ"
description: "ランタイム識別子 (RID) と .NET Core での RID の使用方法について説明します。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 08/22/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b2032f5d-771f-48d9-917c-587d9509035c
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3490fb639efd223dc36190324bdf3a06bc23c10e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="net-core-runtime-identifier-rid-catalog"></a><span data-ttu-id="9be5a-104">.NET Core のランタイム識別子 (RID) のカタログ</span><span class="sxs-lookup"><span data-stu-id="9be5a-104">.NET Core Runtime IDentifier (RID) catalog</span></span>

## <a name="what-are-rids"></a><span data-ttu-id="9be5a-105">RID とは何か。</span><span class="sxs-lookup"><span data-stu-id="9be5a-105">What are RIDs?</span></span>
<span data-ttu-id="9be5a-106">RID は*ランタイム識別子*の略です。</span><span class="sxs-lookup"><span data-stu-id="9be5a-106">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="9be5a-107">RID は、アプリケーションやアセット (つまり、アセンブリ) が実行されるターゲット オペレーティング システムを特定するために利用されます。</span><span class="sxs-lookup"><span data-stu-id="9be5a-107">RIDs are used to identify target operating systems where an application or asset (that is, assembly) will run.</span></span> <span data-ttu-id="9be5a-108">"ubuntu.14.04-x64"、"win7-x64"、"osx.10.11-x64" のような識別子です。</span><span class="sxs-lookup"><span data-stu-id="9be5a-108">They look like this: "ubuntu.14.04-x64", "win7-x64", "osx.10.11-x64".</span></span> <span data-ttu-id="9be5a-109">ネイティブ依存関係のあるパッケージの場合、パッケージを復元できるプラットフォームが指定されます。</span><span class="sxs-lookup"><span data-stu-id="9be5a-109">For the packages with native dependencies, it will designate on which platforms the package can be restored.</span></span> 

<span data-ttu-id="9be5a-110">重要なことですが、RID は不透明な文字列です。</span><span class="sxs-lookup"><span data-stu-id="9be5a-110">It is important to note that RIDs are really opaque strings.</span></span> <span data-ttu-id="9be5a-111">つまり、それを利用する操作に適合する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9be5a-111">This means that they have to match exactly for operations using them to work.</span></span> <span data-ttu-id="9be5a-112">たとえば、[Elementary OS](https://elementary.io/) の場合を考えてみます。これは Ubuntu 14.04 の単純なクローンです。</span><span class="sxs-lookup"><span data-stu-id="9be5a-112">As an example, let us consider the case of [Elementary OS](https://elementary.io/), which is a straightforward clone of Ubuntu 14.04.</span></span> <span data-ttu-id="9be5a-113">.NET Core と CLI はこのバージョンの Ubuntu の上で動作しますが、変更せずに Elementary OS の上で使用すると、パッケージの復元に失敗します。</span><span class="sxs-lookup"><span data-stu-id="9be5a-113">Although .NET Core and CLI work on top of that version of Ubuntu, if you try to use them on Elementary OS without any modifications, the restore operation for any package will fail.</span></span> <span data-ttu-id="9be5a-114">これは、現在のところ、Elementary OS をプラットフォームとして指名する RID がないためです。</span><span class="sxs-lookup"><span data-stu-id="9be5a-114">This is because we currently don't have a RID that designates Elementary OS as a platform.</span></span> 

<span data-ttu-id="9be5a-115">具体的なオペレーティング システムを表す RID は通常、`[os].[version]-[arch]` のようなパターンになります。それぞれ、次のような意味があります。</span><span class="sxs-lookup"><span data-stu-id="9be5a-115">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[arch]` where:</span></span>
- <span data-ttu-id="9be5a-116">`[os]` はオペレーティング システムのモニカー (`ubuntu` など) です。</span><span class="sxs-lookup"><span data-stu-id="9be5a-116">`[os]` is the operating system moniker, for example, `ubuntu`.</span></span>
- <span data-ttu-id="9be5a-117">`[version]` は、バージョン番号をドット (`.`) で区切った形式のオペレーティング システムのバージョンです (例: `15.10`)。厳密な番号であり、これを利用することで、アセットはそのバージョンで表されるオペレーティング システム プラットフォーム API をターゲットにできます。</span><span class="sxs-lookup"><span data-stu-id="9be5a-117">`[version]` is the operating system version in the form of a dot (`.`) separated version number, for example, `15.10`, accurate enough to reasonably enable assets to target operating system platform APIs represented by that version.</span></span>
  - <span data-ttu-id="9be5a-118">これをマーケティング バージョンに**しないでください**。プラットフォーム API の表面が異なる、個別バージョンの複数のオペレーティング システムを表すことがあるためです。</span><span class="sxs-lookup"><span data-stu-id="9be5a-118">This **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>
- <span data-ttu-id="9be5a-119">`[arch]` はプロセッサ アーキテクチャです (例: `x86`、`x64`、`arm`、`arm64`)。</span><span class="sxs-lookup"><span data-stu-id="9be5a-119">`[arch]` is the processor architecture, for example, `x86`, `x64`, `arm`, `arm64`, etc.</span></span>

<span data-ttu-id="9be5a-120">RID グラフは「`runtime.json`」という名前のファイルに入っている「`Microsoft.NETCore.Platforms`」という名前のパッケージに定義されています。これは [CoreFX リポジトリ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="9be5a-120">The RID graph is defined in a package called `Microsoft.NETCore.Platforms` in a file called `runtime.json`, which you can see on the [CoreFX repo](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json).</span></span> <span data-ttu-id="9be5a-121">このファイルを使用する場合、RID の一部に `"#import"` ステートメントが与えられます。</span><span class="sxs-lookup"><span data-stu-id="9be5a-121">If you use this file, you will notice that some of the RIDs have an `"#import"` statement in them.</span></span> <span data-ttu-id="9be5a-122">それらのステートメントは互換性ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="9be5a-122">These statements are compatibility statements.</span></span> <span data-ttu-id="9be5a-123">つまり、インポートした RID を含む RID はその RID のパッケージを復元するためのターゲットになります。</span><span class="sxs-lookup"><span data-stu-id="9be5a-123">That means that a RID that has an imported RID in it can be a target for restoring packages for that RID.</span></span> <span data-ttu-id="9be5a-124">少しわかりにくいですが、例を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="9be5a-124">Slightly confusing, but let's look at an example.</span></span> <span data-ttu-id="9be5a-125">macOS の例:</span><span class="sxs-lookup"><span data-stu-id="9be5a-125">Let's take a look at macOS:</span></span>

```json
"osx.10.11-x64": {
    "#import": [ "osx.10.11", "osx.10.10-x64" ]
}
```
<span data-ttu-id="9be5a-126">上の RID は `osx.10.11-x64` が `osx.10.10-x64` をインポートすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="9be5a-126">The above RID specifies that `osx.10.11-x64` imports `osx.10.10-x64`.</span></span> <span data-ttu-id="9be5a-127">つまり、パッケージを復元するとき、`osx.10.10-x64` を `osx.10.11-x64` で必要とすることを指定するパッケージを NuGet で復元できます。</span><span class="sxs-lookup"><span data-stu-id="9be5a-127">This means that when restoring packages, NuGet will be able to restore packages that specify that they need `osx.10.10-x64` on `osx.10.11-x64`.</span></span>

<span data-ttu-id="9be5a-128">少し大きくした RID グラフの例:</span><span class="sxs-lookup"><span data-stu-id="9be5a-128">A slightly bigger example RID graph:</span></span>  

- `win10-arm`
  - `win10`
  - `win81-arm`
    - `win81`
    - `win8-arm`
      - `win8`
        - `win7`
          - `win`
            - `any`

<span data-ttu-id="9be5a-129">すべての RID は最終的にルート `any` RID にマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="9be5a-129">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="9be5a-130">使用は簡単に見えますが、RID にはいくつか特別な条件があり、使用時にはそれに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9be5a-130">Although they look easy enough to use, there are some special things about RIDs that you have to keep in mind when working with them:</span></span>

* <span data-ttu-id="9be5a-131">**不透明な文字列**であり、ブラック ボックスとして処理する必要があります</span><span class="sxs-lookup"><span data-stu-id="9be5a-131">They are **opaque strings** and should be treated as black boxes</span></span>
    * <span data-ttu-id="9be5a-132">RID をプログラミングで構築することはできません</span><span class="sxs-lookup"><span data-stu-id="9be5a-132">You should not construct RIDs programmatically</span></span>
* <span data-ttu-id="9be5a-133">プラットフォームに既に定義されている RID を使用する必要があり、それは本書で説明するとおりです</span><span class="sxs-lookup"><span data-stu-id="9be5a-133">You need to use the RIDs that are already defined for the platform and this document shows that</span></span>
* <span data-ttu-id="9be5a-134">RID は限定する必要がなく、実際の RID 値からは何も推測しないでください (特定のプラットフォームに必要な RID については本書を参照してください)</span><span class="sxs-lookup"><span data-stu-id="9be5a-134">The RIDs do need to be specific so don't assume anything from the actual RID value; please consult this document to determine which RID(s) you need for a given platform</span></span>

## <a name="using-rids"></a><span data-ttu-id="9be5a-135">RID の使用</span><span class="sxs-lookup"><span data-stu-id="9be5a-135">Using RIDs</span></span>
<span data-ttu-id="9be5a-136">RID を使用するには、どのような RID があるのか知る必要があります</span><span class="sxs-lookup"><span data-stu-id="9be5a-136">In order to use RIDs, you have to know which RIDs there are.</span></span> <span data-ttu-id="9be5a-137">プラットフォームには新しい RID が定期的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="9be5a-137">New RIDs are added regularly to the platform.</span></span> <span data-ttu-id="9be5a-138">最新バージョンについては、CoreFX リポジトリの [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) ファイルをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9be5a-138">For the latest version, please check the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

> [!NOTE]
> <span data-ttu-id="9be5a-139">この情報をよりインタラクティブな形式にするために取り組んでいます。</span><span class="sxs-lookup"><span data-stu-id="9be5a-139">We are working towards getting this information into a more interactive form.</span></span> <span data-ttu-id="9be5a-140">それが実現した際には、このページを更新し、そのツールと使用方法が記載されたドキュメントを紹介します。</span><span class="sxs-lookup"><span data-stu-id="9be5a-140">When that happens, this page will be updated to point to that tool and/or its usage documentation.</span></span> 

## <a name="windows-rids"></a><span data-ttu-id="9be5a-141">Windows RID</span><span class="sxs-lookup"><span data-stu-id="9be5a-141">Windows RIDs</span></span>

* <span data-ttu-id="9be5a-142">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="9be5a-142">Windows 7 / Windows Server 2008 R2</span></span>
    * `win7-x64`
    * `win7-x86`
* <span data-ttu-id="9be5a-143">Windows 8 / Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="9be5a-143">Windows 8 / Windows Server 2012</span></span>
    * `win8-x64`
    * `win8-x86`
    * `win8-arm`
* <span data-ttu-id="9be5a-144">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="9be5a-144">Windows 8.1 / Windows Server 2012 R2</span></span>
    * `win81-x64`
    * `win81-x86`
    * `win81-arm`
* <span data-ttu-id="9be5a-145">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="9be5a-145">Windows 10 / Windows Server 2016</span></span>
    * `win10-x64`
    * `win10-x86`
    * `win10-arm`
    * `win10-arm64`

## <a name="linux-rids"></a><span data-ttu-id="9be5a-146">Linux RID</span><span class="sxs-lookup"><span data-stu-id="9be5a-146">Linux RIDs</span></span>

* <span data-ttu-id="9be5a-147">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="9be5a-147">Red Hat Enterprise Linux</span></span>
    * `rhel.7-x64`
* <span data-ttu-id="9be5a-148">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9be5a-148">Ubuntu</span></span>
    * `ubuntu.14.04-x64`
    * `ubuntu.14.10-x64`
    * `ubuntu.15.04-x64`
    * `ubuntu.15.10-x64`
    * `ubuntu.16.04-x64`
    * `ubuntu.16.10-x64`
* <span data-ttu-id="9be5a-149">CentOS</span><span class="sxs-lookup"><span data-stu-id="9be5a-149">CentOS</span></span>
    * `centos.7-x64`
* <span data-ttu-id="9be5a-150">Debian</span><span class="sxs-lookup"><span data-stu-id="9be5a-150">Debian</span></span>
    * `debian.8-x64`
* <span data-ttu-id="9be5a-151">Fedora</span><span class="sxs-lookup"><span data-stu-id="9be5a-151">Fedora</span></span>
    * `fedora.23-x64`
    * `fedora.24-x64`
* <span data-ttu-id="9be5a-152">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="9be5a-152">OpenSUSE</span></span>
    * `opensuse.13.2-x64`
    * `opensuse.42.1-x64`
* <span data-ttu-id="9be5a-153">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="9be5a-153">Oracle Linux</span></span>
    * `ol.7-x64`
    * `ol.7.0-x64`
    * `ol.7.1-x64`
    * `ol.7.2-x64`
* <span data-ttu-id="9be5a-154">現在サポートされている Ubuntu 派生製品</span><span class="sxs-lookup"><span data-stu-id="9be5a-154">Currently supported Ubuntu derivatives</span></span> 
    * `linuxmint.17-x64`
    * `linuxmint.17.1-x64`
    * `linuxmint.17.2-x64`
    * `linuxmint.17.3-x64`
    * `linuxmint.18-x64`

## <a name="os-x-rids"></a><span data-ttu-id="9be5a-155">OS X RID</span><span class="sxs-lookup"><span data-stu-id="9be5a-155">OS X RIDs</span></span>

* `osx.10.10-x64`
* `osx.10.11-x64`
* `osx.10.12-x64`

