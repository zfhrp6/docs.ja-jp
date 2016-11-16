---
title: "クロス プラットフォーム ツールによるライブラリの開発"
description: "クロス プラットフォーム ツールによるライブラリの開発"
keywords: .NET, .NET Core
author: cartermp
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 9f6e8679-bd7e-4317-b3f9-7255a260d9cf
translationtype: Human Translation
ms.sourcegitcommit: 0882a5ca2f7814e2fd168dce40705d11b199f102
ms.openlocfilehash: caf72bec4a5d3276d1fdeafc4fa3816e5f00c296

---

# <a name="developing-libraries-with-cross-platform-tools"></a>クロス プラットフォーム ツールによるライブラリの開発

**ツールチェーンの進化に伴って、詳細な点が変わる可能性があります。**

この記事では、クロスプラットフォーム CLI ツールを使用して .NET 用ライブラリを作成する方法について説明します。  CLI は、サポートされる任意の OS で動作する効率的で低レベルのエクスペリエンスを提供します。  Visual Studio でライブラリを構築することもできます。Visual Studio で構築する場合は、[Visual Studio ガイドを参照](libraries-with-vs.md)してください。

## <a name="prerequisites"></a>必須コンポーネント

[.NET Core SDK と CLI](https://www.microsoft.com/net/core) がコンピューターにインストールされている必要があります。

このドキュメントで [.NET Framework](http://getdotnet.azurewebsites.net/) バージョンまたはポータブル クラス ライブラリ (PCL) について扱うセクションでは、.NET Framework が Windows コンピューターにインストールされている必要があります。  

また、古い .NET Framework ターゲットをサポートする場合、[.NET ターゲット プラットフォーム ページ](http://getdotnet.azurewebsites.net/target-dotnet-platforms.html)から古い .NET Framework バージョンの Targeting/Developer Pack をインストールする必要があります。  次の表を参照してください。

| .NET Framework のバージョン | ダウンロードするもの |
| ---------------------- | ----------------- |
| 4.6.1 | .NET Framework 4.6.1 Targeting Pack |
| 4.6 | .NET Framework 4.6 Targeting Pack |
| 4.5.2 | .NET Framework 4.5.2 Developer Pack |
| 4.5.1 | .NET Framework 4.5.1 Developer Pack |
| 4.5 | Windows 8 用 Windows ソフトウェア開発キット |
| 4.0 | Windows SDK for Windows 7 および .NET Framework 4 |
| 2.0、3.0、および 3.5 | .NET Framework 3.5 SP1 Runtime (または Windows 8 以降のバージョン) |

## <a name="how-to-target-the-net-standard"></a>.NET Standard をターゲット設定する方法

.NET Standard にあまりなじみがない場合、詳細については、「[.NET Standard Library](../../standard/library.md)」を参照してください。

この記事には、.NET Standard バージョンを多様な実装にマップする表が掲載されています。

| プラットフォーム名 | Alias |  |  |  |  |  | | |
| :---------- | :--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |
|.NET Standard | netstandard | 1.0 | 1.1 | 1.2 | 1.3 | 1.4 | 1.5 | 1.6 |
|.NET Core|netcoreapp|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|1.0|
|.NET Framework|net|&rarr;|4.5|4.5.1|4.6|4.6.1|4.6.2|4.6.3|
|Mono/Xamarin プラットフォーム||&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|*|
|ユニバーサル Windows プラットフォーム|uap|&rarr;|&rarr;|&rarr;|&rarr;|10.0|||
|Windows|win|&rarr;|8.0|8.1|||||
|Windows Phone|wpa|&rarr;|&rarr;|8.1|||||
|Windows Phone Silverlight|wp|8.0|||||||

ライブラリを作成する目的でこの表の意味について説明します。

選択する .NET Platform Standard のバージョンは、最新の API にアクセスできることと、より多くの .NET プラットフォームと Framework バージョンをターゲット設定できることのトレードオフで決まります。  ターゲット設定可能なプラットフォームとバージョンの範囲は、`netstandardX.X` のバージョンを選択し (`X.X` はバージョン番号です)、`project.json` ファイルに追加することで制御します。

さらに、[依存する NuGet パッケージ](https://www.nuget.org/packages/NETStandard.Library/)に対応するのは `NETStandard.Library` バージョン `1.6.0` です。  コンソール アプリなど、`Microsoft.NETCore.App` への依存を妨げるものは何もありませんが、一般的には推奨されません。  `NETStandard.Library` で指定されていないパッケージの API が必要な場合は、`NETStandard.Library` に加え、`project.json` ファイルの `dependencies` セクションにそのバージョンを指定できます。

.NET Standard をターゲット設定する場合、ニーズに応じて主に 3 つのオプションがあります。

1. 最新バージョンの .NET Standard である `netstandard1.6` を使用できます。最新の API にアクセスできることを重視し、対応する実装が少なくなることが気にならない場合にお勧めです。
2. 古いバージョンの .NET Standard を使用すると、以前の .NET 実装をターゲットに設定することができます。 この場合、一部の最新の API にアクセスできないという欠点があります。
    
    たとえば、.NET Framework 4.6 以降との互換性を保証する場合は、`netstandard1.3` を選択します。

    ```json
    {
        "dependencies":{
            "NETStandard.Library":"1.6.0"
        },
        "frameworks":{
            "netstandard1.3":{}
        }
    }
    ```
    
    .NET Standard バージョンは下位互換性があります。 つまり、`netstandard1.0` ライブラリは、`netstandard1.1` プラットフォーム以降で実行されます。  ただし、上位互換性はないため、古い .NET Standard プラットフォームは新しいプラットフォームを参照できません。  つまり、`netstandard1.0` ライブラリは、`netstandard1.1` 以降をターゲットとするライブラリを参照できません。  API とプラットフォームを適切に組み合わせ、ニーズに対応できる Standard バージョンを選択してください。
    
3. .NET Framework バージョン 4.0 以前をターゲットにする場合、または .NET Framework では利用できて .NET Standard では利用できない API (`System.Drawing` など) を使用する場合は、マルチターゲットの方法について次のセクションを参照してください。

## <a name="how-to-target-the-net-framework"></a>.NET Framework をターゲット設定する方法

> [!NOTE]
> 次の手順では、.NET Framework がコンピューターにインストールされていると想定しています。  依存関係のインストールについては、「[前提条件](#prerequisites)」を参照してください。

ここで使用されている .NET Framework バージョンには、現在サポートされていないものもあります。  サポートされないバージョンについては、「[.NET Framework Support Lifecycle Policy FAQ](https://support.microsoft.com/gp/framework_faq/en-us)」(.NET Framework のサポート ライフサイクル ポリシーについてよく寄せられる質問) を参照してください。

最大数の開発者とプロジェクトを対象にしたい場合、基準となるターゲットは .NET Framework 4 です。 .NET Framework をターゲット設定するには、まず、サポートしたい .NET Framework バージョンに対応する正しいターゲット フレームワーク モニカー (TFM) を使用します。

```
.NET Framework 2.0   --> net20
.NET Framework 3.0   --> net30
.NET Framework 3.5   --> net35
.NET Framework 4.0   --> net40
.NET Framework 4.5   --> net45
.NET Framework 4.5.1 --> net451
.NET Framework 4.5.2 --> net452
.NET Framework 4.6   --> net46
.NET Framework 4.6.1 --> net461
.NET Framework 4.6.2 --> net462
.NET Framework 4.6.3 --> net463
```

.NET Framework 4 をターゲットとするライブラリを作成する例を次に示します。

```json
{
    "frameworks":{
        "net40":{}
    }
}
```

以上です。  これは .NET Framework 4 向けにのみコンパイルされていますが、新しいバージョンの .NET Framework のライブラリを使用できます。

## <a name="how-to-target-a-portable-class-library-pcl"></a>ポータブル クラス ライブラリ (PCL) をターゲット設定する方法

> [!NOTE]
> 次の手順では、.NET Framework がコンピューターにインストールされていると想定しています。  依存関係のインストールについては、「[前提条件](#prerequisites)」を参照してください。

PCL プロファイルのターゲット設定は、.NET Standard や .NET Framework のターゲット設定よりも少し複雑です。  初心者の場合は、[この PCL プロファイル一覧を参照](http://embed.plnkr.co/03ck2dCtnJogBKHJ9EjY/preview)して、ターゲットとする PCL プロファイルに対応する NuGet ターゲットを見つけてください。

次に、以下の手順を実行します。

1. `project.json` の `frameworks` に `.NETPortable,Version=v{version},Profile=Profile{profile}` という新しいエントリを作成します。この `{version}` と `{profile}` は、それぞれ PCL バージョン番号とプロファイル番号に対応します。
2. この新しいエントリに、`frameworkAssemblies` エントリ以下のそのターゲットに使用する各アセンブリを列挙します。  これには、`mscorlib`、`System`、`System.Core` が含まれます。
3. マルチターゲット設定の場合 (次のセクションを参照してください)、ターゲット エントリ以下に各ターゲットの依存関係を明示的に列挙する必要があります。  グローバル `dependencies` エントリを使用できなくなります。

次に、PCL Profile 328 をターゲット設定する例を次に示します。 Profile 328 は、.NET Standard 1.4、.NET Framework 4、Windows 8、Windows Phone 8.1、Windows Phone Silverlight 8.1、Silverlight 5 をサポートしています。

```json
{
    "frameworks":{
        ".NETPortable,Version=v4.0,Profile=Profile328":{
            "frameworkAssemblies":{
                "mscorlib":"",
                "System":"",
                "System.Core":""
            }
        }
    }
}
```

*project.json* ファイルのフレームワークとして PCL Profile 328 を含むプロジェクトをビルドすると、*/bin/debug* フォルダーにこのサブフォルダーが作成されます。

```
portable-net40+sl50+netcore45+wpa81+wp8/
```

このフォルダーには、ライブラリの実行に必要な `.dll` ファイルが含まれています。

## <a name="how-to-multitarget"></a>マルチターゲットを設定する方法

> [!NOTE]
> 次の手順では、.NET Framework がコンピューターにインストールされている想定です。  インストールする必要がある依存関係と、そのダウンロードできる場所については、「[前提条件](#prerequisites)」セクションを参照してください。

プロジェクトが .NET Framework と .NET Core の両方をサポートしている場合、状況によっては古いバージョンの .NET Framework をターゲットにする必要があります。 このシナリオで、新しい API と新しいターゲット向けの言語構成を使用する場合、コードで `#if` ディレクティブを使用します。 また、必要に応じて、ターゲットにする各プラットフォームの `project.json file` に異なるパッケージと依存関係追加して、それぞれに異なる必要な API を含めます。

たとえば、HTTP 上でネットワークキング操作を行うライブラリがあるとします。 .NET Standard と .NET Framework バージョン 4.5 以降の場合、`System.Net.Http` 名前空間の `HttpClient` クラスを使用できます。 ただし、それより前のバージョンの .NET Framework に `HttpClient` クラスはないので、代わりに `System.Net` 名前空間の `WebClient` クラスを使用できます。

そこで `project.json` ファイルは次のようになります。

```json
{
    "frameworks":{
        "net40":{
            "frameworkAssemblies": {
                "System.Net":"",
                "System.Text.RegularExpressions":""
            }
        },
        "net452":{
            "frameworkAssemblies":{
                "System.Net":"",
                "System.Net.Http":"",
                "System.Text.RegularExpressions":"",
                "System.Threading.Tasks":""
            }
        },
        "netstandard1.6":{
            "dependencies": {
                "NETStandard.Library":"1.6.0",
            }
        }
    }
}
```

.NET Framework アセンブリは、`net40` および `net452` ターゲットで明示的に参照する必要があり、NuGet 参照も `netstandard1.6` ターゲットに明示的に列挙する必要があります。  これはマルチターゲット シナリオで必要です。

次に、ソース ファイルの `using` ステートメントは次のように調整できます。

```csharp
#if NET40
// This only compiles for the .NET Framework 4 targets
using System.Net;
#else
// This compiles for all other targets
using System.Net.Http;
using System.Threading.Tasks;
#endif
```

ビルド システムは `#if` ディレクティブで使用される次のプリプロセッサ シンボルを認識します。

```
.NET Framework 2.0   --> NET20
.NET Framework 3.5   --> NET35
.NET Framework 4.0   --> NET40
.NET Framework 4.5   --> NET45
.NET Framework 4.5.1 --> NET451
.NET Framework 4.5.2 --> NET452
.NET Framework 4.6   --> NET46
.NET Framework 4.6.1 --> NET461
.NET Framework 4.6.2 --> NET462
.NET Standard 1.0    --> NETSTANDARD1_0
.NET Standard 1.1    --> NETSTANDARD1_1
.NET Standard 1.2    --> NETSTANDARD1_2
.NET Standard 1.3    --> NETSTANDARD1_3
.NET Standard 1.4    --> NETSTANDARD1_4
.NET Standard 1.5    --> NETSTANDARD1_5
.NET Standard 1.6    --> NETSTANDARD1_6
```

また、ソースの中で `#if` を使用して、そのライブラリを条件付きで使用することができます。 例:

```csharp
    public class Library
    {
#if NET40
        private readonly WebClient _client = new WebClient();
        private readonly object _locker = new object();
#else
        private readonly HttpClient _client = new HttpClient();
#endif

#if NET40
        // .NET Framework 4.0 does not have async/await
        public string GetDotNetCount()
        {
            string url = "http://www.dotnetfoundation.org/";
          
            var uri = new Uri(url);
            
            string result = "";
            
            // Lock here to provide thread-safety.
            lock(_locker)
            {
                result = _client.DownloadString(uri);
            }
            
            int dotNetCount = Regex.Matches(result, ".NET").Count;
            
            return $"Dotnet Foundation mentions .NET {dotNetCount} times!";
        }
#else
        // .NET 4.5+ can use async/await!
        public async Task<string> GetDotNetCountAsync()
        {
            string url = "http://www.dotnetfoundation.org/";
            
            // HttpClient is thread-safe, so no need to explicitly lock here
            var result = await _client.GetStringAsync(url);
            
            int dotNetCount = Regex.Matches(result, ".NET").Count;
            
            return $"dotnetfoundation.orgmentions .NET {dotNetCount} times in its HTML!";
        }
#endif
    }
```

*project.json* ファイルのフレームワークとして `net40`、`net45`、`netstandard1.6` を含むプロジェクトをビルドすると、*/bin/debug* フォルダーにこれらのサブフォルダーが作成されます。

```
net40/
net45/
netstandard1.6/
```

### <a name="but-what-about-multitargeting-with-portable-class-libraries"></a>ポータブル クラス ライブラリを使用したマルチターゲットの概要

PCL ターゲットでクロスコンパイルする場合、PCL ターゲットの `buildOptions` の `project.json` ファイルにビルド定義を追加する必要があります。  ソースに、プリプロセッサ シンボルとしてビルド定義を使用する `#if` ディレクティブを使用できます。

たとえば、[PCL profile 328](http://embed.plnkr.co/03ck2dCtnJogBKHJ9EjY/preview) をターゲット設定する場合 (.NET Framework 4、Windows 8、Windows Phone Silverlight 8、Windows Phone 8.1、Silverlight 5)、クロスコンパイル時にこれを "PORTABLE328" として参照することができます。  `project.json` ファイルを `buildOptions` 属性として追加するだけの処理です。

```json
{
    "frameworks":{
        "netstandard1.6":{
           "dependencies":{
                "NETStandard.Library":"1.6.0",
            }
        },
        ".NETPortable,Version=v4.0,Profile=Profile328":{
            "buildOptions": {
                "define": [ "PORTABLE328" ]
            },
            "frameworkAssemblies":{
                "mscorlib":"",
                "System":"",
                "System.Core":"",
                "System.Net"
            }
        }
    }
}

```

これで、そのターゲットに対して条件付きでコンパイルできるようになりました。

```csharp
#if !PORTABLE328
using System.Net.Http;
using System.Threading.Tasks;
// Potentially other namespaces which aren't compatible with Profile 328
#endif
```

`PORTABLE328` はコンパイラから認識されるようになったので、コンパイラで生成される PCL Profile 328 ライブラリに `System.Net.Http` または `System.Threading.Tasks` は含まれません。

*project.json* ファイルのフレームワークとして PCL Profile 328 と `netstandard1.6` を含むプロジェクトをビルドすると、*/bin/debug* フォルダーにこれらのサブフォルダーが作成されます。

```
portable-net40+sl50+netcore45+wpa81+wp8/
netstandard1.6/
```

## <a name="how-to-use-native-dependencies"></a>ネイティブの依存関係を使用する方法

ネイティブの `.dll` ファイルに依存するライブラリを作成する場合があります。  このようなライブラリを作成する場合、2 つの選択肢があります。

1. `project.json` で `.dll` を直接参照します。
2. その `.dll` を独自の NuGet パッケージにパッケージ化し、そのパッケージに依存します。

1 つ目の選択肢では、`project.json` ファイルに次を含める必要があります。

1. `buildOptions` セクションの `allowUnsafe` を `true` に設定に設定します。
2. `runtimes` セクションで[ランタイム識別子 (RID)](../rid-catalog.md) を指定します。
3. 参照しているネイティブの `.dll` ファイルのパスを指定します。

Windows で実行されているプロジェクトのルート ディレクトリにあるネイティブの `.dll` ファイルの `project.json` の例を次に示します。

```json
{
    "buildOptions":{
        "allowUnsafe":true
    },
    "runtimes":{
        "win10-x64":{}
    },
    "packOptions":{
        "files":{
            "mappings":{
                "runtimes/win10-x64/native":{
                    "includeFiles":[ "native-lib.dll"]
                }
            }            
        }
    }
}
```

ライブラリをパッケージとして配布する場合、`.dll` ファイルをプロジェクトのルート レベルに配置することをお勧めします。

2 つ目の選択肢では、`.dll` ファイルから NuGet パッケージをビルドし、NuGet または MyGet フィードでホストし、直接依存する必要があります。  この場合も、`project.json` の `buildOptions` セクションで `allowUnsafe` を `true` に設定する必要があります。  次に例を示します (`MyNativeLib` はバージョン `1.2.0` の NuGet パッケージという想定です)。

```json
{
    "buildOptions":{
        "allowUnsafe":true
    },
    "dependencies":{
        "MyNativeLib":"1.2.0"
    }
}
```

クロスプラットフォームのネイティブ バイナリをパッケージ化する例については、[ASP.NET Libuv パッケージ](https://github.com/aspnet/libuv-package)と、[KestrelHttpServer の対応するリファレンス](https://github.com/aspnet/KestrelHttpServer/blob/1.0.0/src/Microsoft.AspNetCore.Server.Kestrel/project.json#L19)を参照してください。

## <a name="how-to-test-libraries-on-net-core"></a>.NET Core でライブラリをテストする方法

プラットフォーム全体でテストできることが重要です。  [xUnit](http://xunit.github.io/) を使用するのが最も簡単です。xUnit は、.NET Core プロジェクトで使用されるテスト ツールでもあります。  テスト プロジェクトでソリューションをセットアップする方法は、[ソリューションの構造](#structuring-a-solution)によって異なります。  次の例では、すべてのソース プロジェクトが最上位レベルの `/src` フォルダー以下にあり、すべてのテスト プロジェクトが最上位レベルの `/test` フォルダー以下にあるという想定です。

1. テスト プロジェクトがある場所がわかるソリューション レベルに `global.json` ファイルを配置してください。
    
    ```json
    {
        "projects":[ "src", "test"]
    }
    ```
    
    ソリューション フォルダーの構造は次のようになります。
    
    ```
    /SolutionWithSrcAndTest
    |__global.json
    |__/src
    |__/test
    ```
    
2. `/test` フォルダー以下にプロジェクト フォルダーを作成し、その新しいプロジェクト フォルダーに新しいテスト プロジェクトの `project.json` ファイルを作成します。  `project.json` ファイルを作成するには、`dotnet new` コマンドを実行し、後で `project.json` ファイルを変更します。  ファイルは次のようになります。

   * `netcoreapp1.0` は `frameworks` 以下のエントリとしてのみ列挙されます。
   * `Microsoft.NETCore.App` バージョン `1.0.0` の参照。
   * xUnit バージョン `2.2.0-beta2-build3300` の参照。
   * `dotnet-test-xunit` バージョン `2.2.0-preview2-build1029` の参照。
   * テスト対象のライブラリのプロジェクト参照。
   * エントリ `"testRunner":"xunit"`。
   
   次に例を示します (`LibraryUnderTest` バージョン `1.0.0` はテスト対象のライブラリです)。
   
   ```json
   {
        "testRunner":"xunit",
        "dependencies":{
            "LibraryUnderTest":{
                "version":"1.0.0",
                "target":"project"
            },
            "Microsoft.NETCore.App":{
                "version":"1.0.0",
                "type":"platform"
            },
            "xunit":"2.2.0-beta2-build3300",
            "dotnet-test-xunit":"2.2.0-preview2-build1029",
        },
        "frameworks":{
            "netcoreapp1.0":{}
        }
   }
   ```
3. `dotnet restore` を実行してパッケージを復元します。  パッケージをまだ復元したことがない場合は、この操作をソリューション レベルで実行することをお勧めします。

4. テスト プロジェクトに移動し、`dotnet test` でテストを実行します。

    ```
    $ cd path-to-your-test-project
    $ dotnet test
    ```

以上です。  コマンド ライン ツールを使用して、すべてのプラットフォームでライブラリをテストできるようになりました。  すべてをセットアップしてテストに進む場合、ライブラリのテストはとても単純です。

1. ライブラリに変更を加えます。
2. コマンド ラインから、`dotnet test` コマンドを使用してテスト ディレクトリでテストを実行します。

`dotnet test` コマンドを呼び出すと、コードは自動的にリビルドされます。

新しい以下を追加するたびに、忘れずにコマンド ラインから `dotnet restore` を実行するだけで完了です。

## <a name="how-to-use-multiple-projects"></a>複数のプロジェクトを使用する方法

大規模なライブラリで一般的なニーズは、複数のプロジェクトに機能を配置することです。

たとえば、慣用的な C# や F# で使用できるライブラリをビルドするとします。  これは、ライブラリのユーザーは、C# または F# に対して自然な方法で使用することを意味します。  たとえば、C# の場合、次のようにライブラリを使用できます。

```csharp
var convertResult = await AwesomeLibrary.ConvertAsync(data);
var result = AwesomeLibrary.Process(convertResult);
```  

F# の場合は次のようになります。

```fsharp
let result =
    data
    |> AwesomeLibrary.convertAsync 
    |> Async.RunSynchronously 
    |> AwesomeLibrary.process
```

このような使用シナリオは、アクセスされる API が C# と F# 用に異なる構造を持つ必要があることを示します。  これを実現する一般的なアプローチとして、ライブラリのすべてのロジックをコア プロジェクトに取り入れ、C# および F# プロジェクトでコア プロジェクトに呼び出す API レイヤーを定義する方法があります。  以降のセクションでは、次の名前を使用します。

* **AwesomeLibrary.Core** - ライブラリのすべてのロジックを含むコア プロジェクト
* **AwesomeLibrary.CSharp** - C で使用するためのパブリック API を含むプロジェクト#
* **AwesomeLibrary.FSharp** - F で使用するためのパブリック API を含むプロジェクト#

### <a name="projecttoproject-referencing"></a>プロジェクト間参照

プロジェクトを参照する最適な方法は次のとおりです。

1. 参照するプロジェクトを、ディスクに含まれるフォルダーに適した名前にする必要があります。  これは、プロジェクトの参照に使用される名前になります。
2. `"target":"project"` を指定して、使用するプロジェクトの `project.json` ファイルの (1) から名前を参照します。

**AwesomeLibrary.CSharp** と **AwesomeLibrary.FSharp** の両方の `project.json` ファイルは、`project` ターゲットとして **AwesomeLibrary.Core** を参照する必要があります。  マルチターゲット設定していない場合、グローバル `dependencies` エントリを使用できます。

```json
{
    "dependencies":{
        "AwesomeLibrary.Core":{
            "target":"project"
        }
    }
}
```

マルチターゲット設定している場合、グローバル `dependencies` エントリを使用できない場合があります。また、必要に応じて、ターゲットレベルの `dependencies` エントリで **AwesomeLibrary.Core** を参照します。  たとえば、`netstandard1.6` をターゲット設定している場合は、次のように実行できます。

```json
{
    "frameworks":{
        "netstandard1.6":{
            "dependencies":{
                "AwesomeLibrary.Core":{
                    "target":"project"
                }
            }
        }
    }
}
```

### <a name="structuring-a-solution"></a>ソリューションの構築

マルチプロジェクト ソリューションのもう 1 つの重要な側面は、全体のプロジェクト構造を適切に構築することです。 マルチプロジェクト ライブラリを構築するには、最上位レベルの `/src` フォルダーと `/test` フォルダーを使用する必要があります。

```
/AwesomeLibrary
|__global.json
|__/src
   |__/AwesomeLibrary.Core
      |__Source Files
      |__project.json
   |__/AwesomeLibrary.CSharp
      |__Source Files
      |__project.json
   |__/AwesomeLibrary.FSharp
      |__Source Files
      |__project.json
|__/test
   |__/AwesomeLibrary.Core.Tests
      |__Test Files
      |__project.json
   |__/AwesomeLibrary.CSharp.Tests
      |__Test Files
      |__project.json
   |__/AwesomeLibrary.FSharp.Tests
      |__Test Files
      |__project.json
```

このソリューションの `global.json` ファイルは次のようになります。

```json
{
    "projects":["src", "test"]
}
```

このアプローチは、`dotnet new` コマンドのプロジェクト テンプレートで確立された同じパターンに従います。すべてのプロジェクトは `/src` ディレクトリに配置され、すべてのテストは `/test` ディレクトリに配置されます。

パッケージを復元し、プロジェクト全体をビルドし、テストする方法は次のとおりです。

```
$ dotnet restore
$ cd src/AwesomeLibrary.FSharp
$ dotnet build
$ cd ../AwesomeLibrary.CSharp
$ dotnet build
$ cd ../../test/AwesomeLibrary.Core.Tests
$ dotnet test
$ cd ../AwesomeLibrary.CSharp.Tests
$ dotnet test
$ cd ../AwesomeLibrary.FSharp.Tests
$ dotnet test
```

以上です。



<!--HONumber=Nov16_HO1-->


