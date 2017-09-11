---
title: "dotnet-add 参照コマンド - .NET Core CLI"
description: "dotnet-add 参照コマンドは、プロジェクト間参照を追加する便利なオプションを提供します。"
keywords: "dotnet-add, CLI, CLI コマンド, .NET Core"
author: spboyer
ms.author: mairaw
ms.date: 03/15/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 5e2a3efd-443c-4f23-a1b1-a662a5387879
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 98491efc183ad62f47275d0832a32dde5899373d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="dotnet-add-reference"></a><span data-ttu-id="87998-104">dotnet-add 参照</span><span class="sxs-lookup"><span data-stu-id="87998-104">dotnet-add reference</span></span>

## <a name="name"></a><span data-ttu-id="87998-105">名前</span><span class="sxs-lookup"><span data-stu-id="87998-105">Name</span></span>

<span data-ttu-id="87998-106">`dotnet-add reference` - プロジェクト間 (P2P) 参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="87998-106">`dotnet-add reference` - Adds project-to-project (P2P) references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="87998-107">構文</span><span class="sxs-lookup"><span data-stu-id="87998-107">Synopsis</span></span>

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help]`

## <a name="description"></a><span data-ttu-id="87998-108">説明</span><span class="sxs-lookup"><span data-stu-id="87998-108">Description</span></span>

<span data-ttu-id="87998-109">`dotnet add reference` コマンドは、プロジェクトにプロジェクト参照を追加する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="87998-109">The `dotnet add reference` command provides a convenient option to add project references to a project.</span></span> <span data-ttu-id="87998-110">このコマンドを実行すると、[`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) 要素がプロジェクト ファイルに追加されます。</span><span class="sxs-lookup"><span data-stu-id="87998-110">After running the command, the [`<ProjectReference>`](/visualstudio/msbuild/common-msbuild-project-items) elements are added to the project file.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a><span data-ttu-id="87998-111">引数</span><span class="sxs-lookup"><span data-stu-id="87998-111">Arguments</span></span>

`PROJECT`

<span data-ttu-id="87998-112">プロジェクト ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="87998-112">Specifies the project file.</span></span> <span data-ttu-id="87998-113">指定されていない場合、現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="87998-113">If not specified, the command will search the current directory for one.</span></span>

`PROJECT_REFERENCES`

<span data-ttu-id="87998-114">追加するプロジェクト間参照 (P2P) です。</span><span class="sxs-lookup"><span data-stu-id="87998-114">Project-to-project (P2P) references to add.</span></span> <span data-ttu-id="87998-115">1 つ以上のプロジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="87998-115">Specify one or more projects.</span></span> <span data-ttu-id="87998-116">[glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースのシステムで利用できます。</span><span class="sxs-lookup"><span data-stu-id="87998-116">[Glob patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are supported on Unix/Linux-based systems.</span></span>

## <a name="options"></a><span data-ttu-id="87998-117">オプション</span><span class="sxs-lookup"><span data-stu-id="87998-117">Options</span></span>

`-h|--help`

<span data-ttu-id="87998-118">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="87998-118">Prints out a short help for the command.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="87998-119">特定の[フレームワーク](../../standard/frameworks.md)を対象にしている場合にのみ、プロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="87998-119">Adds project references only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

## <a name="examples"></a><span data-ttu-id="87998-120">例</span><span class="sxs-lookup"><span data-stu-id="87998-120">Examples</span></span>

<span data-ttu-id="87998-121">プロジェクト参照を追加する:</span><span class="sxs-lookup"><span data-stu-id="87998-121">Add a project reference:</span></span>

`dotnet add app/app.csproj reference lib/lib.csproj`

<span data-ttu-id="87998-122">複数のプロジェクト参照を追加する:</span><span class="sxs-lookup"><span data-stu-id="87998-122">Add multiple project references:</span></span>

`dotnet add reference lib1/lib1.csproj lib2/lib2.csproj`

<span data-ttu-id="87998-123">Linux/Unix で glob パターンを使って複数のプロジェクト参照を追加する:</span><span class="sxs-lookup"><span data-stu-id="87998-123">Add multiple project references using a globbing pattern on Linux/Unix:</span></span>

`dotnet add app/app.csproj reference **/*.csproj`

