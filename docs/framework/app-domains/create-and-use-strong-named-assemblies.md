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
ms.openlocfilehash: 7d0ff21ee4846b2f5586317e70ac96f37517621f
ms.sourcegitcommit: 3d42e1d73e21c35c540dd4adbea23efcbe1b8b0a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2018
ms.locfileid: "36270501"
---
# <a name="creating-and-using-strong-named-assemblies"></a><span data-ttu-id="262cd-102">厳密な名前付きアセンブリの作成と使用</span><span class="sxs-lookup"><span data-stu-id="262cd-102">Creating and Using Strong-Named Assemblies</span></span>
<a name="top"></a> <span data-ttu-id="262cd-103">厳密な名前は、単純テキスト名、バージョン番号、カルチャ情報 (設定されている場合) から成るアセンブリの識別子と、公開キーおよびデジタル署名で構成されます。</span><span class="sxs-lookup"><span data-stu-id="262cd-103">A strong name consists of the assembly's identity—its simple text name, version number, and culture information (if provided)—plus a public key and a digital signature.</span></span> <span data-ttu-id="262cd-104">このデジタル署名は、対応する秘密キーを使用してアセンブリ ファイルから生成されます。</span><span class="sxs-lookup"><span data-stu-id="262cd-104">It is generated from an assembly file using the corresponding private key.</span></span> <span data-ttu-id="262cd-105">(アセンブリ ファイルにはアセンブリ マニフェストが格納されており、そこに、アセンブリを構成するすべてのファイルの名前とハッシュが含まれます。)</span><span class="sxs-lookup"><span data-stu-id="262cd-105">(The assembly file contains the assembly manifest, which contains the names and hashes of all the files that make up the assembly.)</span></span>  

