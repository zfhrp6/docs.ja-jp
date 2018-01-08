---
title: "dotnet help コマンド - .NET Core CLI"
description: "dotnet help コマンドでは、指定したコマンドについてより詳細なドキュメントがオンラインで表示されます。"
author: mairaw
ms.author: mairaw
ms.date: 08/17/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 47b7b53b9f13935bbd2cf508c7c57d00584822d0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="b9836-103">dotnet help reference</span><span class="sxs-lookup"><span data-stu-id="b9836-103">dotnet help reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="b9836-104">name</span><span class="sxs-lookup"><span data-stu-id="b9836-104">Name</span></span>

<span data-ttu-id="b9836-105">`dotnet help` - 指定したコマンドについて、より詳細なドキュメントがオンラインで表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9836-105">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b9836-106">構文</span><span class="sxs-lookup"><span data-stu-id="b9836-106">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="b9836-107">説明</span><span class="sxs-lookup"><span data-stu-id="b9836-107">Description</span></span>

<span data-ttu-id="b9836-108">`dotnet help` コマンドは、docs.microsoft.com で、指定したコマンドに関する詳細情報のリファレンス ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="b9836-108">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="b9836-109">引数</span><span class="sxs-lookup"><span data-stu-id="b9836-109">Arguments</span></span>

`COMMAND_NAME`

<span data-ttu-id="b9836-110">.NET Core CLI コマンドの名前です。</span><span class="sxs-lookup"><span data-stu-id="b9836-110">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="b9836-111">有効な CLI コマンドの一覧については、[CLI コマンド](index.md#cli-commands)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9836-111">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="b9836-112">オプション</span><span class="sxs-lookup"><span data-stu-id="b9836-112">Options</span></span>

`-h|--help`

<span data-ttu-id="b9836-113">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="b9836-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="b9836-114">使用例</span><span class="sxs-lookup"><span data-stu-id="b9836-114">Examples</span></span>

<span data-ttu-id="b9836-115">ドキュメントの [dotnet new](dotnet-new.md) コマンドに関するページを開きます。</span><span class="sxs-lookup"><span data-stu-id="b9836-115">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

`dotnet help new`
