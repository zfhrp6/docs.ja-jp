---
title: 拡張された厳密な名前付け
ms.date: 03/30/2017
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf4a8df87cd507f2bfb17086e83dc8374a22fe71
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="99d5a-102">拡張された厳密な名前付け</span><span class="sxs-lookup"><span data-stu-id="99d5a-102">Enhanced Strong Naming</span></span>
<span data-ttu-id="99d5a-103">厳密な名前の署名は、アセンブリを識別するための .NET Framework の識別機構です。</span><span class="sxs-lookup"><span data-stu-id="99d5a-103">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="99d5a-104">これは通常、発行元 (署名者) から受取人 (検証者) に対して渡されるデータの整合性を検証するために使用される、公開キーによるデジタル署名です。</span><span class="sxs-lookup"><span data-stu-id="99d5a-104">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="99d5a-105">この署名はアセンブリに対する一意の ID として使用され、これによりアセンブリへの参照のあいまいさをなくします。</span><span class="sxs-lookup"><span data-stu-id="99d5a-105">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="99d5a-106">アセンブリはビルド プロセスの一部として署名され、読み込まれるときに検証されます。</span><span class="sxs-lookup"><span data-stu-id="99d5a-106">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="99d5a-107">厳密な名前の署名により、悪意のあるユーザーがアセンブリを不正に変更して、元の署名者のキーでアセンブリを再署名することを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="99d5a-107">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="99d5a-108">ただし、厳密な名前キーには、発行者に関する信頼できる情報も、証明書の階層構造も含まれていません。</span><span class="sxs-lookup"><span data-stu-id="99d5a-108">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="99d5a-109">厳密な名前の署名は、アセンブリの署名者の信頼性を保証するものではなく、またその署名者がキーの正当な所有者であることを示すものでもありません。厳密な名前の署名は、キーの所有者がアセンブリに署名したことのみを示しています。</span><span class="sxs-lookup"><span data-stu-id="99d5a-109">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="99d5a-110">したがって、信頼できるサードパーティのコードのためのセキュリティの検証コントロールとして、厳密な名前の署名を使用することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="99d5a-110">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="99d5a-111">コードを認証するために推奨される方法は、Microsoft Authenticode です。</span><span class="sxs-lookup"><span data-stu-id="99d5a-111">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="99d5a-112">従来の厳密な名前の制限</span><span class="sxs-lookup"><span data-stu-id="99d5a-112">Limitations of Conventional Strong Names</span></span>  
 <span data-ttu-id="99d5a-113">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以前のバージョンで使用されている厳密な名前付けのテクノロジには次の欠点があります。</span><span class="sxs-lookup"><span data-stu-id="99d5a-113">The strong naming technology used in versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] has the following shortcomings:</span></span>  
  
-   <span data-ttu-id="99d5a-114">キーが常に攻撃を受ける状態に置かれています。テクノロジとハードウェアの向上により、公開キーから秘密キーを推測することが容易になっています。</span><span class="sxs-lookup"><span data-stu-id="99d5a-114">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="99d5a-115">攻撃からの保護には、より大きなキーが必要です。</span><span class="sxs-lookup"><span data-stu-id="99d5a-115">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="99d5a-116">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] より前のバージョンでは任意のサイズのキー (既定のサイズは 1024 ビット) で署名する機能を提供していますが、新しいキーでアセンブリを署名すると、アセンブリの古い ID を参照しているすべてのバイナリが動作しなくなります。</span><span class="sxs-lookup"><span data-stu-id="99d5a-116">.NET Framework versions before the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="99d5a-117">したがって、互換性を維持する場合には、署名キーのサイズの更新は非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="99d5a-117">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
-   <span data-ttu-id="99d5a-118">厳密な名前の署名は SHA-1 アルゴリズムのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="99d5a-118">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="99d5a-119">SHA-1 は、最近、セキュリティが強化されたハッシュ アプリケーションのためには不十分であることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="99d5a-119">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="99d5a-120">したがって、より強力なアルゴリズム (SHA-256 以上) が必要です。</span><span class="sxs-lookup"><span data-stu-id="99d5a-120">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="99d5a-121">SHA-1 は FIPS 準拠の地位を失う可能性があり、これによって FIPS 準拠のソフトウェアとアルゴリズムのみを選択して使用しているユーザーには問題が生じることになります。</span><span class="sxs-lookup"><span data-stu-id="99d5a-121">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="99d5a-122">強化された厳密な名前の利点</span><span class="sxs-lookup"><span data-stu-id="99d5a-122">Advantages of Enhanced Strong Names</span></span>  
 <span data-ttu-id="99d5a-123">強化された厳密な名前の主な利点は、既存の厳密な名前との互換性と、ある ID が別の ID と等価であることを指定できる機能です。</span><span class="sxs-lookup"><span data-stu-id="99d5a-123">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
