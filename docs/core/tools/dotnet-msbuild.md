---
title: "dotnet-msbuild コマンド - .NET Core CLI"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1f02dcd779b9ed249ebd2fedb973383b1dcd8963
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-msbuild"></a><span data-ttu-id="968e2-104">dotnet-msbuild</span><span class="sxs-lookup"><span data-stu-id="968e2-104">dotnet-msbuild</span></span>

## <a name="name"></a><span data-ttu-id="968e2-105">名前</span><span class="sxs-lookup"><span data-stu-id="968e2-105">Name</span></span>

<span data-ttu-id="968e2-106">`dotnet-msbuild` - プロジェクトとそのすべての依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="968e2-106">`dotnet-msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="968e2-107">構文</span><span class="sxs-lookup"><span data-stu-id="968e2-107">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="968e2-108">説明</span><span class="sxs-lookup"><span data-stu-id="968e2-108">Description</span></span>

<span data-ttu-id="968e2-109">`dotnet msbuild` コマンドでは、完全に機能する MSBuild へのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="968e2-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="968e2-110">このコマンドには、既存の MSBuild コマンド ライン クライアントとまったく同じ機能があります。</span><span class="sxs-lookup"><span data-stu-id="968e2-110">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="968e2-111">オプションはすべて同じです。</span><span class="sxs-lookup"><span data-stu-id="968e2-111">The options are all the same.</span></span> <span data-ttu-id="968e2-112">使用可能なオプションについては、「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="968e2-112">Use the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) to obtain information on the available options.</span></span> 

## <a name="examples"></a><span data-ttu-id="968e2-113">例</span><span class="sxs-lookup"><span data-stu-id="968e2-113">Examples</span></span>

<span data-ttu-id="968e2-114">プロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="968e2-114">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="968e2-115">リリース構成を使用して、プロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="968e2-115">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="968e2-116">発行先を実行して、RID `osx.10.11-x64` に発行します。</span><span class="sxs-lookup"><span data-stu-id="968e2-116">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="968e2-117">プロジェクト全体と SDK に付属するすべてのターゲットをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="968e2-117">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`

