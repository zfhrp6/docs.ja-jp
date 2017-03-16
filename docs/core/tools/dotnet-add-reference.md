---
title: "dotnet-add 参照コマンド | Microsoft Docs"
description: "dotnet-add 参照コマンドは、プロジェクト間参照を追加する便利なオプションを提供します。"
keywords: "dotnet-add, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e2a3efd-443c-4f23-a1b1-a662a5387879
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: 7d23377244cfe60730b50bd247209de6e90bec70
ms.lasthandoff: 03/07/2017

---
# <a name="dotnet-add-reference"></a>dotnet-add 参照

## <a name="name"></a>名前

`dotnet-add reference` - プロジェクト間参照を追加します。

## <a name="synopsis"></a>構文

```
dotnet add [project] reference [-f|--framework] <project_references>
dotnet add reference [-h|--help]
```

## <a name="description"></a>説明

`dotnet add reference` コマンドは、プロジェクトにプロジェクト参照を追加する便利なオプションを提供します。 このコマンドを実行すると、[`<ProjectReference>`](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-items) フラグメントがプロジェクト ファイルに追加されます。

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>引数

`project`

操作するプロジェクト ファイル。 指定されていない場合、現在のディレクトリで検索されます。

`project_references`

追加するプロジェクト間参照。 1 つまたは複数のプロジェクトを指定できます。 glob パターンは Unix/Linux ベースの端末で利用できます。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

`-f|--framework <FRAMEWORK>`

特定のフレームワークを対象にしている場合にのみ、プロジェクト参照を追加します。

## <a name="examples"></a>例

プロジェクト参照を追加する:

`dotnet add app/app.csproj reference lib/lib.csproj`

複数のプロジェクト参照を追加する:

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

Linux/Unix でグロビング パターンを使用して複数のプロジェクト参照を追加する:

`dotnet add app/app.csproj reference **/*.csproj`
