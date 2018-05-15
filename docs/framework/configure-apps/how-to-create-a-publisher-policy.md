---
title: '方法: 発行者ポリシーを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 91971e4d41c3a54fa72ae73a3655dab650019676
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="85eca-102">方法: 発行者ポリシーを作成する</span><span class="sxs-lookup"><span data-stu-id="85eca-102">How to: Create a Publisher Policy</span></span>
<span data-ttu-id="85eca-103">アプリケーションがアップグレード済みのアセンブリに発行者ポリシー ファイルを含めることによって、新しいバージョンのアセンブリを使用するアセンブリの販売元の状態のことができます。</span><span class="sxs-lookup"><span data-stu-id="85eca-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="85eca-104">発行者ポリシー ファイルは、アセンブリのリダイレクトやコード ベース設定を指定し、アプリケーション構成ファイルと同じフォーマットを使用します。</span><span class="sxs-lookup"><span data-stu-id="85eca-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="85eca-105">発行者ポリシー ファイルがアセンブリにコンパイルされ、グローバル アセンブリ キャッシュに配置します。</span><span class="sxs-lookup"><span data-stu-id="85eca-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="85eca-106">発行者ポリシーを作成するのには、3 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="85eca-106">There are three steps involved in creating a publisher policy:</span></span>  
  
1.  <span data-ttu-id="85eca-107">発行者ポリシー ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="85eca-107">Create a publisher policy file.</span></span>  
  
2.  <span data-ttu-id="85eca-108">発行者ポリシー アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="85eca-108">Create a publisher policy assembly.</span></span>  
  
