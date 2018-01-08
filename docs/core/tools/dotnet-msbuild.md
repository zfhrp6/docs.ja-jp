---
title: "dotnet msbuild コマンド - .NET Core CLI"
description: "dotnet msbuild コマンドは、MSBuild コマンド ラインへのアクセスを提供します。"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 682b49d44c0fb8242eeb3cb8bf4d158f73b4b9a5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="a9445-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="a9445-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a9445-104">name</span><span class="sxs-lookup"><span data-stu-id="a9445-104">Name</span></span>

<span data-ttu-id="a9445-105">`dotnet msbuild` - プロジェクトとそのすべての依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="a9445-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a9445-106">構文</span><span class="sxs-lookup"><span data-stu-id="a9445-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="a9445-107">説明</span><span class="sxs-lookup"><span data-stu-id="a9445-107">Description</span></span>

<span data-ttu-id="a9445-108">`dotnet msbuild` コマンドでは、完全に機能する MSBuild へのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="a9445-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="a9445-109">このコマンドには、既存の MSBuild コマンド ライン クライアントとまったく同じ機能があります。</span><span class="sxs-lookup"><span data-stu-id="a9445-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="a9445-110">オプションはすべて同じです。</span><span class="sxs-lookup"><span data-stu-id="a9445-110">The options are all the same.</span></span> <span data-ttu-id="a9445-111">使用可能なオプションについては、「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a9445-111">Use the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) to obtain information on the available options.</span></span> 

## <a name="examples"></a><span data-ttu-id="a9445-112">使用例</span><span class="sxs-lookup"><span data-stu-id="a9445-112">Examples</span></span>

<span data-ttu-id="a9445-113">プロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="a9445-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="a9445-114">リリース構成を使用して、プロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="a9445-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="a9445-115">発行先を実行して、RID `osx.10.11-x64` に発行します。</span><span class="sxs-lookup"><span data-stu-id="a9445-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="a9445-116">プロジェクト全体と SDK に付属するすべてのターゲットをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a9445-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`
