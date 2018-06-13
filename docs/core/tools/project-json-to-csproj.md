---
title: project.json と csproj の比較 - .NET Core
description: 「project.json 要素と csproj 要素の間のマッピング」を参照してください。
author: natemcmaster
ms.author: mairaw
ms.date: 03/13/2017
ms.openlocfilehash: d262792cd6821d35dcaf2f4bb9c05625e1bcd2fa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218804"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a><span data-ttu-id="2c2c1-103">project.json プロパティと csproj プロパティの間のマッピング</span><span class="sxs-lookup"><span data-stu-id="2c2c1-103">A mapping between project.json and csproj properties</span></span>

<span data-ttu-id="2c2c1-104">作成者: [Nate McMaster](https://github.com/natemcmaster)</span><span class="sxs-lookup"><span data-stu-id="2c2c1-104">By [Nate McMaster](https://github.com/natemcmaster)</span></span>

<span data-ttu-id="2c2c1-105">.NET Core ツールの開発中、重要なデザイン変更が行われました。*project.json* ファイルのサポートが終了となり、代わりに.NET Core プロジェクトが MSBuild/csproj 形式に移行されました。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-105">During the development of the .NET Core tooling, an important design change was made to no longer support *project.json* files and instead move the .NET Core projects to the MSBuild/csproj format.</span></span>

<span data-ttu-id="2c2c1-106">この記事では、*project.json* の設定が MSBuild/csproj 形式でどのように表示されるか説明します。最新バージョンのツールにプロジェクトをアップグレードするとき、新しい形式の利用方法を知り、移行ツールで行われた変更を理解できます。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-106">This article shows how the settings in *project.json* are represented in the MSBuild/csproj format so you can learn how to use the new format and understand the changes made by the migration tools when you're upgrading your project to the latest version of the tooling.</span></span> 
 
## <a name="the-csproj-format"></a><span data-ttu-id="2c2c1-107">csproj 形式</span><span class="sxs-lookup"><span data-stu-id="2c2c1-107">The csproj format</span></span>

<span data-ttu-id="2c2c1-108">新しい形式の \*.csproj は XML ベースの形式です。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-108">The new format, \*.csproj, is an XML-based format.</span></span> <span data-ttu-id="2c2c1-109">次の例は、`Microsoft.NET.Sdk` を利用した .NET Core プロジェクトのルート ノードです。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-109">The following example shows the root node of a .NET Core project using the `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="2c2c1-110">Web プロジェクトの場合、使用される SDK は `Microsoft.NET.Sdk.Web` です。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-110">For web projects, the SDK used is `Microsoft.NET.Sdk.Web`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a><span data-ttu-id="2c2c1-111">一般的な最上位プロパティ</span><span class="sxs-lookup"><span data-stu-id="2c2c1-111">Common top-level properties</span></span>

### <a name="name"></a><span data-ttu-id="2c2c1-112">name</span><span class="sxs-lookup"><span data-stu-id="2c2c1-112">name</span></span>
```json
{
  "name": "MyProjectName"
}
```

<span data-ttu-id="2c2c1-113">サポート対象から除外されました。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-113">No longer supported.</span></span> <span data-ttu-id="2c2c1-114">csproj では、これは、ディレクトリ名により定義される、プロジェクト ファイル名により決定されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-114">In csproj, this is determined by the project filename, which is defined by the directory name.</span></span> <span data-ttu-id="2c2c1-115">たとえば、`MyProjectName.csproj` のようにします。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-115">For example, `MyProjectName.csproj`.</span></span>

<span data-ttu-id="2c2c1-116">既定では、プロジェクト ファイル名により、`<AssemblyName>` プロパティと `<PackageId>` プロパティの値も指定されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-116">By default, the project filename also specifies the value of the `<AssemblyName>` and `<PackageId>` properties.</span></span> 

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

<span data-ttu-id="2c2c1-117">project.json に `buildOptions\outputName` プロパティが定義されている場合、`<AssemblyName>` には `<PackageId>` 以外の値が設定されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-117">The `<AssemblyName>` will have a different value than `<PackageId>` if `buildOptions\outputName` property was defined in project.json.</span></span> <span data-ttu-id="2c2c1-118">詳細については、「[その他の共通ビルド オプション](#other-common-build-options)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-118">For more information, see [Other common build options](#other-common-build-options).</span></span>

### <a name="version"></a><span data-ttu-id="2c2c1-119">version</span><span class="sxs-lookup"><span data-stu-id="2c2c1-119">version</span></span>

```json
{
  "version": "1.0.0-alpha-*"
}
```
<span data-ttu-id="2c2c1-120">`VersionPrefix` プロパティおよび `VersionSuffix` プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-120">Use the `VersionPrefix` and `VersionSuffix` properties:</span></span>

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

<span data-ttu-id="2c2c1-121">`Version` プロパティを使用することもできますが、これにより、パッケージ処理中にバージョン設定が上書きされることがあります。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-121">You can also use the `Version` property, but this may override version settings during packaging:</span></span>

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a><span data-ttu-id="2c2c1-122">その他の共通のルートレベル オプション</span><span class="sxs-lookup"><span data-stu-id="2c2c1-122">Other common root-level options</span></span>

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

## <a name="frameworks"></a><span data-ttu-id="2c2c1-123">frameworks</span><span class="sxs-lookup"><span data-stu-id="2c2c1-123">frameworks</span></span>

### <a name="one-target-framework"></a><span data-ttu-id="2c2c1-124">1 つのターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="2c2c1-124">One target framework</span></span>
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

### <a name="multiple-target-frameworks"></a><span data-ttu-id="2c2c1-125">複数のターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="2c2c1-125">Multiple target frameworks</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

<span data-ttu-id="2c2c1-126">`TargetFrameworks` プロパティを使用し、ターゲット フレームワークの一覧を定義します。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-126">Use the `TargetFrameworks` property to define your list of target frameworks.</span></span> <span data-ttu-id="2c2c1-127">複数のフレームワーク値を区切るには、セミコロンを使用します。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-127">Use semi-colon to separate multiple framework values.</span></span> 

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a><span data-ttu-id="2c2c1-128">依存関係</span><span class="sxs-lookup"><span data-stu-id="2c2c1-128">dependencies</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c2c1-129">依存関係がパッケージではなく、**プロジェクト**の場合、形式は異なります。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-129">If the dependency is a **project** and not a package, the format is different.</span></span> <span data-ttu-id="2c2c1-130">詳細については、「[依存関係の種類](#dependency-type)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-130">For more information, see the [dependency type](#dependency-type) section.</span></span>

### <a name="netstandardlibrary-metapackage"></a><span data-ttu-id="2c2c1-131">NETStandard.Library のメタパッケージ</span><span class="sxs-lookup"><span data-stu-id="2c2c1-131">NETStandard.Library metapackage</span></span>

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

### <a name="microsoftnetcoreapp-metapackage"></a><span data-ttu-id="2c2c1-132">Microsoft.NETCore.App のメタパッケージ</span><span class="sxs-lookup"><span data-stu-id="2c2c1-132">Microsoft.NETCore.App metapackage</span></span>

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

<span data-ttu-id="2c2c1-133">移行されたプロジェクトの `<RuntimeFrameworkVersion>` 値はインストールした SDK のバージョンにより決定されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-133">Note that the `<RuntimeFrameworkVersion>` value in the migrated project is determined by the version of the SDK you have installed.</span></span>

### <a name="top-level-dependencies"></a><span data-ttu-id="2c2c1-134">最上位の依存関係</span><span class="sxs-lookup"><span data-stu-id="2c2c1-134">Top-level dependencies</span></span>
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

### <a name="per-framework-dependencies"></a><span data-ttu-id="2c2c1-135">フレームワーク別の依存関係</span><span class="sxs-lookup"><span data-stu-id="2c2c1-135">Per-framework dependencies</span></span>
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

### <a name="imports"></a><span data-ttu-id="2c2c1-136">インポート</span><span class="sxs-lookup"><span data-stu-id="2c2c1-136">imports</span></span>

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

### <a name="dependency-type"></a><span data-ttu-id="2c2c1-137">依存関係の種類</span><span class="sxs-lookup"><span data-stu-id="2c2c1-137">dependency type</span></span>

#### <a name="type-project"></a><span data-ttu-id="2c2c1-138">type: project</span><span class="sxs-lookup"><span data-stu-id="2c2c1-138">type: project</span></span>
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
> <span data-ttu-id="2c2c1-139">`dotnet pack --version-suffix $suffix` がプロジェクト参照の依存関係バージョンを決定する方法が無効になります。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-139">This will break the way that `dotnet pack --version-suffix $suffix` determines the dependency version of a project reference.</span></span>


#### <a name="type-build"></a><span data-ttu-id="2c2c1-140">type: build</span><span class="sxs-lookup"><span data-stu-id="2c2c1-140">type: build</span></span>
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

#### <a name="type-platform"></a><span data-ttu-id="2c2c1-141">type: platform</span><span class="sxs-lookup"><span data-stu-id="2c2c1-141">type: platform</span></span>
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

<span data-ttu-id="2c2c1-142">csproj には同等のものがありません。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-142">There is no equivalent in csproj.</span></span> 

## <a name="runtimes"></a><span data-ttu-id="2c2c1-143">runtimes</span><span class="sxs-lookup"><span data-stu-id="2c2c1-143">runtimes</span></span>
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

### <a name="standalone-apps-self-contained-deployment"></a><span data-ttu-id="2c2c1-144">スタンドアロン アプリ (自己完結型の展開)</span><span class="sxs-lookup"><span data-stu-id="2c2c1-144">Standalone apps (self-contained deployment)</span></span>
<span data-ttu-id="2c2c1-145">project.json では、`runtimes` セクションを定義することは、ビルドと公開の間にアプリがスタンドアロンであったことを意味します。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-145">In project.json, defining a `runtimes` section means the app was standalone during build and publish.</span></span>
<span data-ttu-id="2c2c1-146">MSBuild では、ビルド中、すべてのプロジェクトが*移植可能*ですが、スタンドアロンとして公開できます。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-146">In MSBuild, all projects are *portable* during build, but can be published as standalone.</span></span>

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

<span data-ttu-id="2c2c1-147">詳細については、「[自己完結型の展開 (SCD)](../deploying/index.md#self-contained-deployments-scd)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-147">For more information, see [Self-contained deployments (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span>

## <a name="tools"></a><span data-ttu-id="2c2c1-148">ツール</span><span class="sxs-lookup"><span data-stu-id="2c2c1-148">tools</span></span>
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
> <span data-ttu-id="2c2c1-149">ツールの `imports` は、csproj ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-149">`imports` on tools are not supported in csproj.</span></span> <span data-ttu-id="2c2c1-150">インポートを必要とするツールは、新しい `Microsoft.NET.Sdk` で機能しません。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-150">Tools that need imports will not work with the new `Microsoft.NET.Sdk`.</span></span>

## <a name="buildoptions"></a><span data-ttu-id="2c2c1-151">buildOptions</span><span class="sxs-lookup"><span data-stu-id="2c2c1-151">buildOptions</span></span>

<span data-ttu-id="2c2c1-152">「[Files](#files)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-152">See also [Files](#files).</span></span>

### <a name="emitentrypoint"></a><span data-ttu-id="2c2c1-153">emitEntryPoint</span><span class="sxs-lookup"><span data-stu-id="2c2c1-153">emitEntryPoint</span></span>

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

<span data-ttu-id="2c2c1-154">`emitEntryPoint` が `false` であった場合、`OutputType` の値は `Library` に変換されます。これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-154">If `emitEntryPoint` was `false`, the value of `OutputType` is converted to `Library`, which is the default value:</span></span>

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

### <a name="keyfile"></a><span data-ttu-id="2c2c1-155">keyFile</span><span class="sxs-lookup"><span data-stu-id="2c2c1-155">keyFile</span></span>

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

<span data-ttu-id="2c2c1-156">`keyFile` 要素は、MSBuild で 3 つのプロパティになりました。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-156">The `keyFile` element expands to three properties in MSBuild:</span></span>

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a><span data-ttu-id="2c2c1-157">その他の共通ビルド オプション</span><span class="sxs-lookup"><span data-stu-id="2c2c1-157">Other common build options</span></span>

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

## <a name="packoptions"></a><span data-ttu-id="2c2c1-158">packOptions</span><span class="sxs-lookup"><span data-stu-id="2c2c1-158">packOptions</span></span>

<span data-ttu-id="2c2c1-159">「[Files](#files)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-159">See also [Files](#files).</span></span>

### <a name="common-pack-options"></a><span data-ttu-id="2c2c1-160">共通パック オプション</span><span class="sxs-lookup"><span data-stu-id="2c2c1-160">Common pack options</span></span>

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

<span data-ttu-id="2c2c1-161">MSBuild では、`owners` 要素に相当するものはありません。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-161">There is no equivalent for the `owners` element in MSBuild.</span></span> <span data-ttu-id="2c2c1-162">`summary` の場合、MSBuild の `<Description>` プロパティを利用できます (ただし、`summary` の値はそのプロパティに自動的に移行されません)。そのプロパティが [`description`](#-other-common-root-level-options) 要素にマッピングされているためです。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-162">For `summary`, you can use the MSBuild `<Description>` property, even though the value of `summary` is not migrated automatically to that property, since that property is mapped to the [`description`](#-other-common-root-level-options) element.</span></span>

## <a name="scripts"></a><span data-ttu-id="2c2c1-163">スクリプト</span><span class="sxs-lookup"><span data-stu-id="2c2c1-163">scripts</span></span>

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

<span data-ttu-id="2c2c1-164">MSBuild でこれに相当するものは[ターゲット](/visualstudio/msbuild/msbuild-targets)です。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-164">Their equivalent in MSBuild are [targets](/visualstudio/msbuild/msbuild-targets):</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```


## <a name="runtimeoptions"></a><span data-ttu-id="2c2c1-165">runtimeOptions</span><span class="sxs-lookup"><span data-stu-id="2c2c1-165">runtimeOptions</span></span>

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

<span data-ttu-id="2c2c1-166">"System.GC.Server" プロパティを除き、このグループのすべての設定がプロジェクト フォルダーの *runtimeconfig.template.json* というファイルに配置されます。オプションは移行プロセス中にルート オブジェクトに移動します。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-166">All settings in this group, except for the "System.GC.Server" property, are placed into a file called *runtimeconfig.template.json* in the project folder, with options lifted to the root object during the migration process:</span></span>

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

<span data-ttu-id="2c2c1-167">"System.GC.Server" プロパティは csproj ファイルに移行されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-167">The "System.GC.Server" property is migrated into the csproj file:</span></span>
```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

<span data-ttu-id="2c2c1-168">ただし、csproj のこれらの値はすべて MSBuild プロパティと共に設定できます。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-168">However, you can set all those values in the csproj as well as MSBuild properties:</span></span>
```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a><span data-ttu-id="2c2c1-169">shared</span><span class="sxs-lookup"><span data-stu-id="2c2c1-169">shared</span></span>
```json
{
  "shared": "shared/**/*.cs"
}
```

<span data-ttu-id="2c2c1-170">csproj ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-170">Not supported in csproj.</span></span> <span data-ttu-id="2c2c1-171">代わりに、*.nuspec* ファイルにコンテンツ ファイルを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-171">You must instead create include content files in your *.nuspec* file.</span></span> <span data-ttu-id="2c2c1-172">詳細については、「[Including content files](/nuget/schema/nuspec#including-content-files)」 (コンテンツ ファイルを追加する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-172">For more information, see [Including content files](/nuget/schema/nuspec#including-content-files).</span></span>

## <a name="files"></a><span data-ttu-id="2c2c1-173">ファイル</span><span class="sxs-lookup"><span data-stu-id="2c2c1-173">files</span></span>

<span data-ttu-id="2c2c1-174">*project.json* では、ビルドとパックは、複数のフォルダーからのコンパイルと埋め込みまで拡張できます。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-174">In *project.json*, build and pack could be extended to compile and embed from different folders.</span></span>
<span data-ttu-id="2c2c1-175">MSBuild では、これは[項目](/visualstudio/msbuild/common-msbuild-project-items)の使用により行われます。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-175">In MSBuild, this is done using [items](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="2c2c1-176">次の例は一般的な変換です。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-176">The following example is a common conversion:</span></span>

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
> <span data-ttu-id="2c2c1-177">既定の [Glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))の多くは .NET Core SDK により自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-177">Many of the default [globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are added automatically by the .NET Core SDK.</span></span>
> <span data-ttu-id="2c2c1-178">詳細については、「[Default Compile Item Values](https://aka.ms/sdkimplicititems)」 (既定のコンパイル項目値) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-178">For more information, see [Default Compile Item Values](https://aka.ms/sdkimplicititems).</span></span>

<span data-ttu-id="2c2c1-179">すべての MSBuild `ItemGroup` 要素で `Include`、`Exclude`、`Remove` がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-179">All MSBuild `ItemGroup` elements support `Include`, `Exclude`, and `Remove`.</span></span>

<span data-ttu-id="2c2c1-180">.nupkg 内のパッケージ レイアウトは `PackagePath="path"` で変更できます。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-180">Package layout inside the .nupkg can be modified with `PackagePath="path"`.</span></span>

<span data-ttu-id="2c2c1-181">`Content` を除き、ほとんどの項目グループで、パッケージに `Pack="true"` を明示的に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-181">Except for `Content`, most item groups require explicitly adding `Pack="true"` to be included in the package.</span></span> <span data-ttu-id="2c2c1-182">MSBuild の `<IncludeContentInPack>` プロパティが既定で `true` に設定されているため、`Content` はパッケージの*コンテンツ* フォルダーに置かれます。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-182">`Content` will be put in the *content* folder in a package since the MSBuild `<IncludeContentInPack>` property is set to `true` by default.</span></span> <span data-ttu-id="2c2c1-183">詳細については、「[Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package)」 (パッケージにコンテンツを追加する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-183">For more information, see [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span></span>

<span data-ttu-id="2c2c1-184">`PackagePath="%(Identity)"` は、パッケージ パスをプロジェクト関連のファイル パスに設定する簡単な方法です。</span><span class="sxs-lookup"><span data-stu-id="2c2c1-184">`PackagePath="%(Identity)"` is a short way of setting package path to the project-relative file path.</span></span>

## <a name="testrunner"></a><span data-ttu-id="2c2c1-185">testRunner</span><span class="sxs-lookup"><span data-stu-id="2c2c1-185">testRunner</span></span>

### <a name="xunit"></a><span data-ttu-id="2c2c1-186">xUnit</span><span class="sxs-lookup"><span data-stu-id="2c2c1-186">xUnit</span></span>

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

### <a name="mstest"></a><span data-ttu-id="2c2c1-187">MSTest</span><span class="sxs-lookup"><span data-stu-id="2c2c1-187">MSTest</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2c2c1-188">参照</span><span class="sxs-lookup"><span data-stu-id="2c2c1-188">See Also</span></span>

[<span data-ttu-id="2c2c1-189">CLI の変更の概要</span><span class="sxs-lookup"><span data-stu-id="2c2c1-189">High-level overview of changes in CLI</span></span>](../tools/cli-msbuild-architecture.md)