3.  <span data-ttu-id="85eca-109">発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加します。</span><span class="sxs-lookup"><span data-stu-id="85eca-109">Add the publisher policy assembly to the global assembly cache.</span></span>  
  
 <span data-ttu-id="85eca-110">パブリッシャー ポリシー用のスキーマについては、「[アセンブリ バージョンのリダイレクト](../../../docs/framework/configure-apps/redirect-assembly-versions.md)です。</span><span class="sxs-lookup"><span data-stu-id="85eca-110">The schema for publisher policy is described in [Redirecting Assembly Versions](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span></span> <span data-ttu-id="85eca-111">次の例は、発行者ポリシー ファイルの 1 つのバージョンをリダイレクトする`myAssembly`別にします。</span><span class="sxs-lookup"><span data-stu-id="85eca-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->  
         <bindingRedirect oldVersion="1.0.0.0"  
                          newVersion="2.0.0.0"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="85eca-112">コード ベースを指定する方法については、次を参照してください。[アセンブリの場所を指定する](../../../docs/framework/configure-apps/specify-assembly-location.md)です。</span><span class="sxs-lookup"><span data-stu-id="85eca-112">To learn how to specify a code base, see [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  
  
## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="85eca-113">発行者ポリシー アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="85eca-113">Creating the Publisher Policy Assembly</span></span>  
 <span data-ttu-id="85eca-114">使用して、[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md)発行者ポリシー アセンブリを作成します。</span><span class="sxs-lookup"><span data-stu-id="85eca-114">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>  
  
#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="85eca-115">発行者ポリシー アセンブリを作成するには</span><span class="sxs-lookup"><span data-stu-id="85eca-115">To create a publisher policy assembly</span></span>  
  
1.  <span data-ttu-id="85eca-116">コマンド プロンプトで次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="85eca-116">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="85eca-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span><span class="sxs-lookup"><span data-stu-id="85eca-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span></span>  
  
     <span data-ttu-id="85eca-118">このコマンドでは。</span><span class="sxs-lookup"><span data-stu-id="85eca-118">In this command:</span></span>  
  
    -   <span data-ttu-id="85eca-119">*PublisherPolicyFile*引数は、発行者ポリシー ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="85eca-119">The *publisherPolicyFile* argument is the name of the publisher policy file.</span></span>  
  
    -   <span data-ttu-id="85eca-120">*PublisherPolicyAssemblyFile*引数は、このコマンドを実行した結果、発行者ポリシー アセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="85eca-120">The *publisherPolicyAssemblyFile* argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="85eca-121">アセンブリ ファイル名は、形式に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="85eca-121">The assembly file name must follow the format:</span></span>  
  
         <span data-ttu-id="85eca-122">**policy.**</span><span class="sxs-lookup"><span data-stu-id="85eca-122">**policy.**</span></span> <span data-ttu-id="85eca-123">*majorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="85eca-123">*majorNumber* **.**</span></span> <span data-ttu-id="85eca-124">*minorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="85eca-124">*minorNumber* **.**</span></span> <span data-ttu-id="85eca-125">*mainAssemblyName* **.dll**</span><span class="sxs-lookup"><span data-stu-id="85eca-125">*mainAssemblyName* **.dll**</span></span>  
  
    -   <span data-ttu-id="85eca-126">*KeyPairFile*引数は、キーのペアを含むファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="85eca-126">The *keyPairFile* argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="85eca-127">アセンブリと同じキー ペアと発行者ポリシー アセンブリを署名する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85eca-127">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>  
  
    -   <span data-ttu-id="85eca-128">*ProcessorArchitecture*引数がプロセッサ固有のアセンブリの対象となるプラットフォームを識別します。</span><span class="sxs-lookup"><span data-stu-id="85eca-128">The *processorArchitecture* argument identifies the platform targeted by a processor-specific assembly.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="85eca-129">特定のプロセッサ アーキテクチャを対象とする機能は、.NET Framework version 2.0 の新機能です。</span><span class="sxs-lookup"><span data-stu-id="85eca-129">The ability to target a specific processor architecture is new in the .NET Framework version 2.0.</span></span>  
  
     <span data-ttu-id="85eca-130">次のコマンドの作成と呼ばれる発行者ポリシー アセンブリ`policy.1.0.myAssembly`発行者ポリシー ファイルから呼び出す`pub.config`、内のキー ペアを使用してアセンブリに厳密な名前を割り当てます、`sgKey.snk`ファイル、および x86 の対象であるアセンブリを指定しますプロセッサ アーキテクチャです。</span><span class="sxs-lookup"><span data-stu-id="85eca-130">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     <span data-ttu-id="85eca-131">発行者ポリシー アセンブリは、それが適用されるアセンブリのプロセッサ アーキテクチャと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85eca-131">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="85eca-132">このため、アセンブリがある場合、<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A>の値<xref:System.Reflection.ProcessorArchitecture.MSIL>でそのアセンブリの発行者ポリシー アセンブリを作成する必要があります`/platform:anycpu`です。</span><span class="sxs-lookup"><span data-stu-id="85eca-132">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="85eca-133">個別に指定する必要があります各プロセッサ固有のアセンブリの発行者ポリシー アセンブリ。</span><span class="sxs-lookup"><span data-stu-id="85eca-133">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>  
  
     <span data-ttu-id="85eca-134">このルールの結果が設定されて、アセンブリのプロセッサ アーキテクチャを変更するためにバージョン番号のメジャーまたはマイナー コンポーネントを変更する必要があります、正しいプロセッサ アーキテクチャと新しい発行者ポリシー アセンブリを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="85eca-134">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="85eca-135">以前の発行者ポリシー アセンブリは、アセンブリが別のプロセッサ アーキテクチャを持つアセンブリを処理できません。</span><span class="sxs-lookup"><span data-stu-id="85eca-135">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>  
  
     <span data-ttu-id="85eca-136">別の結果としては、プロセッサ アーキテクチャを常に指定されているので、.NET Framework の以前のバージョンを使用してコンパイルされたアセンブリの発行者ポリシー アセンブリを作成するバージョン 2.0 のリンカーを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="85eca-136">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="85eca-137">発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加します。</span><span class="sxs-lookup"><span data-stu-id="85eca-137">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>  
 <span data-ttu-id="85eca-138">使用して、[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加します。</span><span class="sxs-lookup"><span data-stu-id="85eca-138">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="85eca-139">発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加するには</span><span class="sxs-lookup"><span data-stu-id="85eca-139">To add the publisher policy assembly to the global assembly cache</span></span>  
  
1.  <span data-ttu-id="85eca-140">コマンド プロンプトで次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="85eca-140">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="85eca-141">**gacutil/i***publisherPolicyAssemblyFile* </span><span class="sxs-lookup"><span data-stu-id="85eca-141">**gacutil /i**  *publisherPolicyAssemblyFile*</span></span>  
  
     <span data-ttu-id="85eca-142">次のコマンドは、追加`policy.1.0.myAssembly.dll`グローバル アセンブリ キャッシュにします。</span><span class="sxs-lookup"><span data-stu-id="85eca-142">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="85eca-143">ない場合は、元の発行者ポリシー ファイル、アセンブリと同じディレクトリに、発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加できません。</span><span class="sxs-lookup"><span data-stu-id="85eca-143">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85eca-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="85eca-144">See Also</span></span>  
 [<span data-ttu-id="85eca-145">アセンブリを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="85eca-145">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="85eca-146">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="85eca-146">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="85eca-147">アプリの構成</span><span class="sxs-lookup"><span data-stu-id="85eca-147">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="85eca-148">.NET Framework アプリの構成</span><span class="sxs-lookup"><span data-stu-id="85eca-148">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [<span data-ttu-id="85eca-149">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="85eca-149">Runtime Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="85eca-150">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="85eca-150">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="85eca-151">アセンブリ バージョンのリダイレクト</span><span class="sxs-lookup"><span data-stu-id="85eca-151">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
