---
title: "dotnet-add パッケージ コマンド | Microsoft Docs"
description: "dotnet-add パッケージ コマンドは、NuGet パッケージ参照をプロジェクトに追加する便利なオプションを提供します。"
keywords: "dotnet-add , CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 88e0da69-a5ea-46cc-8b46-5493242b7af9
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 806f4383452cb250f302dc30ab2d59f7e4772026
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-add-package"></a>dotnet-add パッケージ

## <a name="name"></a>名前

`dotnet-add package` - プロジェクト ファイルにパッケージ参照を追加します。

## <a name="synopsis"></a>構文

```
dotnet add [project] package <package_name> [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]
dotnet add package [-h|--help]
```

## <a name="description"></a>説明

`dotnet add package` は、プロジェクト ファイルにパッケージ参照を追加する便利なオプションを提供します。 このコマンドの実行後に、追加対象のパッケージがプロジェクト内のすべてのフレームワークと互換性があることを確認する互換性チェックがあります。 互換性チェックに合格すると、[復元](dotnet-restore.md)が実行され、`<PackageReference>` フラグメントがプロジェクト ファイルに追加されます。

たとえば、`Newtonsoft.Json` を *ToDo.csproj* に追加すると、次のような出力が生成されます。

```
Microsoft (R) Build Engine version 15.1.545.13942
Copyright (C) Microsoft Corporation. All rights reserved.

  Writing /var/folders/gj/1mgg_4jx7mbdqbhw1kgcpcjr0000gn/T/tmpm0kTMD.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'ToDo.csproj'.
log  : Restoring packages for ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 119ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/9.0.1/newtonsoft.json.9.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/9.0.1/newtonsoft.json.9.0.1.nupkg 27ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '9.0.1' added to file 'ToDo.csproj'.
```

この *ToDo.csproj* ファイルには、参照されるパッケージの [`<PackageReference>`](https://docs.microsoft.com/nuget/consume-packages/package-references-in-project-files) フラグメントが含まれます。

```xml
<PackageReference Include="Newtonsoft.Json">
  <Version>9.0.1</Version>
</PackageReference>
```

## <a name="arguments"></a>引数

`project`

操作するプロジェクト ファイル。 指定されていない場合、現在のディレクトリで検索されます。

`package_name`

追加するパッケージ参照。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

`-v|--version <VERSION>`

パッケージのバージョン。

`-f|--framework <FRAMEWORK>`

特定のフレームワークを対象にしている場合にのみ、パッケージ参照を追加します。

`-n|--no-restore`

復元のプレビューと互換性チェックを実行せずにパッケージ参照を追加します。

`-s|--source <SOURCE>`

復元操作時に使用する特定の NuGet パッケージのソースを使用します。

`--package-directory <PACKAGE_DIRECTORY>`

指定したディレクトリにパッケージを復元します。

## <a name="examples"></a>例

`Newtonsoft.Json` NuGet パッケージをプロジェクトに追加する:

`dotnet add package Newtonsoft.Json`

特定バージョンのパッケージをプロジェクトに追加する:

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

特定の NuGet ソースを使用してパッケージを追加する:

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`

