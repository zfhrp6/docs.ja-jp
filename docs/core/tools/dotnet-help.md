---
title: dotnet help コマンド - .NET Core CLI
description: dotnet help コマンドでは、指定したコマンドについてより詳細なドキュメントがオンラインで表示されます。
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: ed152717e32ffb294f5d5bd8e5eb74d55e33e506
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696599"
---
# <a name="dotnet-help-reference"></a><span data-ttu-id="fe1a7-103">dotnet help reference</span><span class="sxs-lookup"><span data-stu-id="fe1a7-103">dotnet help reference</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a><span data-ttu-id="fe1a7-104">name</span><span class="sxs-lookup"><span data-stu-id="fe1a7-104">Name</span></span>

<span data-ttu-id="fe1a7-105">`dotnet help` - 指定したコマンドについて、より詳細なドキュメントがオンラインで表示されます。</span><span class="sxs-lookup"><span data-stu-id="fe1a7-105">`dotnet help` - Shows more detailed documentation online for the specified command.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fe1a7-106">構文</span><span class="sxs-lookup"><span data-stu-id="fe1a7-106">Synopsis</span></span>

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a><span data-ttu-id="fe1a7-107">説明</span><span class="sxs-lookup"><span data-stu-id="fe1a7-107">Description</span></span>

<span data-ttu-id="fe1a7-108">`dotnet help` コマンドは、docs.microsoft.com で、指定したコマンドに関する詳細情報のリファレンス ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="fe1a7-108">The `dotnet help` command opens up the reference page for more detailed information about the specified command at docs.microsoft.com.</span></span>

## <a name="arguments"></a><span data-ttu-id="fe1a7-109">引数</span><span class="sxs-lookup"><span data-stu-id="fe1a7-109">Arguments</span></span>

`COMMAND_NAME`

<span data-ttu-id="fe1a7-110">.NET Core CLI コマンドの名前です。</span><span class="sxs-lookup"><span data-stu-id="fe1a7-110">Name of the .NET Core CLI command.</span></span> <span data-ttu-id="fe1a7-111">有効な CLI コマンドの一覧については、[CLI コマンド](index.md#cli-commands)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe1a7-111">For a list of the valid CLI commands, see [CLI commands](index.md#cli-commands).</span></span>

## <a name="options"></a><span data-ttu-id="fe1a7-112">オプション</span><span class="sxs-lookup"><span data-stu-id="fe1a7-112">Options</span></span>

`-h|--help`

<span data-ttu-id="fe1a7-113">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="fe1a7-113">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="fe1a7-114">使用例</span><span class="sxs-lookup"><span data-stu-id="fe1a7-114">Examples</span></span>

<span data-ttu-id="fe1a7-115">ドキュメントの [dotnet new](dotnet-new.md) コマンドに関するページを開きます。</span><span class="sxs-lookup"><span data-stu-id="fe1a7-115">Opens the documentation page for the [dotnet new](dotnet-new.md) command:</span></span>

`dotnet help new`
