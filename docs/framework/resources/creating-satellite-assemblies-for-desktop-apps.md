---
title: "デスクトップ アプリケーションに対するサテライト アセンブリの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- public keys, obtaining
- satellite assemblies
- assemblies [.NET Framework], signing
- application resources, deploying
- Al.exe
- GAC (global assembly cache), satellite assemblies
- Assembly Linker
- directory locations for satellite assemblies
- global assembly cache, satellite assemblies
- packaging application resources
- compiling satellite assemblies
- re-signing assemblies
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: febb9d50bd61eef53f39bb0f36cd4e3a6049e9f5
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a><span data-ttu-id="c1fd0-102">デスクトップ アプリケーションに対するサテライト アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="c1fd0-102">Creating Satellite Assemblies for Desktop Apps</span></span>
<span data-ttu-id="c1fd0-103">リソース ファイルはローカライズされたアプリケーションの中心的な役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-103">Resource files play a central role in localized applications.</span></span> <span data-ttu-id="c1fd0-104">これを使用することで、アプリケーションでは、ユーザー固有の言語とカルチャで文字列、イメージ、およびその他のデータを表示し、ユーザー固有の言語またはカルチャ用のリソースが使用できない場合には代替データを提供できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-104">They enable an application to display strings, images, and other data in the user's own language and culture, and to provide alternate data if resources for the user's own language or culture are unavailable.</span></span> <span data-ttu-id="c1fd0-105">.NET Framework ではハブ アンド スポーク モデルを使用して、ローカライズされたリソースを見つけて取得します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-105">The .NET Framework uses a hub-and-spoke model to locate and retrieve localized resources.</span></span> <span data-ttu-id="c1fd0-106">ハブはニュートラルまたは既定のカルチャと呼ばれる、単一カルチャ用のリソースとローカライズできない実行可能コードを含むメイン アセンブリです。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-106">The hub is the main assembly that contains the non-localizable executable code and the resources for a single culture, which is called the neutral or default culture.</span></span> <span data-ttu-id="c1fd0-107">既定のカルチャはアプリケーションで使用されるフォールバック カルチャです。これは、ローカライズされたリソースが使用できない場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-107">The default culture is the fallback culture for the application; it is used when no localized resources are available.</span></span> <span data-ttu-id="c1fd0-108">アプリケーションの既定のカルチャにカルチャを指定するために <xref:System.Resources.NeutralResourcesLanguageAttribute> 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-108">You use the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute to designate the culture of the application's default culture.</span></span> <span data-ttu-id="c1fd0-109">各スポークは、単一のローカライズされたカルチャ用のリソースを含むがコードは含まないサテライト アセンブリに接続します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-109">Each spoke connects to a satellite assembly that contains the resources for a single localized culture but does not contain any code.</span></span> <span data-ttu-id="c1fd0-110">サテライト アセンブリはメイン アセンブリには含まれないため、アプリケーションのメイン アセンブリを置換しなくても、特定のカルチャに対応するリソースを簡単に更新または置換できます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-110">Because the satellite assemblies are not part of the main assembly, you can easily update or replace resources that correspond to a specific culture without replacing the main assembly for the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1fd0-111">アプリケーションの既定のカルチャのリソースは、サテライト アセンブリにも格納できます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-111">The resources of an application's default culture can also be stored in a satellite assembly.</span></span> <span data-ttu-id="c1fd0-112">これを行うには、<xref:System.Resources.NeutralResourcesLanguageAttribute> 属性に <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=fullName> の値を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-112">To do this, you assign the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute a value of <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=fullName>.</span></span>  
  
## <a name="satellite-assembly-name-and-location"></a><span data-ttu-id="c1fd0-113">サテライト アセンブリの名前と場所</span><span class="sxs-lookup"><span data-stu-id="c1fd0-113">Satellite Assembly Name and Location</span></span>  
 <span data-ttu-id="c1fd0-114">ハブ アンド スポーク モデルでは、簡単に見つけて使用できるように、リソースを特定の場所に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-114">The hub-and-spoke model requires that you place resources in specific locations so that they can be easily located and used.</span></span> <span data-ttu-id="c1fd0-115">リソースのコンパイルと名前の指定を適切に行わなかった場合や、リソースを適切な場所に配置しなかった場合、共通言語ランタイムはリソースを見つけることができず、代わりに既定のカルチャのリソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-115">If you do not compile and name resources as expected, or if you do not place them in the correct locations, the common language runtime will not be able to locate them and will use the resources of the default culture instead.</span></span> <span data-ttu-id="c1fd0-116"><xref:System.Resources.ResourceManager> オブジェクトによって表される .NET Framework リソース マネージャーは、ローカライズされたリソースに自動的にアクセスするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-116">The .NET Framework Resource Manager, represented by a <xref:System.Resources.ResourceManager> object, is used to automatically access localized resources.</span></span> <span data-ttu-id="c1fd0-117">リソース マネージャーでは以下が必要になります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-117">The Resource Manager requires the following:</span></span>  
  
-   <span data-ttu-id="c1fd0-118">単一のサテライト アセンブリには、特定のカルチャ用のリソースをすべて含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-118">A single satellite assembly must include all the resources for a particular culture.</span></span> <span data-ttu-id="c1fd0-119">つまり、複数の .txt ファイルまたは .resx ファイルを単一のバイナリ .resources ファイルにコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-119">In other words, you should compile multiple .txt or .resx files into a single binary .resources file.</span></span>  
  
