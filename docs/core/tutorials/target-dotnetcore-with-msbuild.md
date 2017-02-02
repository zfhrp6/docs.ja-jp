---
title: "MSBuild を使用して .NET Core プロジェクトを作成する"
description: "MSBuild を使用して .NET Core プロジェクトを作成する"
keywords: .NET, .NET Core
author: dsplaisted
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13c66464-4f14-4db6-aa8b-06f25e7ba894
translationtype: Human Translation
ms.sourcegitcommit: 098cb31bb79e47ebb2ad2e8c2f56d2d5d6da4079
ms.openlocfilehash: 6a992d985948a22da58db8317bc04d2f1828fc05

---

# <a name="using-msbuild-to-build-net-core-projects"></a>MSBuild を使用して .NET Core プロジェクトを作成する

.NET Core ツールは [project.json から MSBuild ベースのプロジェクトに移行](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/)されます。
MSBuild を使用する最初のバージョンの .NET Core ツールが次のバージョンの Visual Studio と共に出荷される予定です。  ただし、現在、.NET Core プロジェクトに MSBuild を利用できます。その方法をこのページで紹介します。

.NET Core をターゲットにする新規プロジェクトでは、以下の理由から既定のツールと *project.json* を使用することをお勧めします。

- MSBuild は、まだ *project.json* のさまざまな機能に対応していません。
- ASP.NET ベースのツールの大半は現在のところ、MSBuild プロジェクトと連動していません。
- MSBuild ベースの .NET Core ツールは、リリース時に *project.json* が MSBuild ベースに自動で変換されます。

次の場合は MSBuild の使用を検討してください。

 - MSBuild を使用する既存のプロジェクトを .NET Core に移植する場合
 - プロジェクトで、*project.json* ではサポートが不十分な MSBuild の拡張機能を使用する場合

## <a name="prerequisites"></a>前提条件

