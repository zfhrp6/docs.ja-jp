---
title: dotnet tool uninstall コマンド - .NET Core CLI
description: dotnet tool uninstall コマンドは、マシン上の指定された .NET Core グローバル ツールをアンインストールします。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 5cf80d1756dbf4e88bb52a8028d186d44978f440
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696943"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="5db86-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="5db86-103">dotnet tool uninstall</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="5db86-104">name</span><span class="sxs-lookup"><span data-stu-id="5db86-104">Name</span></span>

<span data-ttu-id="5db86-105">`dotnet tool uninstall` - マシン上の指定された [.NET Core グローバル ツール](global-tools.md)をアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="5db86-105">`dotnet tool uninstall` - Uninstalls the specified [.NET Core Global Tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5db86-106">構文</span><span class="sxs-lookup"><span data-stu-id="5db86-106">Synopsis</span></span>

```
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="5db86-107">説明</span><span class="sxs-lookup"><span data-stu-id="5db86-107">Description</span></span>

<span data-ttu-id="5db86-108">`dotnet tool uninstall` コマンドは、自分のマシンから .NET Core グローバル ツールをアンインストールするための手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="5db86-108">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core Global Tools from your machine.</span></span> <span data-ttu-id="5db86-109">コマンドを使用するには、`--global` オプションを使用してユーザー全体のツールを更新するか、`--tool-path` オプションを使用してツールがインストールされている場所へのパスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5db86-109">To use the command, you either have to specify that you want to remove a user-wide tool using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="5db86-110">引数</span><span class="sxs-lookup"><span data-stu-id="5db86-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="5db86-111">アンインストールする .NET Core グローバル ツールを含む、NuGet パッケージの名前または ID。</span><span class="sxs-lookup"><span data-stu-id="5db86-111">Name/ID of the NuGet package that contains the .NET Core Global Tool to uninstall.</span></span> <span data-ttu-id="5db86-112">パッケージを見つけるには、[dotnet tool list](dotnet-tool-list.md) コマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5db86-112">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="5db86-113">オプション</span><span class="sxs-lookup"><span data-stu-id="5db86-113">Options</span></span>

`-g|--global`

<span data-ttu-id="5db86-114">ツールがユーザー全体のインストールから削除されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="5db86-114">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="5db86-115">`--tool-path` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="5db86-115">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="5db86-116">このオプションを指定しない場合は、`--tool-path` オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5db86-116">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="5db86-117">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="5db86-117">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="5db86-118">グローバル ツールをアンインストールする場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="5db86-118">Specifies the location where to uninstall the Global Tool.</span></span> <span data-ttu-id="5db86-119">パスは絶対パスでも相対パスでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="5db86-119">PATH can be absolute or relative.</span></span> <span data-ttu-id="5db86-120">`--global` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="5db86-120">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="5db86-121">このオプションを指定しない場合は、`--global` オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5db86-121">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="5db86-122">使用例</span><span class="sxs-lookup"><span data-stu-id="5db86-122">Examples</span></span>

<span data-ttu-id="5db86-123">[dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="5db86-123">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool uninstall -g dotnetsay`

<span data-ttu-id="5db86-124">特定の Windows フォルダーから [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="5db86-124">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Windows folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="5db86-125">特定の Linux/macOS フォルダーから [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="5db86-125">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Linux/macOS folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="5db86-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="5db86-126">See also</span></span>

[<span data-ttu-id="5db86-127">.NET Core グローバル ツール</span><span class="sxs-lookup"><span data-stu-id="5db86-127">.NET Core Global Tools</span></span>](global-tools.md)