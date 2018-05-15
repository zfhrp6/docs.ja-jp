---
title: dotnet new のカスタム テンプレートを作成する
description: この楽しいチュートリアルで、dotnet new のカスタム テンプレートを作成する方法を学びましょう。
author: guardrex
ms.author: mairaw
ms.date: 08/12/2017
ms.openlocfilehash: fee2709f54395b9926dae904a448cb92aafb5172
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="create-a-custom-template-for-dotnet-new"></a><span data-ttu-id="7fdff-103">dotnet new のカスタム テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="7fdff-103">Create a custom template for dotnet new</span></span>

<span data-ttu-id="7fdff-104">このチュートリアルでは、次の方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="7fdff-105">既存のプロジェクトまたは新しいコンソール アプリ プロジェクトから基本テンプレートを作成する。</span><span class="sxs-lookup"><span data-stu-id="7fdff-105">Create a basic template from an existing project or a new console app project.</span></span>
- <span data-ttu-id="7fdff-106">nuget.org で、またはローカルの *nupkg* ファイルから配布用にテンプレートをパッケージ化する。</span><span class="sxs-lookup"><span data-stu-id="7fdff-106">Pack the template for distribution at nuget.org or from a local *nupkg* file.</span></span>
- <span data-ttu-id="7fdff-107">nuget.org、ローカル *nupkg* ファイル、またはローカル ファイル システムからテンプレートをインストールする。</span><span class="sxs-lookup"><span data-stu-id="7fdff-107">Install the template from nuget.org, a local *nupkg* file, or the local file system.</span></span>
- <span data-ttu-id="7fdff-108">テンプレートをアンインストールする。</span><span class="sxs-lookup"><span data-stu-id="7fdff-108">Uninstall the template.</span></span>

<span data-ttu-id="7fdff-109">完全なサンプルでチュートリアルを続行する場合は、[サンプル プロジェクト テンプレート](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package)をダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="7fdff-109">If you prefer to proceed through the tutorial with a complete sample, download the [sample project template](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package).</span></span> <span data-ttu-id="7fdff-110">サンプル テンプレートは NuGet 配布用に構成されています。</span><span class="sxs-lookup"><span data-stu-id="7fdff-110">The sample template is configured for NuGet distribution.</span></span>

<span data-ttu-id="7fdff-111">ダウンロードしたサンプルをファイル システム配布で使用する場合、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="7fdff-111">If you wish to use the downloaded sample with file system distribution, do the following:</span></span>

- <span data-ttu-id="7fdff-112">サンプルの *content* フォルダーの中身を 1 つ上のレベルの *GarciaSoftware.ConsoleTemplate.CSharp* フォルダーに移動する。</span><span class="sxs-lookup"><span data-stu-id="7fdff-112">Move the contents of the *content* folder of the sample up one level into the *GarciaSoftware.ConsoleTemplate.CSharp* folder.</span></span>
- <span data-ttu-id="7fdff-113">空になった *content* フォルダーを削除する。</span><span class="sxs-lookup"><span data-stu-id="7fdff-113">Delete the empty *content* folder.</span></span>
- <span data-ttu-id="7fdff-114">*nuspec* ファイルを削除する。</span><span class="sxs-lookup"><span data-stu-id="7fdff-114">Delete the *nuspec* file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7fdff-115">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7fdff-115">Prerequisites</span></span>

