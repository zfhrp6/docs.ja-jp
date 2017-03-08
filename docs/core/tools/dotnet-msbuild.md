---
title: "dotnet-msbuild コマンド | Microsoft Docs"
description: "dotnet-msbuild コマンドは、MSBuild コマンド ラインへのアクセスを提供します。"
keywords: "dotnet-msmsbuild, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
translationtype: Human Translation
ms.sourcegitcommit: 195664ae6409be02ca132900d9c513a7b412acd4
ms.openlocfilehash: a000e49a8672affe5b3bb9bd8a5f7e8095ab0aa9
ms.lasthandoff: 03/07/2017

---
#<a name="dotnet-msbuild"></a>dotnet-msbuild

## <a name="name"></a>名前

`dotnet-msbuild` - プロジェクトとそのすべての依存関係をビルドします。

## <a name="synopsis"></a>構文

```
dotnet msbuild <msbuild_arguments>
dotnet msbuild [-h]
```

## <a name="description"></a>説明

`dotnet msbuild` コマンドでは、完全に機能する MSBuild へのアクセスを許可します。 

このコマンドには、既存の MSBuild コマンド ライン クライアントとまったく同じ機能があります。 オプションはすべて同じです。 「[MSBuild コマンド ライン リファレンス](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference)」を使用すると、オプションについての理解を深めることができます。 

## <a name="examples"></a>例

プロジェクトとその依存関係をビルドします。

`dotnet msbuild`

リリース構成を使用して、プロジェクトとその依存関係をビルドします。

`dotnet msbuild /p:Configuration=Release`

発行先を実行して、RID `osx.10.11-x64` に発行します。

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`
