---
title: dotnet tool update コマンド - .NET Core CLI
description: dotnet tool update コマンドは、マシン上の指定された .NET Core グローバル ツールを更新します。
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 35a0bd0f85f0beed06d4250d8f195ce4fe4fcca4
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696690"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="0f885-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="0f885-103">dotnet tool update</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="0f885-104">name</span><span class="sxs-lookup"><span data-stu-id="0f885-104">Name</span></span>

<span data-ttu-id="0f885-105">`dotnet tool update` - マシン上の指定された [.NET Core グローバル ツール](global-tools.md) を更新します。</span><span class="sxs-lookup"><span data-stu-id="0f885-105">`dotnet tool update` - Updates the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0f885-106">構文</span><span class="sxs-lookup"><span data-stu-id="0f885-106">Synopsis</span></span>

```
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="0f885-107">説明</span><span class="sxs-lookup"><span data-stu-id="0f885-107">Description</span></span>

<span data-ttu-id="0f885-108">`dotnet tool update` コマンドは、マシン上の指定された .NET Core グローバル ツールをパッケージの最新の安定バージョンに更新するための手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="0f885-108">The `dotnet tool update` command provides a way for you to update .NET Core Global Tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="0f885-109">このコマンドは、ツールをアンインストールして再インストールして、効果的に更新します。</span><span class="sxs-lookup"><span data-stu-id="0f885-109">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="0f885-110">コマンドを使用するには、`--global` オプションを使用してユーザー全体のインストールからツールを更新することを指定するか、`--tool-path` オプションを使用してツールがインストールされている場所へのパスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f885-110">To use the command, you either have to specify that you want to update a tool from a user-wide installation using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="0f885-111">引数</span><span class="sxs-lookup"><span data-stu-id="0f885-111">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="0f885-112">更新する .NET Core グローバル ツールが格納されている NuGet パッケージの名前または ID。</span><span class="sxs-lookup"><span data-stu-id="0f885-112">Name/ID of the NuGet package that contains the .NET Core Global Tool to update.</span></span> <span data-ttu-id="0f885-113">パッケージを見つけるには、[dotnet tool list](dotnet-tool-list.md) コマンドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0f885-113">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="0f885-114">オプション</span><span class="sxs-lookup"><span data-stu-id="0f885-114">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="0f885-115">インストール時に使用するために追加の NuGet パッケージ ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="0f885-115">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="0f885-116">使用する NuGet 構成 (*nuget.config*) ファイル。</span><span class="sxs-lookup"><span data-stu-id="0f885-116">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="0f885-117">ツールを更新する[ターゲット フレームワーク](../../standard/frameworks.md)を指定します。</span><span class="sxs-lookup"><span data-stu-id="0f885-117">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

`-g|--global`

<span data-ttu-id="0f885-118">更新プログラムがユーザー全体のツール用であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="0f885-118">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="0f885-119">`--tool-path` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="0f885-119">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="0f885-120">このオプションを指定しない場合は、`--tool-path` オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f885-120">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="0f885-121">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="0f885-121">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="0f885-122">グローバル ツールがインストールされている場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="0f885-122">Specifies the location where the Global Tool is installed.</span></span> <span data-ttu-id="0f885-123">パスは絶対パスでも相対パスでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="0f885-123">PATH can be absolute or relative.</span></span> <span data-ttu-id="0f885-124">`--global` オプションと組み合わせることはできません。</span><span class="sxs-lookup"><span data-stu-id="0f885-124">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="0f885-125">このオプションを指定しない場合は、`--global` オプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f885-125">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="0f885-126">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="0f885-126">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0f885-127">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="0f885-127">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="0f885-128">使用例</span><span class="sxs-lookup"><span data-stu-id="0f885-128">Examples</span></span>

<span data-ttu-id="0f885-129">[dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールを更新します。</span><span class="sxs-lookup"><span data-stu-id="0f885-129">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool update -g dotnetsay`

<span data-ttu-id="0f885-130">特定の Windows フォルダーに配置されている [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールを更新します。</span><span class="sxs-lookup"><span data-stu-id="0f885-130">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Windows folder:</span></span>

`dotnet tool update dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="0f885-131">特定の Linux/macOS フォルダーに配置されている [dotnetsay](https://www.nuget.org/packages/dotnetsay/) グローバル ツールを更新します。</span><span class="sxs-lookup"><span data-stu-id="0f885-131">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Linux/macOS folder:</span></span>

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="0f885-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f885-132">See also</span></span>

[<span data-ttu-id="0f885-133">.NET Core グローバル ツール</span><span class="sxs-lookup"><span data-stu-id="0f885-133">.NET Core Global Tools</span></span>](global-tools.md)