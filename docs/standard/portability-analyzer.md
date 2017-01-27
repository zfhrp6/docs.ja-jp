---
title: .NET Portability Analyzer | .NET
description: ".NET Portability Analyzer ツールを使用して、さまざまな .NET プラットフォーム間で、コードの移植性を評価する方法について説明します。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 07/05/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
translationtype: Human Translation
ms.sourcegitcommit: 8599be1eadcd6f005ef344bf173e8c06fce80725
ms.openlocfilehash: 9e35fd4dff15cec688ee11f98682eb7cb96e9403

---

# <a name="the-net-portability-analyzer"></a>.NET Portability Analyzer

ライブラリをマルチプラットフォーム対応にしたい場合や、 アプリケーションで他の .NET プラットフォームとの互換性を確保するのに必要な作業量を知りたい場合は、 [.NET Portability Analyzer](http://go.microsoft.com/fwlink/?LinkID=507467) が役立ちます。このツールを使用すると、アセンブリを分析して、プログラムが .NET プラットフォーム全体でどの程度柔軟な構造になっているかについて詳細なレポートを生成することができます。 Portability Analyzer は、Visual Studio 拡張機能のコンソール アプリとして提供されます。

## <a name="new-targets"></a>新しいターゲット

*   [.NET Core](https://www.dotnetfoundation.org/netcore): モジュール型の設計で、side-by-side を採用しており、クロスプラットフォームのシナリオを対象としています。 side-by-side 機能により、他のアプリに影響を与えることなく新しい .NET Core バージョンを導入することができます。
*   [ASP.NET Core](https://www.dotnetfoundation.org/aspnet-core): .NET Core 上に構築された最新の Web フレームワークであり、開発者に .NET Core と同じメリットを提供します。
*   [.NET Native](https://blogs.msdn.microsoft.com/dotnet/2014/04/24/net-native-performance): .NET Native の静的コンパイルを使用することで、x64 および ARM マシンで動作する Windows ストア アプリのパフォーマンスが向上します。

## <a name="how-to-use-portability-analyzer"></a>Portability Analyzer の使用方法

.NET Portability Analyzer を使用するには、[Visual Studio ギャラリー](http://go.microsoft.com/fwlink/?LinkID=507467)から拡張機能をダウンロードし、インストールする必要があります。 Visual Studio の **[ツール]** >  > **[オプション]** >  > **[.NET Portability Analyzer]** で設定を行い、ターゲット プラットフォームを選択することができます。 ここでは、ASP.NET Core をすべての .NET Core ベース プラットフォーム (たとえば、[Windows 10 .NET UAP アプリ](http://blogs.windows.com/buildingapps/2015/03/02/a-first-look-at-the-windows-10-universal-app-platform/)) のプロキシとして使用します。

![Portability のスクリーンショット](./media/portability-analyzer/portability-screenshot.png)

プロジェクト全体を分析するには、**ソリューション エクスプローラー**でプロジェクトを右クリックし、**[分析]** >  > **[Analyze Assembly Portability]** (アセンブリの移植性を分析) を選択します。 または、**[分析]** メニューで **[Analyze Assembly Portability]** (アセンブリの移植性を分析) を選択します。 そこから、プロジェクトの実行可能ファイルまたは DLL を選択します。

![移植性ソリューション エクスプローラー](./media/portability-analyzer/portability-solution-explorer.png)

分析を実行すると、.NET 移植性レポートが表示されます。 ターゲット プラットフォームでサポートされていない型のみが一覧に表示され、**[エラー一覧]** の **[メッセージ]** タブで、推奨事項を確認できます。 また、**[メッセージ]** タブから問題のある領域に直接移動することもできます。

![移植性レポート](./media/portability-analyzer/portability-report.png)

Visual Studio を使用しない場合は、 コマンド プロンプトから Portability Analyzer を使用することもできます。 [API Portability Analyzer](http://www.microsoft.com/download/details.aspx?id=42678) をダウンロードします。

*   現在のディレクトリを分析するには、次のコマンドを入力します。`\...\ApiPort.exe .`
*   特定の .dll ファイルの一覧を分析するには、次のコマンドを入力します。`\...\ApiPort.exe first.dll second.dll third.dll`

.NET 移植性レポートは、Excel ファイル (*.xlsx*) として現在のディレクトリに保存されます。 Excel ブックの **[詳細]** タブに詳細情報が記載されています。

.NET Portability Analyzer の詳細については、 .NET ブログの記事「[.NET プラットフォーム間で既存のコードの活用](https://blogs.msdn.microsoft.com/dotnet/2014/08/06/leveraging-existing-code-across-net-platforms/)」を参照してください。



<!--HONumber=Nov16_HO3-->


