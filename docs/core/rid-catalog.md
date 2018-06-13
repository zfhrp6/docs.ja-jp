---
title: .NET Core のランタイム識別子 (RID) のカタログ
description: ランタイム識別子 (RID) と .NET Core での RID の使用方法について説明します。
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.openlocfilehash: 81f9e5f65385bbd81c7fdae7f75c62d11b6f6319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215910"
---
# <a name="net-core-rid-catalog"></a>.NET Core の RID カタログ

RID は*ランタイム識別子*の略です。 RID の値は、アプリケーションが実行されている対象プラットフォームの識別に使用されます。
これは NuGet パッケージのプラットフォーム固有のアセットを表すために、.NET パッケージによって使用されます。 RID は、たとえば `linux-x64`、`ubuntu.14.04-x64`、`win7-x64`、または `osx.10.12-x64` などの値です。
ネイティブ依存関係のあるパッケージの場合、パッケージを復元できるプラットフォームが RID によって指定されます。

プロジェクト ファイルの `<RuntimeIdentifier>` 要素では、1 つの RID を設定できます。 複数の RID は、プロジェクト ファイルの `<RuntimeIdentifiers>` 要素でセミコロン区切りのリストとして定義できます。 以下の [.NET Core CLI コマンド](./tools/index.md)の `--runtime` オプションで使用することもできます。

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet store](./tools/dotnet-store.md)

具体的なオペレーティング システムを表す RID は通常、`[os].[version]-[architecture]-[additional qualifiers]` のようなパターンになります。それぞれ、次のような意味があります。

- `[os]` はオペレーティング システムまたはプラットフォーム システムのモニカーです。 たとえば、`ubuntu` のようにします。

- `[version]` は、オペレーティング システムのバージョンをドット区切りの形式 (`.`) で表したバージョン番号です。 たとえば、`15.10` のようにします。

  - バージョンはマーケティング バージョンに**しないでください**。プラットフォームの API アクセス領域が異なる、オペレーティング システムの複数の別々のバージョンを表すことがあるためです。

- `[architecture]` はプロセッサ アーキテクチャです。 たとえば `x86`、`x64`、`arm` または `arm64` などです。

- `[additional qualifiers]` はさまざまなプラットフォームをさらに区別します。 例 : `aot` または `corert`。

## <a name="rid-graph"></a>RID グラフ

RID グラフまたはランタイム フォールバック グラフとは、相互に互換性のある RID の一覧です。 RID は [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) パッケージで定義されています。 サポートされている RID および RID グラフの一覧は、CoreFX リポジトリにある [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) ファイルで確認できます。 このファイルでは、基本となる RID を除くすべての RID に `"#import"` ステートメントが記述されていることを確認できます。 このステートメントは互換性のある RID を示しています。

NuGet はパッケージを復元する際、指定されたランタイムと正確に一致するものを見つけようとします。
正確に一致するものが見つからない場合、NuGet は、RID グラフに基づいて最も互換性のあるシステムが見つかるまでグラフを遡ります。

次に示す例は、`osx.10.12-x64` の RID として実際に記述されているものです。

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

上の RID は `osx.10.12-x64` が `osx.10.11-x64` をインポートすることを指定します。 そのため、NuGet はパッケージを復元する際、`osx.10.12-x64` と正確に一致するものをパッケージから見つけようとします。 特定のランタイムが見つからなかった場合、NuGet は、たとえば `osx.10.11-x64` ランタイムを指定しているパッケージを復元できます。

次の例は、*runtime.json* ファイルにも定義されている少し大きめの RID グラフです。

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

すべての RID は最終的にルート `any` RID にマッピングされます。

RID を使用する際に留意しておく必要のある注意事項があります。

- RID は**不透明な文字列**であり、ブラック ボックスとして処理する必要があります。
- RID をプログラムによって作成しないでください。
- プラットフォームであらかじめ定義されている RID を使用します。
- RID は特定の値である必要があるため、実際の値から推測した値にしないでください。

## <a name="using-rids"></a>RID の使用

RID を使用するには、どのような RID があるのか知る必要があります。 プラットフォームには新しい RID が定期的に追加されます。
最新の完全バージョンについては、CoreFX リポジトリの [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) ファイルをご覧ください。

.NET Core 2.0 SDK には、ポータブル RID の概念が導入されています。 これは、RID グラフに新しく追加された値であり、特定のバージョンや OS のディストリビューションに関連付けられていません。 特に、複数の Linux ディストリビューションを扱うときに便利です。

次の一覧に、各 OS に使用される最も一般的な RID を示します。 `arm` と `corert` の値は対象外です。

## <a name="windows-rids"></a>Windows RID

- ポータブル
  - `win-x86`
  - `win-x64`
- Windows 7 / Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
- Windows 8 / Windows Server 2012
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- Windows 8.1 / Windows Server 2012 R2
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- Windows 10 / Windows Server 2016
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

詳細については、「[Windows における .NET Core の前提条件](windows-prerequisites.md)」を参照してください。

## <a name="linux-rids"></a>Linux RID

- ポータブル
  - `linux-x64`
- CentOS
  - `centos-x64`
  - `centos.7-x64`
- Debian
  - `debian-x64`
  - `debian.8-x64`
- Fedora
  - `fedora-x64`
  - `fedora.24-x64`
  - `fedora.25-x64` (.NET Core 2.0 以降)
  - `fedora.26-x64` (.NET Core 2.0 以降)
- Gentoo (.NET Core 2.0 以降)
  - `gentoo-x64`
- openSUSE
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- Oracle Linux
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- Red Hat Enterprise Linux
  - `rhel-x64`
  - `rhel.6-x64` (.NET Core 2.0 以降)
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - `rhel.7.3-x64` (.NET Core 2.0 以降)
  - `rhel.7.4-x64` (.NET Core 2.0 以降)
- Tizen (.NET Core 2.0 以降)
  - `tizen`
- Ubuntu
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- Ubuntu の派生ディストリビューション
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - `linuxmint.18.1-x64` (.NET Core 2.0 以降)

詳細については、「[Linux における .NET Core の前提条件](linux-prerequisites.md)」を参照してください。

## <a name="macos-rids"></a>macOS RID

macOS RID では、以前の "OSX" ブランドが使用されています。

- `osx-x64` (.NET Core 2.0 以降のバージョン、最小バージョンは `osx.10.12-x64`)
- `osx.10.10-x64`
- `osx.10.11-x64`
- `osx.10.12-x64` (.NET Core 1.1 以降)
- `osx.10.13-x64`

詳細については、「[macOS における .NET Core の前提条件](macos-prerequisites.md)」を参照してください。

## <a name="android-rids-net-core-20-or-later-versions"></a>Android RID (.NET Core 2.0 以降)

- `android`
- `android.21`

## <a name="see-also"></a>関連項目

[ランタイム ID](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
