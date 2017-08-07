---
title: "dotnet-add 参照コマンド - .NET Core CLI"
description: "dotnet-add 参照コマンドは、プロジェクト間参照を追加する便利なオプションを提供します。"
keywords: "dotnet-add, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e2a3efd-443c-4f23-a1b1-a662a5387879
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 98491efc183ad62f47275d0832a32dde5899373d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-add-reference"></a>dotnet-add 参照

## <a name="name"></a>名前

`dotnet-add reference` - プロジェクト間 (P2P) 参照を追加します。

## <a name="synopsis"></a>構文

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a>説明

`dotnet add reference` コマンドは、プロジェクトにプロジェクト参照を追加する便利なオプションを提供します。 このコマンドを実行すると、[`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) 要素がプロジェクト ファイルに追加されます。

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>引数

`PROJECT`

プロジェクト ファイルを指定します。 指定されていない場合、現在のディレクトリで検索されます。

`PROJECT_REFERENCES`

追加するプロジェクト間参照 (P2P) です。 1 つ以上のプロジェクトを指定します。 [glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースのシステムで利用できます。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

`-f|--framework <FRAMEWORK>`

特定の[フレームワーク](../../standard/frameworks.md)を対象にしている場合にのみ、プロジェクト参照を追加します。

## <a name="examples"></a>例

プロジェクト参照を追加する:

`dotnet add app/app.csproj reference lib/lib.csproj`

複数のプロジェクト参照を追加する:

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

Linux/Unix で glob パターンを使って複数のプロジェクト参照を追加する:

`dotnet add app/app.csproj reference **/*.csproj`

