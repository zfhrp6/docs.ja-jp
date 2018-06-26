---
title: C# 言語のバージョンの選択 - C# ガイド
description: 特定のコンパイラ バージョンを使用して構文の検証を実行するコンパイラを構成します。
ms.date: 05/24/2018
ms.openlocfilehash: 9b91e62168ced0f373e1a55def8b279dc64833d8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207983"
---
# <a name="select-the-c-language-version"></a><span data-ttu-id="c1092-103">C# 言語のバージョンの選択</span><span class="sxs-lookup"><span data-stu-id="c1092-103">Select the C# language version</span></span>

<span data-ttu-id="c1092-104">C# コンパイラは、既定でリリースされている言語の最新のメジャー バージョンに設定されます。</span><span class="sxs-lookup"><span data-stu-id="c1092-104">The C# compiler defaults to the latest major version of the language that has been released.</span></span> <span data-ttu-id="c1092-105">言語の新しいポイント リリースを使用して、プロジェクトをコンパイルすることができます。</span><span class="sxs-lookup"><span data-stu-id="c1092-105">You may choose to compile any project using a new point release of the language.</span></span> <span data-ttu-id="c1092-106">言語の新しいバージョンを選択すると、プロジェクトで最新の言語機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c1092-106">Choosing a newer version of the language enables your project to make use of the latest language features.</span></span> <span data-ttu-id="c1092-107">他のシナリオでは、古いバージョンの言語を使用する場合、プロジェクトがクリーンにコンパイルすることを検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1092-107">In other scenarios, you may need to validate that a project compiles cleanly when using an older version of the language.</span></span>

<span data-ttu-id="c1092-108">この機能によって、開発環境に新しいバージョンの SDK とツールをインストールすることの決定と新しい言語機能をプロジェクトに組み込むことの決定が別になります。</span><span class="sxs-lookup"><span data-stu-id="c1092-108">This capability decouples the decision to install new versions of the SDK and tools in your development environment from the decision to incorporate new language features in a project.</span></span> <span data-ttu-id="c1092-109">ビルド コンピューターに最新の SDK とツールをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="c1092-109">You can install the latest SDK and tools on your build machine.</span></span> <span data-ttu-id="c1092-110">特定バージョンの言語をビルドに使用するように各プロジェクトを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c1092-110">Each project can be configured to use a specific version of the language for its build.</span></span>

<span data-ttu-id="c1092-111">言語バージョンを設定する方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="c1092-111">There are several ways to set the language version:</span></span>

