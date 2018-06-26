---
title: dotnet build-server コマンド - .NET Core CLI
description: dotnet build-server は、ビルドによって起動されたサーバーとやり取りします。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 929b8d74aa5f3f0ad73b108be8a5bf22f86e30d6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696255"
---
# <a name="dotnet-build"></a><span data-ttu-id="c21b1-103">dotnet-build</span><span class="sxs-lookup"><span data-stu-id="c21b1-103">dotnet-build</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="c21b1-104">name</span><span class="sxs-lookup"><span data-stu-id="c21b1-104">Name</span></span>

<span data-ttu-id="c21b1-105">`dotnet build-server` - ビルドによって起動されたサーバーとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="c21b1-105">`dotnet build-server` - Interacts with servers started by a build.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c21b1-106">構文</span><span class="sxs-lookup"><span data-stu-id="c21b1-106">Synopsis</span></span>

```
dotnet build-server shutdown [--msbuild] [--razor] [--vbcscompiler]
dotnet build-server shutdown [-h|--help]
dotnet build-server [-h|--help]
```

## <a name="commands"></a><span data-ttu-id="c21b1-107">コマンド</span><span class="sxs-lookup"><span data-stu-id="c21b1-107">Commands</span></span>

`shutdown`

<span data-ttu-id="c21b1-108">dotnet から起動されるビルド サーバーをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="c21b1-108">Shuts down build servers that are started from dotnet.</span></span> <span data-ttu-id="c21b1-109">既定では、すべてのサーバーがシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="c21b1-109">By default, all servers are shut down.</span></span>

## <a name="options"></a><span data-ttu-id="c21b1-110">オプション</span><span class="sxs-lookup"><span data-stu-id="c21b1-110">Options</span></span>

`-h|--help`

<span data-ttu-id="c21b1-111">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="c21b1-111">Prints out a short help for the command.</span></span>

`--msbuild`

<span data-ttu-id="c21b1-112">MSBuild ビルド サーバーをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="c21b1-112">Shuts down the MSBuild build server.</span></span>

`--razor`

<span data-ttu-id="c21b1-113">Razor ビルド サーバーをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="c21b1-113">Shuts down the Razor build server.</span></span>

`--vbcscompiler`

<span data-ttu-id="c21b1-114">VB/C# コンパイラ ビルド サーバーをシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="c21b1-114">Shuts down the VB/C# compiler build server.</span></span>
