---
title: "dotnet-msbuild コマンド | Microsoft Docs"
description: "dotnet-msbuild コマンドは、MSBuild コマンド ラインへのアクセスを提供します。"
keywords: "dotnet-msmsbuild, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 10/13/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: 06d4210e5dff97d3e96efff8ae8e84efc27fb7d2

---

#<a name="dotnet-msbuild"></a>dotnet-msbuild

[!INCLUDE[preview-warning](../../../includes/warning.md)]

## <a name="name"></a>名前 
dotnet-msbuild -- プロジェクトとそのすべての依存関係をビルドします。

## <a name="synopsis"></a>構文

`dotnet msbuild <msbuild_arguments>`

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



<!--HONumber=Jan17_HO3-->


