---
title: ".NET Core バージョン管理"
description: ".NET Core バージョン管理"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: f6f684b1-1d2c-4105-8376-7c1959e23803
translationtype: Human Translation
ms.sourcegitcommit: 519253bd6dc105afb138268c62347c29a6072fbb
ms.openlocfilehash: 7be49f3ac7a7806e631eacf5004343919654881e
ms.lasthandoff: 04/05/2017

---

# <a name="net-core-versioning"></a>.NET Core バージョン管理

.NET Core は、フレームワークの [NuGet パッケージ](../packages.md)のプラットフォームであり、ユニットとして配布されます。 これらのプラットフォームの各レイヤーは、製品のアジリティ向上のため、および製品の変更を正確に記述するために、個別にバージョン管理できます。 バージョン管理には大きな柔軟性がありますが、製品を理解しやすいように、プラットフォームをユニットとしてバージョン管理することが望まれています。

この製品はいくつかの点でユニークであり、パッケージ マネージャー (NuGet) によってパッケージとして記述され提供されています。 通常は .NET Core をスタンドアロン SDK として取得しますが、SDK は主に NuGet パッケージを便利に体験できるものであり、パッケージと異なるものではありません。 したがって、最初にパッケージの観点からバージョン管理が行われ、以降にその他のバージョン管理が続きます。

## <a name="semantic-versioning"></a>セマンティック バージョン管理

.NET Core は[セマンティック バージョン管理 (SemVer)](http://semver.org/) を使用して、major.minor.patch バージョン管理を採用し、バージョン番号のさまざまな部分を使用して変更の度合いと種類を記述します。

通常、.NET Core には次のバージョン管理テンプレートが適用されます。 既存のバージョン管理に適合するように調整されているケースもあります。 これらのケースについては、このドキュメントの後の部分で説明されています。 たとえば、フレームワークはプラットフォームおよび API の機能を表すことのみを想定しており、メジャー/マイナー バージョン管理に適合します。

### <a name="versioning-form"></a>バージョン管理フォーム

MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]

### <a name="decision-tree"></a>デシジョン ツリー

次の場合は MAJOR です。
  - プラットフォームのサポートをドロップする
  - 既存の依存関係のさらに新しい MAJOR バージョンを採用する 
  - 互換性の独自設定のオフを既定で無効にする

次の場合は MINOR です。
  - パブリック API アクセス領域を追加する 
  - 新しいビヘイビアーを追加する
  - 既存の依存関係のさらに新しい MINOR バージョンを採用する
  - 新しい依存関係を導入する 
  
次の場合は PATCH です。
  - バグ修正を行う
  - より新しいプラットフォームのサポートを追加する
  - 既存の依存関係のさらに新しい PATCH バージョンを採用する
  - (キャプチャされていない) その他のすべての変更

複数の変更がある場合に何をインクリメントするかを判断するときは、最新の変更を選択します。

## <a name="versioning-scheme"></a>バージョン管理スキーム

.NET Core は、次の項目として定義でき、次の方法でバージョン管理されます。

- パッケージとして配布されるランタイムおよびフレームワークの実装。 特に修正プログラムのバージョン管理において、各パッケージは個別にバージョン管理されます。
- バージョン管理されたユニットとして詳細なパッケージを参照するメタパッケージのセット。 メタパッケージは、パッケージとは別個にバージョン管理されます。
- バージョン管理されたスナップショットのセットに記述されている、段階的に大きくなる API セットを表すフレームワークのセット (たとえば、`netstandard`)。

### <a name="packages"></a>パッケージ

