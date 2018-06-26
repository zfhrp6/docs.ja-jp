---
title: dotnet tool install コマンド - .NET Core CLI
description: dotnet tool install コマンドでは、使用しているマシンに指定された .NET Core グローバル ツールをインストールします。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: f3068848910d6672a10ecfb639bac8e18a72818d
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697288"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="2fcf3-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="2fcf3-103">dotnet tool install</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="2fcf3-104">name</span><span class="sxs-lookup"><span data-stu-id="2fcf3-104">Name</span></span>

<span data-ttu-id="2fcf3-105">`dotnet tool install` - 使用しているマシンに指定された [.NET Core グローバル ツール](global-tools.md)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-105">`dotnet tool install` - Installs the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2fcf3-106">構文</span><span class="sxs-lookup"><span data-stu-id="2fcf3-106">Synopsis</span></span>

```
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="2fcf3-107">説明</span><span class="sxs-lookup"><span data-stu-id="2fcf3-107">Description</span></span>

<span data-ttu-id="2fcf3-108">`dotnet tool install` コマンドでは、使用しているマシンに .NET Core グローバル ツールをインストールするための手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-108">The `dotnet tool install` command provides a way for you to install .NET Core Global Tools on your machine.</span></span> <span data-ttu-id="2fcf3-109">コマンドを使用するには、`--global` オプションを使用してユーザー全体のインストールを指定するか、`--tool-path` オプションを使用してツールをインストールするパスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-109">To use the command, you either have to specify that you want a user-wide installation using the `--global` option or you specify a path to install it using the `--tool-path` option.</span></span>

<span data-ttu-id="2fcf3-110">グローバル ツールは、`-g` (または `--global`) オプションを指定した場合、既定では次のディレクトリにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-110">Global Tools are installed in the following directories by default when you specify the `-g` (or `--global`) option:</span></span>

| <span data-ttu-id="2fcf3-111">OS</span><span class="sxs-lookup"><span data-stu-id="2fcf3-111">OS</span></span>          | <span data-ttu-id="2fcf3-112">パス</span><span class="sxs-lookup"><span data-stu-id="2fcf3-112">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="2fcf3-113">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="2fcf3-113">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="2fcf3-114">Windows</span><span class="sxs-lookup"><span data-stu-id="2fcf3-114">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a><span data-ttu-id="2fcf3-115">引数</span><span class="sxs-lookup"><span data-stu-id="2fcf3-115">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="2fcf3-116">インストールする .NET Core グローバル ツールを含む、NuGet パッケージの名前または ID。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-116">Name/ID of the NuGet package that contains the .NET Core Global Tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="2fcf3-117">オプション</span><span class="sxs-lookup"><span data-stu-id="2fcf3-117">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="2fcf3-118">インストール時に使用するために追加の NuGet パッケージ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-118">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="2fcf3-119">使用する NuGet 構成 (*nuget.config*) ファイル。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-119">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="2fcf3-120">ツールをインストールする[ターゲット フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-120">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="2fcf3-121">既定では、.NET Core SDK は最適なターゲット フレームワークの選択を試みます。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-121">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

`-g|--global`

<span data-ttu-id="2fcf3-122">ユーザー全体のインストールを指定します。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-122">Specifies that the installation is user wide.</span></span> <span data-ttu-id="2fcf3-123">`--tool-path` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-123">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="2fcf3-124">このオプションを指定しない場合は、`--tool-path` オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-124">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="2fcf3-125">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-125">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="2fcf3-126">グローバル ツールをインストールする場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-126">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="2fcf3-127">PATH は絶対パスでも相対パスでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-127">PATH can be absolute or relative.</span></span> <span data-ttu-id="2fcf3-128">PATH が存在しない場合、コマンドではパスの作成を試みます。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-128">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="2fcf3-129">`--global` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="2fcf3-130">このオプションを指定しない場合は、`--global` オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-130">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="2fcf3-131">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2fcf3-132">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version <VERSION_NUMBER>`

<span data-ttu-id="2fcf3-133">インストールするツールのバージョン。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-133">The version of the tool to install.</span></span> <span data-ttu-id="2fcf3-134">既定では、安定した最新バージョンのパッケージがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-134">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="2fcf3-135">このオプションを使用して、プレビューまたは古いバージョンのツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-135">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="2fcf3-136">使用例</span><span class="sxs-lookup"><span data-stu-id="2fcf3-136">Examples</span></span>

<span data-ttu-id="2fcf3-137">既定の場所に [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-137">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool in the default location:</span></span>

`dotnet tool install -g dotnetsay`

<span data-ttu-id="2fcf3-138">特定の Windows フォルダーに [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-138">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Windows folder:</span></span>

`dotnet tool install dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="2fcf3-139">特定の Linux/macOS フォルダーに [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-139">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Linux/macOS folder:</span></span>

`dotnet tool install dotnetsay --tool-path ~/bin`

<span data-ttu-id="2fcf3-140">バージョン 2.0.0 の [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="2fcf3-140">Installs version 2.0.0 of the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="2fcf3-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="2fcf3-141">See also</span></span>

[<span data-ttu-id="2fcf3-142">.NET Core グローバル ツール</span><span class="sxs-lookup"><span data-stu-id="2fcf3-142">.NET Core Global Tools</span></span>](global-tools.md)