-   <span data-ttu-id="c1fd0-120">それぞれのローカライズされたカルチャ用のアプリケーション ディレクトリに個別のサブディレクトリが必要になります。ここには、そのカルチャのリソースが格納されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-120">There must be a separate subdirectory in the application directory for each localized culture that stores that culture's resources.</span></span> <span data-ttu-id="c1fd0-121">サブディレクトリ名は、カルチャ名と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-121">The subdirectory name must be the same as the culture name.</span></span> <span data-ttu-id="c1fd0-122">グローバル アセンブリ キャッシュにサテライト アセンブリを格納することもできます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-122">Alternately, you can store your satellite assemblies in the global assembly cache.</span></span> <span data-ttu-id="c1fd0-123">この場合、アセンブリの厳密な名前のカルチャ情報コンポーネントでそのカルチャを示す必要があります </span><span class="sxs-lookup"><span data-stu-id="c1fd0-123">In this case, the culture information component of the assembly's strong name must indicate its culture.</span></span> <span data-ttu-id="c1fd0-124">(このトピックの後半の「[グローバル アセンブリ キャッシュへのサテライト アセンブリのインストール](#SN)」セクションを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-124">(See the [Installing Satellite Assemblies in the Global Assembly Cache](#SN) section later in this topic.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c1fd0-125">アプリケーションにサブカルチャ用のリソースを含める場合は、アプリケーション ディレクトリの下の個別のサブディレクトリにそれぞれサブカルチャを配置します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-125">If your application includes resources for subcultures, place each subculture in a separate subdirectory under the application directory.</span></span> <span data-ttu-id="c1fd0-126">メイン カルチャのディレクトリの下のサブディレクトリにサブカルチャを配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-126">Do not place subcultures in subdirectories under their main culture's directory.</span></span>  
  
-   <span data-ttu-id="c1fd0-127">サテライト アセンブリはアプリケーションと同じ名前を持つ必要があり、ファイル名拡張子として ".resources.dll" を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-127">The satellite assembly must have the same name as the application, and must use the file name extension ".resources.dll".</span></span> <span data-ttu-id="c1fd0-128">たとえば、アプリケーションが Example.exe という名前である場合、各サテライト アセンブリの名前は Example.resources.dll でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-128">For example, if an application is named Example.exe, the name of each satellite assembly should be Example.resources.dll.</span></span> <span data-ttu-id="c1fd0-129">サテライト アセンブリ名は、リソース ファイルのカルチャを示していないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-129">Note that the satellite assembly name does not indicate the culture of its resource files.</span></span> <span data-ttu-id="c1fd0-130">ただし、サテライト アセンブリは、カルチャを指定するディレクトリに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-130">However, the satellite assembly appears in a directory that does specify the culture.</span></span>  
  
-   <span data-ttu-id="c1fd0-131">サテライト アセンブリのカルチャに関する情報は、アセンブリのメタデータに含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-131">Information about the culture of the satellite assembly must be included in the assembly's metadata.</span></span> <span data-ttu-id="c1fd0-132">サテライト アセンブリのメタデータにカルチャ名を格納するには、サテライト アセンブリにリソースを埋め込むために [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用する際に `/culture` オプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-132">To store the culture name in the satellite assembly's metadata, you specify the `/culture` option when you use [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md) to embed resources in the satellite assembly.</span></span>  
  
 <span data-ttu-id="c1fd0-133">[グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)内にインストールしないアプリケーションについて、サンプルのディレクトリ構造と位置に関する要件を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-133">The following illustration shows a sample directory structure and location requirements for applications that you are not installing in the [global assembly cache](../../../docs/framework/app-domains/gac.md).</span></span> <span data-ttu-id="c1fd0-134">拡張子が .txt および .resources の項目は、最終的なアプリケーションには付属していません。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-134">The items with .txt and .resources extensions will not ship with the final application.</span></span> <span data-ttu-id="c1fd0-135">それらは、最終的なサテライト リソース アセンブリを作成するために使用する中間リソース ファイルです。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-135">These are the intermediate resource files used to create the final satellite resource assemblies.</span></span> <span data-ttu-id="c1fd0-136">この例では、.txt ファイルを .resx ファイルに置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-136">In this example, you could substitute .resx files for the .txt files.</span></span> <span data-ttu-id="c1fd0-137">詳細については、「[リソースのパッケージ化と配置](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-137">For more information, see [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).</span></span>  
  
 <span data-ttu-id="c1fd0-138">![サテライト アセンブリ](../../../docs/framework/resources/media/satelliteassemblydir.gif "satelliteassemblydir")</span><span class="sxs-lookup"><span data-stu-id="c1fd0-138">![Satellite assemblies](../../../docs/framework/resources/media/satelliteassemblydir.gif "satelliteassemblydir")</span></span>  
<span data-ttu-id="c1fd0-139">サテライト アセンブリ ディレクトリ</span><span class="sxs-lookup"><span data-stu-id="c1fd0-139">Satellite assembly directory</span></span>  
  
## <a name="compiling-satellite-assemblies"></a><span data-ttu-id="c1fd0-140">コンパイル (サテライト アセンブリの)</span><span class="sxs-lookup"><span data-stu-id="c1fd0-140">Compiling Satellite Assemblies</span></span>  
 <span data-ttu-id="c1fd0-141">バイナリ .resources ファイルにリソースを含む XML ファイル (.resx) または、テキスト ファイルをコンパイルするために [リソース ファイル ジェネレーター (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-141">You use [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to compile text files or XML (.resx) files that contain resources to binary .resources files.</span></span> <span data-ttu-id="c1fd0-142">その後、サテライト アセンブリに .resources ファイルをコンパイルするために [アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-142">You then use [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to compile .resources files into satellite assemblies.</span></span> <span data-ttu-id="c1fd0-143">Al.exe は、指定された .resources ファイルからアセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-143">Al.exe creates an assembly from the .resources files that you specify.</span></span> <span data-ttu-id="c1fd0-144">サテライト アセンブリにはリソースのみを含めることができます。実行可能コードを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-144">Satellite assemblies can contain only resources; they cannot contain any executable code.</span></span>  
  
 <span data-ttu-id="c1fd0-145">次の Al.exe コマンドでは、ドイツ語のリソース ファイル strings.de.resources からアプリケーション `Example` 用のサテライト アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-145">The following Al.exe command creates a satellite assembly for the application `Example` from the German resources file strings.de.resources.</span></span>  
  
```  
al /target:lib /embed:strings.de.resources /culture:de /out:Example.resources.dll  
```  
  
 <span data-ttu-id="c1fd0-146">また、次の Al.exe コマンドでは、ファイル strings.de.resources からアプリケーション `Example` 用のサテライト アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-146">The following Al.exe command also creates a satellite assembly for the application `Example` from the file strings.de.resources.</span></span> <span data-ttu-id="c1fd0-147">**/template** オプションを指定すると、サテライト アセンブリは親アセンブリ (Example.dll) のカルチャ情報を除き、すべてのアセンブリ メタデータを継承します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-147">The **/template** option causes the satellite assembly to inherit all assembly metadata except for its culture information from the parent assembly (Example.dll).</span></span>  
  
```  
al /target:lib /embed:strings.de.resources /culture:de /out:Example.resources.dll /template:Example.dll  
```  
  
 <span data-ttu-id="c1fd0-148">次の表では、これらのコマンドで使用する Al.exe オプションについてさらに詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-148">The following table describes the Al.exe options used in these commands in more detail.</span></span>  
  
|<span data-ttu-id="c1fd0-149">オプション</span><span class="sxs-lookup"><span data-stu-id="c1fd0-149">Option</span></span>|<span data-ttu-id="c1fd0-150">説明</span><span class="sxs-lookup"><span data-stu-id="c1fd0-150">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c1fd0-151">**/target:**lib</span><span class="sxs-lookup"><span data-stu-id="c1fd0-151">**/target:**lib</span></span>|<span data-ttu-id="c1fd0-152">サテライト アセンブリがライブラリ (.dll) ファイルにコンパイルされることを示します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-152">Specifies that your satellite assembly is compiled to a library (.dll) file.</span></span> <span data-ttu-id="c1fd0-153">サテライト アセンブリが実行可能コードを含まず、アプリケーションのメイン アセンブリではないため、サテライト アセンブリは DLL として保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-153">Because a satellite assembly does not contain executable code and is not an application's main assembly, you must save satellite assemblies as DLLs.</span></span>|  
|<span data-ttu-id="c1fd0-154">**/embed:**strings.de.resources</span><span class="sxs-lookup"><span data-stu-id="c1fd0-154">**/embed:**strings.de.resources</span></span>|<span data-ttu-id="c1fd0-155">Al.exe でのアセンブリのコンパイル時に埋め込むリソース ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-155">Specifies the name of the resource file to embed when Al.exe compiles the assembly.</span></span> <span data-ttu-id="c1fd0-156">サテライト アセンブリに複数の .resources ファイルを埋め込むことはできますが、ハブ アンド スポーク モデルに従う場合は、カルチャごとに 1 つのサテライト アセンブリをコンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-156">You can embed multiple .resources files in a satellite assembly, but if you are following the hub-and-spoke model, you must compile one satellite assembly for each culture.</span></span> <span data-ttu-id="c1fd0-157">ただし、文字列とオブジェクトに対して別の .resources ファイルを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-157">However, you can create separate .resources files for strings and objects.</span></span>|  
|<span data-ttu-id="c1fd0-158">**/culture:**de</span><span class="sxs-lookup"><span data-stu-id="c1fd0-158">**/culture:**de</span></span>|<span data-ttu-id="c1fd0-159">コンパイルするリソースのカルチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-159">Specifies the culture of the resource to compile.</span></span> <span data-ttu-id="c1fd0-160">共通言語ランタイムは、指定されたカルチャ用のリソースを検索するときに、この情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-160">The common language runtime uses this information when it searches for the resources for a specified culture.</span></span> <span data-ttu-id="c1fd0-161">このオプションを省略しても、Al.exe ではリソースがコンパイルされますが、ランタイムはユーザーからの要求時にリソースを見つけられなくなります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-161">If you omit this option, Al.exe will still compile the resource, but the runtime will not be able to find it when a user requests it.</span></span>|  
|<span data-ttu-id="c1fd0-162">**/out:**Example.resources.dll</span><span class="sxs-lookup"><span data-stu-id="c1fd0-162">**/out:**Example.resources.dll</span></span>|<span data-ttu-id="c1fd0-163">出力ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-163">Specifies the name of the output file.</span></span> <span data-ttu-id="c1fd0-164">名前は命名標準 *baseName*.resources.*extension* に従う必要があります。ここで、*baseName* はメイン アセンブリの名前、*extension* は有効なファイル名拡張子 (.dll など) です。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-164">The name must follow the naming standard *baseName*.resources.*extension*, where *baseName* is the name of the main assembly and *extension* is a valid file name extension (such as .dll).</span></span> <span data-ttu-id="c1fd0-165">ランタイムは、出力ファイルの名前でサテライト アセンブリのカルチャを判断することはできないことに注意してください。**/culture** オプションを使用して指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-165">Note that the runtime is not able to determine the culture of a satellite assembly based on its output file name; you must use the **/culture** option to specify it.</span></span>|  
|<span data-ttu-id="c1fd0-166">**/template:**Example.dll</span><span class="sxs-lookup"><span data-stu-id="c1fd0-166">**/template:**Example.dll</span></span>|<span data-ttu-id="c1fd0-167">カルチャ フィールドを除く、すべてのアセンブリ メタデータをサテライト アセンブリが継承するアセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-167">Specifies an assembly from which the satellite assembly will inherit all assembly metadata except the culture field.</span></span> <span data-ttu-id="c1fd0-168">このオプションがサテライト アセンブリに影響するのは、[厳密な名前](../../../docs/framework/app-domains/strong-named-assemblies.md)を持つアセンブリを指定する場合のみです。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-168">This option affects satellite assemblies only if you specify an assembly that has a [strong name](../../../docs/framework/app-domains/strong-named-assemblies.md).</span></span>|  
  
 <span data-ttu-id="c1fd0-169">Al.exe で使用できるオプションの一覧については、「[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-169">For a complete list of options available with Al.exe, see [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="satellite-assemblies-an-example"></a><span data-ttu-id="c1fd0-170">サテライト アセンブリ: 例</span><span class="sxs-lookup"><span data-stu-id="c1fd0-170">Satellite Assemblies: An Example</span></span>  
 <span data-ttu-id="c1fd0-171">ローカライズされたあいさつ文を含むメッセージ ボックスを表示する "Hello world" の簡単な例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-171">The following is a simple "Hello world" example that displays a message box containing a localized greeting.</span></span> <span data-ttu-id="c1fd0-172">この例には、英語 (米国)、フランス語 (フランス)、ロシア語 (ロシア) のカルチャ用のリソースが含まれており、そのフォールバック カルチャは英語です。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-172">The example includes resources for the English (United States), French (France), and Russian (Russia) cultures, and its fallback culture is English.</span></span> <span data-ttu-id="c1fd0-173">例を作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-173">To create the example, do the following:</span></span>  
  
1.  <span data-ttu-id="c1fd0-174">既定のカルチャのリソースを含める Greeting.resx または Greeting.txt という名前のリソース ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-174">Create a resource file named Greeting.resx or Greeting.txt to contain the resource for the default culture.</span></span> <span data-ttu-id="c1fd0-175">値が "Hello world!" の `HelloString` という名前の 1 つの文字列を</span><span class="sxs-lookup"><span data-stu-id="c1fd0-175">Store a single string named `HelloString` whose value is "Hello world!"</span></span> <span data-ttu-id="c1fd0-176">このファイルに格納します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-176">in this file.</span></span>  
  
2.  <span data-ttu-id="c1fd0-177">英語 (en) がアプリケーションの既定のカルチャであることを示すには、次の <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> 属性をアプリケーションの AssemblyInfo ファイル、またはアプリケーションのメイン アセンブリにコンパイルされるメイン ソース コード ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-177">To indicate that English (en) is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly.</span></span>  
  
     <span data-ttu-id="c1fd0-178">[!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]  [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="c1fd0-178">[!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]  [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]</span></span>  
  
3.  <span data-ttu-id="c1fd0-179">次のように、アプリケーションに他のカルチャ (en-US、fr-FR および ru-RU) のサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-179">Add support for additional cultures (en-US, fr-FR, and ru-RU) to the application as follows:</span></span>  
  
    -   <span data-ttu-id="c1fd0-180">en-US、つまり、英語 (米国) カルチャをサポートするには、Greeting.en-US.resx または Greeting.en-US.txt という名前のリソース ファイルを作成し、値が "Hi world!" の `HelloString` という名前の 1 つの文字列を格納します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-180">To support the en-US or English (United States) culture, create a resource file named Greeting.en-US.resx or Greeting.en-US.txt, and store in it a single string named `HelloString` whose value is "Hi world!"</span></span>  
  
    -   <span data-ttu-id="c1fd0-181">fr-FR、つまり、フランス語 (フランス) カルチャをサポートするには、Greeting.fr-FR.resx または Greeting.fr-FR.txt という名前のリソース ファイルを作成し、値が "Salut tout le monde!" の `HelloString` という名前の 1 つの文字列を格納します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-181">To support the fr-FR or French (France) culture, create a resource file named Greeting.fr-FR.resx or Greeting.fr-FR.txt, and store in it a single string named `HelloString` whose value is "Salut tout le monde!"</span></span>  
  
    -   <span data-ttu-id="c1fd0-182">ru-RU、つまり、ロシア語 (ロシア) カルチャをサポートするには、Greeting.ru-RU.resx または Greeting.ru-RU.txt という名前のリソース ファイルを作成し、値が "Всем привет!" の `HelloString` という名前の 1 つの文字列を格納します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-182">To support the ru-RU or Russian (Russia) culture, create a resource file named Greeting.ru-RU.resx or Greeting.ru-RU.txt, and store in it a single string named `HelloString` whose value is "Всем привет!"</span></span>  
  
4.  <span data-ttu-id="c1fd0-183">[Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) を使用して、バイナリ .resources ファイルに各テキストまたは XML リソース ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-183">Use [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary .resources file.</span></span> <span data-ttu-id="c1fd0-184">出力は、.resx ファイルまたは .txt ファイルと同じルート ファイル名を持つファイル セットです。ただし、拡張子は .resources になります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-184">The output is a set of files that have the same root file name as the .resx or .txt files, but a .resources extension.</span></span> <span data-ttu-id="c1fd0-185">Visual Studio で例を作成する場合は、コンパイル プロセスが自動的に処理されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-185">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="c1fd0-186">Visual Studio を使用していない場合は、次のコマンドを実行して .resx ファイルを .resources ファイルにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-186">If you aren't using Visual Studio, run the following commands to compile the .resx files into .resources files:</span></span>  
  
    ```  
    resgen Greeting.resx  
    resgen Greeting.en-us.resx  
    resgen Greeting.fr-FR.resx  
    resgen Greeting.ru-RU.resx  
    ```  
  
     <span data-ttu-id="c1fd0-187">リソースが XML ファイルではなく、テキスト ファイルにある場合は、.resx 拡張子を .txt に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-187">If your resources are in text files instead of XML files, replace the .resx extension with .txt.</span></span>  
  
5.  <span data-ttu-id="c1fd0-188">アプリケーションのメイン アセンブリに、既定のカルチャのリソースと一緒に次のソース コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-188">Compile the following source code along with the resources for the default culture into the application's main assembly:</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c1fd0-189">Visual Studio ではなく、コマンド ラインを使用して例を作成する場合は、<xref:System.Resources.ResourceManager> クラス コンストラクターの呼び出しを `ResourceManager rm = new ResourceManager("Greetings",``typeof(Example).Assembly);` に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-189">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to the following: `ResourceManager rm = new ResourceManager("Greetings",``typeof(Example).Assembly);`</span></span>  
  
     <span data-ttu-id="c1fd0-190">[!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]  [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="c1fd0-190">[!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]  [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]</span></span>  
  
     <span data-ttu-id="c1fd0-191">アプリケーションが Example という名前で、コマンド ラインからコンパイルする場合、C# コンパイラのコマンドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-191">If the application is named Example and you are compiling from the command line, the command for the C# compiler is:</span></span>  
  
    ```  
    csc Example.cs /res:Greeting.resources  
    ```  
  
     <span data-ttu-id="c1fd0-192">対応する Visual Basic コンパイラのコマンドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-192">The corresponding Visual Basic compiler command is:</span></span>  
  
    ```  
    vbc Example.vb /res:Greeting.resources  
    ```  
  
6.  <span data-ttu-id="c1fd0-193">アプリケーションでサポートされているそれぞれのローカライズされたカルチャのメイン アプリケーション ディレクトリに、サブディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-193">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="c1fd0-194">en-US、fr-FR および ru-RU サブディレクトリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-194">You should create an en-US, an fr-FR, and an ru-RU subdirectory.</span></span> <span data-ttu-id="c1fd0-195">Visual Studio では、コンパイル プロセスの一環として、これらのサブディレクトリが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-195">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span>  
  
7.  <span data-ttu-id="c1fd0-196">個々のカルチャ固有の .resources ファイルをサテライト アセンブリに埋め込み、適切なディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-196">Embed the individual culture-specific .resources files into satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="c1fd0-197">各 .resources ファイルでこれを行う場合のコマンドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-197">The command to do this for each .resources file is:</span></span>  
  
    ```  
    al /target:lib /embed:Greeting.culture.resources /culture:culture /out:culture\Example.resources.dll  
    ```  
  
     <span data-ttu-id="c1fd0-198">ここで、*culture* はリソースがサテライト アセンブリに含まれるカルチャの名前です。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-198">where *culture* is the name of the culture whose resources the satellite assembly contains.</span></span> <span data-ttu-id="c1fd0-199">Visual Studio ではこのプロセスが自動的に処理されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-199">Visual Studio handles this process automatically.</span></span>  
  
 <span data-ttu-id="c1fd0-200">その後、例を実行できます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-200">You can then run the example.</span></span> <span data-ttu-id="c1fd0-201">サポートされているカルチャのいずれかがランダムに選択され、現在のカルチャになり、ローカライズされたあいさつ文が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-201">It will randomly make one of the supported cultures the current culture and display a localized greeting.</span></span>  
  
<a name="SN"></a>   
## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="c1fd0-202">グローバル アセンブリ キャッシュへのサテライト アセンブリのインストール</span><span class="sxs-lookup"><span data-stu-id="c1fd0-202">Installing Satellite Assemblies in the Global Assembly Cache</span></span>  
 <span data-ttu-id="c1fd0-203">ローカル アプリケーション サブディレクトリにアセンブリをインストールする代わりに、グローバル アセンブリ キャッシュにインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-203">Instead of installing assemblies in a local application subdirectory, you can install them in the global assembly cache.</span></span> <span data-ttu-id="c1fd0-204">これは、複数のアプリケーションで使用されるクラス ライブラリのリソース アセンブリとクラス ライブラリがある場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-204">This is particularly useful if you have class libraries and class library resource assemblies that are used by multiple applications.</span></span>  
  
 <span data-ttu-id="c1fd0-205">アセンブリをグローバル アセンブリ キャッシュにインストールするには、アセンブリに厳密な名前が必要です。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-205">Installing assemblies in the global assembly cache requires that they have strong names.</span></span> <span data-ttu-id="c1fd0-206">厳密な名前のアセンブリには、有効な公開/秘密キーのペアで署名されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-206">Strong-named assemblies are signed with a valid public/private key pair.</span></span> <span data-ttu-id="c1fd0-207">これらには、バインド要求を満たすために使用するアセンブリを判別するためにランタイムが使用するバージョン情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-207">They contain version information that the runtime uses to determine which assembly to use to satisfy a binding request.</span></span> <span data-ttu-id="c1fd0-208">厳密な名前とバージョン管理の詳細については、「[アセンブリのバージョン管理](../../../docs/framework/app-domains/assembly-versioning.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-208">For more information about strong names and versioning, see [Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md).</span></span> <span data-ttu-id="c1fd0-209">厳密な名前の詳細については、「[厳密な名前付きアセンブリ](../../../docs/framework/app-domains/strong-named-assemblies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-209">For more information about strong names, see [Strong-Named Assemblies](../../../docs/framework/app-domains/strong-named-assemblies.md).</span></span>  
  
 <span data-ttu-id="c1fd0-210">通常、アプリケーションの開発中に、最終的な公開/秘密キーのペアにアクセスすることはありません。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-210">When you are developing an application, it is unlikely that you will have access to the final public/private key pair.</span></span> <span data-ttu-id="c1fd0-211">サテライト アセンブリをグローバル アセンブリ キャッシュ内にインストールし、そのアセンブリが確実に予期したとおりに機能するようにするために、遅延署名と呼ばれる技術を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-211">In order to install a satellite assembly in the global assembly cache and ensure that it works as expected, you can use a technique called delayed signing.</span></span> <span data-ttu-id="c1fd0-212">アセンブリに遅延署名する場合、厳密な名前による署名のために、ビルド時にファイル内のスペースを予約しておいてください。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-212">When you delay sign an assembly, at build time you reserve space in the file for the strong name signature.</span></span> <span data-ttu-id="c1fd0-213">実際の署名は、最終的な公開/秘密キーのペアが利用可能になるまで遅延されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-213">The actual signing is delayed until later, when the final public/private key pair is available.</span></span> <span data-ttu-id="c1fd0-214">遅延署名の詳細については、「[アセンブリへの遅延署名](../../../docs/framework/app-domains/delay-sign-assembly.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-214">For more information about delayed signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="obtaining-the-public-key"></a><span data-ttu-id="c1fd0-215">公開キーの取得</span><span class="sxs-lookup"><span data-stu-id="c1fd0-215">Obtaining the Public Key</span></span>  
 <span data-ttu-id="c1fd0-216">アセンブリに遅延署名するには、公開キーにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-216">To delay sign an assembly, you must have access to the public key.</span></span> <span data-ttu-id="c1fd0-217">実際の公開キーを取得するには、最終的な署名を行う社内の組織から取得するか、[厳密な名前ツール (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) を使用して公開キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-217">You can either obtain the real public key from the organization in your company that will do the eventual signing, or create a public key by using the [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
 <span data-ttu-id="c1fd0-218">次の Sn.exe コマンドでは、テスト用の公開/秘密キーのペアを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-218">The following Sn.exe command creates a test public/private key pair.</span></span> <span data-ttu-id="c1fd0-219">**–k** オプションは、Sn.exe で新しいキー ペアを作成し、TestKeyPair.snk という名前のファイルに格納するように指定します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-219">The **–k** option specifies that Sn.exe should create a new key pair and save it in a file named TestKeyPair.snk.</span></span>  
  
```  
sn –k TestKeyPair.snk   
```  
  
 <span data-ttu-id="c1fd0-220">テスト用のキー ペアを含むファイルから公開キーを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-220">You can extract the public key from the file that contains the test key pair.</span></span> <span data-ttu-id="c1fd0-221">次のコマンドでは、TestKeyPair.snk から公開キーを抽出し、PublicKey.snk に保存します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-221">The following command extracts the public key from TestKeyPair.snk and saves it in PublicKey.snk:</span></span>  
  
```  
sn –p TestKeyPair.snk PublicKey.snk  
```  
  
### <a name="delay-signing-an-assembly"></a><span data-ttu-id="c1fd0-222">アセンブリへの遅延署名</span><span class="sxs-lookup"><span data-stu-id="c1fd0-222">Delay Signing an Assembly</span></span>  
 <span data-ttu-id="c1fd0-223">公開キーを取得または作成したら、[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用して、アセンブリをコンパイルし、遅延署名を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-223">After you obtain or create the public key, you use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to compile the assembly and specify delayed signing.</span></span>  
  
 <span data-ttu-id="c1fd0-224">次の Al.exe コマンドでは、strings.ja.resources ファイルからアプリケーション StringLibrary 用の厳密な名前のサテライト アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-224">The following Al.exe command creates a strong-named satellite assembly for the application StringLibrary from the strings.ja.resources file:</span></span>  
  
```  
al /target:lib /embed:strings.ja.resources /culture:ja /out:StringLibrary.resources.dll /delay+ /keyfile:PublicKey.snk  
```  
  
 <span data-ttu-id="c1fd0-225">**/delay+** オプションは、アセンブリ リンカーがアセンブリに遅延署名することを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-225">The **/delay+** option specifies that the Assembly Linker should delay sign the assembly.</span></span> <span data-ttu-id="c1fd0-226">**/keyfile** オプションは、アセンブリへの遅延署名のために使用する公開キーを含むキー ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-226">The **/keyfile** option specifies the name of the key file that contains the public key to use to delay sign the assembly.</span></span>  
  
### <a name="re-signing-an-assembly"></a><span data-ttu-id="c1fd0-227">アセンブリへの再署名</span><span class="sxs-lookup"><span data-stu-id="c1fd0-227">Re-signing an Assembly</span></span>  
 <span data-ttu-id="c1fd0-228">アプリケーションを配置する前に、実際のキー ペアで遅延署名されたサテライト アセンブリに再署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-228">Before you deploy your application, you must re-sign the delay signed satellite assembly with the real key pair.</span></span> <span data-ttu-id="c1fd0-229">これは Sn.exe を使用して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-229">You can do this by using Sn.exe.</span></span>  
  
 <span data-ttu-id="c1fd0-230">次の Sn.exe コマンドでは、ファイル RealKeyPair.snk に格納されているキーのペアで StringLibrary.resources.dll に署名します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-230">The following Sn.exe command signs StringLibrary.resources.dll with the key pair stored in the file RealKeyPair.snk.</span></span> <span data-ttu-id="c1fd0-231">**–R** オプションは、以前に署名または遅延署名されたアセンブリに再署名する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-231">The **–R** option specifies that a previously signed or delay signed assembly is to be re-signed.</span></span>  
  
```  
sn –R StringLibrary.resources.dll RealKeyPair.snk   
```  
  
### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a><span data-ttu-id="c1fd0-232">グローバル アセンブリ キャッシュへのサテライト アセンブリのインストール</span><span class="sxs-lookup"><span data-stu-id="c1fd0-232">Installing a Satellite Assembly in the Global Assembly Cache</span></span>  
 <span data-ttu-id="c1fd0-233">ランタイムはリソース フォールバック プロセスでリソースを検索するときに、まず、[グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)内を調べます </span><span class="sxs-lookup"><span data-stu-id="c1fd0-233">When the runtime searches for resources in the resource fallback process, it looks in the [global assembly cache](../../../docs/framework/app-domains/gac.md) first.</span></span> <span data-ttu-id="c1fd0-234">(詳細については、「[リソースのパッケージ化と配置](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)」トピックの「リソース フォールバック プロセス」セクションを参照してください)。サテライト アセンブリが厳密な名前で署名されたらすぐに[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用して、グローバル アセンブリ キャッシュにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-234">(For more information, see the "Resource Fallback Process" section of the [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.) As soon as a satellite assembly is signed with a strong name, it can be installed in the global assembly cache by using the [Global Assembly Cache Tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
 <span data-ttu-id="c1fd0-235">次の Gacutil.exe コマンドでは、グローバル アセンブリ キャッシュに StringLibrary.resources.dll をインストールします。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-235">The following Gacutil.exe command installs StringLibrary.resources.dll in the global assembly cache:</span></span>  
  
```  
gacutil /i:StringLibrary.resources.dll  
```  
  
 <span data-ttu-id="c1fd0-236">**/i** オプションは、Gacutil.exe でグローバル アセンブリ キャッシュに指定されたアセンブリをインストールする必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-236">The **/i** option specifies that Gacutil.exe should install the specified assembly into the global assembly cache.</span></span> <span data-ttu-id="c1fd0-237">サテライト アセンブリがキャッシュにインストールされた後、中に含まれるリソースは、サテライト アセンブリを使用するようにデザインされたすべてのアプリケーションで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-237">After the satellite assembly is installed in the cache, the resources it contains become available to all applications that are designed to use the satellite assembly.</span></span>  
  
### <a name="resources-in-the-global-assembly-cache-an-example"></a><span data-ttu-id="c1fd0-238">グローバル アセンブリ キャッシュのリソース: 例</span><span class="sxs-lookup"><span data-stu-id="c1fd0-238">Resources in the Global Assembly Cache: An Example</span></span>  
 <span data-ttu-id="c1fd0-239">次の例では、.NET Framework クラス ライブラリのメソッドを使用して、リソース ファイルからローカライズされたあいさつ文を抽出して返します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-239">The following example uses a method in a .NET Framework class library to extract and return a localized greeting from a resource file.</span></span> <span data-ttu-id="c1fd0-240">ライブラリとそのリソースはグローバル アセンブリ キャッシュに登録されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-240">The library and its resources are registered in the global assembly cache.</span></span> <span data-ttu-id="c1fd0-241">例には、英語 (米国)、フランス語 (フランス)、ロシア語 (ロシア)、および英語カルチャ用のリソースが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-241">The example includes resources for the English (United States), French (France), Russian (Russia), and English cultures.</span></span> <span data-ttu-id="c1fd0-242">英語は既定のカルチャです。そのリソースはメイン アセンブリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-242">English is the default culture; its resources are stored in the main assembly.</span></span> <span data-ttu-id="c1fd0-243">この例では、最初に公開キーでライブラリとそのサテライト アセンブリに遅延署名してから、公開/秘密キーのペアで再署名します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-243">The example initially delay signs the library and its satellite assemblies with a public key, then re-signs them with a public/private key pair.</span></span> <span data-ttu-id="c1fd0-244">例を作成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-244">To create the example, do the following:</span></span>  
  
1.  <span data-ttu-id="c1fd0-245">Visual Studio を使用していない場合は、次の[厳密な名前ツール (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) コマンドを使用して、ResKey.snk という名前の公開/秘密キーのペアを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-245">If you are not using Visual Studio, use the following [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command to create a public/private key pair named ResKey.snk:</span></span>  
  
    ```  
    sn –k ResKey.snk  
    ```  
  
     <span data-ttu-id="c1fd0-246">Visual Studio を使用している場合は、プロジェクトの **[プロパティ]** ダイアログ ボックスの **[署名]** タブを使用して、キー ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-246">If you are using Visual Studio, use the **Signing** tab of the project **Properties** dialog box to generate the key file.</span></span>  
  
2.  <span data-ttu-id="c1fd0-247">次の[厳密な名前ツール (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) コマンドを使用して、PublicKey.snk という名前の公開キー ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-247">Use the following [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command to create a public key file named PublicKey.snk:</span></span>  
  
    ```  
    sn –p ResKey.snk PublicKey.snk  
    ```  
  
3.  <span data-ttu-id="c1fd0-248">既定のカルチャのリソースを含める Strings.resx という名前のリソース ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-248">Create a resource file named Strings.resx to contain the resource for the default culture.</span></span> <span data-ttu-id="c1fd0-249">値が "How do you do?" の `Greeting` という名前の 1 つの文字列を</span><span class="sxs-lookup"><span data-stu-id="c1fd0-249">Store a single string named `Greeting` whose value is "How do you do?"</span></span> <span data-ttu-id="c1fd0-250">そのファイルに格納します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-250">in that file.</span></span>  
  
4.  <span data-ttu-id="c1fd0-251">"en" がアプリケーションの既定のカルチャであることを示すには、次の <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> 属性をアプリケーションの AssemblyInfo ファイル、またはアプリケーションのメイン アセンブリにコンパイルされるメイン ソース ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-251">To indicate that "en" is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly:</span></span>  
  
     <span data-ttu-id="c1fd0-252">[!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]  [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="c1fd0-252">[!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]  [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]</span></span>  
  
5.  <span data-ttu-id="c1fd0-253">次のように、アプリケーションに他のカルチャ (en-US、fr-FR および ru-RU カルチャ) のサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-253">Add support for additional cultures (the en-US, fr-FR, and ru-RU cultures) to the application as follows:</span></span>  
  
    -   <span data-ttu-id="c1fd0-254">"en-US"、つまり、英語 (米国) カルチャをサポートするには、Strings.en-US.resx または Strings.en-US.txt という名前のリソース ファイルを作成し、値が "Hello!" の `Greeting` という名前の 1 つの文字列をそのファイルに格納します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-254">To support the "en-US" or English (United States) culture, create a resource file named Strings.en-US.resx or Strings.en-US.txt, and store in it a single string named `Greeting` whose value is "Hello!".</span></span>  
  
    -   <span data-ttu-id="c1fd0-255">"fr-FR"、つまり、フランス語 (フランス) カルチャをサポートするには、Strings.fr-FR.resx または Strings.fr-FR.txt という名前のリソース ファイルを作成し、値が "Bon jour!" の `Greeting` という名前の 1 つの文字列をそのファイルに格納します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-255">To support the "fr-FR" or French (France) culture, create a resource file named Strings.fr-FR.resx or Strings.fr-FR.txt and store in it a single string named `Greeting` whose value is "Bon jour!"</span></span>  
  
    -   <span data-ttu-id="c1fd0-256">"ru-RU"、つまり、ロシア語 (ロシア) カルチャをサポートするには、Strings.ru-RU.resx または Strings.ru-RU.txt という名前のリソース ファイルを作成し、値が "Привет!" の `Greeting` という名前の 1 つの文字列をそのファイルに格納します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-256">To support the "ru-RU" or Russian (Russia) culture, create a resource file named Strings.ru-RU.resx or Strings.ru-RU.txt and store in it a single string named `Greeting` whose value is "Привет!"</span></span>  
  
6.  <span data-ttu-id="c1fd0-257">[Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) を使用して、バイナリ .resources ファイルに各テキストまたは XML リソース ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-257">Use [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary .resources file.</span></span> <span data-ttu-id="c1fd0-258">出力は、.resx ファイルまたは .txt ファイルと同じルート ファイル名を持つファイル セットです。ただし、拡張子は .resources になります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-258">The output is a set of files that have the same root file name as the .resx or .txt files, but a .resources extension.</span></span> <span data-ttu-id="c1fd0-259">Visual Studio で例を作成する場合は、コンパイル プロセスが自動的に処理されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-259">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="c1fd0-260">Visual Studio を使用していない場合は、次のコマンドを実行して .resx ファイルを .resources ファイルにコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-260">If you aren't using Visual Studio, run the following command to compile the .resx files into .resources files:</span></span>  
  
    ```  
    resgen filename  
    ```  
  
     <span data-ttu-id="c1fd0-261">ここで、*filename* は .resx ファイルまたはテキスト ファイルの省略可能なパス、ファイル名、および拡張子です。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-261">where *filename* is the optional path, file name, and extension of the .resx or text file.</span></span>  
  
7.  <span data-ttu-id="c1fd0-262">StringLibrary.dll という名前の遅延署名されたライブラリ アセンブリに、既定のカルチャのリソースと一緒に StringLibrary.vb または StringLibrary.cs の次のソース コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-262">Compile the following source code for StringLibrary.vb or StringLibrary.cs along with the resources for the default culture into a delay signed library assembly named StringLibrary.dll:</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c1fd0-263">Visual Studio ではなく、コマンド ラインを使用して例を作成する場合は、<xref:System.Resources.ResourceManager> クラス コンストラクターの呼び出しを `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);` に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-263">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to         `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.</span></span>  
  
     <span data-ttu-id="c1fd0-264">[!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]  [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="c1fd0-264">[!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]  [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]</span></span>  
  
     <span data-ttu-id="c1fd0-265">C# コンパイラのコマンドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-265">The command for the C# compiler is:</span></span>  
  
    ```  
    csc /t:library /resource:Strings.resources /delaysign+ /keyfile:publickey.snk StringLibrary.cs  
    ```  
  
     <span data-ttu-id="c1fd0-266">対応する Visual Basic コンパイラのコマンドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-266">The corresponding Visual Basic compiler command is:</span></span>  
  
    ```  
    vbc /t:library /resource:Strings.resources /delaysign+ /keyfile:publickey.snk StringLibrary.vb  
    ```  
  
8.  <span data-ttu-id="c1fd0-267">アプリケーションでサポートされているそれぞれのローカライズされたカルチャのメイン アプリケーション ディレクトリに、サブディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-267">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="c1fd0-268">en-US、fr-FR および ru-RU サブディレクトリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-268">You should create an en-US, an fr-FR, and an ru-RU subdirectory.</span></span> <span data-ttu-id="c1fd0-269">Visual Studio では、コンパイル プロセスの一環として、これらのサブディレクトリが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-269">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span> <span data-ttu-id="c1fd0-270">すべてのサテライト アセンブリが同じファイル名を持つため、公開/秘密キーのペアで署名されるまで個々のカルチャ固有のサテライト アセンブリを格納するためにはサブディレクトリが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-270">Because all satellite assemblies have the same file name, the subdirectories are used to store individual culture-specific satellite assemblies until they are signed with a public/private key pair.</span></span>  
  
9. <span data-ttu-id="c1fd0-271">個々のカルチャ固有の .resources ファイルを遅延署名されたサテライト アセンブリに埋め込み、適切なディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-271">Embed the individual culture-specific .resources files into delay signed satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="c1fd0-272">各 .resources ファイルでこれを行う場合のコマンドは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-272">The command to do this for each .resources file is:</span></span>  
  
    ```  
    al /target:lib /embed:Strings.culture.resources /culture:culture /out:culture\StringLibrary.resources.dll /delay+ /keyfile:publickey.snk  
    ```  
  
     <span data-ttu-id="c1fd0-273">ここで、*culture* はカルチャの名前です。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-273">where *culture* is the name of a culture.</span></span> <span data-ttu-id="c1fd0-274">この例では、カルチャ名は en-US、fr-FR、および ru-RU です。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-274">In this example, the culture names are en-US, fr-FR, and ru-RU.</span></span>  
  
10. <span data-ttu-id="c1fd0-275">次のように、[厳密な名前ツール (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) を使用して、StringLibrary.dll に再署名します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-275">Re-sign StringLibrary.dll by using the [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) as follows:</span></span>  
  
    ```  
    sn –R StringLibrary.dll RealKeyPair.snk  
    ```  
  
11. <span data-ttu-id="c1fd0-276">個々のサテライト アセンブリに再署名します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-276">Re-sign the individual satellite assemblies.</span></span> <span data-ttu-id="c1fd0-277">これを行うには、各サテライト アセンブリに対して、次のように[厳密な名前ツール (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-277">To do this, use the [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) as follows for each satellite assembly:</span></span>  
  
    ```  
    sn –R StringLibrary.resources.dll RealKeyPair.snk  
    ```  
  
12. <span data-ttu-id="c1fd0-278">次のコマンドを使用して、グローバル アセンブリ キャッシュに StringLibrary.dll とそのサテライト アセンブリをそれぞれ登録します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-278">Register StringLibrary.dll and each of its satellite assemblies in the global assembly cache by using the following command:</span></span>  
  
    ```  
    gacutil /i filename  
    ```  
  
     <span data-ttu-id="c1fd0-279">ここで、*filename* は登録するファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-279">where *filename* is the name of the file to register.</span></span>  
  
13. <span data-ttu-id="c1fd0-280">Visual Studio を使用している場合は、`Example` という名前の新しい**コンソール アプリケーション** プロジェクトを作成し、StringLibrary.dll への参照と次のソース コードを追加してコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-280">If you are using Visual Studio, create a new **Console Application** project named `Example`, add a reference to StringLibrary.dll and the following source code to it, and compile.</span></span>  
  
     <span data-ttu-id="c1fd0-281">[!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]  [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="c1fd0-281">[!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]  [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]</span></span>  
  
     <span data-ttu-id="c1fd0-282">コマンド ラインからコンパイルするには、C# コンパイラの次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-282">To compile from the command line, use the following command for the C# compiler:</span></span>  
  
    ```  
    csc Example.cs /r:StringLibrary.dll   
    ```  
  
     <span data-ttu-id="c1fd0-283">Visual Basic コンパイラのコマンド ラインは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-283">The command line for the Visual Basic compiler is:</span></span>  
  
    ```  
    vbc Example.vb /r:StringLibrary.dll   
    ```  
  
14. <span data-ttu-id="c1fd0-284">Example.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="c1fd0-284">Run Example.exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1fd0-285">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1fd0-285">See Also</span></span>  
 <span data-ttu-id="c1fd0-286">[リソースのパッケージ化と配置](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) </span><span class="sxs-lookup"><span data-stu-id="c1fd0-286">[Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) </span></span>  
 <span data-ttu-id="c1fd0-287">[アセンブリへの遅延署名](../../../docs/framework/app-domains/delay-sign-assembly.md) </span><span class="sxs-lookup"><span data-stu-id="c1fd0-287">[Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md) </span></span>  
 <span data-ttu-id="c1fd0-288">[Al.exe (アセンブリ リンカー)](../../../docs/framework/tools/al-exe-assembly-linker.md) </span><span class="sxs-lookup"><span data-stu-id="c1fd0-288">[Al.exe (Assembly Linker)](../../../docs/framework/tools/al-exe-assembly-linker.md) </span></span>  
 <span data-ttu-id="c1fd0-289">[Sn.exe (厳密名ツール)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) </span><span class="sxs-lookup"><span data-stu-id="c1fd0-289">[Sn.exe (Strong Name Tool)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) </span></span>  
 <span data-ttu-id="c1fd0-290">[Gacutil.exe (グローバル アセンブリ キャッシュ ツール)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) </span><span class="sxs-lookup"><span data-stu-id="c1fd0-290">[Gacutil.exe (Global Assembly Cache Tool)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) </span></span>  
 [<span data-ttu-id="c1fd0-291">デスクトップ アプリケーションのリソース</span><span class="sxs-lookup"><span data-stu-id="c1fd0-291">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)