- [Visual Studio 2015 更新プログラム 3](https://www.visualstudio.com/en-us/news/releasenotes/vs2015-update3-vs) 以降
- [Visual Studio 用の .NET Core ツール](https://www.visualstudio.com/downloads/download-visual-studio-vs)
- NuGet Visual Studio 拡張機能 [v3.5.0-beta](https://dist.nuget.org/visualstudio-2015-vsix/v3.5.0-beta/NuGet.Tools.vsix) 以降

## <a name="creating-a-library-targeting-net-core"></a>.NET Core をターゲットにするライブラリを作成する

1. Visual Studio メニュー バーで、**[ファイル]** | **[新規]** | **[プロジェクト]** の順に選択し、**[クラス ライブラリ (ポータブル)]** を選択します

  ![新しいプロジェクト](./media/target-dotnetcore-with-msbuild/new-project-dialog-class-library-portable.png)

2. プロジェクトの名前と場所を選択し、**[OK]** をクリックします

3. "ポータブル クラス ライブラリの追加" ダイアログが表示されます。  **[.NET Framework 4.6]** と **[ASP.NET Core 1.0]** をターゲットとして選択し、**[OK]** をクリックします

  ![ポータブル ターゲット ダイアログ](./media/target-dotnetcore-with-msbuild/pcl-targets-dialog-net46-aspnetcore10.png)

4. ソリューション エクスプローラーでプロジェクトを右クリックし、**[プロパティ]** を選択します
5. プロジェクト プロパティの **[ライブラリ]** タブで、**[Target .NET Platform Standard]** リンクをクリックし、ダイアログが表示されたら **[はい]** をクリックします
6. プロジェクトの `project.json` ファイルを開き、次の変更を行います。
    - `NETStandard.Library` パッケージのバージョン番号を `1.6.0` に変更します (これはパッケージの .NET Core 1.0 バージョンです)
    - `netstandard1.6` フレームワーク定義の中に下の `imports` 定義を追加します。  これにより、.NET Standard をターゲットにするように更新されていない .NET Core 互換 NuGet パッケージをプロジェクトは参照できます。

        ```json
        "netstandard1.6": {
            "imports": [ "dnxcore50", "portable-net452" ]
        }
        ```

## <a name="creating-a-net-core-console-application"></a>.NET Core コンソール アプリケーションを作成する
.NET Core のコンソール アプリケーションを作成するには、MSBuild ビルド プロセスをいくつかカスタマイズする必要があります。  [corefxlab](https://github.com/dotnet/corefxlab) リポジトリに .NET Core コンソール アプリケーションのサンプル プロジェクトがあります。「[CoreApp](https://github.com/dotnet/corefxlab/tree/master/samples/NetCoreSample/CoreApp)」という名前です。  [coretemplate](https://github.com/mellinoe/coretemplate) で開始することも推奨されます。変更をプロジェクト ファイルに直接配置する代わりに、別個の MSBuild ターゲット ファイルを利用し、.NET Core をターゲットにします。  

Visual Studio でプロジェクトを作成し、.NET Core をターゲットにするように変更することもできます。  以下の手順は、これを機能させるための最小手順を示しています。  [CoreApp](https://github.com/dotnet/corefxlab/tree/master/samples/NetCoreSample/CoreApp) や [coretemplate](https://github.com/mellinoe/coretemplate) とは対照的に、この方法で作成されたプロジェクトには、Linux や macOS をターゲットにする構成が含まれません。

1. Visual Studio メニュー バーで、**[ファイル]** | **[新規]** | **[プロジェクト]** の順に選択し、**[コンソール アプリケーション]** を選択します
2. プロジェクトの名前と場所を選択し、**[OK]** をクリックします
3. ソリューション エクスプローラーでプロジェクトを右クリックし、**[プロパティ]** を選択し、**[ビルド]** タブに移動します。
4. ([プロパティ] ページの上部にある) **[構成]** ドロップダウンで、**[すべての構成]** を選択し、**[プラットフォーム ターゲット]** を **[x64]** に変更します
5. プロジェクトから `app.config` ファイルを削除します
6. 次のコンテンツのプロジェクトに `project.json` ファイルを追加します。

    ```json
    {
        "dependencies": {
            "Microsoft.NETCore.App": "1.0.0-rc2-3002702"
        },
        "runtimes": {
            "win7-x64": { },
            "ubuntu.14.04-x64": { },
            "osx.10.10-x64": { }
        },
        "frameworks": {
            "netcoreapp1.0": {
                "imports": [ "dnxcore50", "portable-net452" ]
            }
        }
    }
    ```

7. ソリューション エクスプローラーで、プロジェクトを右クリックして **[プロジェクトのアンロード]** を選択し、もう一度右クリックして **[_MyProj.csproj_ の編集]** を選択します。次のような変更を行います
    - すべての既定の `Reference` 項目を削除します (`System`、`System.Core` など)
    - プロジェクトの最初の `PropertyGroup` に次のプロパティを追加します。

        ```xml
        <TargetFrameworkIdentifier>.NETCoreApp</TargetFrameworkIdentifier>
        <TargetFrameworkVersion>v1.0</TargetFrameworkVersion>
        <BaseNuGetRuntimeIdentifier>win7</BaseNuGetRuntimeIdentifier>
        <NoStdLib>true</NoStdLib>
        <NoWarn>$(NoWarn);1701</NoWarn>
        ```

    - ファイルの終わりに次を追加します (`Microsoft.CSharp.Targets` のインポート後に)。

        ```xml
        <PropertyGroup>
            <!-- We don't use any of MSBuild's resolution logic for resolving the framework, so just set these two
                    properties to any folder that exists to skip the GetReferenceAssemblyPaths task (not target) and
                    to prevent it from outputting a warning (MSB3644).
                -->
            <_TargetFrameworkDirectories>$(MSBuildThisFileDirectory)</_TargetFrameworkDirectories>
            <_FullFrameworkReferenceAssemblyPaths>$(MSBuildThisFileDirectory)</_FullFrameworkReferenceAssemblyPaths>

            <!-- MSBuild thinks all EXEs need binding redirects, not so for CoreCLR! -->
            <AutoUnifyAssemblyReferences>true</AutoUnifyAssemblyReferences>
            <AutoGenerateBindingRedirects>false</AutoGenerateBindingRedirects>

            <!-- Set up debug options to run with host, and to use the CoreCLR debug engine -->
            <StartAction>Program</StartAction>
            <StartProgram>$(TargetDir)dotnet.exe</StartProgram>
            <StartArguments>$(TargetPath)</StartArguments>
            <DebugEngines>{2E36F1D4-B23C-435D-AB41-18E608940038}</DebugEngines>
        </PropertyGroup>
        ```

    - .csproj ファイルを閉じ、Visual Studio でプロジェクトをもう一度読み込みます

8. Visual Studio で F5 を押すと、プログラムが実行されます。または、次が含まれる出力フォルダーでコマンド ラインから実行することもできます。`dotnet MyApp.exe` 



<!--HONumber=Jan17_HO3-->


