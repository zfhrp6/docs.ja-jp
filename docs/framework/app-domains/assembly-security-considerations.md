---
title: "アセンブリのセキュリティに関する考慮事項"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], security
- signcodes
- names [.NET Framework], assemblies
- strong-named assemblies, security considerations
- signing assemblies
- assemblies [.NET Framework], signing
- granting permissions, assemblies
- assemblies [.NET Framework], strong-named
- names [.NET Framework], strong names
- permissions [.NET Framework], assemblies
- security [.NET Framework], assemblies
- integrity with assemblies
ms.assetid: 1b5439c1-f3d5-4529-bd69-01814703d067
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 11c66af3a855dac649d5f09944d68fb77a0e8619
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-security-considerations"></a><span data-ttu-id="dc874-102">アセンブリのセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="dc874-102">Assembly Security Considerations</span></span>
<a name="top"></a> <span data-ttu-id="dc874-103">アセンブリを作成する場合は、アセンブリの実行に必要となるアクセス許可セットを指定できます。</span><span class="sxs-lookup"><span data-stu-id="dc874-103">When you build an assembly, you can specify a set of permissions that the assembly requires to run.</span></span> <span data-ttu-id="dc874-104">アセンブリに対して特定のアクセス許可を付与するかどうかは、証拠に基づいて決定されます。</span><span class="sxs-lookup"><span data-stu-id="dc874-104">Whether certain permissions are granted or not granted to an assembly is based on evidence.</span></span>  
  
 <span data-ttu-id="dc874-105">証拠には 2 つの使い方があります。</span><span class="sxs-lookup"><span data-stu-id="dc874-105">There are two distinct ways evidence is used:</span></span>  
  
-   <span data-ttu-id="dc874-106">入力された証拠をローダーによって収集された証拠とマージして、ポリシーの解決に使用される最終的な証拠のセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="dc874-106">The input evidence is merged with the evidence gathered by the loader to create a final set of evidence used for policy resolution.</span></span> <span data-ttu-id="dc874-107">この形式を使用するメソッドには、**Assembly.Load**、**Assembly.LoadFrom**、**Activator.CreateInstance** があります。</span><span class="sxs-lookup"><span data-stu-id="dc874-107">The methods that use this semantic include **Assembly.Load**, **Assembly.LoadFrom**, and **Activator.CreateInstance**.</span></span>  
  
-   <span data-ttu-id="dc874-108">入力された証拠を変更せずに、ポリシーの解決に使用する最終的な証拠のセットとして使用します。</span><span class="sxs-lookup"><span data-stu-id="dc874-108">The input evidence is used unaltered as the final set of evidence used for policy resolution.</span></span> <span data-ttu-id="dc874-109">この形式を使用するメソッドには、**Assembly.Load(byte[])** と **AppDomain.DefineDynamicAssembly()** があります。</span><span class="sxs-lookup"><span data-stu-id="dc874-109">The methods that use this semantic include **Assembly.Load(byte[])** and **AppDomain.DefineDynamicAssembly()**.</span></span>  
  
 <span data-ttu-id="dc874-110">アセンブリが実行されるコンピューターで設定されている[セキュリティ ポリシー](../../../docs/framework/misc/code-access-security-basics.md)により、オプションのアクセス許可を与えることもできます。</span><span class="sxs-lookup"><span data-stu-id="dc874-110">Optional permissions can be granted by the [security policy](../../../docs/framework/misc/code-access-security-basics.md) set on the computer where the assembly will run.</span></span> <span data-ttu-id="dc874-111">発生する可能性があるセキュリティ例外をすべて処理するコードを作成するには、次のいずれかを行います。</span><span class="sxs-lookup"><span data-stu-id="dc874-111">If you want your code to handle all potential security exceptions, you can do one of the following:</span></span>  
  
