---
title: .NET Core に移植する - Windows 互換機能パックの使用
description: Windows 互換機能パックとそれを使用して既存の .NET Framework コードを .NET Core に移植する方法について紹介します。
author: terrajobst
ms.author: mairaw
ms.date: 11/13/2017
ms.openlocfilehash: 51b96d7828285964c1b0cbb835b8eb5ed92c47d6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34566174"
---
# <a name="using-the-windows-compatibility-pack"></a><span data-ttu-id="1476b-103">Windows 互換機能パックの使用</span><span class="sxs-lookup"><span data-stu-id="1476b-103">Using the Windows Compatibility Pack</span></span>

<span data-ttu-id="1476b-104">既存のコードを .NET Core に移植するとき、開発者が直面する最も一般的な問題の 1 つが、.NET Framework にのみ存在する API とテクノロジに対する依存性です。</span><span class="sxs-lookup"><span data-stu-id="1476b-104">One of the most common issues that developers face when porting their existing code to .NET Core is that they depend on APIs and technologies that only exist in the .NET Framework.</span></span> <span data-ttu-id="1476b-105">*Windows 互換機能パック*はそのようなテクノロジを各種提供します。既存コードの実行可能性を上げるような方法で .NET Core アプリケーションと .NET Standard ライブラリをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="1476b-105">The *Windows Compatibility Pack* is about providing many of these technologies so that building .NET Core applications as well as .NET Standard libraries becomes much more viable for existing code.</span></span>

<span data-ttu-id="1476b-106">このパッケージは論理 [.NET Standard 2.0 の拡張](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support)であり、API セットを大幅に増やします。ほとんど変更なしで既存コードがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="1476b-106">This package is a logical [extension of .NET Standard 2.0](../whats-new/dotnet-core-2-0.md#api-changes-and-library-support) that significantly increases API set and existing code compiles with almost no modifications.</span></span> <span data-ttu-id="1476b-107">ただし、.NET Standard の約束 ("これはあらゆる .NET 実装の API を集めたものである") を守る目的で、レジストリ、Windows Management Instrumentation (WMI)、リフレクション出力 API など、すべてのプラットフォームで動作しないテクノロジは含まれていません。</span><span class="sxs-lookup"><span data-stu-id="1476b-107">But in order to keep the promise of .NET Standard ("it is the set of APIs that all .NET implementations provide"), this didn't include technologies that can't work across all platforms, such as registry, Windows Management Instrumentation (WMI), or reflection emit APIs.</span></span>

<span data-ttu-id="1476b-108">*Windows 互換機能パック*は .NET Standard を基盤とし、Windows 専用のテクノロジを利用できます。</span><span class="sxs-lookup"><span data-stu-id="1476b-108">The *Windows Compatibility Pack* sits on top of .NET Standard and provides access to technologies that are Windows only.</span></span> <span data-ttu-id="1476b-109">.NET Core に移行したいが、最初の手順が Windows に留まることである顧客にとって特に便利です。</span><span class="sxs-lookup"><span data-stu-id="1476b-109">It's especially useful for customers that want to move to .NET Core but plan to stay on Windows as a first step.</span></span> <span data-ttu-id="1476b-110">そのようなシナリオでは、Windows 専用テクノロジを利用できないことが移行における唯一のハードルとなります。アーキテクチャ上の利点がありません。</span><span class="sxs-lookup"><span data-stu-id="1476b-110">In that scenario, not being able to use Windows-only technologies is only a migration hurdle with zero architectural benefits.</span></span>

## <a name="package-contents"></a><span data-ttu-id="1476b-111">パッケージの内容</span><span class="sxs-lookup"><span data-stu-id="1476b-111">Package contents</span></span>

<span data-ttu-id="1476b-112">*Windows 互換機能パック*は NuGet パッケージ [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) 経由で提供され、.NET Core または .NET Standard を対象とするプロジェクトから参照できます。</span><span class="sxs-lookup"><span data-stu-id="1476b-112">The *Windows Compatibility Pack* is provided via the NuGet Package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) and can be referenced from projects targeting .NET Core or .NET Standard.</span></span>

<span data-ttu-id="1476b-113">Windows 専用 API やプラットフォーム非依存 API など、約 20,000 の API を提供します。テクノロジ領域には次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="1476b-113">It provides about 20,000 APIs, including Windows-only as well as cross-platform APIs from the following technology areas:</span></span>

