---
title: "project.json と csproj の比較 - .NET Core"
description: "「project.json 要素と csproj 要素の間のマッピング」を参照してください。"
keywords: project.json, csproj, .NET Core, MSBuild
author: natemcmaster
ms.author: mairaw
ms.date: 03/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 79c50621-a24a-4e64-bbb9-b953113e841c
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0f82e82c6a11220e24c85cef19bc131e12c77bf0
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="a-mapping-between-projectjson-and-csproj-properties"></a><span data-ttu-id="19bfe-104">project.json プロパティと csproj プロパティの間のマッピング</span><span class="sxs-lookup"><span data-stu-id="19bfe-104">A mapping between project.json and csproj properties</span></span>

<span data-ttu-id="19bfe-105">作成者: [Nate McMaster](https://github.com/natemcmaster)</span><span class="sxs-lookup"><span data-stu-id="19bfe-105">By [Nate McMaster](https://github.com/natemcmaster)</span></span>

<span data-ttu-id="19bfe-106">.NET Core ツールの開発中、重要なデザイン変更が行われました。*project.json* ファイルのサポートが終了となり、代わりに.NET Core プロジェクトが MSBuild/csproj 形式に移行されました。</span><span class="sxs-lookup"><span data-stu-id="19bfe-106">During the development of the .NET Core tooling, an important design change was made to no longer support *project.json* files and instead move the .NET Core projects to the MSBuild/csproj format.</span></span>

<span data-ttu-id="19bfe-107">この記事では、*project.json* の設定が MSBuild/csproj 形式でどのように表示されるか説明します。最新バージョンのツールにプロジェクトをアップグレードするとき、新しい形式の利用方法を知り、移行ツールで行われた変更を理解できます。</span><span class="sxs-lookup"><span data-stu-id="19bfe-107">This article shows how the settings in *project.json* are represented in the MSBuild/csproj format so you can learn how to use the new format and understand the changes made by the migration tools when you're upgrading your project to the latest version of the tooling.</span></span> 
 
## <a name="the-csproj-format"></a><span data-ttu-id="19bfe-108">csproj 形式</span><span class="sxs-lookup"><span data-stu-id="19bfe-108">The csproj format</span></span>

<span data-ttu-id="19bfe-109">新しい形式の \*.csproj は XML ベースの形式です。</span><span class="sxs-lookup"><span data-stu-id="19bfe-109">The new format, \*.csproj, is an XML-based format.</span></span> <span data-ttu-id="19bfe-110">次の例は、`Microsoft.NET.Sdk` を利用した .NET Core プロジェクトのルート ノードです。</span><span class="sxs-lookup"><span data-stu-id="19bfe-110">The following example shows the root node of a .NET Core project using the `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="19bfe-111">Web プロジェクトの場合、使用される SDK は `Microsoft.NET.Sdk.Web` です。</span><span class="sxs-lookup"><span data-stu-id="19bfe-111">For web projects, the SDK used is `Microsoft.NET.Sdk.Web`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a><span data-ttu-id="19bfe-112">一般的な最上位プロパティ</span><span class="sxs-lookup"><span data-stu-id="19bfe-112">Common top-level properties</span></span>

### <a name="name"></a><span data-ttu-id="19bfe-113">name</span><span class="sxs-lookup"><span data-stu-id="19bfe-113">name</span></span>
```json
{
  "name": "MyProjectName"
}
```

<span data-ttu-id="19bfe-114">サポート対象から除外されました。</span><span class="sxs-lookup"><span data-stu-id="19bfe-114">No longer supported.</span></span> <span data-ttu-id="19bfe-115">csproj では、これは、ディレクトリ名により定義される、プロジェクト ファイル名により決定されます。</span><span class="sxs-lookup"><span data-stu-id="19bfe-115">In csproj, this is determined by the project filename, which is defined by the directory name.</span></span> <span data-ttu-id="19bfe-116">たとえば、`MyProjectName.csproj` のようにします。</span><span class="sxs-lookup"><span data-stu-id="19bfe-116">For example, `MyProjectName.csproj`.</span></span>

<span data-ttu-id="19bfe-117">既定では、プロジェクト ファイル名により、`<AssemblyName>` プロパティと `<PackageId>` プロパティの値も指定されます。</span><span class="sxs-lookup"><span data-stu-id="19bfe-117">By default, the project filename also specifies the value of the `<AssemblyName>` and `<PackageId>` properties.</span></span> 

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

<span data-ttu-id="19bfe-118">project.json に `buildOptions\outputName` プロパティが定義されている場合、`<AssemblyName>` には `<PackageId>` 以外の値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="19bfe-118">The `<AssemblyName>` will have a different value than `<PackageId>` if `buildOptions\outputName` property was defined in project.json.</span></span> <span data-ttu-id="19bfe-119">詳細については、「[その他の共通ビルド オプション](#other-common-build-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19bfe-119">For more information, see [Other common build options](#other-common-build-options).</span></span>

### <a name="version"></a><span data-ttu-id="19bfe-120">version</span><span class="sxs-lookup"><span data-stu-id="19bfe-120">version</span></span>

```json
{
  "version": "1.0.0-alpha-*"
}
```
<span data-ttu-id="19bfe-121">`VersionPrefix` プロパティおよび `VersionSuffix` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="19bfe-121">Use the `VersionPrefix` and `VersionSuffix` properties:</span></span>

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

<span data-ttu-id="19bfe-122">`Version` プロパティを使用することもできますが、これにより、パッケージ処理中にバージョン設定が上書きされることがあります。</span><span class="sxs-lookup"><span data-stu-id="19bfe-122">You can also use the `Version` property, but this may override version settings during packaging:</span></span>

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a><span data-ttu-id="19bfe-123">その他の共通のルートレベル オプション</span><span class="sxs-lookup"><span data-stu-id="19bfe-123">Other common root-level options</span></span>

```json
{
  "authors": [ "Anne", "Bob" ],
  "company": "Contoso",
  "language": "en-US",
  "title": "My library",
  "description": "This is my library.\r\nAnd it's really great!",
  "copyright": "Nugetizer 3000",
  "userSecretsId": "xyz123"
}
```

```xml
<PropertyGroup>
  <Authors>Anne;Bob</Authors>
  <Company>Contoso</Company>
  <NeutralLanguage>en-US</NeutralLanguage>
  <AssemblyTitle>My library</AssemblyTitle>
  <Description>This is my library.
And it's really great!</Description>
  <Copyright>Nugetizer 3000</Copyright>
  <UserSecretsId>xyz123</UserSecretsId>
</PropertyGroup>
```

## <a name="frameworks"></a><span data-ttu-id="19bfe-124">frameworks</span><span class="sxs-lookup"><span data-stu-id="19bfe-124">frameworks</span></span>

### <a name="one-target-framework"></a><span data-ttu-id="19bfe-125">1 つのターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="19bfe-125">One target framework</span></span>
```json
{
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp1.0</TargetFramework>
</PropertyGroup>
```

### <a name="multiple-target-frameworks"></a><span data-ttu-id="19bfe-126">複数のターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="19bfe-126">Multiple target frameworks</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

<span data-ttu-id="19bfe-127">`TargetFrameworks` プロパティを使用し、ターゲット フレームワークの一覧を定義します。</span><span class="sxs-lookup"><span data-stu-id="19bfe-127">Use the `TargetFrameworks` property to define your list of target frameworks.</span></span> <span data-ttu-id="19bfe-128">複数のフレームワーク値を区切るには、セミコロンを使用します。</span><span class="sxs-lookup"><span data-stu-id="19bfe-128">Use semi-colon to separate multiple framework values.</span></span> 

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a><span data-ttu-id="19bfe-129">依存関係</span><span class="sxs-lookup"><span data-stu-id="19bfe-129">dependencies</span></span>

> [!IMPORTANT]
> <span data-ttu-id="19bfe-130">依存関係がパッケージではなく、**プロジェクト**の場合、形式は異なります。</span><span class="sxs-lookup"><span data-stu-id="19bfe-130">If the dependency is a **project** and not a package, the format is different.</span></span> <span data-ttu-id="19bfe-131">詳細については、「[依存関係の種類](#dependency-type)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="19bfe-131">For more information, see the [dependency type](#dependency-type) section.</span></span>

### <a name="netstandardlibrary-metapackage"></a><span data-ttu-id="19bfe-132">NETStandard.Library のメタパッケージ</span><span class="sxs-lookup"><span data-stu-id="19bfe-132">NETStandard.Library metapackage</span></span>

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  }
}
```

```xml
<PropertyGroup>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

### <a name="microsoftnetcoreapp-metapackage"></a><span data-ttu-id="19bfe-133">Microsoft.NETCore.App のメタパッケージ</span><span class="sxs-lookup"><span data-stu-id="19bfe-133">Microsoft.NETCore.App metapackage</span></span>

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0"
  }
}
```

```xml
<PropertyGroup>
  <RuntimeFrameworkVersion>1.0.3</RuntimeFrameworkVersion>
</PropertyGroup>
```

<span data-ttu-id="19bfe-134">移行されたプロジェクトの `<RuntimeFrameworkVersion>` 値はインストールした SDK のバージョンにより決定されます。</span><span class="sxs-lookup"><span data-stu-id="19bfe-134">Note that the `<RuntimeFrameworkVersion>` value in the migrated project is determined by the version of the SDK you have installed.</span></span>

### <a name="top-level-dependencies"></a><span data-ttu-id="19bfe-135">最上位の依存関係</span><span class="sxs-lookup"><span data-stu-id="19bfe-135">Top-level dependencies</span></span>
```json
{
  "dependencies": {
    "Microsoft.AspNetCore": "1.1.0"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore" Version="1.1.0" />
</ItemGroup>
```

### <a name="per-framework-dependencies"></a><span data-ttu-id="19bfe-136">フレームワーク別の依存関係</span><span class="sxs-lookup"><span data-stu-id="19bfe-136">Per-framework dependencies</span></span>
```json
{
  "framework": {
    "net451": {
      "dependencies": {
        "System.Collections.Immutable": "1.3.1"
      }
    },
    "netstandard1.5": {
      "dependencies": {
        "Newtonsoft.Json": "9.0.1"
      }
    }
  }
}
```

```xml
<ItemGroup Condition="'$(TargetFramework)'=='net451'">
  <PackageReference Include="System.Collections.Immutable" Version="1.3.1" />
</ItemGroup>

<ItemGroup Condition="'$(TargetFramework)'=='netstandard1.5'">
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
</ItemGroup>
```

### <a name="imports"></a><span data-ttu-id="19bfe-137">インポート</span><span class="sxs-lookup"><span data-stu-id="19bfe-137">imports</span></span>

```json
{
  "dependencies": {
    "YamlDotNet": "4.0.1-pre309"
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dnxcore50",
        "dotnet"
      ]
    }
  }
}
```

```xml
<PropertyGroup>
  <PackageTargetFallback>dnxcore50;dotnet</PackageTargetFallback>
</PropertyGroup>
<ItemGroup>
  <PackageReference Include="YamlDotNet" Version="4.0.1-pre309" />
</ItemGroup>
```

### <a name="dependency-type"></a><span data-ttu-id="19bfe-138">依存関係の種類</span><span class="sxs-lookup"><span data-stu-id="19bfe-138">dependency type</span></span>

#### <a name="type-project"></a><span data-ttu-id="19bfe-139">type: project</span><span class="sxs-lookup"><span data-stu-id="19bfe-139">type: project</span></span>
```json
{
  "dependencies": {
    "MyOtherProject": "1.0.0-*",
    "AnotherProject": {
      "type": "project"
    }
  }
}
```

```xml
<ItemGroup>
  <ProjectReference Include="..\MyOtherProject\MyOtherProject.csproj" />
  <ProjectReference Include="..\AnotherProject\AnotherProject.csproj" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="19bfe-140">`dotnet pack --version-suffix $suffix` がプロジェクト参照の依存関係バージョンを決定する方法が無効になります。</span><span class="sxs-lookup"><span data-stu-id="19bfe-140">This will break the way that `dotnet pack --version-suffix $suffix` determines the dependency version of a project reference.</span></span>


#### <a name="type-build"></a><span data-ttu-id="19bfe-141">type: build</span><span class="sxs-lookup"><span data-stu-id="19bfe-141">type: build</span></span>
```json
{
  "dependencies": {
    "Microsoft.EntityFrameworkCore.Design": {
      "version": "1.1.0",
      "type": "build"
    }
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="1.1.0" PrivateAssets="All" />
</ItemGroup>
```

#### <a name="type-platform"></a><span data-ttu-id="19bfe-142">type: platform</span><span class="sxs-lookup"><span data-stu-id="19bfe-142">type: platform</span></span>
```json
{
  "dependencies": {
    "Microsoft.NETCore.App": {
      "version": "1.1.0",
      "type": "platform"
    }
  }
}
```

<span data-ttu-id="19bfe-143">csproj には同等のものがありません。</span><span class="sxs-lookup"><span data-stu-id="19bfe-143">There is no equivalent in csproj.</span></span> 

## <a name="runtimes"></a><span data-ttu-id="19bfe-144">runtimes</span><span class="sxs-lookup"><span data-stu-id="19bfe-144">runtimes</span></span>
```json
{
  "runtimes": {
    "win7-x64": {},
    "osx.10.11-x64": {},
    "ubuntu.16.04-x64": {}
  }
}
```

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win7-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="standalone-apps-self-contained-deployment"></a><span data-ttu-id="19bfe-145">スタンドアロン アプリ (自己完結型の展開)</span><span class="sxs-lookup"><span data-stu-id="19bfe-145">Standalone apps (self-contained deployment)</span></span>
<span data-ttu-id="19bfe-146">project.json では、`runtimes` セクションを定義することは、ビルドと公開の間にアプリがスタンドアロンであったことを意味します。</span><span class="sxs-lookup"><span data-stu-id="19bfe-146">In project.json, defining a `runtimes` section means the app was standalone during build and publish.</span></span>
<span data-ttu-id="19bfe-147">MSBuild では、ビルド中、すべてのプロジェクトが*移植可能*ですが、スタンドアロンとして公開できます。</span><span class="sxs-lookup"><span data-stu-id="19bfe-147">In MSBuild, all projects are *portable* during build, but can be published as standalone.</span></span>

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

<span data-ttu-id="19bfe-148">詳細については、「[自己完結型の展開 (SCD)](../deploying/index.md#self-contained-deployments-scd)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19bfe-148">For more information, see [Self-contained deployments (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span>

## <a name="tools"></a><span data-ttu-id="19bfe-149">ツール</span><span class="sxs-lookup"><span data-stu-id="19bfe-149">tools</span></span>
```json
{
  "tools": {
    "Microsoft.EntityFrameworkCore.Tools.DotNet": "1.0.0-*"
  }
}
```

```xml
<ItemGroup>
  <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.0" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="19bfe-150">ツールの `imports` は、csproj ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="19bfe-150">`imports` on tools are not supported in csproj.</span></span> <span data-ttu-id="19bfe-151">インポートを必要とするツールは、新しい `Microsoft.NET.Sdk` で機能しません。</span><span class="sxs-lookup"><span data-stu-id="19bfe-151">Tools that need imports will not work with the new `Microsoft.NET.Sdk`.</span></span>

## <a name="buildoptions"></a><span data-ttu-id="19bfe-152">buildOptions</span><span class="sxs-lookup"><span data-stu-id="19bfe-152">buildOptions</span></span>

<span data-ttu-id="19bfe-153">「[Files](#files)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="19bfe-153">See also [Files](#files).</span></span>

### <a name="emitentrypoint"></a><span data-ttu-id="19bfe-154">emitEntryPoint</span><span class="sxs-lookup"><span data-stu-id="19bfe-154">emitEntryPoint</span></span>

```json
{
  "buildOptions": {
    "emitEntryPoint": true
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="19bfe-155">`emitEntryPoint` が `false` であった場合、`OutputType` の値は `Library` に変換されます。これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="19bfe-155">If `emitEntryPoint` was `false`, the value of `OutputType` is converted to `Library`, which is the default value:</span></span>

```json
{
  "buildOptions": {
    "emitEntryPoint": false
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Library</OutputType>
  <!-- or, omit altogether. It defaults to 'Library' -->
</PropertyGroup>
```

### <a name="keyfile"></a><span data-ttu-id="19bfe-156">keyFile</span><span class="sxs-lookup"><span data-stu-id="19bfe-156">keyFile</span></span>

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

<span data-ttu-id="19bfe-157">`keyFile` 要素は、MSBuild で 3 つのプロパティになりました。</span><span class="sxs-lookup"><span data-stu-id="19bfe-157">The `keyFile` element expands to three properties in MSBuild:</span></span>

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a><span data-ttu-id="19bfe-158">その他の共通ビルド オプション</span><span class="sxs-lookup"><span data-stu-id="19bfe-158">Other common build options</span></span>

```json
{
  "buildOptions": {
    "warningsAsErrors": true,
    "nowarn": ["CS0168", "CS0219"],
    "xmlDoc": true,
    "preserveCompilationContext": true,
    "outputName": "Different.AssemblyName",
    "debugType": "portable",
    "allowUnsafe": true,
    "define": ["TEST", "OTHERCONDITION"]
  }
}
```

```xml
<PropertyGroup>
  <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
  <NoWarn>$(NoWarn);CS0168;CS0219</NoWarn>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
  <PreserveCompilationContext>true</PreserveCompilationContext>
  <AssemblyName>Different.AssemblyName</AssemblyName>
  <DebugType>portable</DebugType>
  <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  <DefineConstants>$(DefineConstants);TEST;OTHERCONDITION</DefineConstants>
</PropertyGroup>
```

## <a name="packoptions"></a><span data-ttu-id="19bfe-159">packOptions</span><span class="sxs-lookup"><span data-stu-id="19bfe-159">packOptions</span></span>

<span data-ttu-id="19bfe-160">「[Files](#files)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="19bfe-160">See also [Files](#files).</span></span>

### <a name="common-pack-options"></a><span data-ttu-id="19bfe-161">共通パック オプション</span><span class="sxs-lookup"><span data-stu-id="19bfe-161">Common pack options</span></span>

```json
{
  "packOptions": {    
    "summary": "numl is a machine learning library intended to ease the use of using standard modeling techniques for both prediction and clustering.",
    "tags": ["machine learning", "framework"],
    "releaseNotes": "Version 0.9.12-beta",
    "iconUrl": "http://numl.net/images/ico.png",
    "projectUrl": "http://numl.net",
    "licenseUrl": "https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md",
    "requireLicenseAcceptance": false,
    "repository": {
      "type": "git",
      "url": "https://raw.githubusercontent.com/sethjuarez/numl"
    },
    "owners": ["Seth Juarez"]
  }
}
```

```xml
<PropertyGroup>
  <!-- summary is not migrated from project.json, but you can use the <Description> property for that if needed. -->
  <PackageTags>machine learning;framework</PackageTags>
  <PackageReleaseNotes>Version 0.9.12-beta</PackageReleaseNotes>
  <PackageIconUrl>http://numl.net/images/ico.png</PackageIconUrl>
  <PackageProjectUrl>http://numl.net</PackageProjectUrl>
  <PackageLicenseUrl>https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md</PackageLicenseUrl>
  <PackageRequireLicenseAcceptance>false</PackageRequireLicenseAcceptance>
  <RepositoryType>git</RepositoryType>
  <RepositoryUrl>https://raw.githubusercontent.com/sethjuarez/numl</RepositoryUrl>
  <!-- owners is not supported in MSBuild -->
</PropertyGroup>
```

<span data-ttu-id="19bfe-162">MSBuild では、`owners` 要素に相当するものはありません。</span><span class="sxs-lookup"><span data-stu-id="19bfe-162">There is no equivalent for the `owners` element in MSBuild.</span></span> <span data-ttu-id="19bfe-163">`summary` の場合、MSBuild の `<Description>` プロパティを利用できます (ただし、`summary` の値はそのプロパティに自動的に移行されません)。そのプロパティが [`description`](#-other-common-root-level-options) 要素にマッピングされているためです。</span><span class="sxs-lookup"><span data-stu-id="19bfe-163">For `summary`, you can use the MSBuild `<Description>` property, even though the value of `summary` is not migrated automatically to that property, since that property is mapped to the [`description`](#-other-common-root-level-options) element.</span></span>

## <a name="scripts"></a><span data-ttu-id="19bfe-164">スクリプト</span><span class="sxs-lookup"><span data-stu-id="19bfe-164">scripts</span></span>

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

<span data-ttu-id="19bfe-165">MSBuild でこれに相当するものは[ターゲット](/visualstudio/msbuild/msbuild-targets)です。</span><span class="sxs-lookup"><span data-stu-id="19bfe-165">Their equivalent in MSBuild are [targets](/visualstudio/msbuild/msbuild-targets):</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```


## <a name="runtimeoptions"></a><span data-ttu-id="19bfe-166">runtimeOptions</span><span class="sxs-lookup"><span data-stu-id="19bfe-166">runtimeOptions</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "System.GC.Server": true,
      "System.GC.Concurrent": true,
      "System.GC.RetainVM": true,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

<span data-ttu-id="19bfe-167">"System.GC.Server" プロパティを除き、このグループのすべての設定がプロジェクト フォルダーの *runtimeconfig.template.json* というファイルに配置されます。オプションは移行プロセス中にルート オブジェクトに移動します。</span><span class="sxs-lookup"><span data-stu-id="19bfe-167">All settings in this group, except for the "System.GC.Server" property, are placed into a file called *runtimeconfig.template.json* in the project folder, with options lifted to the root object during the migration process:</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": true,
    "System.GC.RetainVM": true,
    "System.Threading.ThreadPool.MinThreads": 4,
    "System.Threading.ThreadPool.MaxThreads": 25
  }
}
```

<span data-ttu-id="19bfe-168">"System.GC.Server" プロパティは csproj ファイルに移行されます。</span><span class="sxs-lookup"><span data-stu-id="19bfe-168">The "System.GC.Server" property is migrated into the csproj file:</span></span>
```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

<span data-ttu-id="19bfe-169">ただし、csproj のこれらの値はすべて MSBuild プロパティと共に設定できます。</span><span class="sxs-lookup"><span data-stu-id="19bfe-169">However, you can set all those values in the csproj as well as MSBuild properties:</span></span>
```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a><span data-ttu-id="19bfe-170">shared</span><span class="sxs-lookup"><span data-stu-id="19bfe-170">shared</span></span>
```json
{
  "shared": "shared/**/*.cs"
}
```

<span data-ttu-id="19bfe-171">csproj ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="19bfe-171">Not supported in csproj.</span></span> <span data-ttu-id="19bfe-172">代わりに、*.nuspec* ファイルにコンテンツ ファイルを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19bfe-172">You must instead create include content files in your *.nuspec* file.</span></span> <span data-ttu-id="19bfe-173">詳細については、「[Including content files](/nuget/schema/nuspec#including-content-files)」 (コンテンツ ファイルを追加する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19bfe-173">For more information, see [Including content files](/nuget/schema/nuspec#including-content-files).</span></span>

## <a name="files"></a><span data-ttu-id="19bfe-174">ファイル</span><span class="sxs-lookup"><span data-stu-id="19bfe-174">files</span></span>

<span data-ttu-id="19bfe-175">*project.json* では、ビルドとパックは、複数のフォルダーからのコンパイルと埋め込みまで拡張できます。</span><span class="sxs-lookup"><span data-stu-id="19bfe-175">In *project.json*, build and pack could be extended to compile and embed from different folders.</span></span>
<span data-ttu-id="19bfe-176">MSBuild では、これは[項目](/visualstudio/msbuild/common-msbuild-project-items)の使用により行われます。</span><span class="sxs-lookup"><span data-stu-id="19bfe-176">In MSBuild, this is done using [items](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="19bfe-177">次の例は一般的な変換です。</span><span class="sxs-lookup"><span data-stu-id="19bfe-177">The following example is a common conversion:</span></span>

```json
{
  "buildOptions": {
    "compile": {
      "copyToOutput": "notes.txt",
      "include": "../Shared/*.cs",
      "exclude": "../Shared/Not/*.cs"
    },
    "embed": {
      "include": "../Shared/*.resx"
    }
  },
  "packOptions": {
    "include": "Views/",
    "mappings": {
      "some/path/in/project.txt": "in/package.txt"
    }
  },
  "publishOptions": {
    "include": [
      "files/",
      "publishnotes.txt"
    ]
  }
}
```

```xml
<ItemGroup>
  <Compile Include="..\Shared\*.cs" Exclude="..\Shared\Not\*.cs" />
  <EmbeddedResource Include="..\Shared\*.resx" />
  <Content Include="Views\**\*" PackagePath="%(Identity)" />
  <None Include="some/path/in/project.txt" Pack="true" PackagePath="in/package.txt" />
  
  <None Include="notes.txt" CopyToOutputDirectory="Always" />
  <!-- CopyToOutputDirectory = { Always, PreserveNewest, Never } -->

  <Content Include="files\**\*" CopyToPublishDirectory="PreserveNewest" />
  <None Include="publishnotes.txt" CopyToPublishDirectory="Always" />
  <!-- CopyToPublishDirectory = { Always, PreserveNewest, Never } -->
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="19bfe-178">既定の [Glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))の多くは .NET Core SDK により自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="19bfe-178">Many of the default [globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are added automatically by the .NET Core SDK.</span></span>
> <span data-ttu-id="19bfe-179">詳細については、「[Default Compile Item Values](https://aka.ms/sdkimplicititems)」 (既定のコンパイル項目値) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19bfe-179">For more information, see [Default Compile Item Values](https://aka.ms/sdkimplicititems).</span></span>

<span data-ttu-id="19bfe-180">すべての MSBuild `ItemGroup` 要素で `Include`、`Exclude`、`Remove` がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="19bfe-180">All MSBuild `ItemGroup` elements support `Include`, `Exclude`, and `Remove`.</span></span>

<span data-ttu-id="19bfe-181">.nupkg 内のパッケージ レイアウトは `PackagePath="path"` で変更できます。</span><span class="sxs-lookup"><span data-stu-id="19bfe-181">Package layout inside the .nupkg can be modified with `PackagePath="path"`.</span></span>

<span data-ttu-id="19bfe-182">`Content` を除き、ほとんどの項目グループで、パッケージに `Pack="true"` を明示的に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19bfe-182">Except for `Content`, most item groups require explicitly adding `Pack="true"` to be included in the package.</span></span> <span data-ttu-id="19bfe-183">MSBuild の `<IncludeContentInPack>` プロパティが既定で `true` に設定されているため、`Content` はパッケージの*コンテンツ* フォルダーに置かれます。</span><span class="sxs-lookup"><span data-stu-id="19bfe-183">`Content` will be put in the *content* folder in a package since the MSBuild `<IncludeContentInPack>` property is set to `true` by default.</span></span> <span data-ttu-id="19bfe-184">詳細については、「[Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package)」 (パッケージにコンテンツを追加する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19bfe-184">For more information, see [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span></span>

<span data-ttu-id="19bfe-185">`PackagePath="%(Identity)"` は、パッケージ パスをプロジェクト関連のファイル パスに設定する簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="19bfe-185">`PackagePath="%(Identity)"` is a short way of setting package path to the project-relative file path.</span></span>

## <a name="testrunner"></a><span data-ttu-id="19bfe-186">testRunner</span><span class="sxs-lookup"><span data-stu-id="19bfe-186">testRunner</span></span>

### <a name="xunit"></a><span data-ttu-id="19bfe-187">xUnit</span><span class="sxs-lookup"><span data-stu-id="19bfe-187">xUnit</span></span>

```json
{
  "testRunner": "xunit",
  "dependencies": {
    "dotnet-test-xunit": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="xunit" Version="2.2.0-*" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0-*" />
</ItemGroup>
```

### <a name="mstest"></a><span data-ttu-id="19bfe-188">MSTest</span><span class="sxs-lookup"><span data-stu-id="19bfe-188">MSTest</span></span>

```json
{
  "testRunner": "mstest",
  "dependencies": {
    "dotnet-test-mstest": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.12-*" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11-*" />
</ItemGroup>
```

## <a name="see-also"></a><span data-ttu-id="19bfe-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="19bfe-189">See Also</span></span>

[<span data-ttu-id="19bfe-190">CLI の変更の概要</span><span class="sxs-lookup"><span data-stu-id="19bfe-190">High-level overview of changes in CLI</span></span>](../tools/cli-msbuild-architecture.md)

