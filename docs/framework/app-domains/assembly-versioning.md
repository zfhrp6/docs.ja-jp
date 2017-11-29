---
title: "アセンブリのバージョン管理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a956e0c4521e4a1079b331868e811e68af2e710d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-versioning"></a><span data-ttu-id="f493a-102">アセンブリのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="f493a-102">Assembly Versioning</span></span>
<span data-ttu-id="f493a-103">共通言語ランタイムを使用するアセンブリのバージョン管理は、すべてアセンブリ レベルで行われます。</span><span class="sxs-lookup"><span data-stu-id="f493a-103">All versioning of assemblies that use the common language runtime is done at the assembly level.</span></span> <span data-ttu-id="f493a-104">アセンブリの特定のバージョン、および依存する各アセンブリのバージョンは、アセンブリのマニフェストに記録されます。</span><span class="sxs-lookup"><span data-stu-id="f493a-104">The specific version of an assembly and the versions of dependent assemblies are recorded in the assembly's manifest.</span></span> <span data-ttu-id="f493a-105">ランタイムの既定のバージョン ポリシーは、構成ファイル (アプリケーション構成ファイル、発行者ポリシー ファイル、コンピューター管理者の構成ファイル) に指定した明示的なバージョン ポリシーでオーバーライドされない限り、アプリケーションが作成およびテストされた時点のバージョンの場合にだけそのアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="f493a-105">The default version policy for the runtime is that applications run only with the versions they were built and tested with, unless overridden by explicit version policy in configuration files (the application configuration file, the publisher policy file, and the computer's administrator configuration file).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f493a-106">バージョン管理は、厳密な名前付きのアセンブリに対してだけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="f493a-106">Versioning is done only on assemblies with strong names.</span></span>  
  
 <span data-ttu-id="f493a-107">ランタイムは、アセンブリ バインディング要求を解決するために、いくつかの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f493a-107">The runtime performs several steps to resolve an assembly binding request:</span></span>  
  
1.  <span data-ttu-id="f493a-108">元のアセンブリ参照を確認し、バインド先のアセンブリのバージョンを確認します。</span><span class="sxs-lookup"><span data-stu-id="f493a-108">Checks the original assembly reference to determine the version of the assembly to be bound.</span></span>  
  
2.  <span data-ttu-id="f493a-109">バージョン ポリシーを適用するために利用できる構成ファイルをすべてチェックします。</span><span class="sxs-lookup"><span data-stu-id="f493a-109">Checks for all applicable configuration files to apply version policy.</span></span>  
  
3.  <span data-ttu-id="f493a-110">元のアセンブリ参照と、構成ファイルで指定されているリダイレクトから正しいアセンブリを判断し、呼び出し元のアセンブリにバインドされるバージョンを判断します。</span><span class="sxs-lookup"><span data-stu-id="f493a-110">Determines the correct assembly from the original assembly reference and any redirection specified in the configuration files, and determines the version that should be bound to the calling assembly.</span></span>  
  
4.  <span data-ttu-id="f493a-111">グローバル アセンブリ キャッシュと、構成ファイルで指定されたコードベースをチェックした後、「[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)」に説明されているプローブ規則を使用して、アプリケーションのディレクトリとサブディレクトリをチェックします。</span><span class="sxs-lookup"><span data-stu-id="f493a-111">Checks the global assembly cache, codebases specified in configuration files, and then checks the application's directory and subdirectories using the probing rules explained in [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="f493a-112">これらの手順を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="f493a-112">The following illustration shows these steps.</span></span>  
  
 <span data-ttu-id="f493a-113">![.assembly extern myAssembly](../../../docs/framework/app-domains/media/versioningover.gif "versioningover")</span><span class="sxs-lookup"><span data-stu-id="f493a-113">![.assembly extern myAssembly](../../../docs/framework/app-domains/media/versioningover.gif "versioningover")</span></span>  