-   <span data-ttu-id="dc874-112">コードを実行するために必要なすべてのアクセス許可に対してアクセス許可要求を挿入し、アクセス許可が与えられなかった場合に生じる読み込み時エラーをあらかじめ処理しておく。</span><span class="sxs-lookup"><span data-stu-id="dc874-112">Insert a permission request for all the permissions your code must have, and handle up front the load-time failure that occurs if the permissions are not granted.</span></span>  
  
-   <span data-ttu-id="dc874-113">コードを実行するために必要なアクセス許可を取得するためのアクセス許可要求は使用せず、アクセス許可が与えられなかった場合のセキュリティ例外を処理できるように準備しておく。</span><span class="sxs-lookup"><span data-stu-id="dc874-113">Do not use a permission request to obtain permissions your code might need, but be prepared to handle security exceptions if permissions are not granted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dc874-114">セキュリティは複雑な分野で、選択できるオプションも数多くあります。</span><span class="sxs-lookup"><span data-stu-id="dc874-114">Security is a complex area, and you have many options to choose from.</span></span> <span data-ttu-id="dc874-115">詳細については、「[セキュリティの基本概念](../../../docs/standard/security/key-security-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc874-115">For more information, see [Key Security Concepts](../../../docs/standard/security/key-security-concepts.md).</span></span>  
  
 <span data-ttu-id="dc874-116">アセンブリの読み込み時に、セキュリティ ポリシーへの追加情報としてアセンブリの証拠が使用されます。</span><span class="sxs-lookup"><span data-stu-id="dc874-116">At load time, the assembly's evidence is used as input to security policy.</span></span> <span data-ttu-id="dc874-117">セキュリティ ポリシーは、エンタープライズとコンピューターの管理者、およびユーザー ポリシー設定によって確立され、すべてのマネージ コードが実行されるときに与えられるアクセス許可セットを決定します。</span><span class="sxs-lookup"><span data-stu-id="dc874-117">Security policy is established by the enterprise and the computer's administrator as well as by user policy settings, and determines the set of permissions that is granted to all managed code when executed.</span></span> <span data-ttu-id="dc874-118">セキュリティ ポリシーは、アセンブリの発行者 (署名ツールで生成されたシグネチャがある場合)、アセンブリのダウンロード元の Web サイトおよびゾーン (Internet Explorer の用語)、またはアセンブリの厳密な名前に対して設定できます。</span><span class="sxs-lookup"><span data-stu-id="dc874-118">Security policy can be established for the publisher of the assembly (if it has a signing tool generated signature), for the Web site and zone (in Internet Explorer terms) the assembly was downloaded from, or for the assembly's strong name.</span></span> <span data-ttu-id="dc874-119">たとえば、コンピューター管理者は、Web サイトからダウンロードされ、所定のソフトウェア企業の署名のあるすべてのコードについて、コンピューター上のデータベースへのアクセスは許可するが、ディスクへの書き込みは許可しない、というセキュリティ ポリシーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="dc874-119">For example, a computer's administrator can establish security policy that allows all code downloaded from a Web site and signed by a given software company to access a database on a computer, but does not grant access to write to the computer's disk.</span></span>  
  
