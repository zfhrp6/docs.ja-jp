---
title: ".NET Core - Windows 互換機能パックを使用してへの移植"
description: "Windows 互換機能パックについて学習できますを使用する方法、既存の .NET Framework コードを .NET Core ポートと"
keywords: ".NET、.NET core、Windows の互換性"
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 5094baee77aba4d1e148f807d842a4a2d3405cf7
ms.sourcegitcommit: 86cf9b4c7104485a9870645705b9a1a4b6ca8e2b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2017
---
# <a name="using-the-windows-compatibility-pack"></a><span data-ttu-id="9c6a6-104">Windows 互換機能パックを使用します。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-104">Using the Windows Compatibility Pack</span></span>

<span data-ttu-id="9c6a6-105">.NET Core に、既存のコードを移植するときに開発者が直面する最も一般的な問題の 1 つは、互い Api と .NET Framework にのみ存在するためのテクノロジに依存することです。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-105">One of the most common issues that developers face when porting their existing code to .NET Core is that they depend on APIs and technologies that only exist in the .NET Framework.</span></span> <span data-ttu-id="9c6a6-106">*Windows 互換機能パック*は標準の .NET ライブラリだけでなく、.NET Core アプリケーションの構築の既存のコードにより利用になるように、これらのテクノロジの多くを提供するについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-106">The *Windows Compatibility Pack* is about providing many of these technologies so that building .NET Core applications as well as .NET Standard libraries becomes much more viable for existing code.</span></span>

<span data-ttu-id="9c6a6-107">このパッケージは、論理[.NET 標準 2.0 の拡張機能](../whats-new/index.md#api-changes-and-library-support)が大幅に増加 API セットおよび既存のコードがコンパイルされるほとんど変更なしでします。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-107">This package is a logical [extension of .NET Standard 2.0](../whats-new/index.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="9c6a6-108">.NET 標準の約束を維持するのには (「はすべて .NET の実装を提供する Api のセット」)、この Windows Management Instrumentation (WMI)、レジストリなどのすべてのプラットフォームで動作するテクノロジが含まれていなかったか、リフレクション出力Api。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-108">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="9c6a6-109">*Windows 互換機能パック*.NET 標準の上に上に存在し、Windows は、のみテクノロジへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-109">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="9c6a6-110">.NET Core が最初の手順として Windows に収めるプランに移動するお客様にとって特に便利です。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-110">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="9c6a6-111">シナリオでは、ゼロ アーキテクチャの利点と移行ハードルだけは、Windows 限定のテクノロジを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-111">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="9c6a6-112">パッケージの内容</span><span class="sxs-lookup"><span data-stu-id="9c6a6-112">Package contents</span></span>

<span data-ttu-id="9c6a6-113">*Windows 互換機能パック*NuGet パッケージによって提供される[Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) .NET Core または .NET 標準をターゲットとするプロジェクトから参照できます。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-113">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="9c6a6-114">20,000 提供 Api では、次のテクノロジ分野から Windows のみだけでなくクロスプラット フォームの Api を含みます。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-114">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="9c6a6-115">コード ページ</span><span class="sxs-lookup"><span data-stu-id="9c6a6-115">Code Pages</span></span>
* <span data-ttu-id="9c6a6-116">CodeDom</span><span class="sxs-lookup"><span data-stu-id="9c6a6-116">CodeDom</span></span>
* <span data-ttu-id="9c6a6-117">構成</span><span class="sxs-lookup"><span data-stu-id="9c6a6-117">Configuration</span></span>
* <span data-ttu-id="9c6a6-118">ディレクトリ サービス</span><span class="sxs-lookup"><span data-stu-id="9c6a6-118">Directory Services</span></span>
* <span data-ttu-id="9c6a6-119">描画</span><span class="sxs-lookup"><span data-stu-id="9c6a6-119">Drawing</span></span>
* <span data-ttu-id="9c6a6-120">ODBC</span><span class="sxs-lookup"><span data-stu-id="9c6a6-120">ODBC</span></span>
* <span data-ttu-id="9c6a6-121">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="9c6a6-121">Permissions</span></span>
* <span data-ttu-id="9c6a6-122">ポート</span><span class="sxs-lookup"><span data-stu-id="9c6a6-122">Ports</span></span>
* <span data-ttu-id="9c6a6-123">Windows アクセス制御リスト (ACL)</span><span class="sxs-lookup"><span data-stu-id="9c6a6-123">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="9c6a6-124">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="9c6a6-124">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="9c6a6-125">Windows の暗号化</span><span class="sxs-lookup"><span data-stu-id="9c6a6-125">Windows Cryptography</span></span>
* <span data-ttu-id="9c6a6-126">Windows イベント ログ</span><span class="sxs-lookup"><span data-stu-id="9c6a6-126">Windows EventLog</span></span>
* <span data-ttu-id="9c6a6-127">WMI (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="9c6a6-127">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="9c6a6-128">Windows パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="9c6a6-128">Windows Performance Counters</span></span>
* <span data-ttu-id="9c6a6-129">Windows レジストリ</span><span class="sxs-lookup"><span data-stu-id="9c6a6-129">Windows Registry</span></span>
* <span data-ttu-id="9c6a6-130">Windows ランタイムのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="9c6a6-130">Windows Runtime Caching</span></span>
* <span data-ttu-id="9c6a6-131">Windows サービス</span><span class="sxs-lookup"><span data-stu-id="9c6a6-131">Windows Services</span></span>

<span data-ttu-id="9c6a6-132">詳細については、次を参照してください。、[互換機能パックの spec](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md)です。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-132">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="9c6a6-133">作業開始</span><span class="sxs-lookup"><span data-stu-id="9c6a6-133">Get started</span></span>

1. <span data-ttu-id="9c6a6-134">、移植する前に必ずを見て、[移植プロセス](index.md)です。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-134">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="9c6a6-135">NuGet パッケージのインストールには .NET Core または .NET Standard の既存のコードを移植するときに[Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)です。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-135">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="9c6a6-136">Windows に収める場合は、すべて設定します。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-136">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="9c6a6-137">Linux または macOS で .NET Core アプリケーションまたは .NET 標準ライブラリを実行する場合は、使用、 [API アナライザー](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/)クロスプラット フォームを使用できない Api の使用方法を検索します。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-137">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="9c6a6-138">それらの Api の使用法を削除、クロスプラット フォームの代替手段と置き換えてかのようなプラットフォームの確認を使用して保護します。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-138">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

    ```csharp
    private static string GetLoggingPath()
    {
        // Verify the code is running on Windows.
        if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
        {
            using (var key = Registry.CurrentUser.OpenSubKey(@"Software\Fabrikam\AssetManagement"))
            {
                if (key?.GetValue("LoggingDirectoryPath") is string configuredPath)
                    return configuredPath;
            }
        }

        // This is either not running on Windows or no logging path was configured,
        // so just use the path for non-roaming user-specific data files.
        var appDataPath = Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData);
        return Path.Combine(appDataPath, "Fabrikam", "AssetManagement", "Logging");
    }
    ```

<span data-ttu-id="9c6a6-139">チェック アウト デモについては、 [Windows 互換機能パックの Channel 9 ビデオ](https://channel9.msdn.com/Events/Connect/2017/T123)です。</span><span class="sxs-lookup"><span data-stu-id="9c6a6-139">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

