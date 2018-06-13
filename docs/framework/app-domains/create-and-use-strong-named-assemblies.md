---
title: 厳密な名前付きアセンブリの作成と使用
ms.date: 08/01/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, about strong-named assemblies
- strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- strong-named assemblies, scenarios
- assemblies [.NET Framework], strong-named
- strong-named assemblies, loading into trusted application domains
- assembly binding, strong-named
ms.assetid: ffbf6d9e-4a88-4a8a-9645-4ce0ee1ee5f9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94659919d4e902f8562e669fbb0f98d6ebc679ab
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744643"
---
# <a name="creating-and-using-strong-named-assemblies"></a><span data-ttu-id="7497c-102">厳密な名前付きアセンブリの作成と使用</span><span class="sxs-lookup"><span data-stu-id="7497c-102">Creating and Using Strong-Named Assemblies</span></span>
<a name="top"></a> <span data-ttu-id="7497c-103">厳密な名前は、単純テキスト名、バージョン番号、カルチャ情報 (設定されている場合) から成るアセンブリの識別子と、公開キーおよびデジタル署名で構成されます。</span><span class="sxs-lookup"><span data-stu-id="7497c-103">A strong name consists of the assembly's identity—its simple text name, version number, and culture information (if provided)—plus a public key and a digital signature.</span></span> <span data-ttu-id="7497c-104">このデジタル署名は、対応する秘密キーを使用してアセンブリ ファイルから生成されます。</span><span class="sxs-lookup"><span data-stu-id="7497c-104">It is generated from an assembly file using the corresponding private key.</span></span> <span data-ttu-id="7497c-105">(アセンブリ ファイルにはアセンブリ マニフェストが格納されており、そこに、アセンブリを構成するすべてのファイルの名前とハッシュが含まれます。)</span><span class="sxs-lookup"><span data-stu-id="7497c-105">(The assembly file contains the assembly manifest, which contains the names and hashes of all the files that make up the assembly.)</span></span>  
  
 <span data-ttu-id="7497c-106">厳密な名前のアセンブリは、他の厳密な名前のアセンブリでのタイプだけを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7497c-106">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="7497c-107">それ以外の場合は、厳密な名前のアセンブリの整合性が損なわれます。</span><span class="sxs-lookup"><span data-stu-id="7497c-107">Otherwise, the integrity of the strong-named assembly would be compromised.</span></span>  
  
 <span data-ttu-id="7497c-108">この概要は、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="7497c-108">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="7497c-109">厳密な名前のシナリオ</span><span class="sxs-lookup"><span data-stu-id="7497c-109">Strong Name Scenario</span></span>](#strong_name_scenario)  
  
-   [<span data-ttu-id="7497c-110">信頼されたアセンブリの署名検証のバイパス</span><span class="sxs-lookup"><span data-stu-id="7497c-110">Bypassing Signature Verification of Trusted Assemblies</span></span>](#bypassing_signature_verification)  
  
-   [<span data-ttu-id="7497c-111">関連トピック</span><span class="sxs-lookup"><span data-stu-id="7497c-111">Related Topics</span></span>](#related_topics)  
  
<a name="strong_name_scenario"></a>   
## <a name="strong-name-scenario"></a><span data-ttu-id="7497c-112">厳密な名前のシナリオ</span><span class="sxs-lookup"><span data-stu-id="7497c-112">Strong Name Scenario</span></span>  
 <span data-ttu-id="7497c-113">次のシナリオは、厳密な名前のアセンブリに署名した後にそれをその名前で参照するプロセスの概要を示しています。</span><span class="sxs-lookup"><span data-stu-id="7497c-113">The following scenario outlines the process of signing an assembly with a strong name and later referencing it by that name.</span></span>  
  
1.  <span data-ttu-id="7497c-114">アセンブリ A は、次のいずれかの方法を使用して厳密な名前で作成されます。</span><span class="sxs-lookup"><span data-stu-id="7497c-114">Assembly A is created with a strong name using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="7497c-115">[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] など、厳密な名前の作成をサポートする開発環境を使用する。</span><span class="sxs-lookup"><span data-stu-id="7497c-115">Using a development environment that supports creating strong names, such as [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].</span></span>  
  
    -   <span data-ttu-id="7497c-116">[厳密名ツール (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) を使用して暗号化キー ペアを作成し、コマンド ライン コンパイラまたは[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) のいずれかを使用してそのキー ペアをアセンブリに割り当てる。</span><span class="sxs-lookup"><span data-stu-id="7497c-116">Creating a cryptographic key pair using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) and assigning that key pair to the assembly using either a command-line compiler or the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="7497c-117">Windows ソフトウェア開発キット (SDK) には、Sn.exe と Al.exe の両方が用意されています。</span><span class="sxs-lookup"><span data-stu-id="7497c-117">The Windows Software Development Kit (SDK) provides both Sn.exe and Al.exe.</span></span>  
  
2.  <span data-ttu-id="7497c-118">開発環境またはツールは、アセンブリのマニフェストを含むファイルのハッシュに、開発者の秘密キーで署名します。</span><span class="sxs-lookup"><span data-stu-id="7497c-118">The development environment or tool signs the hash of the file containing the assembly's manifest with the developer's private key.</span></span> <span data-ttu-id="7497c-119">このデジタル署名は、アセンブリ A のマニフェストを含むポータブル実行可能 (PE) ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7497c-119">This digital signature is stored in the portable executable (PE) file that contains Assembly A's manifest.</span></span>  
  
3.  <span data-ttu-id="7497c-120">アセンブリ B はアセンブリ A のコンシューマーです。アセンブリ B のマニフェストの参照セクションには、アセンブリ A の公開キーを表すトークンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7497c-120">Assembly B is a consumer of Assembly A. The reference section of Assembly B's manifest includes a token that represents Assembly A's public key.</span></span> <span data-ttu-id="7497c-121">トークンは完全な公開キーの一部であり、スペースを節約するために、キー自体ではなくこれが使用されます。</span><span class="sxs-lookup"><span data-stu-id="7497c-121">A token is a portion of the full public key and is used rather than the key itself to save space.</span></span>  
  
4.  <span data-ttu-id="7497c-122">共通言語ランタイムは、アセンブリがグローバル アセンブリ キャッシュに入れられる際に、厳密な名前の署名を確認します。</span><span class="sxs-lookup"><span data-stu-id="7497c-122">The common language runtime verifies the strong name signature when the assembly is placed in the global assembly cache.</span></span> <span data-ttu-id="7497c-123">実行時に厳密な名前でバインドするとき、共通言語ランタイムは、アセンブリ B のマニフェストに格納されているキーと、アセンブリ A の厳密な名前を生成するために使用されたキーを比較します。 .NET Framework のセキュリティ チェックに合格してバインドが成功すると、アセンブリ B は、アセンブリ A のビットが改ざんされていないことと、これらのビットが実際にアセンブリ A の開発者からのものであることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="7497c-123">When binding by strong name at run time, the common language runtime compares the key stored in Assembly B's manifest with the key used to generate the strong name for Assembly A. If the .NET Framework security checks pass and the bind succeeds, Assembly B has a guarantee that Assembly A's bits have not been tampered with and that these bits actually come from the developers of Assembly A.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7497c-124">このシナリオは、信頼の問題を扱っていません。</span><span class="sxs-lookup"><span data-stu-id="7497c-124">This scenario doesn't address trust issues.</span></span> <span data-ttu-id="7497c-125">厳密な名前に加えて、完全な Microsoft Authenticode 署名をアセンブリに持たせることができます。</span><span class="sxs-lookup"><span data-stu-id="7497c-125">Assemblies can carry full Microsoft Authenticode signatures in addition to a strong name.</span></span> <span data-ttu-id="7497c-126">Authenticode 署名には、信頼を確立するための証明書が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7497c-126">Authenticode signatures include a certificate that establishes trust.</span></span> <span data-ttu-id="7497c-127">厳密な名前を使用すると、コードにこのように署名する必要がないということに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7497c-127">It's important to note that strong names don't require code to be signed in this way.</span></span> <span data-ttu-id="7497c-128">厳密な名前は、一意の ID を提供するだけです。</span><span class="sxs-lookup"><span data-stu-id="7497c-128">Strong names only provide a unique identity.</span></span>  
  
 [<span data-ttu-id="7497c-129">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="7497c-129">Back to top</span></span>](#top)  
  
<a name="bypassing_signature_verification"></a>   
## <a name="bypassing-signature-verification-of-trusted-assemblies"></a><span data-ttu-id="7497c-130">信頼されたアセンブリの署名検証のバイパス</span><span class="sxs-lookup"><span data-stu-id="7497c-130">Bypassing Signature Verification of Trusted Assemblies</span></span>  
 <span data-ttu-id="7497c-131">[!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)] 以降、たとえば `MyComputer` ゾーンの既定のアプリケーション ドメインなど、完全に信頼されたアプリケーション ドメインにアセンブリが読み込まれるときに、厳密な名前の署名は検証されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="7497c-131">Starting with the [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], strong-name signatures are not validated when an assembly is loaded into a full-trust application domain, such as the default application domain for the `MyComputer` zone.</span></span> <span data-ttu-id="7497c-132">これは厳密な名前のバイパス機能と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="7497c-132">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="7497c-133">完全に信頼された環境では、<xref:System.Security.Permissions.StrongNameIdentityPermission> に対する完全に信頼された署名済みアセンブリの要求は、その署名に関係なく、常に成功します。</span><span class="sxs-lookup"><span data-stu-id="7497c-133">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies, regardless of their signature.</span></span> <span data-ttu-id="7497c-134">このような場合、厳密な名前のバイパス機能は、完全に信頼されたアセンブリの厳密名署名検証という不要なオーバーヘッドを回避するので、アセンブリを高速で読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="7497c-134">The strong-name bypass feature avoids the unnecessary overhead of strong-name signature verification of full-trust assemblies in this situation, allowing the assemblies to load faster.</span></span>  
  
 <span data-ttu-id="7497c-135">バイ パス機能は、厳密な名前で署名されていて、次の特性を持つアセンブリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="7497c-135">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="7497c-136"><xref:System.Security.Policy.StrongName> 証拠なしで完全に信頼されている (たとえば、`MyComputer` ゾーン証拠を持っている)。</span><span class="sxs-lookup"><span data-stu-id="7497c-136">Fully trusted without <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
-   <span data-ttu-id="7497c-137">完全に信頼された <xref:System.AppDomain> に読み込まれる。</span><span class="sxs-lookup"><span data-stu-id="7497c-137">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="7497c-138">その <xref:System.AppDomain> の <xref:System.AppDomainSetup.ApplicationBase%2A> プロパティに基づいた場所から読み込まれる。</span><span class="sxs-lookup"><span data-stu-id="7497c-138">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="7497c-139">遅延署名されていない。</span><span class="sxs-lookup"><span data-stu-id="7497c-139">Not delay-signed.</span></span>  
  
 <span data-ttu-id="7497c-140">この機能は、個々のアプリケーションに対して、またはコンピューターに対して無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="7497c-140">This feature can be disabled for individual applications or for a computer.</span></span> <span data-ttu-id="7497c-141">「[方法: 厳密な名前のバイパス機能を無効にする](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7497c-141">See [How to: Disable the Strong-Name Bypass Feature](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
 [<span data-ttu-id="7497c-142">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="7497c-142">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="7497c-143">関連トピック</span><span class="sxs-lookup"><span data-stu-id="7497c-143">Related Topics</span></span>  
  
|<span data-ttu-id="7497c-144">Title</span><span class="sxs-lookup"><span data-stu-id="7497c-144">Title</span></span>|<span data-ttu-id="7497c-145">説明</span><span class="sxs-lookup"><span data-stu-id="7497c-145">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="7497c-146">方法: 公開キーと秘密キーのキー ペアを作成する</span><span class="sxs-lookup"><span data-stu-id="7497c-146">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)|<span data-ttu-id="7497c-147">署名とアセンブリの暗号化キー ペアを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7497c-147">Describes how to create a cryptographic key pair for signing an assembly.</span></span>|  
|[<span data-ttu-id="7497c-148">方法: 厳密な名前でアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="7497c-148">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)|<span data-ttu-id="7497c-149">厳密な名前のアセンブリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7497c-149">Describes how to create a strong-named assembly.</span></span>|  
|[<span data-ttu-id="7497c-150">拡張された厳密な名前付け</span><span class="sxs-lookup"><span data-stu-id="7497c-150">Enhanced Strong Naming</span></span>](../../../docs/framework/app-domains/enhanced-strong-naming.md)|<span data-ttu-id="7497c-151">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] での厳密な名前の拡張について説明します。</span><span class="sxs-lookup"><span data-stu-id="7497c-151">Describes enhancements to strong-names in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|[<span data-ttu-id="7497c-152">方法 : 厳密な名前のアセンブリを参照する</span><span class="sxs-lookup"><span data-stu-id="7497c-152">How to: Reference a Strong-Named Assembly</span></span>](../../../docs/framework/app-domains/how-to-reference-a-strong-named-assembly.md)|<span data-ttu-id="7497c-153">コンパイル時または実行時に厳密な名前のアセンブリでタイプまたはリソースを参照する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7497c-153">Describes how to reference types or resources in a strong-named assembly at compile time or run time.</span></span>|  
|[<span data-ttu-id="7497c-154">方法: 厳密な名前のバイパス機能を無効にする</span><span class="sxs-lookup"><span data-stu-id="7497c-154">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)|<span data-ttu-id="7497c-155">厳密な名前の署名の検証をバイパスする機能を無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7497c-155">Describes how to disable the feature that bypasses the validation of strong-name signatures.</span></span> <span data-ttu-id="7497c-156">すべてのまたは特定のアプリケーションに対して、この機能を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="7497c-156">This feature can be disabled for all or for specific applications.</span></span>|  
|[<span data-ttu-id="7497c-157">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="7497c-157">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)|<span data-ttu-id="7497c-158">単一ファイル アセンブリおよびマルチファイル アセンブリの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="7497c-158">Provides an overview of single-file and multifile assemblies.</span></span>|  
|[<span data-ttu-id="7497c-159">Visual Studio 内でアセンブリに遅延署名する方法</span><span class="sxs-lookup"><span data-stu-id="7497c-159">How to Delay Sign an Assembly in Visual Studio</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|<span data-ttu-id="7497c-160">アセンブリを作成した後に厳密な名前でアセンブリに署名する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7497c-160">Explains how to sign an assembly with a strong name after the assembly has been created.</span></span>|  
|[<span data-ttu-id="7497c-161">Sn.exe (厳密名ツール)</span><span class="sxs-lookup"><span data-stu-id="7497c-161">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)|<span data-ttu-id="7497c-162">厳密な名前のアセンブリの作成に役立つ、.NET Framework に付属のツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7497c-162">Describes the tool included in the .NET Framework that helps create assemblies with strong names.</span></span> <span data-ttu-id="7497c-163">このツールには、キーの管理、署名の生成、署名の検査に関する各オプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="7497c-163">This tool provides options for key management, signature generation, and signature verification.</span></span>|  
|[<span data-ttu-id="7497c-164">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="7497c-164">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)|<span data-ttu-id="7497c-165">モジュールまたはリソース ファイルからアセンブリ マニフェストを含むファイルを生成する、.NET Framework に付属のツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7497c-165">Describes the tool included in the .NET Framework that generates a file that has an assembly manifest from modules or resource files.</span></span>|