- <span data-ttu-id="c1092-112">[Visual Studio のクイック アクション](#visual-studio-quick-action)を利用する。</span><span class="sxs-lookup"><span data-stu-id="c1092-112">Rely on a [Visual Studio quick action](#visual-studio-quick-action).</span></span>
- <span data-ttu-id="c1092-113">[Visual Studio UI](#set-the-language-version-in-visual-studio) で言語バージョンを設定する。</span><span class="sxs-lookup"><span data-stu-id="c1092-113">Set the language version in the [Visual Studio UI](#set-the-language-version-in-visual-studio).</span></span>
- <span data-ttu-id="c1092-114">[**.csproj** ファイルを手動で編集する](#edit-the-csproj-file)。</span><span class="sxs-lookup"><span data-stu-id="c1092-114">Manually edit your [**.csproj** file](#edit-the-csproj-file).</span></span>
- <span data-ttu-id="c1092-115">[サブディレクトリ内の複数のプロジェクトに対して](#configure-multiple-projects)言語バージョンを設定する。</span><span class="sxs-lookup"><span data-stu-id="c1092-115">Set the language version [for multiple projects in a subdirectory](#configure-multiple-projects).</span></span>
- <span data-ttu-id="c1092-116">[`-langversion` コンパイラ オプション](#set-the-langversion-compiler-option)を構成する。</span><span class="sxs-lookup"><span data-stu-id="c1092-116">Configure the [`-langversion` compiler option](#set-the-langversion-compiler-option).</span></span>

## <a name="visual-studio-quick-action"></a><span data-ttu-id="c1092-117">Visual Studio のクイック アクション</span><span class="sxs-lookup"><span data-stu-id="c1092-117">Visual Studio quick action</span></span>

<span data-ttu-id="c1092-118">Visual Studio は、必要な言語バージョンを判断するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c1092-118">Visual Studio helps you determine the language version you need.</span></span> <span data-ttu-id="c1092-119">現在構成されているバージョンで使用できない言語機能を使用する場合、Visual Studio は、プロジェクトの言語バージョンを更新する可能性のある修正プログラムを示します。</span><span class="sxs-lookup"><span data-stu-id="c1092-119">If you use a language feature that is not available for the currently configured version, Visual Studio shows a potential fix to update the language version for the project.</span></span>

## <a name="set-the-language-version-in-visual-studio"></a><span data-ttu-id="c1092-120">Visual Studio で言語バージョンを設定する</span><span class="sxs-lookup"><span data-stu-id="c1092-120">Set the language version in Visual Studio</span></span>

<span data-ttu-id="c1092-121">Visual Studio のバージョンを設定できます。</span><span class="sxs-lookup"><span data-stu-id="c1092-121">You can set the version in Visual Studio.</span></span> <span data-ttu-id="c1092-122">ソリューション エクスプローラーでプロジェクト ノードを右クリックして、**[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c1092-122">Right-click on the project node in Solution Explorer and select **Properties**.</span></span> <span data-ttu-id="c1092-123">**[ビルド]** タブを選択し、**[詳細設定]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="c1092-123">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="c1092-124">ドロップダウン リストで、バージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="c1092-124">In the dropdown, select the version.</span></span> <span data-ttu-id="c1092-125">次の図は "最新の" 設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="c1092-125">The following image shows the "latest" setting:</span></span>

![言語バージョンを指定できる高度なビルド設定のスクリーン ショット](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> <span data-ttu-id="c1092-127">Visual Studio IDE を使用して csproj ファイルを更新する場合、IDE によって、ビルド構成ごとにノードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c1092-127">If you use the Visual Studio IDE to update your csproj files, the IDE creates separate nodes for each build configuration.</span></span> <span data-ttu-id="c1092-128">一般的に、すべてのビルド構成で同じように値を設定しますが、ビルド構成ごとに明示的に設定する必要があります。あるいは、この設定を変更するとき、"すべての構成" を選択します。</span><span class="sxs-lookup"><span data-stu-id="c1092-128">You'll typically set the value the same in all build configurations, but you need to set it explicitly for each build configuration, or select "All Configurations" when you modify this setting.</span></span> <span data-ttu-id="c1092-129">csproj ファイルに次が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1092-129">You'll see the following in your csproj file:</span></span>
>
>```xml
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
>  <LangVersion>latest</LangVersion>
></PropertyGroup>
>
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
>  <LangVersion>latest</LangVersion>
> </PropertyGroup>
> ```
>

## <a name="edit-the-csproj-file"></a><span data-ttu-id="c1092-130">csproj ファイルを編集する</span><span class="sxs-lookup"><span data-stu-id="c1092-130">Edit the csproj file</span></span>

<span data-ttu-id="c1092-131">**.csproj** ファイルで言語バージョンを設定できます。</span><span class="sxs-lookup"><span data-stu-id="c1092-131">You can set the language version in your **.csproj** file.</span></span> <span data-ttu-id="c1092-132">次のような要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="c1092-132">Add an element like the following:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="c1092-133">値 `latest` は、C# 言語の最新のマイナー バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="c1092-133">The value `latest` uses the latest minor version of the C# language.</span></span> <span data-ttu-id="c1092-134">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c1092-134">Valid values are:</span></span>

|<span data-ttu-id="c1092-135">[値]</span><span class="sxs-lookup"><span data-stu-id="c1092-135">Value</span></span>|<span data-ttu-id="c1092-136">説明</span><span class="sxs-lookup"><span data-stu-id="c1092-136">Meaning</span></span>|
|------------|-------------|
|<span data-ttu-id="c1092-137">default</span><span class="sxs-lookup"><span data-stu-id="c1092-137">default</span></span>|<span data-ttu-id="c1092-138">コンパイラは、最新のメジャー バージョンからサポートできるすべての有効な言語構文を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c1092-138">The compiler accepts all valid language syntax from the latest major version that it can support.</span></span>|
|<span data-ttu-id="c1092-139">ISO-1</span><span class="sxs-lookup"><span data-stu-id="c1092-139">ISO-1</span></span>|<span data-ttu-id="c1092-140">コンパイラは、ISO/IEC 23270:2003 C# (1.0/1.2) に含まれている構文のみを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c1092-140">The compiler accepts only syntax that is included in ISO/IEC 23270:2003 C# (1.0/1.2)</span></span> |
|<span data-ttu-id="c1092-141">ISO-2</span><span class="sxs-lookup"><span data-stu-id="c1092-141">ISO-2</span></span>|<span data-ttu-id="c1092-142">コンパイラは、ISO/IEC 23270:2006 C# (2.0) に含まれている構文のみを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c1092-142">The compiler accepts only syntax that is included in ISO/IEC 23270:2006 C# (2.0)</span></span> |
|<span data-ttu-id="c1092-143">3</span><span class="sxs-lookup"><span data-stu-id="c1092-143">3</span></span>|<span data-ttu-id="c1092-144">コンパイラは、C# 3.0 以下に含まれている構文のみを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c1092-144">The compiler accepts only syntax that is included in C# 3.0 or lower.</span></span>|
|<span data-ttu-id="c1092-145">4</span><span class="sxs-lookup"><span data-stu-id="c1092-145">4</span></span>|<span data-ttu-id="c1092-146">コンパイラは、C# 4.0 以下に含まれている構文のみを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c1092-146">The compiler accepts only syntax that is included in C# 4.0 or lower.</span></span>|
|<span data-ttu-id="c1092-147">5</span><span class="sxs-lookup"><span data-stu-id="c1092-147">5</span></span>|<span data-ttu-id="c1092-148">コンパイラは、C# 5.0 以下に含まれている構文のみを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c1092-148">The compiler accepts only syntax that is included in C# 5.0 or lower.</span></span>|
|<span data-ttu-id="c1092-149">6</span><span class="sxs-lookup"><span data-stu-id="c1092-149">6</span></span>|<span data-ttu-id="c1092-150">コンパイラは、C# 6.0 以下に含まれている構文のみを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c1092-150">The compiler accepts only syntax that is included in C# 6.0 or lower.</span></span>|
|<span data-ttu-id="c1092-151">7</span><span class="sxs-lookup"><span data-stu-id="c1092-151">7</span></span>|<span data-ttu-id="c1092-152">コンパイラは、C# 7.0 以下に含まれている構文のみを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c1092-152">The compiler accepts only syntax that is included in C# 7.0 or lower.</span></span>|
|<span data-ttu-id="c1092-153">7.1</span><span class="sxs-lookup"><span data-stu-id="c1092-153">7.1</span></span>|<span data-ttu-id="c1092-154">コンパイラは、C# 7.1 以下に含まれている構文のみを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c1092-154">The compiler accepts only syntax that is included in C# 7.1 or lower.</span></span>|
|<span data-ttu-id="c1092-155">7.2</span><span class="sxs-lookup"><span data-stu-id="c1092-155">7.2</span></span>|<span data-ttu-id="c1092-156">コンパイラは、C# 7.2 以下に含まれている構文のみを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c1092-156">The compiler accepts only syntax that is included in C# 7.2 or lower.</span></span>|
|<span data-ttu-id="c1092-157">7.3</span><span class="sxs-lookup"><span data-stu-id="c1092-157">7.3</span></span>|<span data-ttu-id="c1092-158">コンパイラは、C# 7.3 以下に含まれている構文のみを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c1092-158">The compiler accepts only syntax that is included in C# 7.3 or lower.</span></span>|
|<span data-ttu-id="c1092-159">latest</span><span class="sxs-lookup"><span data-stu-id="c1092-159">latest</span></span>|<span data-ttu-id="c1092-160">コンパイラは、サポートできるすべての有効な言語の構文を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="c1092-160">The compiler accepts all valid language syntax that it can support.</span></span>|

<span data-ttu-id="c1092-161">特殊文字列の `default` と `latest` はそれぞれ、ビルド コンピューターにインストールされている最新のメジャー言語バージョン (C# 7.0) とマイナー言語バージョン (C# 7.3) に解決されます。</span><span class="sxs-lookup"><span data-stu-id="c1092-161">The special strings `default` and `latest` resolve to the latest major (C# 7.0) and minor (C# 7.3) language versions installed on the build machine, respectively.</span></span>

## <a name="configure-multiple-projects"></a><span data-ttu-id="c1092-162">複数のプロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="c1092-162">Configure multiple projects</span></span>

<span data-ttu-id="c1092-163">複数のディレクトリを構成する `<LangVersion>` 要素を含む **Directory.build.props** ファイルを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="c1092-163">You can create a **Directory.build.props** file that contains the `<LangVersion>` element to configure multiple directories.</span></span> <span data-ttu-id="c1092-164">この操作は通常、ソリューション ディレクトリで実行します。</span><span class="sxs-lookup"><span data-stu-id="c1092-164">You typically do that in your solution directory.</span></span> <span data-ttu-id="c1092-165">ソリューション ディレクトリ内の **Directory.build.props** ファイルに以下を追加します。</span><span class="sxs-lookup"><span data-stu-id="c1092-165">Add the following to a **Directory.build.props** file in your solution directory:</span></span>

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

<span data-ttu-id="c1092-166">これで、そのファイルを含むディレクトリのすべてのサブディレクトリ内のビルドで、C# バージョン 7.3 構文が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c1092-166">Now, builds in every subdirectory of the directory containing that file will use C# version 7.3 syntax.</span></span> <span data-ttu-id="c1092-167">詳しくは、「[ビルドのカスタマイズ](/visualstudio/msbuild/customize-your-build)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1092-167">For more information, see the article on [Customize your build](/visualstudio/msbuild/customize-your-build).</span></span>

## <a name="set-the-langversion-compiler-option"></a><span data-ttu-id="c1092-168">言語コンパイラ オプションを設定する</span><span class="sxs-lookup"><span data-stu-id="c1092-168">Set the langversion compiler option</span></span>

<span data-ttu-id="c1092-169">`-langversion` コマンド ライン オプションを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c1092-169">You can use the `-langversion` command-line option.</span></span> <span data-ttu-id="c1092-170">詳しくは、[-langversion](../language-reference/compiler-options/langversion-compiler-option.md) コンパイラ オプションに関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1092-170">For more information, see the article on the [-langversion](../language-reference/compiler-options/langversion-compiler-option.md) compiler option.</span></span> <span data-ttu-id="c1092-171">「`csc -langversion:?`」と入力して、有効な値の一覧を確認できます。</span><span class="sxs-lookup"><span data-stu-id="c1092-171">You can see a list of the valid values by typing  `csc -langversion:?`.</span></span>
