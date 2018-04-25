---
title: .NET Standard の新機能
description: この記事では、.NET Standard の新しいバージョンごとに、組み込まれた新機能と機能強化をまとめます。
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.prod: .net
ms.topic: article
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 13efc4a927d744662ba8d2e1210d5f8fc166a472
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="7d0b0-103">.NET Standard の新機能</span><span class="sxs-lookup"><span data-stu-id="7d0b0-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="7d0b0-104">.NET Standard は、バージョン管理されており、各バージョンの標準に準拠した .NET 実装で利用できる必要がある一連の API が定義された正式な仕様です。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="7d0b0-105">.NET Standard はライブラリ開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="7d0b0-106">あるバージョンの .NET Standard をターゲットとするライブラリは、そのバージョンの標準をサポートする .NET Framework、.NET Core、または Xamarin 実装で使用できます。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="7d0b0-107">.NET Standard の最新バージョンは 2.0 です。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="7d0b0-108">.NET Core 2.0 SDK に加えて、.NET Core ワークロードがインストールされた Visual Studio 2017 Version 15.3 にも含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="7d0b0-109">サポートされている .NET 実装</span><span class="sxs-lookup"><span data-stu-id="7d0b0-109">Supported .NET implementations</span></span>

<span data-ttu-id="7d0b0-110">.NET Standard 2.0 は、次の .NET 実装でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="7d0b0-111">.NET Core 2.0 以降</span><span class="sxs-lookup"><span data-stu-id="7d0b0-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="7d0b0-112">.NET Framework 4.6.1 以降</span><span class="sxs-lookup"><span data-stu-id="7d0b0-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="7d0b0-113">Mono 5.4 以降</span><span class="sxs-lookup"><span data-stu-id="7d0b0-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="7d0b0-114">Xamarin.iOS 10.14 以降</span><span class="sxs-lookup"><span data-stu-id="7d0b0-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="7d0b0-115">Xamarin.Mac 3.8 以降</span><span class="sxs-lookup"><span data-stu-id="7d0b0-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="7d0b0-116">Xamarin.Android 8.0 以降</span><span class="sxs-lookup"><span data-stu-id="7d0b0-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="7d0b0-117">ユニバーサル Windows プラットフォーム 10.0.16299 以降</span><span class="sxs-lookup"><span data-stu-id="7d0b0-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="7d0b0-118">.NET Standard 2.0 の新機能</span><span class="sxs-lookup"><span data-stu-id="7d0b0-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="7d0b0-119">.NET Standard 2.0 には、次の新機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="7d0b0-120">大幅に拡張された一連の API</span><span class="sxs-lookup"><span data-stu-id="7d0b0-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="7d0b0-121">.NET Standard バージョン 1.6 には、比較的少数の API が含まれました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="7d0b0-122">除外された API の中には、.NET Framework または Xamarin で一般的に使用されていた多くの API がありました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="7d0b0-123">その結果、複数の .NET 実装をターゲットとするアプリケーションやライブラリを開発する場合に、使い慣れた API に適した代替のものを開発者が見つけなければならないので、開発は複雑になります。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="7d0b0-124">.NET Standard 2.0 では、以前のバージョンの標準である .NET Standard 1.6 で使用できる API に 20,000 個を超える API を追加して、この制限に対処しています。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="7d0b0-125">.NET Standard 2.0 に追加された API の一覧については、「[.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)」(.NET Standard 2.0 と 1.6) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="7d0b0-126">.NET Standard 2.0 の <xref:System> 名前空間には、以下のような追加がありました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="7d0b0-127"><xref:System.AppDomain> クラスのサポート。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="7d0b0-128"><xref:System.Array> クラスに追加されたメンバーの配列操作のサポートを改善しました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="7d0b0-129"><xref:System.Attribute> クラスに追加されたメンバーの属性操作のサポートを改善しました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="7d0b0-130">カレンダーのサポートを改善し、<xref:System.DateTime> 値の書式設定オプションを追加しました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="7d0b0-131"><xref:System.Decimal> の丸め処理機能を追加しました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="7d0b0-132"><xref:System.Environment> クラスの機能を追加しました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="7d0b0-133"><xref:System.GC> クラスによるガベージ コレクターの制御を強化しました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="7d0b0-134"><xref:System.String> クラスの文字列の比較、列挙、正規化のサポートを強化しました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="7d0b0-135"><xref:System.TimeZoneInfo.AdjustmentRule> クラスと <xref:System.TimeZoneInfo.TransitionTime> クラスでの夏時間の調整および移行時間のサポート。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="7d0b0-136"><xref:System.Type> クラスの機能が大幅に強化されました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="7d0b0-137"><xref:System.Runtime.Serialization.SerializationInfo> および <xref:System.Runtime.Serialization.StreamingContext> パラメーターを使用する例外コンストラクターを追加することで、例外オブジェクトの逆シリアル化のサポートを改善しました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="7d0b0-138">.NET Framework ライブラリのサポート</span><span class="sxs-lookup"><span data-stu-id="7d0b0-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="7d0b0-139">大部分のライブラリは、.NET Standard ではなく .NET Framework をターゲットとしています。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="7d0b0-140">ただし、このようなライブラリの呼び出しのほとんどは、.NET Standard 2.0 に含まれている API に対する呼び出しです。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="7d0b0-141">.NET Standard 2.0 以降、[互換性 shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification) を使用して .NET Standard ライブラリから .NET Framework ライブラリにアクセスできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="7d0b0-142">この互換レイヤーは開発者に対して透過的です。 .NET Framework ライブラリを利用するために必要なことはありません。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="7d0b0-143">唯一の要件は、.NET Framework クラス ライブラリから呼び出される API が .NET Standard 2.0 に含まれている必要があることです。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="7d0b0-144">Visual Basic のサポート</span><span class="sxs-lookup"><span data-stu-id="7d0b0-144">Support for Visual Basic</span></span>

