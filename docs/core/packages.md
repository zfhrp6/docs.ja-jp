---
title: "パッケージ、メタパッケージ、フレームワーク"
description: "パッケージ、メタパッケージ、フレームワーク"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 609b0845-49e7-4864-957b-21ffe1b93bf2
translationtype: Human Translation
ms.sourcegitcommit: cb2e83b35b5a4aae14c89bcbdf26b064885a477a
ms.openlocfilehash: af6c83755068cc311b59c1a337898c177cc6d537

---

# <a name="packages-metapackages-and-frameworks"></a>パッケージ、メタパッケージ、フレームワーク

.NET Core は、NuGet パッケージで作成されたプラットフォームです。 製品のエクスペリエンスには、粒度の細かいパッケージの定義から恩恵を受けるものもあれば、粒度の粗いパッケージの定義から恩恵を受けるものもあります。 この二重性に対応するために、製品は、粒度の細かいパッケージ セットとして配布され、俗に "メタパッケージ" と呼ばれるパッケージの種類を使用して粒度の粗いチャンク単位で記述されます。

各 .NET Core パッケージは、フレームワークとして表現される、複数の .NET ランタイムでの実行に対応しています。 このようなフレームワークには、`net46` (.NET Framework に相当する) のような従来のフレームワークもあれば、 フレームワークを定義するために新しいモデルを確立し、"パッケージ ベースのフレームワーク" と見なすことができる新しいフレームワークもあります。 パッケージ ベースのフレームワークは、完全にパッケージとして形成および定義されるので、パッケージとフレームワークの間に強力なリレーションシップが形成されます。

## <a name="packages"></a>パッケージ

