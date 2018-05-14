---
title: dotnet msbuild コマンド - .NET Core CLI
description: dotnet msbuild コマンドは、MSBuild コマンド ラインへのアクセスを提供します。
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: c51c058391de4925afd4339fe84e28500d692e1a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>name

`dotnet msbuild` - プロジェクトとそのすべての依存関係をビルドします。

## <a name="synopsis"></a>構文

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a>説明

`dotnet msbuild` コマンドでは、完全に機能する MSBuild へのアクセスを許可します。

このコマンドには、既存の MSBuild コマンド ライン クライアントとまったく同じ機能があります。 オプションはすべて同じです。 使用可能なオプションについては、「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」をご覧ください。 

## <a name="examples"></a>使用例

プロジェクトとその依存関係をビルドします。

`dotnet msbuild`

リリース構成を使用して、プロジェクトとその依存関係をビルドします。

`dotnet msbuild /p:Configuration=Release`

発行先を実行して、RID `osx.10.11-x64` に発行します。

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

プロジェクト全体と SDK に付属するすべてのターゲットをご覧ください。

`dotnet msbuild /pp`
