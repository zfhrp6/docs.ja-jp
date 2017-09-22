---
title: "dotnet new コマンド - .NET Core CLI"
description: "dotnet new コマンドは、指定されたテンプレートに基づいて新しい .NET Core プロジェクトを作成します。"
keywords: "dotnet-new, CLI, CLI コマンド, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: fcc3ed2e-9265-4d50-b59e-dc2e5c190b34
ms.translationtype: HT
ms.sourcegitcommit: a7af88d8d7b19e201c0f7829915e817daa61c838
ms.openlocfilehash: d64881380febee08414f57a36ed92079e8d69ed6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/08/2017

---
# <a name="dotnet-new"></a>dotnet new

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名前

`dotnet new` - 指定したテンプレートに基づいて、新しいプロジェクト、構成ファイル、またはソリューションを作成します。

## <a name="synopsis"></a>構文

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet new <TEMPLATE> [--force] [-i|--install] [-lang|--language] [-n|--name] [-o|--output] [-u|--uninstall] [Template options]
dotnet new <TEMPLATE> [-l|--list] [--type]
dotnet new [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet new <TEMPLATE> [-lang|--language] [-n|--name] [-o|--output] [-all|--show-all] [-h|--help] [Template options]
dotnet new <TEMPLATE> [-l|--list]
dotnet new [-all|--show-all]
dotnet new [-h|--help]
```
---

## <a name="description"></a>説明

`dotnet new` コマンドは、有効な .NET Core プロジェクトを初期化する便利な手段を提供します。 

このコマンドは、[テンプレート エンジン](https://github.com/dotnet/templating)を呼び出し、指定されたテンプレートとオプションに基づいて、ディスク上に成果物を作成します。

## <a name="arguments"></a>引数

`TEMPLATE`

コマンドが呼び出されたときにインスタンス化するテンプレート。 各テンプレートには、渡すことができるオプションが存在する場合があります。 詳細については、[テンプレートのオプション](#template-options)を参照してください。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

このコマンドには、テンプレートの既定の一覧が含まれています。 使用可能なテンプレートの一覧を取得するには、`dotnet new -l` を使います。 次の表は、.NET Core 2.0 SDK にプレインストールされているテンプレートの一覧です。 テンプレートの既定の言語は、角かっこで示されます。

|テンプレートの説明                          | テンプレート名  | 言語     |
|----------------------------------------------|----------------|---------------|
| コンソール アプリケーション                          | コンソール        | [C#], F#, VB  |
| クラス ライブラリ                                | classlib       | [C#], F#, VB  |
| 単体テスト プロジェクト                            | mstest         | [C#], F#, VB  |
| xUnit テスト プロジェクト                           | xunit          | [C#], F#, VB  |
| ASP.NET Core 空                           | Web            | [C#], F#      |
| ASP.NET Core Web アプリ (モデル ビュー コントローラー) | mvc            | [C#], F#      |
| ASP.NET Core Web アプリ                         | razor          | [C#]          |
| Angular 付きの ASP.NET Core                    | angular        | [C#]          |
| React.js 付きの ASP.NET Core                   | react          | [C#]          |
| React.js および Redux 付きの ASP.NET Core         | reactredux     | [C#]          |
| ASP.NET Core Web API                         | webapi         | [C#], F#      |
| global.json file                             | globaljson     |               |
| Nuget 構成                                 | nugetconfig    |               |
| Web 構成                                   | webconfig      |               |
| ソリューション ファイル                                | sln            |               |
| Razor ページ                                   | ページ           |               |
| MVC/ViewImports                              | viewimports    |               |
| MVC ViewStart                                | viewstart      |               |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

このコマンドには、テンプレートの既定の一覧が含まれています。 使用可能なテンプレートの一覧を取得するには、`dotnet new -all` を使います。 次の表は、.NET Core 1.x SDK にプレインストールされているテンプレートの一覧です。 テンプレートの既定の言語は、角かっこで示されます。

|テンプレートの説明  | テンプレート名  | 言語 |
|----------------------|----------------|-----------|
| コンソール アプリケーション  | コンソール        | [C#], F#  |
| クラス ライブラリ        | classlib       | [C#], F#  |
| 単体テスト プロジェクト    | mstest         | [C#], F#  |
| xUnit テスト プロジェクト   | xunit          | [C#], F#  |
| ASP.NET Core 空   | Web            | [C#]      |
| ASP.NET Core Web アプリ | mvc            | [C#], F#  |
| ASP.NET Core Web API | webapi         | [C#]      |
| Nuget 構成         | nugetconfig    |           |
| Web 構成           | webconfig      |           |
| ソリューション ファイル        | sln            |           |

---

## <a name="options"></a>オプション

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`--force`

既存のファイルを変更する場合でも、コンテンツが強制的に生成されます。 これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。

`-h|--help`

コマンドのヘルプを印刷します。 `dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。

`-i|--install <PATH|NUGET_ID>`

指定された `PATH` または `NUGET_ID` からソース パックまたはテンプレート パックをインストールします。 カスタム テンプレートの作成方法については、[「dotnet new のカスタム テンプレート」](custom-templates.md) を参照してください。

`-l|--list`

指定した名前を含むテンプレートを列挙します。 `dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。 たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。

`-lang|--language {C#|F#|VB}`

作成するテンプレートの言語。 使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。 一部のテンプレートでは無効です。

`-n|--name <OUTPUT_NAME>`

作成される出力の名前です。 名前が指定されていない場合、現在のディレクトリの名前が使用されます。

`-o|--output <OUTPUT_DIRECTORY>`

生成された出力を配置する場所。 既定値は、現在のディレクトリです。

`--type`

使用可能な種類に基づいて、テンプレートをフィルター処理します。 定義済みの値は、"project"、"item"、または "other" です。

`-u|--uninstall <PATH|NUGET_ID>`

指定された `PATH` または `NUGET_ID` で、ソース パックまたはテンプレート パックをアンインストールします。

> [!NOTE]
> `PATH` を使用してテンプレートをアンインストールするには、完全修飾パスを使用する必要があります。 たとえば、*C:/Users/\<ユーザー>/Documents/Templates/GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、*./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。
> また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-all|--show-all`

`dotnet new` コマンドのコンテキストでのみ実行すると、特定の種類のプロジェクトに対するすべてのテンプレートが表示されます。 `dotnet new web -all` など、特定のテンプレートのコンテキストで実行すると、`-all` は強制作成フラグとして解釈されます。 これは、出力ディレクトリに既にプロジェクトが含まれている場合に必要です。

`-h|--help`

コマンドのヘルプを印刷します。 `dotnet new` コマンド自体、または `dotnet new mvc --help` などの任意のテンプレートに対して呼び出すことができます。

`-l|--list`

指定した名前を含むテンプレートを列挙します。 `dotnet new` コマンドに対して呼び出すと、指定されたディレクトリで使用できるテンプレートが列挙されます。 たとえば、ディレクトリに既にプロジェクトが含まれている場合、すべてのプロジェクト テンプレートは列挙されません。

`-lang|--language {C#|F#}`

作成するテンプレートの言語。 使用できる言語は、テンプレートによって異なります ([引数](#arguments)の既定値を参照してください)。 一部のテンプレートでは無効です。

`-n|--name <OUTPUT_NAME>`

作成される出力の名前です。 名前が指定されていない場合、現在のディレクトリの名前が使用されます。

`-o|--output <OUTPUT_DIRECTORY>`

生成された出力を配置する場所。 既定値は、現在のディレクトリです。

---

## <a name="template-options"></a>テンプレート オプション

プロジェクト テンプレートはそれぞれ、追加のオプションが与えられている場合があります。 コア テンプレートの場合、次のオプションが追加されています。

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**console, angular, react, reactredux**

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**classlib**

`-f|--framework <FRAMEWORK>` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 値: .NET Core クラス ライブラリを作成するには `netcoreapp2.0`、.NET 標準クラス ライブラリを作成するには `netstandard2.0` です。 既定値は `netstandard2.0` です。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**mstest, xunit**

`-p|--enable-pack` - [dotnet pack](dotnet-pack.md) を使用してプロジェクトのパッケージ化を有効にします。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**globaljson**

`--sdk-version <VERSION_NUMBER>` - *global.json* ファイル内で使用する .NET Core SDK のバージョンを指定します。

**web**

`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**webapi**

`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。 次の値を指定できます。

- `None` - 認証は行われません (既定)。
- `IndividualB2C` - Azure AD B2C での個別認証。
- `SingleOrg` - 単一のテナントに対する組織認証。
- `Windows` - Windows 認証。

`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。 `IndividualB2C` 認証で使用します。 既定値は `https://login.microsoftonline.com/tfp/` です。

`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。 `IndividualB2C` 認証で使用します。

`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。 `SingleOrg` 認証で使用します。 既定値は `https://login.microsoftonline.com/` です。

`--client-id <ID>` - このプロジェクトのクライアント ID です。 `IndividualB2C` 認証または `SingleOrg` 認証で使用します。 既定値は `11111111-1111-1111-11111111111111111` です。

`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。 `SingleOrg` 認証または `IndividualB2C` 認証で使用します。 既定値は `qualified.domain.name` です。

`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。 `SingleOrg` 認証で使用します。 既定値は `22222222-2222-2222-2222-222222222222` です。

`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。 `SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。

`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。

`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。 `Individual` 認証または `IndividualB2C` 認証にのみ適用されます。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**mvc, razor**

`-au|--auth <AUTHENTICATION_TYPE>` - 使う認証の種類。 次の値を指定できます。

- `None` - 認証は行われません (既定)。
- `Individual` - 個別認証です。
- `IndividualB2C` - Azure AD B2C での個別認証。
- `SingleOrg` - 単一のテナントに対する組織認証。
- `MultiOrg` - 複数のテナントに対する組織認証です。
- `Windows` - Windows 認証。

`--aad-b2c-instance <INSTANCE>` - 接続先の Azure Active Directory B2C インスタンス。 `IndividualB2C` 認証で使用します。 既定値は `https://login.microsoftonline.com/tfp/` です。

`-ssp|--susi-policy-id <ID>` - このプロジェクト用のサインインおよびサインアップ ポリシー ID です。 `IndividualB2C` 認証で使用します。

`-rp|--reset-password-policy-id <ID>` - このプロジェクトのリセット パスワード ポリシー ID です。 `IndividualB2C` 認証で使用します。

`-ep|--edit-profile-policy-id <ID>` - このプロジェクトの編集プロファイル ポリシー ID です。 `IndividualB2C` 認証で使用します。

`--aad-instance <INSTANCE>` - 接続先の Azure Active Directory インスタンスです。 `SingleOrg` 認証または `MultiOrg` 認証で使用します。 既定値は `https://login.microsoftonline.com/` です。

`--client-id <ID>` - このプロジェクトのクライアント ID です。 `IndividualB2C` 認証、`SingleOrg` 認証、または `MultiOrg` 認証で使用します。 既定値は `11111111-1111-1111-11111111111111111` です。

`--domain <DOMAIN>` - ディレクトリ テナントのドメインです。 `SingleOrg` 認証または `IndividualB2C` 認証で使用します。 既定値は `qualified.domain.name` です。

`--tenant-id <ID>` - 接続先のディレクトリの TenantId ID です。 `SingleOrg` 認証で使用します。 既定値は `22222222-2222-2222-2222-222222222222` です。

`--callback-path <PATH>` - リダイレクト URI のアプリケーションの基本パス内の要求パスです。 `SingleOrg` 認証または `IndividualB2C` 認証で使用します。 既定値は `/signin-oidc` です。

`-r|--org-read-access` - このアプリケーションにディレクトリへの読み取りアクセスを許可します。 `SingleOrg` 認証または `MultiOrg` 認証にのみ適用されます。

`--use-launch-settings` - 生成されたテンプレート出力に *launchSettings.json* を含めます。

`--use-browserlink` - プロジェクトに BrowserLink を含めます。

`-uld|--use-local-db` - SQLite ではなく LocalDB が使用されるように指定します。 `Individual` 認証または `IndividualB2C` 認証にのみ適用されます。

`--no-restore` - プロジェクトの作成中には暗黙的な復元を実行しません。

**page**

`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。 既定値は `MyApp.Namespace` です。

`-np|--no-pagemodel` - PageModel なしでページを作成します。

**viewimports**

`-na|--namespace <NAMESPACE_NAME>` - 生成するコードの名前空間です。 既定値は `MyApp.Namespace` です。

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**console、xunit、mstest、web、webapi**

`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 値: `netcoreapp1.0` または `netcoreapp1.1` です。 既定値は `netcoreapp1.0` です。

**classlib**

`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 値: `netcoreapp1.0`、`netcoreapp1.1`、または `netstandard1.0` から `netstandard1.6` です。 既定値は `netstandard1.4` です。

**mvc**

`-f|--framework` - ターゲットにする[フレームワーク](../../standard/frameworks.md)を指定します。 値: `netcoreapp1.0` または `netcoreapp1.1` です。 既定値は `netcoreapp1.0` です。

`-au|--auth` - 使う認証の種類。 値: `None` または `Individual` です。 既定値は `None` です。

`-uld|--use-local-db` - SQLite の代わりに LocalDB を使うかどうかを指定します。 値: `true` または `false` です。 既定値は `false` です。

---

## <a name="examples"></a>例

現在のディレクトリに、F# コンソール アプリケーション プロジェクトを作成します。

`dotnet new console -lang f#`

指定したディレクトリ内に .NET 標準クラス ライブラリ プロジェクトを作成します (.NET Core 2.0 SDK またはそれ以降のバージョンでのみ使用可能)。

`dotnet new classlib -lang VB -o MyLibrary`

現在のディレクトリに新しい ASP.NET Core C# MVC アプリケーション プロジェクトを作成します。.NET Core 2.0 を対象にする認証はありません。

`dotnet new mvc -au None -f netcoreapp2.0`

.NET Core 2.0 を対象にする新しい xUnit アプリケーションを作成します。

`dotnet new xunit --framework netcoreapp2.0`

MVC に利用できるすべてのテンプレートを一覧表示します。

`dotnet new mvc -l`

## <a name="see-also"></a>関連項目

[dotnet new のカスタム テンプレート](custom-templates.md)  
[dotnet new のカスタム テンプレートを作成する](~/docs/core/tutorials/create-custom-template.md)  
[dotnet/dotnet-template-samples GitHub リポジトリ](https://github.com/dotnet/dotnet-template-samples)  
[dotnet new で使用できるテンプレート](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)