* <span data-ttu-id="1476b-114">コード ページ</span><span class="sxs-lookup"><span data-stu-id="1476b-114">Code Pages</span></span>
* <span data-ttu-id="1476b-115">CodeDom</span><span class="sxs-lookup"><span data-stu-id="1476b-115">CodeDom</span></span>
* <span data-ttu-id="1476b-116">構成</span><span class="sxs-lookup"><span data-stu-id="1476b-116">Configuration</span></span>
* <span data-ttu-id="1476b-117">ディレクトリ サービス</span><span class="sxs-lookup"><span data-stu-id="1476b-117">Directory Services</span></span>
* <span data-ttu-id="1476b-118">描画</span><span class="sxs-lookup"><span data-stu-id="1476b-118">Drawing</span></span>
* <span data-ttu-id="1476b-119">ODBC</span><span class="sxs-lookup"><span data-stu-id="1476b-119">ODBC</span></span>
* <span data-ttu-id="1476b-120">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="1476b-120">Permissions</span></span>
* <span data-ttu-id="1476b-121">ポート</span><span class="sxs-lookup"><span data-stu-id="1476b-121">Ports</span></span>
* <span data-ttu-id="1476b-122">Windows アクセス制御リスト (ACL)</span><span class="sxs-lookup"><span data-stu-id="1476b-122">Windows Access Control Lists (ACL)</span></span>
* <span data-ttu-id="1476b-123">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="1476b-123">Windows Communication Foundation (WCF)</span></span>
* <span data-ttu-id="1476b-124">Windows 暗号化</span><span class="sxs-lookup"><span data-stu-id="1476b-124">Windows Cryptography</span></span>
* <span data-ttu-id="1476b-125">Windows EventLog</span><span class="sxs-lookup"><span data-stu-id="1476b-125">Windows EventLog</span></span>
* <span data-ttu-id="1476b-126">WMI (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="1476b-126">Windows Management Instrumentation (WMI)</span></span>
* <span data-ttu-id="1476b-127">Windows パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="1476b-127">Windows Performance Counters</span></span>
* <span data-ttu-id="1476b-128">Windows レジストリ</span><span class="sxs-lookup"><span data-stu-id="1476b-128">Windows Registry</span></span>
* <span data-ttu-id="1476b-129">Windows ランタイム キャッシュ</span><span class="sxs-lookup"><span data-stu-id="1476b-129">Windows Runtime Caching</span></span>
* <span data-ttu-id="1476b-130">Windows サービス</span><span class="sxs-lookup"><span data-stu-id="1476b-130">Windows Services</span></span>

<span data-ttu-id="1476b-131">詳細については、[互換機能パックの仕様](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1476b-131">For more information, see the [spec of the compatibility pack](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="1476b-132">作業開始</span><span class="sxs-lookup"><span data-stu-id="1476b-132">Get started</span></span>

1. <span data-ttu-id="1476b-133">移植の前に、[移植プロセス](index.md)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="1476b-133">Before porting, make sure to take a look at the [Porting Process](index.md).</span></span>

2. <span data-ttu-id="1476b-134">.NET Core または .NET Standard に既存のポートを移植するとき、NuGet パッケージ [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="1476b-134">When porting existing code to .NET Core or .NET Standard, install the NuGet package [Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span>

3. <span data-ttu-id="1476b-135">Windows に留まる場合、すでに用意はできています。</span><span class="sxs-lookup"><span data-stu-id="1476b-135">If you want to stay on Windows, you're all set.</span></span>

4. <span data-ttu-id="1476b-136">.NET Core アプリケーションまたは .NET Standard ライブラリを Linux または macOS で実行する場合、[API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) を使用し、プラットフォーム非依存で機能しない API の使用を見つけます。</span><span class="sxs-lookup"><span data-stu-id="1476b-136">If you want to run the .NET Core application or .NET Standard library on Linux or macOS, use the [API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) to find usage of APIs that won't work cross-platform.</span></span>

5. <span data-ttu-id="1476b-137">そのような API の使用を取り除くか、プラットフォーム非依存の代替で置換するか、プラットフォーム チェックで保護します (以下参照)。</span><span class="sxs-lookup"><span data-stu-id="1476b-137">Either remove the usages of those APIs, replace them with cross-platform alternatives, or guard them using a platform check, like:</span></span>

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

<span data-ttu-id="1476b-138">デモについては、[Windows 互換機能パックの Channel 9 動画](https://channel9.msdn.com/Events/Connect/2017/T123)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1476b-138">For a demo, check out the [Channel 9 video of the Windows Compatibility Pack](https://channel9.msdn.com/Events/Connect/2017/T123).</span></span>