- <span data-ttu-id="7fdff-116">[.NET Core 2.0 SDK](https://www.microsoft.com/net/core) 以降のバージョンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="7fdff-116">Install the [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) or later versions.</span></span>
- <span data-ttu-id="7fdff-117">参照トピックの「[dotnet new のカスタム テンプレート](../tools/custom-templates.md)」を確認しておきます。</span><span class="sxs-lookup"><span data-stu-id="7fdff-117">Read the reference topic [Custom templates for dotnet new](../tools/custom-templates.md).</span></span>

## <a name="create-a-template-from-a-project"></a><span data-ttu-id="7fdff-118">プロジェクトからテンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="7fdff-118">Create a template from a project</span></span>

<span data-ttu-id="7fdff-119">コンパイルして実行できることが確認されている既存のプロジェクトを利用するか、ハード ドライブのフォルダーで新しいコンソール アプリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-119">Use an existing project that you've confirmed compiles and runs, or create a new console app project in a folder on your hard drive.</span></span> <span data-ttu-id="7fdff-120">このチュートリアルでは、ユーザーのプロファイルの *Documents\Templates* に保存されている *GarciaSoftware.ConsoleTemplate.CSharp* をプロジェクト フォルダーとして想定しています。</span><span class="sxs-lookup"><span data-stu-id="7fdff-120">This tutorial assumes that the name of the project folder is *GarciaSoftware.ConsoleTemplate.CSharp* stored at *Documents\Templates* in the user's profile.</span></span> <span data-ttu-id="7fdff-121">チュートリアルのプロジェクト テンプレート名は、*\<会社名>.\<テンプレートの種類>.\<プログラミング言語>* という形式になりますが、プロジェクトとテンプレートには自由に名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="7fdff-121">The tutorial project template name is in the format *\<Company Name>.\<Template Type>.\<Programming Language>*, but you're free to name your project and template anything you wish.</span></span>

1. <span data-ttu-id="7fdff-122">*.template.config* という名前のプロジェクトのルートにフォルダーを追加します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-122">Add a folder to the root of the project named *.template.config*.</span></span>
1. <span data-ttu-id="7fdff-123">*.template.config* フォルダー内で、テンプレートを構成する *template.json* ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-123">Inside the *.template.config* folder, create a *template.json* file to configure your template.</span></span> <span data-ttu-id="7fdff-124">*template.json* ファイルの詳細情報とメンバー定義については、「[dotnet new のカスタム テンプレート](../tools/custom-templates.md#templatejson)」トピックと JSON Schema Store の [*template.json*](http://json.schemastore.org/template) スキーマを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fdff-124">For more information and member definitions for the *template.json* file, see the [Custom templates for dotnet new](../tools/custom-templates.md#templatejson) topic and the [*template.json* schema at the JSON Schema Store](http://json.schemastore.org/template).</span></span>

```json
{
    "$schema": "http://json.schemastore.org/template",
    "author": "Catalina Garcia",
    "classifications": [ "Common", "Console" ],
    "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
    "name": "Garcia Software Console Application",
    "shortName": "garciaconsole"
}
```

<span data-ttu-id="7fdff-125">テンプレートは完成となります。</span><span class="sxs-lookup"><span data-stu-id="7fdff-125">The template is finished.</span></span> <span data-ttu-id="7fdff-126">この時点で、テンプレート配布の選択肢が 2 つ与えられます。</span><span class="sxs-lookup"><span data-stu-id="7fdff-126">At this point, you have two options for template distribution.</span></span> <span data-ttu-id="7fdff-127">このチュートリアルを続行するには、いずれかのパスを選択します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-127">To continue this tutorial, choose one path or the other:</span></span>

1. <span data-ttu-id="7fdff-128">[NuGet 配布](#use-nuget-distribution): NuGet またはローカル *nupkg* ファイルからテンプレートをインストールし、インストールしたテンプレートを使用します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-128">[NuGet distribution](#use-nuget-distribution): install the template from NuGet or from the local *nupkg* file, and use the installed template.</span></span>
2. <span data-ttu-id="7fdff-129">[ファイル システム配布](#use-file-system-distribution)。</span><span class="sxs-lookup"><span data-stu-id="7fdff-129">[File system distribution](#use-file-system-distribution).</span></span>

## <a name="use-nuget-distribution"></a><span data-ttu-id="7fdff-130">NuGet 配布を利用する</span><span class="sxs-lookup"><span data-stu-id="7fdff-130">Use NuGet Distribution</span></span>

### <a name="pack-the-template-into-a-nuget-package"></a><span data-ttu-id="7fdff-131">テンプレートをパッケージ化し、NuGet パッケージを作成する</span><span class="sxs-lookup"><span data-stu-id="7fdff-131">Pack the template into a NuGet package</span></span>

1. <span data-ttu-id="7fdff-132">NuGet パッケージのフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-132">Create a folder for the NuGet package.</span></span> <span data-ttu-id="7fdff-133">このチュートリアルでは、*GarciaSoftware.ConsoleTemplate.CSharp* フォルダーが使用されます。このフォルダーは、ユーザーのプロファイルの *Documents\NuGetTemplates* フォルダーの中に作成されています。</span><span class="sxs-lookup"><span data-stu-id="7fdff-133">For the tutorial, the folder name *GarciaSoftware.ConsoleTemplate.CSharp* is used, and the folder is created inside a *Documents\NuGetTemplates* folder in the user's profile.</span></span> <span data-ttu-id="7fdff-134">プロジェクト ファイルを保存する目的で、新しいテンプレート フォルダー内に *content* という名前のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-134">Create a folder named *content* inside of the new template folder to hold the project files.</span></span>
1. <span data-ttu-id="7fdff-135">作成した *content* フォルダーに、プロジェクト フォルダーの中身を *.template.config/template.json* ファイルと共にコピーします。</span><span class="sxs-lookup"><span data-stu-id="7fdff-135">Copy the contents of your project folder, together with its *.template.config/template.json* file, into the *content* folder you created.</span></span>
1. <span data-ttu-id="7fdff-136">*content* フォルダーの隣に、[*nuspec*](/nuget/create-packages/creating-a-package) ファイルを追加します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-136">Next to the *content* folder, add a [*nuspec* file](/nuget/create-packages/creating-a-package).</span></span> <span data-ttu-id="7fdff-137">nuspec ファイルは XML マニフェスト ファイルであり、パッケージの中身が記述され、NuGet パッケージの作成プロセスを実行します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-137">The nuspec file is an XML manifest file that describes a package's contents and drives the process of creating the NuGet package.</span></span>
   
   ![NuGet パッケージのレイアウトを示すディレクトリ構造](./media/create-custom-template/nugetdirectorylayout.png)

1. <span data-ttu-id="7fdff-139">*nuspec* ファイルの **\<packageTypes>** 要素の中に、**\<packageType>** 要素を追加し、`name` 属性の値を `Template` にします。</span><span class="sxs-lookup"><span data-stu-id="7fdff-139">Inside of a **\<packageTypes>** element in the *nuspec* file, include a **\<packageType>** element with a `name` attribute value of `Template`.</span></span> <span data-ttu-id="7fdff-140">*content* フォルダーと *nuspec* ファイルの両方を同じディレクトリに入れます。</span><span class="sxs-lookup"><span data-stu-id="7fdff-140">Both the *content* folder and the *nuspec* file should reside in the same directory.</span></span> <span data-ttu-id="7fdff-141">下の表は、NuGet パッケージとしてテンプレートを生成するために必要な *nuspec* ファイルの最小要素をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="7fdff-141">The table shows the minimum *nuspec* file elements required to produce a template as a NuGet package.</span></span>

   | <span data-ttu-id="7fdff-142">要素</span><span class="sxs-lookup"><span data-stu-id="7fdff-142">Element</span></span>            | <span data-ttu-id="7fdff-143">型</span><span class="sxs-lookup"><span data-stu-id="7fdff-143">Type</span></span>   | <span data-ttu-id="7fdff-144">説明</span><span class="sxs-lookup"><span data-stu-id="7fdff-144">Description</span></span> |
   | ------------------ | ------ | ----------- |
   | <span data-ttu-id="7fdff-145">**\<authors>**</span><span class="sxs-lookup"><span data-stu-id="7fdff-145">**\<authors>**</span></span>     | <span data-ttu-id="7fdff-146">string</span><span class="sxs-lookup"><span data-stu-id="7fdff-146">string</span></span> | <span data-ttu-id="7fdff-147">パッケージ作成者の一覧。コンマで区切られています。nuget.org のプロファイル名と一致します。作成者は nuget.org の NuGet ギャラリーに表示され、同じ作成者によるパッケージの相互参照に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7fdff-147">A comma-separated list of packages authors, matching the profile names on nuget.org. Authors are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span> |
   | <span data-ttu-id="7fdff-148">**\<description>**</span><span class="sxs-lookup"><span data-stu-id="7fdff-148">**\<description>**</span></span> | <span data-ttu-id="7fdff-149">string</span><span class="sxs-lookup"><span data-stu-id="7fdff-149">string</span></span> | <span data-ttu-id="7fdff-150">UI 画面用のパッケージの長い説明。</span><span class="sxs-lookup"><span data-stu-id="7fdff-150">A long description of the package for UI display.</span></span> |
   | <span data-ttu-id="7fdff-151">**\<id>**</span><span class="sxs-lookup"><span data-stu-id="7fdff-151">**\<id>**</span></span>          | <span data-ttu-id="7fdff-152">string</span><span class="sxs-lookup"><span data-stu-id="7fdff-152">string</span></span> | <span data-ttu-id="7fdff-153">パッケージの識別子で、大文字と小文字が区別されます。nuget.org 全体で、あるいはパッケージが置かれるギャラリーで一意でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="7fdff-153">The case-insensitive package identifier, which must be unique across nuget.org or whatever gallery the package will reside in.</span></span> <span data-ttu-id="7fdff-154">ID には、URL によっては無効なスペースや文字が含まれることがあります。また、一般的に、.NET の名前空間ルールに従います。</span><span class="sxs-lookup"><span data-stu-id="7fdff-154">IDs may not contain spaces or characters that are not valid for a URL and generally follow .NET namespace rules.</span></span> <span data-ttu-id="7fdff-155">手引きについては、「[Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number)」 (一意のパッケージ識別子を選択し、バージョン番号を設定する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7fdff-155">See [Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number) for guidance.</span></span> |
   | <span data-ttu-id="7fdff-156">**\<packageType>**</span><span class="sxs-lookup"><span data-stu-id="7fdff-156">**\<packageType>**</span></span> | <span data-ttu-id="7fdff-157">string</span><span class="sxs-lookup"><span data-stu-id="7fdff-157">string</span></span> | <span data-ttu-id="7fdff-158">この要素を **\<metadata>** 要素の中の **\<packageTypes>** 要素内に置きます。</span><span class="sxs-lookup"><span data-stu-id="7fdff-158">Place this element inside a **\<packageTypes>** element among the **\<metadata>** elements.</span></span> <span data-ttu-id="7fdff-159">**\<packageType>** 要素の `name` 属性を `Template` に設定します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-159">Set the `name` attribute of the **\<packageType>** element to `Template`.</span></span> |
   | <span data-ttu-id="7fdff-160">**\<version>**</span><span class="sxs-lookup"><span data-stu-id="7fdff-160">**\<version>**</span></span>     | <span data-ttu-id="7fdff-161">string</span><span class="sxs-lookup"><span data-stu-id="7fdff-161">string</span></span> | <span data-ttu-id="7fdff-162">パッケージのバージョン。major.minor.patch パターンになります。</span><span class="sxs-lookup"><span data-stu-id="7fdff-162">The version of the package, following the major.minor.patch pattern.</span></span> <span data-ttu-id="7fdff-163">[プレリリース バージョン](/nuget/create-packages/prerelease-packages#semantic-versioning)に説明があるように、バージョン番号にはプレリリース接尾辞が含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="7fdff-163">Version numbers may include a pre-release suffix as described in [Pre-release versions](/nuget/create-packages/prerelease-packages#semantic-versioning).</span></span> |

   <span data-ttu-id="7fdff-164">*nuspec* ファイルの完全スキーマについては、[.nuspec リファレンス](/nuget/schema/nuspec)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7fdff-164">See the [.nuspec reference](/nuget/schema/nuspec) for the complete *nuspec* file schema.</span></span>

   <span data-ttu-id="7fdff-165">このチュートリアルの *nuspec* ファイルの名前は *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* であり、中身は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7fdff-165">The *nuspec* file for the tutorial is named *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* and contains the following content:</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. <span data-ttu-id="7fdff-166">`nuget pack <PATH_TO_NUSPEC_FILE>` コマンドで[パッケージを作成](/nuget/create-packages/creating-a-package#creating-the-package)します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-166">[Create the package](/nuget/create-packages/creating-a-package#creating-the-package) using the `nuget pack <PATH_TO_NUSPEC_FILE>` command.</span></span> <span data-ttu-id="7fdff-167">次のコマンドでは、NuGet アセットが保持されているフォルダーが *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* にあると想定しています。</span><span class="sxs-lookup"><span data-stu-id="7fdff-167">The following command assumes that the folder that holds the NuGet assets is at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*.</span></span> <span data-ttu-id="7fdff-168">ただし、システムのどこにフォルダーを置いても、`nuget pack` コマンドは *nuspec* ファイルのパスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="7fdff-168">But wherever you place the folder on your system, the `nuget pack` command accepts the path to the *nuspec* file:</span></span>

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a><span data-ttu-id="7fdff-169">パッケージを nuget.org に公開する</span><span class="sxs-lookup"><span data-stu-id="7fdff-169">Publishing the package to nuget.org</span></span>

<span data-ttu-id="7fdff-170">NuGet パッケージを公開するには、「[Create and publish a package](/nuget/quickstart/create-and-publish-a-package#publish-the-package)」 (パッケージを作成して公開する) トピックの手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="7fdff-170">To publish a NuGet package, follow the instructions in the [Create and publish a package](/nuget/quickstart/create-and-publish-a-package#publish-the-package) topic.</span></span> <span data-ttu-id="7fdff-171">ただし、チュートリアル テンプレートを NuGet に公開することは推奨されません。公開後は一覧から外すことはできますが、削除することができないためです。</span><span class="sxs-lookup"><span data-stu-id="7fdff-171">However, we recommend that you don't publish the tutorial template to NuGet as it can never be deleted once published, only delisted.</span></span> <span data-ttu-id="7fdff-172">これで *nupkg* ファイルの形式で NuGet パッケージができました。下の指示に従い、ローカル *nupkg* ファイルから直接、テンプレートをインストールすることを推奨します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-172">Now that you have the NuGet package in the form of a *nupkg* file, we suggest that you follow the instructions below to install the template directly from the local *nupkg* file.</span></span>

### <a name="install-the-template-from-a-nuget-package"></a><span data-ttu-id="7fdff-173">NuGet パッケージからテンプレートをインストールする</span><span class="sxs-lookup"><span data-stu-id="7fdff-173">Install the template from a NuGet package</span></span>

#### <a name="install-the-template-from-the-local-nupkg-file"></a><span data-ttu-id="7fdff-174">ローカル *nupkg* ファイルからテンプレートをインストールする</span><span class="sxs-lookup"><span data-stu-id="7fdff-174">Install the template from the local *nupkg* file</span></span>

<span data-ttu-id="7fdff-175">作成した *nupkg* ファイルからテンプレートをインストールするには、`-i|--install` オプションを付けて `dotnet new` コマンドを実行します。*nupkg* ファイルのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-175">To install the template from the *nupkg* file that you produced, use the `dotnet new` command with the `-i|--install` option and provide the path to the *nupkg* file:</span></span>

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="7fdff-176">nuget.org に保存されている NuGet パッケージからテンプレートをインストールする</span><span class="sxs-lookup"><span data-stu-id="7fdff-176">Install the template from a NuGet package stored at nuget.org</span></span>

<span data-ttu-id="7fdff-177">nuget.org に保存されている NuGet パッケージからテンプレートをインストールする場合、`-i|--install` オプションを付けて `dotnet new` コマンドを実行します。NuGet パッケージの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-177">If you wish to install a template from a NuGet package stored at nuget.org, use the `dotnet new` command with the `-i|--install` option and supply the name of the NuGet package:</span></span>

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="7fdff-178">次の例は、デモンストレーション目的のみで提供されます。</span><span class="sxs-lookup"><span data-stu-id="7fdff-178">The example is for demonstration purposes only.</span></span> <span data-ttu-id="7fdff-179">nuget.org には `GarciaSoftware.ConsoleTemplate.CSharp` NuGet パッケージがありません。NuGet からテスト テンプレートを公開し、利用する行為は推奨されません。</span><span class="sxs-lookup"><span data-stu-id="7fdff-179">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org, and we don't recommend that you publish and consume test templates from NuGet.</span></span> <span data-ttu-id="7fdff-180">コマンドを実行しても、テンプレートはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="7fdff-180">If you run the command, no template is installed.</span></span> <span data-ttu-id="7fdff-181">ただし、nuget.org に公開されていないテンプレートをインストールできます。前のセクション「[ローカル nupkg ファイルからテンプレートをインストールする](#install-the-template-from-the-local-nupkg-file)」にあるように、ローカル ファイル システムで直接、*nupkg* ファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-181">However, you can install a template that hasn't been published to nuget.org by referencing the *nupkg* file directly on your local file system as shown in the previous section [Install the template from the local nupkg file](#install-the-template-from-the-local-nupkg-file).</span></span>

<span data-ttu-id="7fdff-182">nuget.org でパッケージからテンプレートをインストールする方法を実演例で確認する場合は、[dotnet-new の NUnit 3 テンプレート](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="7fdff-182">If you'd like a live example of how to install a template from a package at nuget.org, you can use the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/).</span></span> <span data-ttu-id="7fdff-183">このテンプレートで、NUnit 単体テストを使用するプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="7fdff-183">This template sets up a project to use NUnit unit testing.</span></span> <span data-ttu-id="7fdff-184">次のコマンドでインストールします。</span><span class="sxs-lookup"><span data-stu-id="7fdff-184">Use the following command to install it:</span></span>

```console
dotnet new -i NUnit3.DotNetNew.Template
```

<span data-ttu-id="7fdff-185">`dotnet new -l` でテンプレートを一覧表示すると、テンプレートの一覧で *NUnit 3 Test Project* を確認できます。Short Name は *nunit* です。</span><span class="sxs-lookup"><span data-stu-id="7fdff-185">When you list the templates with `dotnet new -l`, you see the *NUnit 3 Test Project* with a short name of *nunit* in the template list.</span></span> <span data-ttu-id="7fdff-186">次のセクションでこのテンプレートを利用できます。</span><span class="sxs-lookup"><span data-stu-id="7fdff-186">You're ready to use the template in the next section.</span></span>

![コンソール ウィンドウ。NUnit テンプレートとインストールされているその他のテンプレートを確認できます。](./media/create-custom-template/nunit1.png)

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="7fdff-188">テンプレートからプロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="7fdff-188">Create a project from the template</span></span>

<span data-ttu-id="7fdff-189">テンプレートを NuGet からインストールしたら、そのテンプレートを使用します。(`-o|--output` オプションを利用して特定のディレクトリを指定するのでなければ) テンプレート エンジンの出力を置くディレクトリから `dotnet new <TEMPLATE>` コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-189">After the template is installed from NuGet, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="7fdff-190">詳細については、「[`dotnet new` オプション](~/docs/core/tools/dotnet-new.md#options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fdff-190">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="7fdff-191">テンプレートの省略名 (短い名前) を `dotnet new` コマンドに直接指定します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-191">Supply the template's short name directly to the `dotnet new` command.</span></span> <span data-ttu-id="7fdff-192">NUnit テンプレートからプロジェクトを作成するには、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-192">To create a project from the NUnit template, run the following command:</span></span>

```console
dotnet new nunit
```

<span data-ttu-id="7fdff-193">プロジェクトが作成され、プロジェクトのパッケージが復元されたことがコンソールに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7fdff-193">The console shows that the project is created and that the project's packages are restored.</span></span> <span data-ttu-id="7fdff-194">コマンドを実行すると、プロジェクトが使用できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="7fdff-194">After the command is run, the project is ready for use.</span></span>

![コンソール ウィンドウ。dotnet new コマンドの出力を確認できます。NUnit プロジェクトが作成され、プロジェクトの依存関係が復元されました。](./media/create-custom-template/nunit2.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a><span data-ttu-id="7fdff-196">nuget.org に保存されている NuGet パッケージからテンプレートをアンインストールするには</span><span class="sxs-lookup"><span data-stu-id="7fdff-196">To uninstall a template from a NuGet package stored at nuget.org</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="7fdff-197">次の例は、デモンストレーション目的のみで提供されます。</span><span class="sxs-lookup"><span data-stu-id="7fdff-197">The example is for demonstration purposes only.</span></span> <span data-ttu-id="7fdff-198">nuget.org には `GarciaSoftware.ConsoleTemplate.CSharp` NuGet パッケージがありません。あるいは、.NET Core SDK と共にインストールされていません。</span><span class="sxs-lookup"><span data-stu-id="7fdff-198">There isn't a `GarciaSoftware.ConsoleTemplate.CSharp` NuGet package at nuget.org or installed with the .NET Core SDK.</span></span> <span data-ttu-id="7fdff-199">コマンドを実行すると、パッケージ/テンプレートはアンインストールされません。次の例外が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7fdff-199">If you run the command, no package/template is uninstalled and you receive the following exception:</span></span>
> 
> > <span data-ttu-id="7fdff-200">Could not find something to uninstall called 'GarciaSoftware.ConsoleTemplate.CSharp'. ('GarciaSoftware.ConsoleTemplate.CSharp' という名前のアンインストール対象が見つかりませんでした。)</span><span class="sxs-lookup"><span data-stu-id="7fdff-200">Could not find something to uninstall called 'GarciaSoftware.ConsoleTemplate.CSharp'.</span></span>

<span data-ttu-id="7fdff-201">[dotnet-new の NUnit 3 テンプレート](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/)をインストールしているとき、それをアンインストールする場合、次のコマンドを利用します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-201">If you installed the [NUnit 3 template for dotnet-new](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/) and wish to uninstall it, use the following command:</span></span>

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a><span data-ttu-id="7fdff-202">ローカル nupkg ファイルからテンプレートをアンインストールする</span><span class="sxs-lookup"><span data-stu-id="7fdff-202">Uninstall the template from a local nupkg file</span></span>

<span data-ttu-id="7fdff-203">テンプレートをアンインストールするとき、*nupkg* ファイルのパスを利用しないでください。</span><span class="sxs-lookup"><span data-stu-id="7fdff-203">When you wish to uninstall the template, don't attempt to use the path to the *nupkg* file.</span></span> <span data-ttu-id="7fdff-204">*`dotnet new -u <PATH_TO_NUPKG_FILE>` でテンプレートをアンインストールしようとすると失敗します。*</span><span class="sxs-lookup"><span data-stu-id="7fdff-204">*Attempting to uninstall a template using `dotnet new -u <PATH_TO_NUPKG_FILE>` fails.*</span></span> <span data-ttu-id="7fdff-205">パッケージはその `id` で参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fdff-205">Reference the package by its `id`:</span></span>

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a><span data-ttu-id="7fdff-206">ファイル システム配布を使用する</span><span class="sxs-lookup"><span data-stu-id="7fdff-206">Use file system distribution</span></span>

<span data-ttu-id="7fdff-207">テンプレートを配布するには、ネットワーク上のユーザーがアクセスできる場所にプロジェクト テンプレート フォルダーを置きます。</span><span class="sxs-lookup"><span data-stu-id="7fdff-207">To distribute the template, place the project template folder in a location accessible to users on your network.</span></span> <span data-ttu-id="7fdff-208">`-i|--install` オプションを付けて `dotnet new` コマンドを実行します。テンプレート フォルダー (プロジェクトと *.template.config* フォルダーが含まれるプロジェクト フォルダー) のパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-208">Use the `dotnet new` command with the `-i|--install` option and specify the path to the template folder (the project folder containing the project and the *.template.config* folder).</span></span>

<span data-ttu-id="7fdff-209">このチュートリアルでは、ユーザーのプロファイルの *Documents/Templates* フォルダーにプロジェクト テンプレートが保存されていると想定しています。</span><span class="sxs-lookup"><span data-stu-id="7fdff-209">The tutorial assumes the project template is stored in the *Documents/Templates* folder of the user's profile.</span></span> <span data-ttu-id="7fdff-210">その場所から、次のコマンドでテンプレートをインストールします。\<USER> はユーザーのプロファイルの名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-210">From that location, install the template with the following command replacing \<USER> with the user's profile name:</span></span>

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a><span data-ttu-id="7fdff-211">テンプレートからプロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="7fdff-211">Create a project from the template</span></span>

<span data-ttu-id="7fdff-212">テンプレートをファイル システムからインストールしたら、そのテンプレートを使用します。(`-o|--output` オプションを利用して特定のディレクトリを指定するのでなければ) テンプレート エンジンの出力を置くディレクトリから `dotnet new <TEMPLATE>` コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-212">After the template is installed from the file system, use the template by executing the `dotnet new <TEMPLATE>` command from the directory where you want to the template engine's output placed (unless you're using the `-o|--output` option to specify a specific directory).</span></span> <span data-ttu-id="7fdff-213">詳細については、「[`dotnet new` オプション](~/docs/core/tools/dotnet-new.md#options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fdff-213">For more information, see [`dotnet new` Options](~/docs/core/tools/dotnet-new.md#options).</span></span> <span data-ttu-id="7fdff-214">テンプレートの省略名 (短い名前) を `dotnet new` コマンドに直接指定します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-214">Supply the template's short name directly to the `dotnet new` command.</span></span>

<span data-ttu-id="7fdff-215">*C:\Users\\\<USER>\Documents\Projects\MyConsoleApp* に作成された新しいプロジェクト フォルダーで、`garciaconsole` テンプレートからプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7fdff-215">From a new project folder created at *C:\Users\\\<USER>\Documents\Projects\MyConsoleApp*, create a project from the `garciaconsole` template:</span></span>

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a><span data-ttu-id="7fdff-216">テンプレートをアンインストールする</span><span class="sxs-lookup"><span data-stu-id="7fdff-216">Uninstall the template</span></span>

<span data-ttu-id="7fdff-217">ローカル ファイル システムの *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* にテンプレートを作成した場合、`-u|--uninstall` スイッチとテンプレート フォルダーのパスを指定してアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="7fdff-217">If you created the template on your local file system at *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp*, uninstall it with the `-u|--uninstall` switch and the path to the template folder:</span></span>

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> <span data-ttu-id="7fdff-218">テンプレートをお使いのローカル ファイル システムからアンインストールするには、完全修飾パスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7fdff-218">To uninstall the template from your local file system, you need to fully qualify the path.</span></span> <span data-ttu-id="7fdff-219">たとえば、*C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、*./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="7fdff-219">For example, *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* will work, but *./GarciaSoftware.ConsoleTemplate.CSharp* from the containing folder will not.</span></span>
> <span data-ttu-id="7fdff-220">また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。</span><span class="sxs-lookup"><span data-stu-id="7fdff-220">Additionally, do not include a final terminating directory slash on your template path.</span></span>

## <a name="see-also"></a><span data-ttu-id="7fdff-221">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fdff-221">See also</span></span>

[<span data-ttu-id="7fdff-222">dotnet/templating GitHub リポジトリ Wiki</span><span class="sxs-lookup"><span data-stu-id="7fdff-222">dotnet/templating GitHub repo Wiki</span></span>](https://github.com/dotnet/templating/wiki)  
[<span data-ttu-id="7fdff-223">dotnet/dotnet-template-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="7fdff-223">dotnet/dotnet-template-samples GitHub repo</span></span>](https://github.com/dotnet/dotnet-template-samples)  
[<span data-ttu-id="7fdff-224">dotnet new の独自のテンプレートを作成する方法</span><span class="sxs-lookup"><span data-stu-id="7fdff-224">How to create your own templates for dotnet new</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/04/02/how-to-create-your-own-templates-for-dotnet-new/)  
[<span data-ttu-id="7fdff-225">JSON Schema Store の *template.json* スキーマ</span><span class="sxs-lookup"><span data-stu-id="7fdff-225">*template.json* schema at the JSON Schema Store</span></span>](http://json.schemastore.org/template)  