> [!WARNING]
> <span data-ttu-id="262cd-106">セキュリティに関しては、厳格な名前に依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="262cd-106">Do not rely on strong names for security.</span></span> <span data-ttu-id="262cd-107">厳格な名前は、一意の ID を提供するだけです。</span><span class="sxs-lookup"><span data-stu-id="262cd-107">They provide a unique identity only.</span></span>
  
 <span data-ttu-id="262cd-108">厳密な名前のアセンブリは、他の厳密な名前のアセンブリでのタイプだけを使用できます。</span><span class="sxs-lookup"><span data-stu-id="262cd-108">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="262cd-109">それ以外の場合は、厳密な名前のアセンブリの整合性が損なわれます。</span><span class="sxs-lookup"><span data-stu-id="262cd-109">Otherwise, the integrity of the strong-named assembly would be compromised.</span></span>  
  
 <span data-ttu-id="262cd-110">この概要は、次のセクションで構成されています。</span><span class="sxs-lookup"><span data-stu-id="262cd-110">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="262cd-111">厳密な名前のシナリオ</span><span class="sxs-lookup"><span data-stu-id="262cd-111">Strong Name Scenario</span></span>](#strong_name_scenario)  
  
-   [<span data-ttu-id="262cd-112">信頼されたアセンブリの署名検証のバイパス</span><span class="sxs-lookup"><span data-stu-id="262cd-112">Bypassing Signature Verification of Trusted Assemblies</span></span>](#bypassing_signature_verification)  
  
-   [<span data-ttu-id="262cd-113">関連トピック</span><span class="sxs-lookup"><span data-stu-id="262cd-113">Related Topics</span></span>](#related_topics)  
  
<a name="strong_name_scenario"></a>   
## <a name="strong-name-scenario"></a><span data-ttu-id="262cd-114">厳密な名前のシナリオ</span><span class="sxs-lookup"><span data-stu-id="262cd-114">Strong Name Scenario</span></span>  
 <span data-ttu-id="262cd-115">次のシナリオは、厳密な名前のアセンブリに署名した後にそれをその名前で参照するプロセスの概要を示しています。</span><span class="sxs-lookup"><span data-stu-id="262cd-115">The following scenario outlines the process of signing an assembly with a strong name and later referencing it by that name.</span></span>  
  
1.  <span data-ttu-id="262cd-116">アセンブリ A は、次のいずれかの方法を使用して厳密な名前で作成されます。</span><span class="sxs-lookup"><span data-stu-id="262cd-116">Assembly A is created with a strong name using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="262cd-117">[!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] など、厳密な名前の作成をサポートする開発環境を使用する。</span><span class="sxs-lookup"><span data-stu-id="262cd-117">Using a development environment that supports creating strong names, such as [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)].</span></span>  
  
    -   <span data-ttu-id="262cd-118">[厳密名ツール (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) を使用して暗号化キー ペアを作成し、コマンド ライン コンパイラまたは[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) のいずれかを使用してそのキー ペアをアセンブリに割り当てる。</span><span class="sxs-lookup"><span data-stu-id="262cd-118">Creating a cryptographic key pair using the [Strong Name tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) and assigning that key pair to the assembly using either a command-line compiler or the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="262cd-119">Windows ソフトウェア開発キット (SDK) には、Sn.exe と Al.exe の両方が用意されています。</span><span class="sxs-lookup"><span data-stu-id="262cd-119">The Windows Software Development Kit (SDK) provides both Sn.exe and Al.exe.</span></span>  
  
2.  <span data-ttu-id="262cd-120">開発環境またはツールは、アセンブリのマニフェストを含むファイルのハッシュに、開発者の秘密キーで署名します。</span><span class="sxs-lookup"><span data-stu-id="262cd-120">The development environment or tool signs the hash of the file containing the assembly's manifest with the developer's private key.</span></span> <span data-ttu-id="262cd-121">このデジタル署名は、アセンブリ A のマニフェストを含むポータブル実行可能 (PE) ファイルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="262cd-121">This digital signature is stored in the portable executable (PE) file that contains Assembly A's manifest.</span></span>  
  
3.  <span data-ttu-id="262cd-122">アセンブリ B はアセンブリ A のコンシューマーです。アセンブリ B のマニフェストの参照セクションには、アセンブリ A の公開キーを表すトークンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="262cd-122">Assembly B is a consumer of Assembly A. The reference section of Assembly B's manifest includes a token that represents Assembly A's public key.</span></span> <span data-ttu-id="262cd-123">トークンは完全な公開キーの一部であり、スペースを節約するために、キー自体ではなくこれが使用されます。</span><span class="sxs-lookup"><span data-stu-id="262cd-123">A token is a portion of the full public key and is used rather than the key itself to save space.</span></span>  
  
4.  <span data-ttu-id="262cd-124">共通言語ランタイムは、アセンブリがグローバル アセンブリ キャッシュに入れられる際に、厳密な名前の署名を確認します。</span><span class="sxs-lookup"><span data-stu-id="262cd-124">The common language runtime verifies the strong name signature when the assembly is placed in the global assembly cache.</span></span> <span data-ttu-id="262cd-125">実行時に厳密な名前でバインドするとき、共通言語ランタイムは、アセンブリ B のマニフェストに格納されているキーと、アセンブリ A の厳密な名前を生成するために使用されたキーを比較します。 .NET Framework のセキュリティ チェックに合格してバインドが成功すると、アセンブリ B は、アセンブリ A のビットが改ざんされていないことと、これらのビットが実際にアセンブリ A の開発者からのものであることが保証されます。</span><span class="sxs-lookup"><span data-stu-id="262cd-125">When binding by strong name at run time, the common language runtime compares the key stored in Assembly B's manifest with the key used to generate the strong name for Assembly A. If the .NET Framework security checks pass and the bind succeeds, Assembly B has a guarantee that Assembly A's bits have not been tampered with and that these bits actually come from the developers of Assembly A.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="262cd-126">このシナリオは、信頼の問題を扱っていません。</span><span class="sxs-lookup"><span data-stu-id="262cd-126">This scenario doesn't address trust issues.</span></span> <span data-ttu-id="262cd-127">厳密な名前に加えて、完全な Microsoft Authenticode 署名をアセンブリに持たせることができます。</span><span class="sxs-lookup"><span data-stu-id="262cd-127">Assemblies can carry full Microsoft Authenticode signatures in addition to a strong name.</span></span> <span data-ttu-id="262cd-128">Authenticode 署名には、信頼を確立するための証明書が含まれます。</span><span class="sxs-lookup"><span data-stu-id="262cd-128">Authenticode signatures include a certificate that establishes trust.</span></span> <span data-ttu-id="262cd-129">厳密な名前を使用すると、コードにこのように署名する必要がないということに注意してください。</span><span class="sxs-lookup"><span data-stu-id="262cd-129">It's important to note that strong names don't require code to be signed in this way.</span></span> <span data-ttu-id="262cd-130">厳密な名前は、一意の ID を提供するだけです。</span><span class="sxs-lookup"><span data-stu-id="262cd-130">Strong names only provide a unique identity.</span></span>  
  
 [<span data-ttu-id="262cd-131">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="262cd-131">Back to top</span></span>](#top)  
  
<a name="bypassing_signature_verification"></a>   
## <a name="bypassing-signature-verification-of-trusted-assemblies"></a><span data-ttu-id="262cd-132">信頼されたアセンブリの署名検証のバイパス</span><span class="sxs-lookup"><span data-stu-id="262cd-132">Bypassing Signature Verification of Trusted Assemblies</span></span>  
 <span data-ttu-id="262cd-133">[!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)] 以降、たとえば `MyComputer` ゾーンの既定のアプリケーション ドメインなど、完全に信頼されたアプリケーション ドメインにアセンブリが読み込まれるときに、厳密な名前の署名は検証されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="262cd-133">Starting with the [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], strong-name signatures are not validated when an assembly is loaded into a full-trust application domain, such as the default application domain for the `MyComputer` zone.</span></span> <span data-ttu-id="262cd-134">これは厳密な名前のバイパス機能と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="262cd-134">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="262cd-135">完全に信頼された環境では、<xref:System.Security.Permissions.StrongNameIdentityPermission> に対する完全に信頼された署名済みアセンブリの要求は、その署名に関係なく、常に成功します。</span><span class="sxs-lookup"><span data-stu-id="262cd-135">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies, regardless of their signature.</span></span> <span data-ttu-id="262cd-136">このような場合、厳密な名前のバイパス機能は、完全に信頼されたアセンブリの厳密名署名検証という不要なオーバーヘッドを回避するので、アセンブリを高速で読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="262cd-136">The strong-name bypass feature avoids the unnecessary overhead of strong-name signature verification of full-trust assemblies in this situation, allowing the assemblies to load faster.</span></span>  
  
 <span data-ttu-id="262cd-137">バイ パス機能は、厳密な名前で署名されていて、次の特性を持つアセンブリに適用されます。</span><span class="sxs-lookup"><span data-stu-id="262cd-137">The bypass feature applies to any assembly that is signed with a strong name and that has the following characteristics:</span></span>  
  
-   <span data-ttu-id="262cd-138"><xref:System.Security.Policy.StrongName> 証拠なしで完全に信頼されている (たとえば、`MyComputer` ゾーン証拠を持っている)。</span><span class="sxs-lookup"><span data-stu-id="262cd-138">Fully trusted without <xref:System.Security.Policy.StrongName> evidence (for example, has `MyComputer` zone evidence).</span></span>  
  
-   <span data-ttu-id="262cd-139">完全に信頼された <xref:System.AppDomain> に読み込まれる。</span><span class="sxs-lookup"><span data-stu-id="262cd-139">Loaded into a fully trusted <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="262cd-140">その <xref:System.AppDomain> の <xref:System.AppDomainSetup.ApplicationBase%2A> プロパティに基づいた場所から読み込まれる。</span><span class="sxs-lookup"><span data-stu-id="262cd-140">Loaded from a location under the <xref:System.AppDomainSetup.ApplicationBase%2A> property of that <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="262cd-141">遅延署名されていない。</span><span class="sxs-lookup"><span data-stu-id="262cd-141">Not delay-signed.</span></span>  
  
 <span data-ttu-id="262cd-142">この機能は、個々のアプリケーションに対して、またはコンピューターに対して無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="262cd-142">This feature can be disabled for individual applications or for a computer.</span></span> <span data-ttu-id="262cd-143">「[方法: 厳密な名前のバイパス機能を無効にする](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="262cd-143">See [How to: Disable the Strong-Name Bypass Feature](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md).</span></span>  
  
 [<span data-ttu-id="262cd-144">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="262cd-144">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="262cd-145">関連トピック</span><span class="sxs-lookup"><span data-stu-id="262cd-145">Related Topics</span></span>  
  
|<span data-ttu-id="262cd-146">Title</span><span class="sxs-lookup"><span data-stu-id="262cd-146">Title</span></span>|<span data-ttu-id="262cd-147">説明</span><span class="sxs-lookup"><span data-stu-id="262cd-147">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="262cd-148">方法: 公開キーと秘密キーのキー ペアを作成する</span><span class="sxs-lookup"><span data-stu-id="262cd-148">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)|<span data-ttu-id="262cd-149">署名とアセンブリの暗号化キー ペアを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="262cd-149">Describes how to create a cryptographic key pair for signing an assembly.</span></span>|  
|[<span data-ttu-id="262cd-150">方法: 厳密な名前でアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="262cd-150">How to: Sign an Assembly with a Strong Name</span></span>](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)|<span data-ttu-id="262cd-151">厳密な名前のアセンブリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="262cd-151">Describes how to create a strong-named assembly.</span></span>|  
|[<span data-ttu-id="262cd-152">拡張された厳密な名前付け</span><span class="sxs-lookup"><span data-stu-id="262cd-152">Enhanced Strong Naming</span></span>](../../../docs/framework/app-domains/enhanced-strong-naming.md)|<span data-ttu-id="262cd-153">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] での厳密な名前の拡張について説明します。</span><span class="sxs-lookup"><span data-stu-id="262cd-153">Describes enhancements to strong-names in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span>|  
|[<span data-ttu-id="262cd-154">方法 : 厳密な名前のアセンブリを参照する</span><span class="sxs-lookup"><span data-stu-id="262cd-154">How to: Reference a Strong-Named Assembly</span></span>](../../../docs/framework/app-domains/how-to-reference-a-strong-named-assembly.md)|<span data-ttu-id="262cd-155">コンパイル時または実行時に厳密な名前のアセンブリでタイプまたはリソースを参照する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="262cd-155">Describes how to reference types or resources in a strong-named assembly at compile time or run time.</span></span>|  
|[<span data-ttu-id="262cd-156">方法: 厳密な名前のバイパス機能を無効にする</span><span class="sxs-lookup"><span data-stu-id="262cd-156">How to: Disable the Strong-Name Bypass Feature</span></span>](../../../docs/framework/app-domains/how-to-disable-the-strong-name-bypass-feature.md)|<span data-ttu-id="262cd-157">厳密な名前の署名の検証をバイパスする機能を無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="262cd-157">Describes how to disable the feature that bypasses the validation of strong-name signatures.</span></span> <span data-ttu-id="262cd-158">すべてのまたは特定のアプリケーションに対して、この機能を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="262cd-158">This feature can be disabled for all or for specific applications.</span></span>|  
|[<span data-ttu-id="262cd-159">アセンブリの作成</span><span class="sxs-lookup"><span data-stu-id="262cd-159">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)|<span data-ttu-id="262cd-160">単一ファイル アセンブリおよびマルチファイル アセンブリの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="262cd-160">Provides an overview of single-file and multifile assemblies.</span></span>|  
|[<span data-ttu-id="262cd-161">Visual Studio 内でアセンブリに遅延署名する方法</span><span class="sxs-lookup"><span data-stu-id="262cd-161">How to Delay Sign an Assembly in Visual Studio</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing#how-to-sign-an-assembly-in-visual-studio)|<span data-ttu-id="262cd-162">アセンブリを作成した後に厳密な名前でアセンブリに署名する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="262cd-162">Explains how to sign an assembly with a strong name after the assembly has been created.</span></span>|  
|[<span data-ttu-id="262cd-163">Sn.exe (厳密名ツール)</span><span class="sxs-lookup"><span data-stu-id="262cd-163">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)|<span data-ttu-id="262cd-164">厳密な名前のアセンブリの作成に役立つ、.NET Framework に付属のツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="262cd-164">Describes the tool included in the .NET Framework that helps create assemblies with strong names.</span></span> <span data-ttu-id="262cd-165">このツールには、キーの管理、署名の生成、署名の検査に関する各オプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="262cd-165">This tool provides options for key management, signature generation, and signature verification.</span></span>|  
|[<span data-ttu-id="262cd-166">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="262cd-166">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)|<span data-ttu-id="262cd-167">モジュールまたはリソース ファイルからアセンブリ マニフェストを含むファイルを生成する、.NET Framework に付属のツールについて説明します。</span><span class="sxs-lookup"><span data-stu-id="262cd-167">Describes the tool included in the .NET Framework that generates a file that has an assembly manifest from modules or resource files.</span></span>|
