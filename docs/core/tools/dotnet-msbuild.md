---
title: "dotnet msbuild コマンド - .NET Core CLI"
description: "dotnet msbuild コマンドは、MSBuild コマンド ラインへのアクセスを提供します。"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 96e4eac528abad2b336a979a98c9be2bee5d17ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>名前

`dotnet msbuild` - プロジェクトとそのすべての依存関係をビルドします。

## <a name="synopsis"></a>構文

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>説明

`dotnet msbuild` コマンドでは、完全に機能する MSBuild へのアクセスを許可します。

このコマンドには、既存の MSBuild コマンド ライン クライアントとまったく同じ機能があります。 オプションはすべて同じです。 使用可能なオプションについては、「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」をご覧ください。 

## <a name="examples"></a>例

プロジェクトとその依存関係をビルドします。

`dotnet msbuild`

リリース構成を使用して、プロジェクトとその依存関係をビルドします。

`dotnet msbuild /p:Configuration=Release`

発行先を実行して、RID `osx.10.11-x64` に発行します。

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

プロジェクト全体と SDK に付属するすべてのターゲットをご覧ください。

`dotnet msbuild /pp`