## <a name="strong-named-assemblies-and-signing-tools"></a><span data-ttu-id="dc874-120">厳密な名前付きアセンブリと署名ツール</span><span class="sxs-lookup"><span data-stu-id="dc874-120">Strong-Named Assemblies and Signing Tools</span></span>  
 <span data-ttu-id="dc874-121">アセンブリには異なる、補完的な 2 つの方法で署名できます。厳密な名前を利用するか、[SignTool.exe (署名ツール)](../../../docs/framework/tools/signtool-exe.md) を利用します。</span><span class="sxs-lookup"><span data-stu-id="dc874-121">You can sign an assembly in two different but complementary ways: with a strong name or by using  [SignTool.exe (Sign Tool)](../../../docs/framework/tools/signtool-exe.md).</span></span> <span data-ttu-id="dc874-122">厳密な名前を使用してアセンブリに署名すると、アセンブリ マニフェストを格納しているファイルに公開キー暗号化が追加されます。</span><span class="sxs-lookup"><span data-stu-id="dc874-122">Signing an assembly with a strong name adds public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="dc874-123">厳密な名前による署名では、名前の一意性の検証を支援し、名前の悪用を防止し、参照が解決されたときに呼び出し元に ID を提供できます。</span><span class="sxs-lookup"><span data-stu-id="dc874-123">Strong name signing helps to verify name uniqueness, prevent name spoofing, and provide callers with some identity when a reference is resolved.</span></span>  
  
 <span data-ttu-id="dc874-124">ただし、厳密な名前そのものには信頼性がないため、信頼性という点では [SignTool.exe (署名ツール)](../../../docs/framework/tools/signtool-exe.md) が重要になります。</span><span class="sxs-lookup"><span data-stu-id="dc874-124">However, no level of trust is associated with a strong name, which makes [SignTool.exe (Sign Tool)](../../../docs/framework/tools/signtool-exe.md) important.</span></span> <span data-ttu-id="dc874-125">2 つの署名ツールでは、発行者が第三者機関に対して自分の身元を証明し、証明書を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc874-125">The two signing tools require a publisher to prove its identity to a third-party authority and obtain a certificate.</span></span> <span data-ttu-id="dc874-126">取得した証明書はファイルに埋め込まれ、管理者はその証明書を使用してコードの正当性を信頼するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="dc874-126">This certificate is then embedded in your file and can be used by an administrator to decide whether to trust the code's authenticity.</span></span>  
  
 <span data-ttu-id="dc874-127">アセンブリには、厳密な名前と [SignTool.exe (署名ツール)](../../../docs/framework/tools/signtool-exe.md) を使用して作成されたデジタル署名の両方を与えるか、またはそのいずれか一方だけを適用できます。</span><span class="sxs-lookup"><span data-stu-id="dc874-127">You can give both a strong name and a digital signature created using [SignTool.exe (Sign Tool)](../../../docs/framework/tools/signtool-exe.md) to an assembly, or you can use either alone.</span></span> <span data-ttu-id="dc874-128">2 つの署名ツールでは、署名できるファイルは一度に 1 つだけです。マルチファイル アセンブリの場合は、アセンブリ マニフェストを格納しているファイルに署名します。</span><span class="sxs-lookup"><span data-stu-id="dc874-128">The two signing tools can sign only one file at a time; for a multifile assembly, you sign the file that contains the assembly manifest.</span></span> <span data-ttu-id="dc874-129">厳密な名前はアセンブリ マニフェストが格納されているファイルに保存されますが、[SignTool.exe (署名ツール)](../../../docs/framework/tools/signtool-exe.md) を使用して作成された署名は、アセンブリ マニフェストが格納されているポータブル実行可能 (PE: Portable Executable) ファイルの予約された専用スロットに保存されます。</span><span class="sxs-lookup"><span data-stu-id="dc874-129">A strong name is stored in the file containing the assembly manifest, but a signature created using [SignTool.exe (Sign Tool)](../../../docs/framework/tools/signtool-exe.md) is stored in a reserved slot in the portable executable (PE) file containing the assembly manifest.</span></span> <span data-ttu-id="dc874-130">[SignTool.exe (署名ツール)](../../../docs/framework/tools/signtool-exe.md) を使用するアセンブリに対する署名は、[SignTool.exe (署名ツール)](../../../docs/framework/tools/signtool-exe.md) で生成された署名に依存する信頼階層が既に存在する場合や、またはポリシーがキー部分だけを使用し、信頼階層はチェックしていない場合に、(厳密な名前と組み合わせて、または単独で) 使用できます。</span><span class="sxs-lookup"><span data-stu-id="dc874-130">Signing of an assembly using [SignTool.exe (Sign Tool)](../../../docs/framework/tools/signtool-exe.md) can be used (with or without a strong name) when you already have a trust hierarchy that relies on[SignTool.exe (Sign Tool)](../../../docs/framework/tools/signtool-exe.md) generated signatures, or when your policy uses only the key portion and does not check a chain of trust.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc874-131">アセンブリに対して厳密な名前と署名ツールの署名の両方を使用する場合は、厳密な名前を先に割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="dc874-131">When using both a strong name and a signing tool signature on an assembly, the strong name must be assigned first.</span></span>  
  
 <span data-ttu-id="dc874-132">共通言語ランタイムは、ハッシュ検査も実行します。アセンブリ マニフェストには、アセンブリを構成するすべてのファイルのリストが格納されており、マニフェスト作成時の状態の各ファイルのハッシュも含まれています。</span><span class="sxs-lookup"><span data-stu-id="dc874-132">The common language runtime also performs a hash verification; the assembly manifest contains a list of all files that make up the assembly, including a hash of each file as it existed when the manifest was built.</span></span> <span data-ttu-id="dc874-133">各ファイルが読み込まれたときに、その内容がハッシュされ、マニフェストに格納されているハッシュ値と比較されます。</span><span class="sxs-lookup"><span data-stu-id="dc874-133">As each file is loaded, its contents are hashed and compared with the hash value stored in the manifest.</span></span> <span data-ttu-id="dc874-134">2 つのハッシュが一致しない場合、アセンブリは読み込まれません。</span><span class="sxs-lookup"><span data-stu-id="dc874-134">If the two hashes do not match, the assembly fails to load.</span></span>  
  
 <span data-ttu-id="dc874-135">厳密な名前と [SignTool.exe (署名ツール)](../../../docs/framework/tools/signtool-exe.md) を使用する署名によって整合性が保証されるため、これら 2 種類のアセンブリ証拠に基づいてコード アクセス セキュリティ ポリシーを設定できます。</span><span class="sxs-lookup"><span data-stu-id="dc874-135">Because strong naming and signing using [SignTool.exe (Sign Tool)](../../../docs/framework/tools/signtool-exe.md) guarantee integrity, you can base code access security policy on these two forms of assembly evidence.</span></span> <span data-ttu-id="dc874-136">厳密な名前と [SignTool.exe (署名ツール)](../../../docs/framework/tools/signtool-exe.md) を使用する署名では、デジタル署名と証明書によって整合性が保証されます。</span><span class="sxs-lookup"><span data-stu-id="dc874-136">Strong naming and signing using [SignTool.exe (Sign Tool)](../../../docs/framework/tools/signtool-exe.md) guarantee integrity through digital signatures and certificates.</span></span> <span data-ttu-id="dc874-137">以上で述べた技術 (ハッシュ検査、厳密な名前、[SignTool.exe (署名ツール)](../../../docs/framework/tools/signtool-exe.md) を使用する署名) をすべて組み合わせて使用することで、アセンブリがどのような方法によっても変更されていないことが保証されます。</span><span class="sxs-lookup"><span data-stu-id="dc874-137">All the technologies mentioned—hash verification, strong naming, and signing using [SignTool.exe (Sign Tool)](../../../docs/framework/tools/signtool-exe.md)—work together to ensure that the assembly has not been altered in any way.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc874-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="dc874-138">See Also</span></span>  
 [<span data-ttu-id="dc874-139">厳密な名前付きアセンブリ</span><span class="sxs-lookup"><span data-stu-id="dc874-139">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)  
 [<span data-ttu-id="dc874-140">共通言語ランタイムのアセンブリ</span><span class="sxs-lookup"><span data-stu-id="dc874-140">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="dc874-141">SignTool.exe (署名ツール)</span><span class="sxs-lookup"><span data-stu-id="dc874-141">SignTool.exe (Sign Tool)</span></span>](../../../docs/framework/tools/signtool-exe.md)
