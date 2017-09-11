---
title: "Certmgr.exe (証明書マネージャー ツール)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
caps.latest.revision: 27
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bd5d1011a8f8aeadfc7729c3a4f6f56a033110a9
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="certmgrexe-certificate-manager-tool"></a><span data-ttu-id="82149-102">Certmgr.exe (証明書マネージャー ツール)</span><span class="sxs-lookup"><span data-stu-id="82149-102">Certmgr.exe (Certificate Manager Tool)</span></span>
<span data-ttu-id="82149-103">証明書マネージャー ツール (Certmgr.exe) は、証明書、証明書信頼リスト (CTL: Certificate Trust List)、および証明書失効リスト (CRL: Certificate Revocation List) を管理します。</span><span class="sxs-lookup"><span data-stu-id="82149-103">The Certificate Manager tool (Certmgr.exe) manages certificates, certificate trust lists (CTLs), and certificate revocation lists (CRLs).</span></span>  
  
 <span data-ttu-id="82149-104">証明書マネージャーは Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="82149-104">The Certificate Manager is automatically installed with Visual Studio.</span></span> <span data-ttu-id="82149-105">ツールを開始するには、[Visual Studio 用開発者コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="82149-105">To start the tool, use the [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82149-106">証明書マネージャー ツール (Certmgr.exe) はコマンド ライン ユーティリティですが、証明書 (Certmgr.msc) は Microsoft 管理コンソール (MMC: Microsoft Management Console) スナップインです。</span><span class="sxs-lookup"><span data-stu-id="82149-106">The Certificate Manager tool (Certmgr.exe) is a command-line utility, whereas Certificates (Certmgr.msc) is a Microsoft Management Console (MMC) snap-in.</span></span> <span data-ttu-id="82149-107">通常、Certmgr.msc は Windows のシステム ディレクトリにあるので、コマンド ラインで「`certmgr`」と入力すると、Visual Studio コマンド プロンプトを開いていた場合でも証明書 MMC スナップインが読み込まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="82149-107">Because Certmgr.msc is usually found in the Windows System directory, entering `certmgr` at the command line may load the Certificates MMC snap-in even if you have opened the Visual Studio Command Prompt.</span></span> <span data-ttu-id="82149-108">これは、PATH 環境変数で、スナップインのパスが証明書マネージャー ツールのパスよりも前に指定されているためです。</span><span class="sxs-lookup"><span data-stu-id="82149-108">This occurs because the path to the snap-in precedes the path to the Certificate Manager tool in the PATH environment variable.</span></span> <span data-ttu-id="82149-109">この問題が発生した場合は、実行可能ファイルのパスを指定して Certmgr.exe コマンドを実行できます。</span><span class="sxs-lookup"><span data-stu-id="82149-109">If you encounter this problem, you can execute Certmgr.exe commands by specifying the path to the executable.</span></span>  
  
 <span data-ttu-id="82149-110">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="82149-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="82149-111">このツールを実行するには、開発者コマンド プロンプト (または、Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="82149-111">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="82149-112">詳細については、「[Visual Studio 用開発者コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82149-112">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="82149-113">X.509 証明書の概要については、「[証明書の使用](../../../docs/framework/wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82149-113">For an overview of X.509 certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
 <span data-ttu-id="82149-114">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="82149-114">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82149-115">構文</span><span class="sxs-lookup"><span data-stu-id="82149-115">Syntax</span></span>  
  
```  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82149-116">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82149-116">Parameters</span></span>  
  
|<span data-ttu-id="82149-117">引数</span><span class="sxs-lookup"><span data-stu-id="82149-117">Argument</span></span>|<span data-ttu-id="82149-118">説明</span><span class="sxs-lookup"><span data-stu-id="82149-118">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="82149-119">*sourceStorename*</span><span class="sxs-lookup"><span data-stu-id="82149-119">*sourceStorename*</span></span>|<span data-ttu-id="82149-120">追加、削除、保存、または表示する既存の証明書、CTL、または CRL を含む証明書ストア。</span><span class="sxs-lookup"><span data-stu-id="82149-120">The certificate store that contains the existing certificates, CTLs, or CRLs to add, delete, save, or display.</span></span> <span data-ttu-id="82149-121">ストア ファイルまたはシステム ストアを指定できます。</span><span class="sxs-lookup"><span data-stu-id="82149-121">This can be a store file or a systems store.</span></span>|  
|<span data-ttu-id="82149-122">*destinationStorename*</span><span class="sxs-lookup"><span data-stu-id="82149-122">*destinationStorename*</span></span>|<span data-ttu-id="82149-123">出力証明書ストアまたはファイル。</span><span class="sxs-lookup"><span data-stu-id="82149-123">The output certificate store or file.</span></span>|  
  
|<span data-ttu-id="82149-124">オプション</span><span class="sxs-lookup"><span data-stu-id="82149-124">Option</span></span>|<span data-ttu-id="82149-125">説明</span><span class="sxs-lookup"><span data-stu-id="82149-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="82149-126">**/add**</span><span class="sxs-lookup"><span data-stu-id="82149-126">**/add**</span></span>|<span data-ttu-id="82149-127">証明書、CTL、および CRL を証明書ストアに追加します。</span><span class="sxs-lookup"><span data-stu-id="82149-127">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>|  
|<span data-ttu-id="82149-128">**/all**</span><span class="sxs-lookup"><span data-stu-id="82149-128">**/all**</span></span>|<span data-ttu-id="82149-129">**/add** を指定して使用した場合は、すべてのエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="82149-129">Adds all entries when used with **/add**.</span></span> <span data-ttu-id="82149-130">**/del** を指定して使用した場合は、すべてのエントリを削除します。</span><span class="sxs-lookup"><span data-stu-id="82149-130">Deletes all entries when used with **/del**.</span></span> <span data-ttu-id="82149-131">**/add**、**/del** のいずれのオプションも指定せずに使用した場合は、すべてのエントリを表示します。</span><span class="sxs-lookup"><span data-stu-id="82149-131">Displays all entries when used without the **/add** or **/del** options.</span></span> <span data-ttu-id="82149-132">**/all** オプションは、**/put** オプションと共に指定できません。</span><span class="sxs-lookup"><span data-stu-id="82149-132">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="82149-133">**/c**</span><span class="sxs-lookup"><span data-stu-id="82149-133">**/c**</span></span>|<span data-ttu-id="82149-134">**/add** を指定して使用した場合は、証明書を追加します。</span><span class="sxs-lookup"><span data-stu-id="82149-134">Adds certificates when used with **/add**.</span></span> <span data-ttu-id="82149-135">**/del** を指定して使用した場合は、証明書を削除します。</span><span class="sxs-lookup"><span data-stu-id="82149-135">Deletes certificates when used with **/del**.</span></span> <span data-ttu-id="82149-136">**/put** を指定して使用した場合は、証明書を保存します。</span><span class="sxs-lookup"><span data-stu-id="82149-136">Saves certificates when used with **/put**.</span></span> <span data-ttu-id="82149-137">**/add**、**/del**、**/put** のいずれのオプションも指定せずに使用した場合は、証明書を表示します。</span><span class="sxs-lookup"><span data-stu-id="82149-137">Displays certificates when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="82149-138">**/CRL**</span><span class="sxs-lookup"><span data-stu-id="82149-138">**/CRL**</span></span>|<span data-ttu-id="82149-139">**/add** を指定して使用した場合は、CRL を追加します。</span><span class="sxs-lookup"><span data-stu-id="82149-139">Adds CRLs when used with **/add**.</span></span> <span data-ttu-id="82149-140">**/del** を指定して使用した場合は、CRL を削除します。</span><span class="sxs-lookup"><span data-stu-id="82149-140">Deletes CRLs when used with **/del**.</span></span> <span data-ttu-id="82149-141">**/put** を指定して使用した場合は、CRL を保存します。</span><span class="sxs-lookup"><span data-stu-id="82149-141">Saves CRLs when used with **/put**.</span></span> <span data-ttu-id="82149-142">**/add**、**/del**、**/put** のいずれのオプションも指定せずに使用した場合は、CRL を表示します。</span><span class="sxs-lookup"><span data-stu-id="82149-142">Displays CRLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="82149-143">**/CTL**</span><span class="sxs-lookup"><span data-stu-id="82149-143">**/CTL**</span></span>|<span data-ttu-id="82149-144">**/add** を指定して使用した場合は、CTL を追加します。</span><span class="sxs-lookup"><span data-stu-id="82149-144">Adds CTLs when used with **/add**.</span></span> <span data-ttu-id="82149-145">**/del** を指定して使用した場合は、CTL を削除します。</span><span class="sxs-lookup"><span data-stu-id="82149-145">Deletes CTLs when used with **/del**.</span></span> <span data-ttu-id="82149-146">**/put** を指定して使用した場合は、CTL を保存します。</span><span class="sxs-lookup"><span data-stu-id="82149-146">Saves CTLs when used with **/put**.</span></span> <span data-ttu-id="82149-147">**/add**、**/del**、**/put** のいずれのオプションも指定せずに使用した場合は、CTL を表示します。</span><span class="sxs-lookup"><span data-stu-id="82149-147">Displays CTLs when used without the **/add**, **/del**, or **/put** option.</span></span>|  
|<span data-ttu-id="82149-148">**/del**</span><span class="sxs-lookup"><span data-stu-id="82149-148">**/del**</span></span>|<span data-ttu-id="82149-149">証明書、CTL、および CRL を証明書ストアから削除します。</span><span class="sxs-lookup"><span data-stu-id="82149-149">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>|  
|<span data-ttu-id="82149-150">**/e** *encodingType*</span><span class="sxs-lookup"><span data-stu-id="82149-150">**/e** *encodingType*</span></span>|<span data-ttu-id="82149-151">証明書のエンコード タイプを指定します。</span><span class="sxs-lookup"><span data-stu-id="82149-151">Specifies the certificate encoding type.</span></span> <span data-ttu-id="82149-152">既定値は、`X509_ASN_ENCODING` です。</span><span class="sxs-lookup"><span data-stu-id="82149-152">The default is `X509_ASN_ENCODING`.</span></span>|  
|<span data-ttu-id="82149-153">**/f** *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="82149-153">**/f** *dwFlags*</span></span>|<span data-ttu-id="82149-154">ストア オープン フラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="82149-154">Specifies the store open flag.</span></span> <span data-ttu-id="82149-155">これは **CertOpenStore** に渡される *dwFlags* パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="82149-155">This is the *dwFlags* parameter passed to **CertOpenStore**.</span></span> <span data-ttu-id="82149-156">既定値は CERT_SYSTEM_STORE_CURRENT_USER です。</span><span class="sxs-lookup"><span data-stu-id="82149-156">The default value is CERT_SYSTEM_STORE_CURRENT_USER.</span></span> <span data-ttu-id="82149-157">このオプションは **/y** オプションを使用した場合にだけ有効です。</span><span class="sxs-lookup"><span data-stu-id="82149-157">This option is considered only if the **/y** option is used.</span></span>|  
|<span data-ttu-id="82149-158">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="82149-158">**/h**[**elp**]</span></span>|<span data-ttu-id="82149-159">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="82149-159">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="82149-160">**/n** *nam*</span><span class="sxs-lookup"><span data-stu-id="82149-160">**/n** *nam*</span></span>|<span data-ttu-id="82149-161">追加、削除、または保存する証明書の共通名を指定します。</span><span class="sxs-lookup"><span data-stu-id="82149-161">Specifies the common name of the certificate to add, delete, or save.</span></span> <span data-ttu-id="82149-162">このオプションは証明書についてだけ使用できます。CTL または CRL については使用できません。</span><span class="sxs-lookup"><span data-stu-id="82149-162">This option can only be used with certificates; it cannot be used with CTLs or CRLs.</span></span>|  
|<span data-ttu-id="82149-163">**/put**</span><span class="sxs-lookup"><span data-stu-id="82149-163">**/put**</span></span>|<span data-ttu-id="82149-164">証明書ストアに含まれている X.509 証明書、CTL、または CRL をファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="82149-164">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span> <span data-ttu-id="82149-165">ファイルは X.509 形式で保存されます。</span><span class="sxs-lookup"><span data-stu-id="82149-165">The file is saved in X.509 format.</span></span> <span data-ttu-id="82149-166">**/7** オプションを **/put** オプションと一緒に使用すると、ファイルを PKCS #7 形式で保存できます。</span><span class="sxs-lookup"><span data-stu-id="82149-166">You can use the **/7** option with the **/put** option to save the file in PKCS #7 format.</span></span> <span data-ttu-id="82149-167">**/put** オプションの後ろには、**/c**、**/CTL**、**/CRL** のいずれかのオプションを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="82149-167">The **/put** option must be followed by either **/c**, **/CTL**, or **/CRL**.</span></span> <span data-ttu-id="82149-168">**/all** オプションは、**/put** オプションと共に指定できません。</span><span class="sxs-lookup"><span data-stu-id="82149-168">The **/all** option cannot be used with **/put**.</span></span>|  
|<span data-ttu-id="82149-169">**/r** *location*</span><span class="sxs-lookup"><span data-stu-id="82149-169">**/r** *location*</span></span>|<span data-ttu-id="82149-170">システム ストアのレジストリの位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="82149-170">Identifies the registry location of the system store.</span></span> <span data-ttu-id="82149-171">このオプションは、**/s** オプションを指定した場合にだけ有効です。</span><span class="sxs-lookup"><span data-stu-id="82149-171">This option is considered only if you specify the **/s** option.</span></span> <span data-ttu-id="82149-172">*location* には、次のいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="82149-172">*location* must be one of the following:</span></span><br /><br /> <span data-ttu-id="82149-173">-   証明書ストアが HKEY_CURRENT_USER キーに含まれる場合は `currentUser` を指定します。</span><span class="sxs-lookup"><span data-stu-id="82149-173">-   `currentUser` indicates that the certificate store is under the HKEY_CURRENT_USER key.</span></span> <span data-ttu-id="82149-174">既定値です。</span><span class="sxs-lookup"><span data-stu-id="82149-174">This is the default.</span></span><br /><span data-ttu-id="82149-175">-   証明書ストアが HKEY_LOCAL_MACHINE キーに含まれる場合は `localMachine` を指定します。</span><span class="sxs-lookup"><span data-stu-id="82149-175">-   `localMachine` indicates that the certificate store is under the HKEY_LOCAL_MACHINE key.</span></span>|  
|<span data-ttu-id="82149-176">**/s**</span><span class="sxs-lookup"><span data-stu-id="82149-176">**/s**</span></span>|<span data-ttu-id="82149-177">証明書ストアがシステム ストアであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="82149-177">Indicates that the certificate store is a system store.</span></span> <span data-ttu-id="82149-178">このオプションを指定しない場合、ストアは **StoreFile** と見なされます。</span><span class="sxs-lookup"><span data-stu-id="82149-178">If you do not specify this option, the store is considered to be a **StoreFile**.</span></span>|  
|<span data-ttu-id="82149-179">**/sha1** *sha1Hash*</span><span class="sxs-lookup"><span data-stu-id="82149-179">**/sha1** *sha1Hash*</span></span>|<span data-ttu-id="82149-180">追加、削除、または保存する証明書、CTL、または CRL の SHA1 ハッシュを指定します。</span><span class="sxs-lookup"><span data-stu-id="82149-180">Specifies the SHA1 hash of the certificate, CTL, or CRL to add, delete, or save.</span></span>|  
|<span data-ttu-id="82149-181">**/v**</span><span class="sxs-lookup"><span data-stu-id="82149-181">**/v**</span></span>|<span data-ttu-id="82149-182">詳細出力モードを指定します。このモードでは、証明書、CTL、および CRL に関する詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="82149-182">Specifies verbose mode; displays detailed information about certificates, CTLs, and CRLs.</span></span> <span data-ttu-id="82149-183">このオプションは、**/add**、**/del**、または **/put** のオプションと共に指定できません。</span><span class="sxs-lookup"><span data-stu-id="82149-183">This option cannot be used with the **/add**, **/del**, or **/put** options.</span></span>|  
|<span data-ttu-id="82149-184">**/y** *provider*</span><span class="sxs-lookup"><span data-stu-id="82149-184">**/y** *provider*</span></span>|<span data-ttu-id="82149-185">ストア プロバイダー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="82149-185">Specifies the store provider name.</span></span>|  
|<span data-ttu-id="82149-186">**/7**</span><span class="sxs-lookup"><span data-stu-id="82149-186">**/7**</span></span>|<span data-ttu-id="82149-187">出力証明書ストアを PKCS #7 オブジェクトとして保存します。</span><span class="sxs-lookup"><span data-stu-id="82149-187">Saves the destination store as a PKCS #7 object.</span></span>|  
|<span data-ttu-id="82149-188">**/?**</span><span class="sxs-lookup"><span data-stu-id="82149-188">**/?**</span></span>|<span data-ttu-id="82149-189">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="82149-189">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82149-190">コメント</span><span class="sxs-lookup"><span data-stu-id="82149-190">Remarks</span></span>  
 <span data-ttu-id="82149-191">Certmgr.exe は次の基本的な機能を実行します。</span><span class="sxs-lookup"><span data-stu-id="82149-191">Certmgr.exe performs the following basic functions:</span></span>  
  
-   <span data-ttu-id="82149-192">証明書、CTL、および CRL をコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="82149-192">Displays certificates, CTLs, and CRLs to the console.</span></span>  
  
-   <span data-ttu-id="82149-193">証明書、CTL、および CRL を証明書ストアに追加します。</span><span class="sxs-lookup"><span data-stu-id="82149-193">Adds certificates, CTLs, and CRLs to a certificate store.</span></span>  
  
-   <span data-ttu-id="82149-194">証明書、CTL、および CRL を証明書ストアから削除します。</span><span class="sxs-lookup"><span data-stu-id="82149-194">Deletes certificates, CTLs, and CRLs from a certificate store.</span></span>  
  
-   <span data-ttu-id="82149-195">証明書ストアに含まれている X.509 証明書、CTL、または CRL をファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="82149-195">Saves an X.509 certificate, CTL, or CRL from a certificate store to a file.</span></span>  
  
 <span data-ttu-id="82149-196">Certmgr.exe は、**StoreFile** とシステム ストアという 2 つの種類の証明書ストアに対して機能します。</span><span class="sxs-lookup"><span data-stu-id="82149-196">Certmgr.exe works with two types of certificate stores: **StoreFile** and system store.</span></span> <span data-ttu-id="82149-197">証明書ストアの種類を指定する必要はありません。Certmgr.exe がストアの種類を識別し、適切な操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="82149-197">It is not necessary to specify the type of certificate store; Certmgr.exe can identify the store type and perform the appropriate operations.</span></span>  
  
 <span data-ttu-id="82149-198">オプションを何も指定せずに Certmgr.exe を実行すると、証明書の管理タスクの実行時に役立つ GUI を備えた certmgr.msc スナップインが起動します。これらのタスクはコマンド ラインでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="82149-198">Running Certmgr.exe without specifying any options launches the certmgr.msc snap-in, which has a GUI that helps with the certificate management tasks that are also available from the command line.</span></span> <span data-ttu-id="82149-199">この GUI には、証明書、CTL、および CRL をディスクから証明書ストアへとコピーする、インポート ウィザードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="82149-199">The GUI provides an import wizard, which copies certificates, CTLs, and CRLs from your disk to a certificate store.</span></span>  
  
 <span data-ttu-id="82149-200">次のコードをコンパイルおよび実行することによって、`sourceStorename` パラメーターおよび `destinationStorename` パラメーターについて X509Certificate ストアの名前を検索できます。</span><span class="sxs-lookup"><span data-stu-id="82149-200">You can find the names of X509Certificate stores for the `sourceStorename` and `destinationStorename` parameters by compiling and running the following code.</span></span>  
  
 <span data-ttu-id="82149-201">[!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)] [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="82149-201">[!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)] [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]</span></span>  
  
 <span data-ttu-id="82149-202">証明書の詳細については、「[証明書の使用](../../../docs/framework/wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82149-202">For more information about certificates, see [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="82149-203">例</span><span class="sxs-lookup"><span data-stu-id="82149-203">Examples</span></span>  
 <span data-ttu-id="82149-204">既定のシステム ストアである `my` を詳細出力モードで表示するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="82149-204">The following command displays a default system store called `my` with verbose output.</span></span>  
  
```  
certmgr /v /s my  
```  
  
 <span data-ttu-id="82149-205">`myFile.ext` という名前のファイルに含まれるすべての証明書を `newFile.ext` という名前の新しいファイルに追加するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="82149-205">The following command adds all the certificates in a file called `myFile.ext` to a new file called `newFile.ext`.</span></span>  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 <span data-ttu-id="82149-206">`testcert.cer` という名前のファイルに含まれる証明書をシステム ストア `my` に追加するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="82149-206">The following command adds the certificate in a file named `testcert.cer` to the `my` system store.</span></span>  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 <span data-ttu-id="82149-207">`TrustedCert.cer` という名前のファイルに含まれる証明書をルート証明書ストアに追加するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="82149-207">The following command adds the certificate in a file named `TrustedCert.cer` to the root certificate store.</span></span>  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 <span data-ttu-id="82149-208">システム ストア `myCert` に含まれていて共通名が `my` の証明書を `newCert.cer` という名前のファイルに保存するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="82149-208">The following command saves a certificate with the common name `myCert` in the `my` system store to a file called `newCert.cer`.</span></span>  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 <span data-ttu-id="82149-209">システム ストア `my` に含まれるすべての CTL を削除し、その結果得られるストアを `newStore.str` という名前のファイルに格納するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="82149-209">The following command deletes all CTLs in the `my` system store and saves the resulting store to a file called `newStore.str`.</span></span>  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 <span data-ttu-id="82149-210">システム ストア `my` に含まれる証明書をファイル `newFile` に保存するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="82149-210">The following command saves a certificate in the `my` system store in the file `newFile`.</span></span> <span data-ttu-id="82149-211">`my` から `newFile` に保存する証明書の番号を入力するためのプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="82149-211">You will be prompted to enter the certificate number from `my` to put in `newFile`.</span></span>  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a><span data-ttu-id="82149-212">関連項目</span><span class="sxs-lookup"><span data-stu-id="82149-212">See Also</span></span>  
 <span data-ttu-id="82149-213">[.NET Framework ツール](../../../docs/framework/tools/index.md) </span><span class="sxs-lookup"><span data-stu-id="82149-213">[Tools](../../../docs/framework/tools/index.md) </span></span>  
 <span data-ttu-id="82149-214">[Makecert.exe (証明書作成ツール)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) </span><span class="sxs-lookup"><span data-stu-id="82149-214">[Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) </span></span>  
 [<span data-ttu-id="82149-215">Visual Studio 用開発者コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="82149-215">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