.NET core は、プリミティブ、上位レベルのデータ型、アプリ コンポジション型、および一般的なユーティリティを提供する一連のパッケージに分割されます。 これらのパッケージはいずれも、同じ名前の単一アセンブリです。 たとえば、[System.Runtime](https://www.nuget.org/packages/System.Runtime) には、System.Runtime.dll が含まれています。 

粒度の細かい方法でパッケージを定義することには、次の利点があります。

- 粒度の細かいパッケージの場合は、ほかのパッケージのテストが比較的に抑えられるので、独自のスケジュールに合わせて配布することができます。
- 粒度の細かいパッケージでは、さまざまな OS および CPU をサポートできます。
- 粒度の細かいパッケージは、1 つライブラリのみに固有の依存関係を持つことができます。
- アプリ配布の対象に未参照のパッケージが含まれないので、アプリのサイズが小さくなります。

これらの利点の一部は、特定の状況でのみ使用されます。 たとえば、NET Core パッケージは、通常、同じプラットフォーム サポートを使用して、同じスケジュールで配布されます。 サポートを行う場合は、修正プログラムをサイズの小さな単一のパッケージ更新プログラムとして配布およびインストールすることができます。 変更の範囲が狭いため、検証と修正プログラムを使用できるようにするまでの時間は、単一のライブラリで必要とされる内容に限定されます。

.NET Core 用の主な NuGet パッケージを次に一覧します。

- [System.Runtime](https://www.nuget.org/packages/System.Runtime) - 最も基本的な .NET Core パッケージです。[Object](http://docs.microsoft.com/dotnet/core/api/System.Object)、[String](http://docs.microsoft.com/dotnet/core/api/System.String)、[Array](http://docs.microsoft.com/dotnet/core/api/System.Array)、[Action](http://docs.microsoft.com/dotnet/core/api/System.Action)、[IList&lt;T&gt;](http://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IList-1) などがあります。
- [System.Collections](https://www.nuget.org/packages/System.Collections) - (主な) ジェネリック コレクションのセットです。[List&lt;T&gt;](http://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.List-1) や [Dictionary&lt;K,V&gt;](http://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.Dictionary-2) などがあります。
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) - HTTP ネットワーク通信の種類のセットです。[HttpClient](http://docs.microsoft.com/dotnet/core/api/System.Net.Http.HttpClient) や [HttpResponseMessage](http://docs.microsoft.com/dotnet/core/api/System.Net.Http.HttpResponseMessage) などがあります。
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) - ローカルまたはネットワークに接続されたディスク ベースの記憶域に対する読み取りおよび書き込みの種類のセットです。[File](http://docs.microsoft.com/dotnet/core/api/System.IO.File) や [Directory](http://docs.microsoft.com/dotnet/core/api/System.IO.Directory) などがあります。
- [System.Linq](https://www.nuget.org/packages/System.Linq) - オブジェクトに対するクエリの種類のセットです。Enumerable や [ILookup&lt;TKey, TElement&gt;](http://docs.microsoft.com/dotnet/core/api/System.Linq.ILookup-2) などがあります。
- [System.Reflection](https://www.nuget.org/packages/System.Reflection) - 読み込み、検査、およびアクティブ化の種類のセットです。[Assembly](http://docs.microsoft.com/dotnet/core/api/System.Reflection.Assembly)、[TypeInfo](http://docs.microsoft.com/dotnet/core/api/System.Reflection.TypeInfo)、[MethodInfo](http://docs.microsoft.com/dotnet/core/api/System.Reflection.MethodInfo) などがあります。

パッケージは project.json で参照されます。 次の例では、[System.Runtime](https://www.nuget.org/packages/System.Runtime/) パッケージが参照されています。 

```json
{
  "dependencies": {
    "System.Runtime": "4.1.0"
  },
  "frameworks": {
    "netstandard1.6": {}
  }
}
```

ほとんどの場合、下位レベルの .NET Core パッケージを直接参照することはありません。最終的に管理対象のパッケージが多くなりすぎるためです。 代わりに、メタパッケージを参照します。

## <a name="metapackages"></a>メタパッケージ

メタパッケージは、統合して意味をなすパッケージ セットを記述するための NuGet パッケージの規則です。 メタパッケージでは、パッケージ間に依存関係を設定して、パッケージ セットを表現します。 メタパッケージでは必要に応じて、フレームワークを指定して、このパッケージ セットのフレームワークを確立することができます。 

メタパッケージを参照することにより、各依存パッケージへの参照を 1 つのジェスチャとして実際に追加します。 つまり、そのようなパッケージ内のライブラリはすべて、IntelliSense (または同様のエクスペリエンス) で使用することができ (ref または lib)、さらにアプリの公開でも使用できます (lib のみ)。 

注: 用語 "lib" と "ref" は、NuGet パッケージ内のフォルダーを示します。 "ref" フォルダーでは、アセンブリ メタデータを使用してパッケージのパブリック API について記述します。 "lib" フォルダーには、特定のフレームワーク用のそのパブリック API の実装が含まれます。 

メタパッケージを使用する利点は次のとおりです。

- 一連の粒度の細かいパッケージを参照するのに便利なユーザー エクスペリエンスを提供できます。 
- テストされ一体となって優れた機能を発揮するパッケージ セット (特定のバージョンを含む) を定義できます。

.NET Standard Library のメタパッケージ:

- [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) - ".NET Standard Library" に含まれるライブラリについて記述します。 .NET Standard Library をサポートするすべての .NET 実装 (.NET Framework、.NET Core および Mono など) に適用されます。 "netstandard" フレームワークを確立します。

主な .NET Core メタパッケージを次に示します。

- [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) - .NET Core 配布に含まれるライブラリについて記述します。 [`.NETCoreApp` フレームワーク](https://github.com/dotnet/core-setup/blob/master/pkg/projects/Microsoft.NETCore.App/Microsoft.NETCore.App.pkgproj)を確立します。 よりサイズの小さな `NETStandard.Library` に依存します。
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) - mscorlib ベースのポータブル クラス ライブラリ (PCL) を .NET Core で実行できるようにするための互換性ファサードのセットです。

メタパッケージは、ほかの NuGet パッケージと同じように project.json で参照されます。 

次の例では、.NET ランタイム間で移植可能なライブラリの作成に使用される `NETStandard.Library` メタ パッケージが参照されています。

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  },
  "frameworks": {
    "netstandard1.6": {}
  }
}
```

次の例では、.NET Core で実行され .NET Core をフル活用することを意図したアプリおよびライブラリを作成する場合に使用される `Microsoft.NETCore.App` メタパッケージが参照されています。 `NETStandard.Library` によって指定されたサイズの大きなライブラリ セットへのアクセスを実現します。

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0"
  },
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

## <a name="frameworks"></a>フレームワーク

各 .NET Core パッケージは、フレームワーク フォルダー (前述した lib フォルダーおよび ref フォルダー内の) で宣言されたフレームワーク セットをサポートします。 フレームワークでは、特定のフレームワークを対象とするときに依存することができる使用可能な API セット (および、場合によってはその他の特性) について記述します。 フレームワークのバージョンは、新しい API が追加されると更新されます。

たとえば、 [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) では、次のフレームワークをサポートします。

- .NETFramework,Version=4.6
- .NETStandard,Version=1.3
- 6 Xamarin プラットフォーム (xamarinios10 など)

上記フレームワークの最初の 2 つの例は、フレームワークの 2 種類の定義方法を示したものであるので、この 2 つを比べることには意義があります。

`.NETFramework,Version=4.6` フレームワークは、.NET Framework 4.6 で使用できる API を表します。 .NET Framework 4.6 参照アセンブリでコンパイルされたライブラリを生成し、NuGet パッケージの net46 lib フォルダーに置かれているそれらのライブラリを配布することができます。 このフレームワークは、.NET Framework 4.6 を対象とするアプリ、または .NET Framework 4.6 と互換性のあるアプリで使用されます。 これは、すべてのフレームワークの従来のしくみです。

`.NETStandard,Version=1.3` フレームワークは、パッケージ ベースのフレームワークです。 これは、フレームワークに関して API を定義して公開するためにフレームワークを対象とするパッケージに依存します。

## <a name="packagebased-frameworks"></a>パッケージ ベースのフレームワーク

フレームワークとパッケージの間には双方向のリレーションシップがあります。 リレーションシップの 1 番目の部分は、特定のフレームワーク (`netstandard1.3` など) で使用可能な API を定義することです。 `netstandard1.3` (または`netstandard1.0` のような互換性のあるフレームワーク) を対象とするパッケージは、`netstandard1.3` で使用可能な API を定義します。 循環定義のように思われるかもしれませんが、そうではありません。 "パッケージ ベース" であるため、フレームワークの API 定義は、パッケージから取得されます。 フレームワーク自体で、API の定義は行われません。

リレーションシップの 2 番目の部分は、資産の選択です。 パッケージには、複数のフレームワークの資産を含めることができます。 パッケージ セットおよび/またはメタパッケージ セットへの参照を指定する場合は、選択すべき資産 (たとえば、`net46` または `netstandard1.3`) を決定するためにフレームワークが必要です。 正しい資産を選択することが重要です。 たとえば、`net46` 資産が .NET Framework 4.0 または .NET Core 1.0 と互換性を持たない可能性があります。

![パッケージ ベースのフレームワークのコンポジション](./media/packages/package-framework.png)

このリレーションシップは上図のようになります。 *API* は、*フレームワーク*を対象とし、定義します。 *フレームワーク*は、*資産の選択*で使用されます。 *資産* は、API を提供します。

パッケージ ベースのフレームワークの定義がどこで終了し、その定義の利用がどこで始まるのかは、興味深い問題です。 フレームワークのビューを特定の project.json ファイルの機能とみなす場合もあるでしょう。 依存関係の発行者とは別に、依存関係はフレームワークのビューを作成します。

.NET Core では、次の 2 つのパッケージ ベースのプライマリ フレームワークが使用されます。

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

.NET Standard (TFM: `netstandard`) フレームワークは、[.NET Standard Library](../standard/library.md) によって定義され、.NET Standard Library の上に構築された API を表します。 複数のランタイムでの実行を意図したライブラリは、このフレームワークを対象とする必要があります。 それらのライブラリは、.NET Core、.NET Framework、Mono/Xamarin など、.NET Standard 準拠のランタイムでサポートされます。 このようなランタイムはそれぞれが、実装される API に応じて、一連の .NET Standard バージョンをサポートします。 

`NETStandard.Library` メタパッケージは、`netstandard` フレームワークを対象とします。 `netstandard` を対象とする最も一般的な方法は、このメタパッケージを参照することです。 それは、.NET Standard Library を定義する約 40 の .NET ライブラリと関連する API について説明しており、それらにアクセスできるようにしています。 `netstandard` を対象とする追加のパッケージを参照することで、追加の API へのアクセス権を取得できます。

特定の [NETStandard.Library バージョン](versions/index.md) は、(クロージャを介して) 公開された最上位の `netstandard` バージョンと一致します。 project.json 内のフレームワーク参照は、基になるパッケージから適切な資産を選択するために使用されます。 この場合、`netstandard1.6` 資産は、`netstandard1.4` や `net46` とは対照的に必須となります。 

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  },
  "frameworks": {
    "netstandard1.6": {}
  }
}
```

project.json 内のフレームワーク参照とメタパッケージ参照は一致する必要はありません。 たとえば、次の project.json が有効です。

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  },
  "frameworks": {
    "netstandard1.3": {}
  }
}
```

`netstandard1.3` を対象とするのに `NETStandard.Library` のバージョン 1.6.0 を使用するのは、奇妙に思えるかもしれません。 これは、メタパッケージでは古い `netstandard` バージョンのサポートが継続されていることから、使用例として有効です。 メタパッケージのバージョン 1.6.0 が標準とされている状況で、これをすべてのライブラリ (`netstandard` の各種バージョンを対象とする) で使用する場合が考えられます。 この方法を使用した場合、`NETStandard.Library` 1.6.0 を復元する必要があるだけで、それより前のバージョンの復元は必要ありません。 

逆は無効になります (`netstandard1.6` を対象とするが、`NETStandard.Library` のバージョン 1.3.0 を使用する)。 上位フレームワークと下位メタパッケージの組み合わせを対象とすることはできません。下位バージョンのメタパッケージはその上位フレームワークに対して資産を公開しないことが理由です。 メタパッケージの [バージョン管理スキーム] は、メタパッケージが、記述したフレームワークの最上位バージョンと一致することをアサートします。 バージョン管理スキームにより、`netstandard1.6` 資産が含まれている場合、`NETStandard.Library` の最初のバージョンは v1.6.0 となります。 上記の例では対称性を考慮して v1.3.0 が使用されていますが、実際には存在しません。

### <a name="net-core-application"></a>.NET Core アプリケーション

.NET Core アプリケーション (TFM: `netcoreapp`) フレームワークは、.NET Core 配布に付属のパッケージおよび関連する API と、.NET Core 配布によって提供されるコンソール アプリケーション モデルを表します。 .NET Core アプリは、コンソール アプリケーション モデルを対象とすることから、.NET Core での実行のみを意図するライブラリとして、このフレームワークを使用する必要があります。 このフレームワークを使用すると、アプリとライブラリは .NET Core でのみの実行に限定されます。 

`Microsoft.NETCore.App` メタパッケージは、`netcoreapp` フレームワークを対象とします。 これは、約 60 のライブラリにアクセスできるようにします (約 40 個は `NETStandard.Library` パッケージによって提供され、さらに約 20 個の追加分)。 `netcoreapp` または互換性を持つフレームワーク (`netstandard` など) を対象とする追加のライブラリを参照することで、追加の API にアクセスできます。 

`Microsoft.NETCore.App` によって提供される追加ライブラリの大部分も、依存関係がほかの `netstandard` ライブラリによって満足されるならば、`netstandard` を対象とします。 つまり、`netstandard` ライブラリは、それらのパッケージを依存関係として参照することもできます。 


<!--HONumber=Nov16_HO1-->


