---
title: "dotnet-msbuild コマンド - .NET Core CLI | Microsoft Docs"
description: "dotnet-msbuild コマンドは、MSBuild コマンド ラインへのアクセスを提供します。"
keywords: "dotnet-msmsbuild, CLI, CLI コマンド, .NET Core"
author: blackdwarf
ms.author: mairaw
ms.date: 05/24/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: ffdc40ba-ef33-463e-aa35-b0af1fe615a2
ms.translationtype: Human Translation
ms.sourcegitcommit: df4b2ddd322e4bd2ebaf444439107e88a983f988
ms.openlocfilehash: 2267ef0b5785959456ea443405b6708a423d00ba
ms.contentlocale: ja-jp
ms.lasthandoff: 05/30/2017

---

<a id="dotnet-msbuild" class="xliff"></a>

# dotnet-msbuild

<a id="name" class="xliff"></a>

## 名前

`dotnet-msbuild` - プロジェクトとそのすべての依存関係をビルドします。

<a id="synopsis" class="xliff"></a>

## 構文

`dotnet msbuild <msbuild_arguments> [-h]`

<a id="description" class="xliff"></a>

## 説明

`dotnet msbuild` コマンドでは、完全に機能する MSBuild へのアクセスを許可します。

このコマンドには、既存の MSBuild コマンド ライン クライアントとまったく同じ機能があります。 オプションはすべて同じです。 使用可能なオプションについては、「[MSBuild コマンド ライン リファレンス](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference)」をご覧ください。 

<a id="examples" class="xliff"></a>

## 例

プロジェクトとその依存関係をビルドします。

`dotnet msbuild`

リリース構成を使用して、プロジェクトとその依存関係をビルドします。

`dotnet msbuild /p:Configuration=Release`

発行先を実行して、RID `osx.10.11-x64` に発行します。

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

プロジェクト全体と SDK に付属するすべてのターゲットをご覧ください。

`dotnet msbuild /pp`
