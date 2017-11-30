---
title: ".NET 標準の新機能"
ms.custom: updateeachrelease
ms.date: 11/08/2017
ms.prod: .net
ms.topic: article
ms.technology: dotnet-standard
ms.##devlang: dotnet
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e938c009b79af3b2f36094bbb74f4d38baeeac0b
ms.sourcegitcommit: 281070dee88db86ec3bb4634d5f558d1a4e159dd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/11/2017
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="3a83c-102">.NET 標準の新機能</span><span class="sxs-lookup"><span data-stu-id="3a83c-102">What's new in the .NET Standard</span></span>

<span data-ttu-id="3a83c-103">.NET 標準は、そのバージョンの標準に準拠している .NET の実装で使用できる必要がありますのある Api のバージョン管理されたセットを定義する正式な仕様です。</span><span class="sxs-lookup"><span data-stu-id="3a83c-103">The .NET Standard is a formal specification that defines a versioned set of APIs which must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="3a83c-104">.NET Standard はライブラリ開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="3a83c-104">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="3a83c-105">.NET 標準バージョンを対象とするライブラリは、そのバージョンの標準をサポートする任意の .NET Framework、.NET Core または Xamarin 実装で使用できます。</span><span class="sxs-lookup"><span data-stu-id="3a83c-105">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="3a83c-106">.NET 標準の最新バージョンは 2.0 です。</span><span class="sxs-lookup"><span data-stu-id="3a83c-106">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="3a83c-107">インストールされている、.NET Core のワークロードで、.NET Core 2.0 SDK、および Visual Studio 2017 バージョン 15.3 に含まれます。</span><span class="sxs-lookup"><span data-stu-id="3a83c-107">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="3a83c-108">サポートされている .NET の実装</span><span class="sxs-lookup"><span data-stu-id="3a83c-108">Supported .NET implementations</span></span>

<span data-ttu-id="3a83c-109">標準の .NET 2.0 は、次の .NET の実装によってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="3a83c-109">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="3a83c-110">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="3a83c-110">.NET Core 2.0</span></span>
- <span data-ttu-id="3a83c-111">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="3a83c-111">.NET Framework 4.6.1</span></span>
- <span data-ttu-id="3a83c-112">モノラル 5.4</span><span class="sxs-lookup"><span data-stu-id="3a83c-112">Mono 5.4</span></span>
- <span data-ttu-id="3a83c-113">Xamarin.iOS 10.14</span><span class="sxs-lookup"><span data-stu-id="3a83c-113">Xamarin.iOS 10.14</span></span>
- <span data-ttu-id="3a83c-114">Xamarin.Mac 3.8</span><span class="sxs-lookup"><span data-stu-id="3a83c-114">Xamarin.Mac 3.8</span></span>
- <span data-ttu-id="3a83c-115">Xamarin.Android 8.0</span><span class="sxs-lookup"><span data-stu-id="3a83c-115">Xamarin.Android 8.0</span></span>
- <span data-ttu-id="3a83c-116">ユニバーサル Windows プラットフォーム 10.0.16299</span><span class="sxs-lookup"><span data-stu-id="3a83c-116">Universal Windows Platform 10.0.16299</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="3a83c-117">標準の .NET 2.0 の新機能</span><span class="sxs-lookup"><span data-stu-id="3a83c-117">What's new in the .NET Standard 2.0</span></span>
 
<span data-ttu-id="3a83c-118">標準の .NET 2.0 には、次の新機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3a83c-118">The .NET Standard 2.0 includes the following new features:</span></span>

<span data-ttu-id="3a83c-119">**大幅に拡張された一連の Api**</span><span class="sxs-lookup"><span data-stu-id="3a83c-119">**A vastly expanded set of APIs**</span></span>

<span data-ttu-id="3a83c-120">バージョン 1.6、を介して .NET 標準は、Api の比較的小さなサブセットを含めます。</span><span class="sxs-lookup"><span data-stu-id="3a83c-120">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="3a83c-121">除外される間、.NET Framework または Xamarin でよく使用されていた Api の多くが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3a83c-121">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="3a83c-122">これは、アプリケーションと .NET の複数の実装を対象とするライブラリを開発するときに、開発者が使い慣れた Api の適切な代替を見つけることが必要なために、開発は複雑になります。</span><span class="sxs-lookup"><span data-stu-id="3a83c-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="3a83c-123">標準の .NET 2.0 では、.NET 標準 1.6、標準の以前のバージョンで使用できたより以上 20,000 以上の Api を追加することでこの制限を説明します。</span><span class="sxs-lookup"><span data-stu-id="3a83c-123">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="3a83c-124">標準の .NET 2.0 に追加されている Api の一覧は、次を参照してください。 [.NET 標準 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)です。</span><span class="sxs-lookup"><span data-stu-id="3a83c-124">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span> 

