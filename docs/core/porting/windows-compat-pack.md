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
# <a name="using-the-windows-compatibility-pack"></a>Windows 互換機能パックを使用します。

.NET Core に、既存のコードを移植するときに開発者が直面する最も一般的な問題の 1 つは、互い Api と .NET Framework にのみ存在するためのテクノロジに依存することです。 *Windows 互換機能パック*は標準の .NET ライブラリだけでなく、.NET Core アプリケーションの構築の既存のコードにより利用になるように、これらのテクノロジの多くを提供するについて説明します。

このパッケージは、論理[.NET 標準 2.0 の拡張機能](../whats-new/index.md#api-changes-and-library-support)が大幅に増加 API セットおよび既存のコードがコンパイルされるほとんど変更なしでします。 .NET 標準の約束を維持するのには (「はすべて .NET の実装を提供する Api のセット」)、この Windows Management Instrumentation (WMI)、レジストリなどのすべてのプラットフォームで動作するテクノロジが含まれていなかったか、リフレクション出力Api。

*Windows 互換機能パック*.NET 標準の上に上に存在し、Windows は、のみテクノロジへのアクセスを提供します。 .NET Core が最初の手順として Windows に収めるプランに移動するお客様にとって特に便利です。 シナリオでは、ゼロ アーキテクチャの利点と移行ハードルだけは、Windows 限定のテクノロジを使用することはできません。

## <a name="package-contents"></a>パッケージの内容

*Windows 互換機能パック*NuGet パッケージによって提供される[Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility) .NET Core または .NET 標準をターゲットとするプロジェクトから参照できます。

20,000 提供 Api では、次のテクノロジ分野から Windows のみだけでなくクロスプラット フォームの Api を含みます。

* コード ページ
* CodeDom
* 構成
* ディレクトリ サービス
* 描画
* ODBC
* アクセス許可
* ポート
* Windows アクセス制御リスト (ACL)
* Windows Communication Foundation (WCF)
* Windows の暗号化
* Windows イベント ログ
* WMI (Windows Management Instrumentation)
* Windows パフォーマンス カウンター
* Windows レジストリ
* Windows ランタイムのキャッシュ
* Windows サービス

詳細については、次を参照してください。、[互換機能パックの spec](https://github.com/dotnet/designs/blob/master/accepted/compat-pack/compat-pack.md)です。

## <a name="get-started"></a>作業開始

1. 、移植する前に必ずを見て、[移植プロセス](index.md)です。

2. NuGet パッケージのインストールには .NET Core または .NET Standard の既存のコードを移植するときに[Microsoft.Windows.Compatibility](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)です。

3. Windows に収める場合は、すべて設定します。

4. Linux または macOS で .NET Core アプリケーションまたは .NET 標準ライブラリを実行する場合は、使用、 [API アナライザー](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/)クロスプラット フォームを使用できない Api の使用方法を検索します。

5. それらの Api の使用法を削除、クロスプラット フォームの代替手段と置き換えてかのようなプラットフォームの確認を使用して保護します。

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

チェック アウト デモについては、 [Windows 互換機能パックの Channel 9 ビデオ](https://channel9.msdn.com/Events/Connect/2017/T123)です。