ライブラリ パッケージは独立して進化し、バージョン管理されます。 .NET Framework システム\* アセンブリと重複するパッケージは、通常は 4.x バージョンを使用し、.NET Framework 4.x のバージョン管理 (履歴選択) に適合します。 .NET Framework ライブラリと重複しないパッケージ (たとえば、[System.Reflection.Metadata](https://www.nuget.org/packages/System.Reflection.Metadata)) は、通常は 1.0 から開始し、インクリメントしていきます。

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) によって記述されるパッケージは、プラットフォームのベースに位置するので、特別に扱われます。

- NETStandard.Library パッケージは、それらの間に実装レベルの依存関係があるため、通常はセットとしてバージョン管理されます。
- API は、.NET Core のメジャーまたはマイナー リリースの一部としてのみ、NETStandard.Library パッケージに追加されます。このような追加では、新しい `netstandard` バージョンの追加が必要となるためです。 これは SemVer 要件の追加要件です。

### <a name="metapackages"></a>メタパッケージ

.NET Core メタパッケージのバージョン管理は、マップ先のフレームワークに基づいています。 メタパッケージは、マップ先のフレームワークの最新のバージョン番号 (たとえば、netstandard1.6) をそのパッケージ クロージャに採用します。 

更新されたパッケージを参照するメタパッケージの更新は、メタパッケージの修正プログラム バージョンを使用して表されます。 修正プログラム バージョンには、更新されたフレームワーク バージョンが含まれることはありません。 したがって、メタパッケージは、厳密には SemVer 準拠であると言えません。そのバージョン管理スキームが、基になるパッケージでの変更の度合いを表さず、主に API レベルであるためです。 

.NET Core には、次の 2 の主なメタパッケージがあります。

**NETStandard.Library**

- .NET Core 1.0 の場合は v1.6 (これらのバージョンは、通常、または意図的に一致しません)。
- `netstandard` フレームワークにマップされます。 
- .NET プラットフォームが [.NET 標準](../../standard/library.md)プラットフォームと見なされるために実装しなければならない、最新のアプリ開発に必要と考えられるパッケージを記述します。

**Microsoft.NETCore.App**

- .NET Core 1.0 の場合は v1.0 (これらのバージョンは一致します)。
- `netcoreapp` フレームワークにマップされます。
- .NET Core 配布に含まれるパッケージを記述します。

注: [`Microsoft.NETCore.Portable.Compatibility`](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) は、別の .NET Core メタパッケージです。 特定のフレームワークにマップされないので、パッケージのようにバージョン管理されます。

### <a name="frameworks"></a>フレームワーク

フレームワーク バージョンは、新しい API が追加されると更新されます。 これらは API のシェイプを表し、実装には関係しないので、修正プログラム バージョンの概念はありません。 メジャーおよびマイナー バージョン管理は、前に指定した SemVer 規則に従います。

`netcoreapp` フレームワークは、.NET Core 配布に関連付けられており、 .NET Core で使用されるバージョン番号に従います。 たとえば、.NET Core 2.0 がリリースされると、`netcoreapp2.0` をターゲットとします。 `netstandard` フレームワークは、すべての .NET ランタイムに等しく適用できるので、そのいずれのバージョン管理スキームとも一致しません。

## <a name="versioning-in-practice"></a>実際のバージョン管理

GitHub の .NET Core リポジトリでは、コミットおよび PR が毎日発生し、多くのライブラリの新しいビルドが生成されます。 変更が行われるたびに、.NET Core の新しいパブリック バージョンを作成するのは実用的ではありません。 代わりに、.NET Core の新しいパブリック安定バージョンを作成する前に、大まかに定義された期間 (たとえば、数週間や数か月) にわたって、変更が集計されます。

.NET Core の新しいバージョンは、次の複数の意味を持ちます。

- パッケージおよびメタパッケージの新しいバージョン。
- 新しい API の追加を仮定した場合の、さまざまなフレームワークの新しいバージョン。
- .NET Core 配布の新しいバージョン。

### <a name="shipping-a-patch-release"></a>修正プログラム リリースの配布

.NET Core v1.0.0 の安定バージョンを配布した後は、バグを修正してパフォーマンスと信頼性を高めるために、.NET Core ライブラリに対して修正プログラム レベルの変更 (新しい API なし) が行われます。 更新された .NET Core ライブラリ パッケージを参照するように、さまざまなメタパッケージが更新されます。 メタパッケージは、修正プログラムの更新 (x.y.z) としてバージョン管理されます。 フレームワークは更新されません。 新しい .NET Core 配布は、`Microsoft.NETCore.App` メタパッケージと一致するバージョン番号でリリースされます。

次の project.json の例に示す修正プログラムの更新を参照してください。

```
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.1"
  },
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

### <a name="shipping-a-minor-release"></a>マイナー リリースの配布

.NET Core v1.0.0 の安定バージョンを配布した後は、新しいシナリオを有効にするために .NET Core ライブラリに新しい API が追加されます。 更新された .NET Core ライブラリ パッケージを参照するように、さまざまなメタパッケージが更新されます。 メタパッケージは、より新しいフレームワーク バージョンと一致するように、修正プログラムの更新 (x.y) としてバージョン管理されます。 新しい API を記述するように、さまざまなフレームワークが更新されます。 新しい .NET Core 配布は、`Microsoft.NETCore.App` メタパッケージと一致するバージョン番号でリリースされます。

次のプロジェクト ファイルの例に示すマイナー更新を参照してください。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp1.1</TargetFramework>
  </PropertyGroup>
</Project>
```

### <a name="shipping-a-major-release"></a>メジャー リリースの配布

.NET Core v1.y.z の安定バージョンを配布した後は、新しい主要なシナリオを有効にするために .NET Core ライブラリに新しい API が追加されます。 たとえば、プラットフォームのサポートがドロップされます。 更新された .NET Core ライブラリ パッケージを参照するように、さまざまなメタパッケージが更新されます。 `Microsoft.NETCore.App` メタパッケージと `netcore` フレームワークは、メジャー更新 (x.) としてバージョン管理されます。 `NETStandard.Library` メタパッケージは、複数の .NET 実装に適用されるので、マイナー更新 (x.y) としてバージョン管理される可能性があります。 新しい .NET Core 配布は、`Microsoft.NETCore.App` メタパッケージと一致するバージョン番号でリリースされます。

次のプロジェクト ファイルの例に示すメジャー更新を参照してください  (ただし、`netcoreapp2.0` はリリースされていません)。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
  </PropertyGroup>
</Project>

```

