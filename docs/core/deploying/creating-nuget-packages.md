---
title: クロス プラットフォーム ツールによる NuGet パッケージの作成
description: ’dotnet pack’ コマンドを使用して NuGet パッケージを作成する方法を説明します。
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 6be94c2e2cef443f69b2d6df7c2d490cb1fb629d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a><span data-ttu-id="f7df2-103">クロスプラットフォーム ツールを使用して NuGet パッケージを作成する方法</span><span class="sxs-lookup"><span data-stu-id="f7df2-103">How to Create a NuGet Package with Cross Platform Tools</span></span>

> [!NOTE]
> <span data-ttu-id="f7df2-104">以下は、Unix を使用する場合のコマンド ライン サンプルです。</span><span class="sxs-lookup"><span data-stu-id="f7df2-104">The following shows command-line samples using Unix.</span></span>  <span data-ttu-id="f7df2-105">ここに示されている `dotnet pack` コマンドは Windows でも同じように機能します。</span><span class="sxs-lookup"><span data-stu-id="f7df2-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="f7df2-106">.NET Core 1.0 では、ライブラリは NuGet パッケージとして配布する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7df2-106">For .NET Core 1.0, libraries are expected to be distributed as NuGet packages.</span></span>  <span data-ttu-id="f7df2-107">実際に、.NET Standard ライブラリはすべてそのように配布され、使用されています。</span><span class="sxs-lookup"><span data-stu-id="f7df2-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span>  <span data-ttu-id="f7df2-108">`dotnet pack` コマンドを使用して行うのが最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="f7df2-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="f7df2-109">たとえば、NuGet 経由で配布する新しい優れたライブラリを作成したとします。</span><span class="sxs-lookup"><span data-stu-id="f7df2-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span>  <span data-ttu-id="f7df2-110">クロス プラットフォーム ツールを使用して NuGet パッケージを作成すれば、正確に実行できます。</span><span class="sxs-lookup"><span data-stu-id="f7df2-110">You can create a NuGet package with cross platform tools to do exactly that!</span></span>  <span data-ttu-id="f7df2-111">次の例では、`netstandard1.0` をターゲットとする **SuperAwesomeLibrary** というライブラリを想定します。</span><span class="sxs-lookup"><span data-stu-id="f7df2-111">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="f7df2-112">推移的依存関係がある (つまり、別のプロジェクトに依存するプロジェクトがある) 場合、NuGet パッケージを作成する前に `dotnet restore` コマンドでソリューション全体のパッケージを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f7df2-112">If you have transitive dependencies; that is, a project which depends on another project, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span>  <span data-ttu-id="f7df2-113">そうしないと、`dotnet pack` コマンドが正しく機能しません。</span><span class="sxs-lookup"><span data-stu-id="f7df2-113">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]


<span data-ttu-id="f7df2-114">パッケージが復元されたことを確認したら、以下のコマンドを実行してライブラリがあるディレクトリに移動できます。</span><span class="sxs-lookup"><span data-stu-id="f7df2-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

`$ cd src/SuperAwesomeLibrary`

<span data-ttu-id="f7df2-115">その後、コマンド ラインから以下の 1 つのコマンドのみを実行します。</span><span class="sxs-lookup"><span data-stu-id="f7df2-115">Then it's just a single command from the command line:</span></span>
    
`$ dotnet pack`

<span data-ttu-id="f7df2-116">これで `/bin/Debug` フォルダーは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f7df2-116">Your `/bin/Debug` folder will now look like this:</span></span>

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="f7df2-117">この場合、デバッグ可能なパッケージが生成されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f7df2-117">Note that this will produce a package which is capable of being debugged.</span></span>  <span data-ttu-id="f7df2-118">リリース バイナリと共に NuGet パッケージをビルドする場合、`-c`/`--configuration` スイッチを追加して、引数として `release` を使用するだけです。</span><span class="sxs-lookup"><span data-stu-id="f7df2-118">If you want to build a NuGet package with release binaries, all you need to do is add the `-c`/`--configuration` switch and use `release` as the argument.</span></span>

`$ dotnet pack --configuration release`

<span data-ttu-id="f7df2-119">これで、`/bin` フォルダーに、NuGet パッケージとリリース バイナリを含む `release` フォルダーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="f7df2-119">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="f7df2-120">これで、NuGet パッケージを発行するために必要なファイルが準備できました。</span><span class="sxs-lookup"><span data-stu-id="f7df2-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="f7df2-121">`dotnet pack`と `dotnet publish` を混同しないようにしてください</span><span class="sxs-lookup"><span data-stu-id="f7df2-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="f7df2-122">ここで `dotnet publish` コマンドを使用しても意味がありません。</span><span class="sxs-lookup"><span data-stu-id="f7df2-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span>  <span data-ttu-id="f7df2-123">`dotnet publish` コマンドは、同じバンドルにすべての依存関係があるアプリケーションを配置するためのものであり、NuGet 経由で配布して使用する NuGet パッケージを生成するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="f7df2-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -  not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>