<span data-ttu-id="f493a-114">アセンブリ バインディング要求の解決</span><span class="sxs-lookup"><span data-stu-id="f493a-114">Resolving an assembly binding request</span></span>  
  
 <span data-ttu-id="f493a-115">アプリケーションの設定の詳細については、「[アプリの構成](../../../docs/framework/configure-apps/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f493a-115">For more information about configuring applications, see [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="f493a-116">バインド ポリシーの詳細については、「[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f493a-116">For more information about binding policy, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="f493a-117">バージョン情報</span><span class="sxs-lookup"><span data-stu-id="f493a-117">Version Information</span></span>  
 <span data-ttu-id="f493a-118">各アセンブリは、次の 2 種類の形でバージョン情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="f493a-118">Each assembly has two distinct ways of expressing version information:</span></span>  
  
-   <span data-ttu-id="f493a-119">アセンブリのバージョン番号。アセンブリ名やカルチャ情報と共に、アセンブリの識別子を構成します。</span><span class="sxs-lookup"><span data-stu-id="f493a-119">The assembly's version number, which, together with the assembly name and culture information, is part of the assembly's identity.</span></span> <span data-ttu-id="f493a-120">この番号は、バージョン ポリシーを強制適用するためにランタイムで使用され、実行時の型解決プロセスで重要な役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="f493a-120">This number is used by the runtime to enforce version policy and plays a key part in the type resolution process at run time.</span></span>  
  
-   <span data-ttu-id="f493a-121">補足バージョン。これは、情報の提供だけを目的とした、追加のバージョン情報を表す文字列です。</span><span class="sxs-lookup"><span data-stu-id="f493a-121">An informational version, which is a string that represents additional version information included for informational purposes only.</span></span>  
  
### <a name="assembly-version-number"></a><span data-ttu-id="f493a-122">アセンブリのバージョン番号</span><span class="sxs-lookup"><span data-stu-id="f493a-122">Assembly Version Number</span></span>  
 <span data-ttu-id="f493a-123">各アセンブリの識別子には、バージョン番号が含まれています。</span><span class="sxs-lookup"><span data-stu-id="f493a-123">Each assembly has a version number as part of its identity.</span></span> <span data-ttu-id="f493a-124">そのため、バージョン番号が異なる 2 つのアセンブリは、ランタイムでは、まったく異なるアセンブリと見なされます。</span><span class="sxs-lookup"><span data-stu-id="f493a-124">As such, two assemblies that differ by version number are considered by the runtime to be completely different assemblies.</span></span> <span data-ttu-id="f493a-125">このバージョン番号は、次に示す形式の 4 つの部分から成る文字列として表されます。</span><span class="sxs-lookup"><span data-stu-id="f493a-125">This version number is physically represented as a four-part string with the following format:</span></span>  
  
 <span data-ttu-id="f493a-126">\<*メジャー バージョン*>.\<*マイナー バージョン*>.\<*ビルド番号*>.\<*改訂番号*></span><span class="sxs-lookup"><span data-stu-id="f493a-126">\<*major version*>.\<*minor version*>.\<*build number*>.\<*revision*></span></span>  
  
 <span data-ttu-id="f493a-127">たとえばバージョン 1.5.1254.0 の場合、1 はメジャー バージョン、5 はマイナー バージョン、1254 はビルド番号、0 はリビジョン番号を表します。</span><span class="sxs-lookup"><span data-stu-id="f493a-127">For example, version 1.5.1254.0 indicates 1 as the major version, 5 as the minor version, 1254 as the build number, and 0 as the revision number.</span></span>  
  
 <span data-ttu-id="f493a-128">バージョン番号は、アセンブリ名や公開キーなどのほかの識別子情報や、アプリケーションに関連付けられているほかの複数のアセンブリの関係や識別子に関する情報と共に、アセンブリ マニフェストに保存されます。</span><span class="sxs-lookup"><span data-stu-id="f493a-128">The version number is stored in the assembly manifest along with other identity information, including the assembly name and public key, as well as information on relationships and identities of other assemblies connected with the application.</span></span>  
  
 <span data-ttu-id="f493a-129">アセンブリの作成時に、開発ツールによって、アセンブリ マニフェストで参照される各アセンブリについての依存情報が記録されます。</span><span class="sxs-lookup"><span data-stu-id="f493a-129">When an assembly is built, the development tool records dependency information for each assembly that is referenced in the assembly manifest.</span></span> <span data-ttu-id="f493a-130">ランタイムは、これらのバージョン番号と、管理者、アプリケーション、または発行者が設定した構成情報を組み合わせて使用し、参照先アセンブリの正しいバージョンを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="f493a-130">The runtime uses these version numbers, in conjunction with configuration information set by an administrator, an application, or a publisher, to load the proper version of a referenced assembly.</span></span>  
  
 <span data-ttu-id="f493a-131">バージョン管理の目的のため、ランタイムでは、通常の名前の付いたアセンブリと、厳密な名前の付いたアセンブリが区別されます。</span><span class="sxs-lookup"><span data-stu-id="f493a-131">The runtime distinguishes between regular and strong-named assemblies for the purposes of versioning.</span></span> <span data-ttu-id="f493a-132">バージョンのチェックは、厳密な名前付きのアセンブリに対してだけ実行されます。</span><span class="sxs-lookup"><span data-stu-id="f493a-132">Version checking only occurs with strong-named assemblies.</span></span>  
  
 <span data-ttu-id="f493a-133">バージョン バインド ポリシーの指定については、「[アプリの構成](../../../docs/framework/configure-apps/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f493a-133">For information about specifying version binding policies, see [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="f493a-134">ランタイムがバージョン情報を使用して特定のアセンブリを見つけ出す方法については、「[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f493a-134">For information about how the runtime uses version information to find a particular assembly, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
### <a name="assembly-informational-version"></a><span data-ttu-id="f493a-135">アセンブリの補足バージョン</span><span class="sxs-lookup"><span data-stu-id="f493a-135">Assembly Informational Version</span></span>  
 <span data-ttu-id="f493a-136">補足バージョンは、情報の提供だけを目的として、追加のバージョン情報をアセンブリに追加するための文字列です。この情報は実行時には使用されません。</span><span class="sxs-lookup"><span data-stu-id="f493a-136">The informational version is a string that attaches additional version information to an assembly for informational purposes only; this information is not used at run time.</span></span> <span data-ttu-id="f493a-137">補足バージョンはテキスト ベースで、その製品のマーケティング資料、パッケージ、あるいは製品名に対応するものであり、実行時には使用されません。</span><span class="sxs-lookup"><span data-stu-id="f493a-137">The text-based informational version corresponds to the product's marketing literature, packaging, or product name and is not used by the runtime.</span></span> <span data-ttu-id="f493a-138">たとえば、補足バージョンの例は "共通言語ランタイム バージョン 1.0" や "NET Control SP 2" などになります。</span><span class="sxs-lookup"><span data-stu-id="f493a-138">For example, an informational version could be "Common Language Runtime version 1.0" or "NET Control SP 2".</span></span> <span data-ttu-id="f493a-139">Microsoft Windows のファイル プロパティ ダイアログの [バージョン] タブでは、この情報は [製品バージョン] という項目に表示されます。</span><span class="sxs-lookup"><span data-stu-id="f493a-139">On the Version tab of the file properties dialog in Microsoft Windows, this information appears in the item "Product Version".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f493a-140">任意のテキストを指定できますが、文字列がアセンブリのバージョン番号で使用されている形式でなかったり、形式が正しくてもワイルドカードを含んでいたりすると、コンパイルで警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f493a-140">Although you can specify any text, a warning message appears on compilation if the string is not in the format used by the assembly version number, or if it is in that format but contains wildcards.</span></span> <span data-ttu-id="f493a-141">この警告は、実行には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="f493a-141">This warning is harmless.</span></span>  
  
 <span data-ttu-id="f493a-142">補足バージョンは、カスタム属性 <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType> を使って表されます。</span><span class="sxs-lookup"><span data-stu-id="f493a-142">The informational version is represented using the custom attribute <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f493a-143">補足バージョン属性の詳細については、「[アセンブリ属性の設定](../../../docs/framework/app-domains/set-assembly-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f493a-143">For more information about the informational version attribute, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f493a-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="f493a-144">See Also</span></span>  
 [<span data-ttu-id="f493a-145">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="f493a-145">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="f493a-146">アプリの構成</span><span class="sxs-lookup"><span data-stu-id="f493a-146">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="f493a-147">アセンブリ属性の設定</span><span class="sxs-lookup"><span data-stu-id="f493a-147">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 [<span data-ttu-id="f493a-148">共通言語ランタイムのアセンブリ</span><span class="sxs-lookup"><span data-stu-id="f493a-148">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
