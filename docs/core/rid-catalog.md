---
title: ".NET Core のランタイム識別子 (RID) のカタログ"
description: ".NET Core のランタイム識別子 (RID) のカタログ"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 08/22/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b2032f5d-771f-48d9-917c-587d9509035c
translationtype: Human Translation
ms.sourcegitcommit: 811b9539019b7cc2817b5742760ae52fbc2f95dd
ms.openlocfilehash: fc59a9f3333f01caf9622dd500a5de6e2ae5132b
ms.lasthandoff: 03/02/2017

---

# <a name="net-core-runtime-identifier-rid-catalog"></a>.NET Core のランタイム識別子 (RID) のカタログ

## <a name="what-are-rids"></a>RID とは何か。
RID は*ランタイム識別子*の略です。 RID は、アプリケーションやアセット (つまり、アセンブリ) が実行されるターゲット オペレーティング システムを特定するために利用されます。 "ubuntu.14.04-x64"、"win7-x64"、"osx.10.11-x64" のような識別子です。 ネイティブ依存関係のあるパッケージの場合、パッケージを復元できるプラットフォームが指定されます。 

重要なことですが、RID は不透明な文字列です。 つまり、それを利用する操作に適合する必要があります。 たとえば、[Elementary OS](https://elementary.io/) の場合を考えてみます。これは Ubuntu 14.04 の単純なクローンです。 .NET Core と CLI はこのバージョンの Ubuntu の上で動作しますが、変更せずに Elementary OS の上で使用すると、パッケージの復元に失敗します。 これは、現在のところ、Elementary OS をプラットフォームとして指名する RID がないためです。 

具体的なオペレーティング システムを表す RID は通常、`[os].[version]-[arch]` のようなパターンになります。それぞれ、次のような意味があります。
- `[os]` はオペレーティング システムのモニカー (`ubuntu` など) です。
- `[version]` は、バージョン番号をドット (`.`) で区切った形式のオペレーティング システムのバージョンです (例: `15.10`)。厳密な番号であり、これを利用することで、アセットはそのバージョンで表されるオペレーティング システム プラットフォーム API をターゲットにできます。
  - これをマーケティング バージョンに**しないでください**。プラットフォーム API の表面が異なる、個別バージョンの複数のオペレーティング システムを表すことがあるためです。
- `[arch]` はプロセッサ アーキテクチャです (例: `x86`、`x64`、`arm`、`arm64`)。

RID グラフは「`runtime.json`」という名前のファイルに入っている「`Microsoft.NETCore.Platforms`」という名前のパッケージに定義されています。これは [CoreFX リポジトリ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json)で確認できます。 このファイルを使用する場合、RID の一部に `"#import"` ステートメントが与えられます。 それらのステートメントは互換性ステートメントです。 つまり、インポートした RID を含む RID はその RID のパッケージを復元するためのターゲットになります。 少しわかりにくいですが、例を見てみましょう。 macOS の例:

```json
"osx.10.11-x64": {
    "#import": [ "osx.10.11", "osx.10.10-x64" ]
}
```
上の RID は `osx.10.11-x64` が `osx.10.10-x64` をインポートすることを指定します。 つまり、パッケージを復元するとき、`osx.10.10-x64` を `osx.10.11-x64` で必要とすることを指定するパッケージを NuGet で復元できます。

少し大きくした RID グラフの例:  

- `win10-arm`
  - `win10`
  - `win81-arm`
    - `win81`
    - `win8-arm`
      - `win8`
        - `win7`
          - `win`
            - `any`

すべての RID は最終的にルート `any` RID にマッピングされます。

使用は簡単に見えますが、RID にはいくつか特別な条件があり、使用時にはそれに注意する必要があります。

* **不透明な文字列**であり、ブラック ボックスとして処理する必要があります
    * RID をプログラミングで構築することはできません
* プラットフォームに既に定義されている RID を使用する必要があり、それは本書で説明するとおりです
* RID は限定する必要がなく、実際の RID 値からは何も推測しないでください (特定のプラットフォームに必要な RID については本書を参照してください)

## <a name="using-rids"></a>RID の使用
RID を使用するには、どのような RID があるのか知る必要があります プラットフォームには新しい RID が定期的に追加されます。 最新バージョンについては、CoreFX リポジトリの [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) ファイルをご覧ください。

> [!NOTE]
> この情報をよりインタラクティブな形式にするために取り組んでいます。 それが実現した際には、このページを更新し、そのツールと使用方法が記載されたドキュメントを紹介します。 

## <a name="windows-rids"></a>Windows RID

* Windows 7 / Windows Server 2008 R2
    * `win7-x64`
    * `win7-x86`
* Windows 8 / Windows Server 2012
    * `win8-x64`
    * `win8-x86`
    * `win8-arm`
* Windows 8.1 / Windows Server 2012 R2
    * `win81-x64`
    * `win81-x86`
    * `win81-arm`
* Windows 10 / Windows Server 2016
    * `win10-x64`
    * `win10-x86`
    * `win10-arm`
    * `win10-arm64`

## <a name="linux-rids"></a>Linux RID

* Red Hat Enterprise Linux
    * `rhel.7-x64`
* Ubuntu
    * `ubuntu.14.04-x64`
    * `ubuntu.14.10-x64`
    * `ubuntu.15.04-x64`
    * `ubuntu.15.10-x64`
    * `ubuntu.16.04-x64`
    * `ubuntu.16.10-x64`
* CentOS
    * `centos.7-x64`
* Debian
    * `debian.8-x64`
* Fedora
    * `fedora.23-x64`
    * `fedora.24-x64`
* OpenSUSE
    * `opensuse.13.2-x64`
    * `opensuse.42.1-x64`
* Oracle Linux
    * `ol.7-x64`
    * `ol.7.0-x64`
    * `ol.7.1-x64`
    * `ol.7.2-x64`
* 現在サポートされている Ubuntu 派生製品 
    * `linuxmint.17-x64`
    * `linuxmint.17.1-x64`
    * `linuxmint.17.2-x64`
    * `linuxmint.17.3-x64`
    * `linuxmint.18-x64`

## <a name="os-x-rids"></a>OS X RID

* `osx.10.10-x64`
* `osx.10.11-x64`
* `osx.10.12-x64`