<span data-ttu-id="7d0b0-145">Visual Basic で .NET Standard ライブラリを開発できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="7d0b0-146">.NET Core ワークロードがインストールされた Visual Studio 2017 Version 15.3 以降を使用している Visual Basic 開発者向けに、Visual Studio には .NET Standard Class Library テンプレートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-146">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="7d0b0-147">他の開発ツールと環境を使用している Visual Basic 開発者の場合、[dotnet new](../../core/tools/dotnet-new.md) コマンドを使用して .NET Standard ライブラリ プロジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="7d0b0-148">詳細については、「[.NET Standard ライブラリのツールのサポート](#tooling-support-for-net-standard-libraries)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="7d0b0-149">.NET Standard ライブラリのツールのサポート</span><span class="sxs-lookup"><span data-stu-id="7d0b0-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="7d0b0-150">.NET Core 2.0 と .NET Standard 2.0 がリリースされ、Visual Studio 2017 と [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) には .NET Standard ライブラリの作成をサポートするツールが追加されました。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="7d0b0-151">**.NET Core クロスプラットフォーム開発**ワークロードを使用して Visual Studio をインストールする場合は、次の図に示すように、プロジェクト テンプレートを使用して .NET Standard 2.0 ライブラリ プロジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="7d0b0-152">C#</span><span class="sxs-lookup"><span data-stu-id="7d0b0-152">C#</span></span>](#tab/csharp)

![新しい .NET Standard ライブラリ プロジェクトを追加する](./media/std-project-cs.png)

<span data-ttu-id="7d0b0-154">.NET Core CLI を使用している場合、次の [dotnet new](../../core/tools/dotnet-new.md) コマンドを実行すると、.NET Standard 2.0 をターゲットとするクラス ライブラリ プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="7d0b0-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d0b0-155">Visual Basic</span></span>](#tab/vb)

![新しい .NET Standard ライブラリ プロジェクトを追加する](./media/std-project-vb.png)

<span data-ttu-id="7d0b0-157">.NET Core CLI を使用している場合、次の [dotnet new](../../core/tools/dotnet-new.md) コマンドを実行すると、.NET Standard 2.0 をターゲットとするクラス ライブラリ プロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7d0b0-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="7d0b0-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="7d0b0-158">See also</span></span>

[<span data-ttu-id="7d0b0-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="7d0b0-159">.NET Standard</span></span>](../net-standard.md)  
[<span data-ttu-id="7d0b0-160">.NET Standard の概要</span><span class="sxs-lookup"><span data-stu-id="7d0b0-160">Introducing .NET Standard</span></span>](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