<span data-ttu-id="3a83c-125">いくつかの追加機能を<xref:System>.NET 規格 2.0 で名前空間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3a83c-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="3a83c-126">サポート、<xref:System.AppDomain>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3a83c-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="3a83c-127">配列内の他のメンバーからの操作のサポートの向上、<xref:System.Array>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3a83c-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="3a83c-128">属性の追加メンバーを操作するためのサポートが強化、<xref:System.Attribute>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3a83c-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="3a83c-129">サポートおよびの追加の書式設定オプションをより深くカレンダー<xref:System.DateTime>値。</span><span class="sxs-lookup"><span data-stu-id="3a83c-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="3a83c-130">追加<xref:System.Decimal>機能の丸め処理を行います。</span><span class="sxs-lookup"><span data-stu-id="3a83c-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="3a83c-131">追加の機能、<xref:System.Environment>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3a83c-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="3a83c-132">ガベージ コレクターを制御を強化、<xref:System.GC>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3a83c-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="3a83c-133">文字列比較、列挙、および正規化の拡張サポートを<xref:System.String>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3a83c-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="3a83c-134">夏時間の調整と遷移の時刻のサポート、<xref:System.TimeZoneInfo.AdjustmentRule>と<xref:System.TimeZoneInfo.TransitionTime>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3a83c-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="3a83c-135">機能を大幅に強化されて、<xref:System.Type>クラスです。</span><span class="sxs-lookup"><span data-stu-id="3a83c-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="3a83c-136">例外のコンス トラクターを追加することによって例外オブジェクトの逆シリアル化のサポートの向上<xref:System.Runtime.Serialization.SerializationInfo>と<xref:System.Runtime.Serialization.StreamingContext>パラメーター。</span><span class="sxs-lookup"><span data-stu-id="3a83c-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

<span data-ttu-id="3a83c-137">**.NET Framework ライブラリのサポート**</span><span class="sxs-lookup"><span data-stu-id="3a83c-137">**Support for .NET Framework libraries**</span></span>

<span data-ttu-id="3a83c-138">.NET Framework はなく、標準の .NET ライブラリの圧倒的を対象します。</span><span class="sxs-lookup"><span data-stu-id="3a83c-138">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="3a83c-139">ただし、これらのライブラリでの呼び出しのほとんどは、標準の .NET 2.0 に含まれる Api には。</span><span class="sxs-lookup"><span data-stu-id="3a83c-139">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="3a83c-140">標準の .NET 2.0 から始めてからアクセスできます .NET Framework ライブラリ、標準の .NET ライブラリを使用して、[互換性 shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification)です。</span><span class="sxs-lookup"><span data-stu-id="3a83c-140">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="3a83c-141">この互換性レイヤーが開発者; に対して透過的です。.NET Framework ライブラリを活用するために何もする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3a83c-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="3a83c-142">1 つの要件は、標準 .NET 2.0 では、.NET Framework クラス ライブラリによって呼び出される Api を含める必要があることです。</span><span class="sxs-lookup"><span data-stu-id="3a83c-142">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

<span data-ttu-id="3a83c-143">**Visual Basic のサポート**</span><span class="sxs-lookup"><span data-stu-id="3a83c-143">**Support for Visual Basic**</span></span>

<span data-ttu-id="3a83c-144">Visual Basic で標準の .NET ライブラリを開発できます。</span><span class="sxs-lookup"><span data-stu-id="3a83c-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="3a83c-145">Visual Studio 2017 バージョン 15.3 を使用している Visual Basic 開発者、またはインストールされている、.NET Core のワークロードで後では、Visual Studio には今すぐ .NET 標準的なクラス ライブラリ テンプレートが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3a83c-145">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="3a83c-146">その他の開発ツールや環境を使用している Visual Basic 開発者は、使用することができます、 [dotnet 新しい](../../core/tools/dotnet-new.md).NET 標準ライブラリ プロジェクトを作成するコマンド。</span><span class="sxs-lookup"><span data-stu-id="3a83c-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="3a83c-147">詳細については、次を参照してください。、 [.NET 標準ライブラリ用ツール サポート](#tooling)です。</span><span class="sxs-lookup"><span data-stu-id="3a83c-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling).</span></span>

<span data-ttu-id="3a83c-148"><a name="tooling" />**.NET 標準ライブラリ用ツール サポート**</span><span class="sxs-lookup"><span data-stu-id="3a83c-148"><a name="tooling" />**Tooling support for .NET Standard libraries**</span></span>

<span data-ttu-id="3a83c-149">.NET Core 2.0 と .NET 標準 2.0、Visual Studio 2017 年両方のリリースでは、 [.NET Core コマンド ライン インターフェイス (CLI)](../../core/tools/index.md) .NET 標準ライブラリの作成用ツール サポートが含まれます。</span><span class="sxs-lookup"><span data-stu-id="3a83c-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span> 

<span data-ttu-id="3a83c-150">Visual Studio をインストールする場合、 **.NET Core クロスプラット フォーム開発**ワークロードをプロジェクト テンプレートを使用して、次の図に示すとして .NET 標準 2.0 ライブラリ プロジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="3a83c-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows.</span></span> 

# <a name="ctabcsharp"></a>[<span data-ttu-id="3a83c-151">C#</span><span class="sxs-lookup"><span data-stu-id="3a83c-151">C#</span></span>](#tab/csharp)
![新しい .NET 標準のライブラリ プロジェクトに追加します。](./media/std-project-cs.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="3a83c-153">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a83c-153">Visual Basic</span></span>](#tab/visual-basic)
<a name="add-new-net-standard-library-projectmediastd-project-vbpng"></a>![新しい .NET 標準のライブラリ プロジェクトに追加します。](./media/std-project-vb.png)
---

<span data-ttu-id="3a83c-155">使用するかどうかは、次の .NET Core CLI [dotnet 新しい](../../core/tools/dotnet-new.md)コマンドは、標準の .NET 2.0 を対象とするクラス ライブラリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a83c-155">If you are using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0.</span></span>

```csharp
dotnet new classlib
```
```vb
dotnet new classlib -lang vb
```
  
## <a name="see-also"></a><span data-ttu-id="3a83c-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a83c-156">See Also</span></span>
<span data-ttu-id="3a83c-157">[.NET 標準](../net-standard.md)
[.NET 標準の概要](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span><span class="sxs-lookup"><span data-stu-id="3a83c-157">[.NET Standard](../net-standard.md)
[Introducing .NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span></span>