-   <span data-ttu-id="99d5a-124">既存の署名付きアセンブリを持つ開発者は、以前の ID を参照するアセンブリとの互換性を保ちながら、それらのアセンブリの ID を SHA-2 アルゴリズムに移行できます。</span><span class="sxs-lookup"><span data-stu-id="99d5a-124">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
-   <span data-ttu-id="99d5a-125">新しいアセンブリを作成する際に、既存の厳密な名前の署名を考慮する必要のない開発者は、より安全な SHA-2 アルゴリズムを使用して、今までどおりにアセンブリに署名できます。</span><span class="sxs-lookup"><span data-stu-id="99d5a-125">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="using-enhanced-strong-names"></a><span data-ttu-id="99d5a-126">強化された厳密な名前の使用</span><span class="sxs-lookup"><span data-stu-id="99d5a-126">Using Enhanced Strong Names</span></span>  
 <span data-ttu-id="99d5a-127">厳密な名前のキーは署名キーと ID のキーで構成されます。</span><span class="sxs-lookup"><span data-stu-id="99d5a-127">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="99d5a-128">アセンブリは署名キーで署名され、ID キーで識別されます。</span><span class="sxs-lookup"><span data-stu-id="99d5a-128">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="99d5a-129">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] より前では、これらの 2 つのキーは同一です。</span><span class="sxs-lookup"><span data-stu-id="99d5a-129">Prior to the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], these two keys were identical.</span></span> <span data-ttu-id="99d5a-130">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、ID キーは、.NET Framework の以前のバージョンと同じですが、署名キーは、より強力なハッシュ アルゴリズムを備えています。</span><span class="sxs-lookup"><span data-stu-id="99d5a-130">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="99d5a-131">さらに、副署名を作成するために、署名キーは ID キーで署名されます。</span><span class="sxs-lookup"><span data-stu-id="99d5a-131">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="99d5a-132"><xref:System.Reflection.AssemblySignatureKeyAttribute> 属性によって、アセンブリのメタデータはアセンブリの ID に既存の公開キーを使用することができ、これによって、古いアセンブリ参照は引き続き動作します。</span><span class="sxs-lookup"><span data-stu-id="99d5a-132">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="99d5a-133"><xref:System.Reflection.AssemblySignatureKeyAttribute> の属性は副署名を使用して、新しい署名キーの所有者が古い ID キーの所有者にもなるようにします。</span><span class="sxs-lookup"><span data-stu-id="99d5a-133">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="signing-with-sha-2-without-key-migration"></a><span data-ttu-id="99d5a-134">キー移行を伴わない SHA-2 による署名</span><span class="sxs-lookup"><span data-stu-id="99d5a-134">Signing with SHA-2, Without Key Migration</span></span>  
 <span data-ttu-id="99d5a-135">厳密な名前の署名を移行せずにアセンブリに署名するには、コマンド プロンプト ウィンドウから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="99d5a-135">Run the following commands from a Command Prompt window to sign an assembly without migrating a strong name signature:</span></span>  
  
1.  <span data-ttu-id="99d5a-136">新しい ID キーを生成します (必要な場合)。</span><span class="sxs-lookup"><span data-stu-id="99d5a-136">Generate the new identity key (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  <span data-ttu-id="99d5a-137">ID の公開キーを抽出し、このキーで署名する場合に SHA-2 アルゴリズムを使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="99d5a-137">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="99d5a-138">ID 公開キー ファイルで、アセンブリに遅延署名します。</span><span class="sxs-lookup"><span data-stu-id="99d5a-138">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  <span data-ttu-id="99d5a-139">完全な ID キーのペアでアセンブリに再署名します。</span><span class="sxs-lookup"><span data-stu-id="99d5a-139">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a><span data-ttu-id="99d5a-140">キー移行を伴う SHA-2 による署名</span><span class="sxs-lookup"><span data-stu-id="99d5a-140">Signing with SHA-2, with Key Migration</span></span>  
 <span data-ttu-id="99d5a-141">移行した厳密な名前の署名でアセンブリに署名するには、コマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="99d5a-141">Run the following commands from a Command Prompt window to sign an assembly with a migrated strong name signature.</span></span>  
  
1.  <span data-ttu-id="99d5a-142">ID キーと署名キーのペアを生成します (必要な場合)。</span><span class="sxs-lookup"><span data-stu-id="99d5a-142">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  <span data-ttu-id="99d5a-143">署名の公開キーを抽出し、このキーで署名する場合に SHA-2 アルゴリズムを使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="99d5a-143">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  <span data-ttu-id="99d5a-144">副署名を生成するハッシュ アルゴリズムを決定する ID の公開キーを抽出します。</span><span class="sxs-lookup"><span data-stu-id="99d5a-144">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  <span data-ttu-id="99d5a-145"><xref:System.Reflection.AssemblySignatureKeyAttribute> の属性のパラメーターを生成し、アセンブリに属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="99d5a-145">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```  
    sn -ac IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  
  
5.  <span data-ttu-id="99d5a-146">ID 公開キーでアセンブリに遅延署名します。</span><span class="sxs-lookup"><span data-stu-id="99d5a-146">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  <span data-ttu-id="99d5a-147">完全な署名キーのペアでアセンブリに署名します。</span><span class="sxs-lookup"><span data-stu-id="99d5a-147">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="99d5a-148">参照</span><span class="sxs-lookup"><span data-stu-id="99d5a-148">See Also</span></span>  
 [<span data-ttu-id="99d5a-149">厳密な名前付きアセンブリの作成と使用</span><span class="sxs-lookup"><span data-stu-id="99d5a-149">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
