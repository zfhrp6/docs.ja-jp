---
title: '方法 : 開発中に使用する一時的な証明書を作成する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates [WCF], creating temporary certificates
- temporary certificates [WCF]
ms.assetid: bc5f6637-5513-4d27-99bb-51aad7741e4a
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f5a096fd6e052fc744af5cee1ab0d322e1daafe6
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-temporary-certificates-for-use-during-development"></a><span data-ttu-id="f46aa-102">方法 : 開発中に使用する一時的な証明書を作成する</span><span class="sxs-lookup"><span data-stu-id="f46aa-102">How to: Create Temporary Certificates for Use During Development</span></span>
<span data-ttu-id="f46aa-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]を使ってセキュリティ保護されたサービスやクライアントを開発する場合、資格情報として使えるように X.509 証明書を提供する必要が生じることも少なくありません。</span><span class="sxs-lookup"><span data-stu-id="f46aa-103">When developing a secure service or client using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], it is often necessary to supply an X.509 certificate to be used as a credential.</span></span> <span data-ttu-id="f46aa-104">証明書は通常、単独ではなく、いくつもの証明書が信頼チェーンとしてつながった形で存在しており、その最上位に位置するルート証明機関の証明書は、各コンピューターの [信頼されたルート証明機関] の証明書ストアに格納されています。</span><span class="sxs-lookup"><span data-stu-id="f46aa-104">The certificate typically is part of a chain of certificates with a root authority found in the Trusted Root Certification Authorities store of the computer.</span></span> <span data-ttu-id="f46aa-105">証明書を調べて順に信頼チェーンをたどっていくと、たとえば所属する会社や事業部門が運営する、ルート証明機関に到達します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-105">Having a certificate chain enables you to scope a set of certificates where typically the root authority is from your organization or business unit.</span></span> <span data-ttu-id="f46aa-106">開発時にこの過程をエミュレートするためには、セキュリティ要件を満たす 2 種類の証明書を作る必要があります。</span><span class="sxs-lookup"><span data-stu-id="f46aa-106">To emulate this at development time, you can create two certificates to satisfy the security requirements.</span></span> <span data-ttu-id="f46aa-107">1 つは自己署名証明書で、[信頼されたルート証明機関] の証明書ストアに配置します。もう 1 つは、先の自己署名証明書を使って署名を施した証明書で、[ローカル コンピューター] の [個人] ストア、または [現在のユーザー] の [個人] ストアに配置します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-107">The first is a self-signed certificate that is placed in the Trusted Root Certification Authorities store, and the second certificate is created from the first and is placed in either the Personal store of the Local Machine location, or the Personal store of the Current User location.</span></span> <span data-ttu-id="f46aa-108">ここでは、 [SDK に付属する](http://go.microsoft.com/fwlink/?LinkId=248185)証明書作成ツール (MakeCert.exe) [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] を使用して、これら 2 つの証明書を作成する手順を示します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-108">This topic walks through the steps to create these two certificates using the [Certificate Creation Tool (MakeCert.exe)](http://go.microsoft.com/fwlink/?LinkId=248185), which is provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f46aa-109">証明書作成ツールによって作成された証明書は、テスト目的にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f46aa-109">The certificates the Certification Creation tool generates are provided for testing purposes only.</span></span> <span data-ttu-id="f46aa-110">実際にサービスやクライアントを業務に使用する際には、証明機関から取得した、適切な証明書が必要です。</span><span class="sxs-lookup"><span data-stu-id="f46aa-110">When deploying a service or client, be sure to use an appropriate certificate provided by a certification authority.</span></span> <span data-ttu-id="f46aa-111">所属する会社が運営している [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 証明書サーバー、または専門の第三者機関から取得してください。</span><span class="sxs-lookup"><span data-stu-id="f46aa-111">This could either be from a [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] certificate server in your organization or a third party.</span></span>  
>   
>  <span data-ttu-id="f46aa-112">既定では、 [Makecert.exe (証明書作成ツール)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)がルート証明機関と呼ばれる証明書を作成"Root Agency **"。**</span><span class="sxs-lookup"><span data-stu-id="f46aa-112">By default, the [Makecert.exe (Certificate Creation Tool)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d) creates certificates whose root authority is called "Root Agency **."**</span></span> <span data-ttu-id="f46aa-113">というルート証明機関の証明書を作成します。"Root Agency" は、[信頼されたルート証明機関] の証明書ストアに含まれていないため、作成された証明書はセキュリティで保護されません。</span><span class="sxs-lookup"><span data-stu-id="f46aa-113">Because the "Root Agency" is not in the Trusted Root Certification Authorities store, this makes these certificates insecure.</span></span> <span data-ttu-id="f46aa-114">そこで自己署名証明書を作り、[信頼されたルート証明機関] の証明書ストアに置くことにより、実際の運用環境をより忠実にシミュレートする開発環境を構築できます。</span><span class="sxs-lookup"><span data-stu-id="f46aa-114">Creating a self-signed certificate that is placed in the Trusted Root Certification Authorities store enables you to create a development environment that more closely simulates your deployment environment.</span></span>  
  
 <span data-ttu-id="f46aa-115">作成して、証明書の使用に関する詳細については、次を参照してください。[証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)です。</span><span class="sxs-lookup"><span data-stu-id="f46aa-115">For more information about creating and using certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="f46aa-116">詳細については、資格情報として証明書を使用して、次を参照してください。 [Services のセキュリティ保護とクライアント](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)です。</span><span class="sxs-lookup"><span data-stu-id="f46aa-116">For more information about using a certificate as a credential, see [Securing Services and Clients](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="f46aa-117">Microsoft Authenticode テクノロジの使用方法については、「 [Authenticode Overviews and Tutorials (Authenticode の概要とチュートリアル)](http://go.microsoft.com/fwlink/?LinkId=88919)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f46aa-117">For a tutorial about using Microsoft Authenticode technology, see [Authenticode Overviews and Tutorials](http://go.microsoft.com/fwlink/?LinkId=88919).</span></span>  
  
### <a name="to-create-a-self-signed-root-authority-certificate-and-export-the-private-key"></a><span data-ttu-id="f46aa-118">自己署名ルート証明書を作成して秘密キーをエクスポートするには</span><span class="sxs-lookup"><span data-stu-id="f46aa-118">To create a self-signed root authority certificate and export the private key</span></span>  
  
1.  <span data-ttu-id="f46aa-119">次のスイッチを指定して MakeCert.exe ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-119">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="f46aa-120">`-n` `subjectName`。</span><span class="sxs-lookup"><span data-stu-id="f46aa-120">`-n` `subjectName`.</span></span> <span data-ttu-id="f46aa-121">サブジェクト名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-121">Specifies the subject name.</span></span> <span data-ttu-id="f46aa-122">命名規則では、サブジェクト名の前に、"Common Name" を示す "CN = " を付加します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-122">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    2.  <span data-ttu-id="f46aa-123">`-r`。</span><span class="sxs-lookup"><span data-stu-id="f46aa-123">`-r`.</span></span> <span data-ttu-id="f46aa-124">証明書が自己署名されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-124">Specifies that the certificate will be self-signed.</span></span>  
  
    3.  <span data-ttu-id="f46aa-125">`-sv` `privateKeyFile`。</span><span class="sxs-lookup"><span data-stu-id="f46aa-125">`-sv` `privateKeyFile`.</span></span> <span data-ttu-id="f46aa-126">秘密キーを書き出すファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-126">Specifies the file that contains the private key container.</span></span>  
  
     <span data-ttu-id="f46aa-127">たとえば次のコマンドを実行すると、サブジェクト名を "CN=TempCA" とした自己署名証明書が作成されます。</span><span class="sxs-lookup"><span data-stu-id="f46aa-127">For example, the following command creates a self-signed certificate with a subject name of "CN=TempCA."</span></span>  
  
    ```  
    makecert -n "CN=TempCA" -r -sv TempCA.pvk TempCA.cer  
    ```  
  
     <span data-ttu-id="f46aa-128">秘密キーを保護するためのパスワードを入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="f46aa-128">You will be prompted to provide a password to protect the private key.</span></span> <span data-ttu-id="f46aa-129">このパスワードは、このルート証明書によって署名された証明書を作成する際に必要になります。</span><span class="sxs-lookup"><span data-stu-id="f46aa-129">This password is required when creating a certificate signed by this root certificate.</span></span>  
  
### <a name="to-create-a-new-certificate-signed-by-a-root-authority-certificate"></a><span data-ttu-id="f46aa-130">ルート証明書によって署名された新しい証明書を作成するには</span><span class="sxs-lookup"><span data-stu-id="f46aa-130">To create a new certificate signed by a root authority certificate</span></span>  
  
1.  <span data-ttu-id="f46aa-131">次のスイッチを指定して MakeCert.exe ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-131">Use the MakeCert.exe tool with the following switches:</span></span>  
  
    1.  <span data-ttu-id="f46aa-132">`-sk` `subjectKey`。</span><span class="sxs-lookup"><span data-stu-id="f46aa-132">`-sk` `subjectKey`.</span></span> <span data-ttu-id="f46aa-133">秘密キーを格納する、サブジェクトのキー コンテナーの位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-133">The location of the subject's key container that holds the private key.</span></span> <span data-ttu-id="f46aa-134">キー コンテナーが存在しない場合は、作成されます。</span><span class="sxs-lookup"><span data-stu-id="f46aa-134">If a key container does not exist, one is created.</span></span> <span data-ttu-id="f46aa-135">-sk も -sv も指定しなかった場合、既定で JoeSoft という名前のキー コンテナーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f46aa-135">If neither of the -sk or -sv options is used, a key container called JoeSoft is created by default.</span></span>  
  
    2.  <span data-ttu-id="f46aa-136">`-n` `subjectName`。</span><span class="sxs-lookup"><span data-stu-id="f46aa-136">`-n` `subjectName`.</span></span> <span data-ttu-id="f46aa-137">サブジェクト名を指定します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-137">Specifies the subject name.</span></span> <span data-ttu-id="f46aa-138">命名規則では、サブジェクト名の前に、"Common Name" を示す "CN = " を付加します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-138">The convention is to prefix the subject name with "CN = " for "Common Name".</span></span>  
  
    3.  <span data-ttu-id="f46aa-139">`-iv` `issuerKeyFile`。</span><span class="sxs-lookup"><span data-stu-id="f46aa-139">`-iv` `issuerKeyFile`.</span></span> <span data-ttu-id="f46aa-140">発行元の秘密キー ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-140">Specifies the issuer's private key file.</span></span>  
  
    4.  <span data-ttu-id="f46aa-141">`-ic` `issuerCertFile`。</span><span class="sxs-lookup"><span data-stu-id="f46aa-141">`-ic` `issuerCertFile`.</span></span> <span data-ttu-id="f46aa-142">発行元の証明書の位置を指定します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-142">Specifies the location of the issuer's certificate.</span></span>  
  
     <span data-ttu-id="f46aa-143">たとえば、次のコマンドを実行すると、サブジェクト名が `TempCA` で、発行元の秘密キーを使用する証明書が作成されます。ルート証明機関 `"CN=SignedByCA"` の証明書を使って署名されます。</span><span class="sxs-lookup"><span data-stu-id="f46aa-143">For example, the following command creates a certificate signed by the `TempCA` root authority certificate with a subject name of `"CN=SignedByCA"` using the private key of the issuer.</span></span>  
  
    ```  
    makecert -sk SignedByCA -iv TempCA.pvk -n "CN=SignedByCA" -ic TempCA.cer SignedByCA.cer -sr currentuser -ss My  
    ```  
  
## <a name="installing-a-certificate-in-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="f46aa-144">信頼されたルート証明機関の証明書ストアに証明書をインストールする</span><span class="sxs-lookup"><span data-stu-id="f46aa-144">Installing a Certificate in the Trusted Root Certification Authorities Store</span></span>  
 <span data-ttu-id="f46aa-145">作成された自己署名証明書は、[信頼されたルート証明機関] の証明書ストアにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="f46aa-145">Once a self-signed certificate is created, you can install it in the Trusted Root Certification Authorities store.</span></span> <span data-ttu-id="f46aa-146">この証明書で署名された証明書は、この時点で信頼できるものと見なされるようになります。</span><span class="sxs-lookup"><span data-stu-id="f46aa-146">Any certificates that are signed with the certificate at this point are trusted by the computer.</span></span> <span data-ttu-id="f46aa-147">したがって、この証明書が不要になった場合は、直ちに証明書ストアから削除してください。</span><span class="sxs-lookup"><span data-stu-id="f46aa-147">For this reason, delete the certificate from the store as soon as you no longer need it.</span></span> <span data-ttu-id="f46aa-148">この証明書を削除すると、それを使って署名した証明書は認証されなくなります。</span><span class="sxs-lookup"><span data-stu-id="f46aa-148">When you delete this root authority certificate, all other certificates that signed with it become unauthorized.</span></span> <span data-ttu-id="f46aa-149">ルート証明機関の証明書は、必要に応じて一連の証明書を有効化する手段の 1 つにすぎません。</span><span class="sxs-lookup"><span data-stu-id="f46aa-149">Root authority certificates are simply a mechanism whereby a group of certificates can be scoped as necessary.</span></span> <span data-ttu-id="f46aa-150">たとえばピアツーピア アプリケーションの場合、証明書が提示されれば相手の識別情報を信頼できるので、ルート証明機関は必要ないのが普通です。</span><span class="sxs-lookup"><span data-stu-id="f46aa-150">For example, in peer-to-peer applications, there is typically no need for a root authority because you simply trust the identity of an individual by its supplied certificate.</span></span>  
  
#### <a name="to-install-a-self-signed-certificate-in-the-trusted-root-certification-authorities"></a><span data-ttu-id="f46aa-151">自己署名証明書を信頼されたルート証明機関としてインストールするには</span><span class="sxs-lookup"><span data-stu-id="f46aa-151">To install a self-signed certificate in the Trusted Root Certification Authorities</span></span>  
  
1.  <span data-ttu-id="f46aa-152">証明書スナップインを開きます。</span><span class="sxs-lookup"><span data-stu-id="f46aa-152">Open the certificate snap-in.</span></span> <span data-ttu-id="f46aa-153">詳細については、次を参照してください。[する方法: MMC スナップインで証明書の表示](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)です。</span><span class="sxs-lookup"><span data-stu-id="f46aa-153">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2.  <span data-ttu-id="f46aa-154">証明書の格納先となる、 **[ローカル コンピューター]** または **[現在のユーザー]** のフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f46aa-154">Open the folder to store the certificate, either the **Local Computer** or the **Current User**.</span></span>  
  
3.  <span data-ttu-id="f46aa-155">**[信頼されたルート証明機関]** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="f46aa-155">Open the **Trusted Root Certification Authorities** folder.</span></span>  
  
4.  <span data-ttu-id="f46aa-156">**[証明書]** フォルダーを右クリックして、 **[すべてのタスク]** メニューの **[インポート]** を実行します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-156">Right-click the **Certificates** folder and click **All Tasks**, then click **Import**.</span></span>  
  
5.  <span data-ttu-id="f46aa-157">ウィザード画面が開くので、その指示に従って TempCa.cer を証明書ストアにインポートしてください。</span><span class="sxs-lookup"><span data-stu-id="f46aa-157">Follow the on-screen wizard instructions to import the TempCa.cer into the store.</span></span>  
  
## <a name="using-certificates-with-wcf"></a><span data-ttu-id="f46aa-158">WCF で証明書を使用する</span><span class="sxs-lookup"><span data-stu-id="f46aa-158">Using Certificates With WCF</span></span>  
 <span data-ttu-id="f46aa-159">一時的な証明書を設定したら、それを使用して、クライアント資格情報の種類として証明書を指定する WCF ソリューションを開発できます。</span><span class="sxs-lookup"><span data-stu-id="f46aa-159">Once you have set up the temporary certificates, you can use them to develop WCF solutions that specify certificates as a client credential type.</span></span> <span data-ttu-id="f46aa-160">たとえば、次の XML 構成では、メッセージ セキュリティを設定して、クライアント資格情報の種類として証明書を指定しています。</span><span class="sxs-lookup"><span data-stu-id="f46aa-160">For example, the following XML configuration specifies message security and a certificate as the client credential type.</span></span>  
  
#### <a name="to-specify-a-certificate-as-the-client-credential-type"></a><span data-ttu-id="f46aa-161">クライアント資格情報の種類として証明書を指定するには</span><span class="sxs-lookup"><span data-stu-id="f46aa-161">To specify a certificate as the client credential type</span></span>  
  
-   <span data-ttu-id="f46aa-162">サービスの構成ファイルで、次の XML を使用して、セキュリティ モードをメッセージに、クライアント資格情報の種類を証明書に設定します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-162">In the configuration file for a service, use the following XML to set the security mode to message, and the client credential type to certificate.</span></span>  
  
    ```xml  
    <bindings>       
      <wsHttpBinding>  
        <binding name="CertificateForClient">  
          <security>  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    ```  
  
 <span data-ttu-id="f46aa-163">クライアントの構成ファイルで、証明書は、ユーザーのストアにあり、SubjectName フィールドの値「"cohowinery という」を検索することで見つかることを指定するのに次の XML を使用します。</span><span class="sxs-lookup"><span data-stu-id="f46aa-163">In the configuration file for a client, use the following XML to specify that the certificate is found in the user’s store, and can be found by searching the SubjectName field for the value "CohoWinery."</span></span>  
  
```xml  
<behaviors>  
  <endpointBehaviors>  
    <behavior name="CertForClient">  
      <clientCredentials>  
        <clientCertificate findValue="CohoWinery" x509FindType="FindBySubjectName" />  
       </clientCredentials>  
     </behavior>  
   </endpointBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="f46aa-164">WCF での証明書の使用に関する詳細については、「 [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f46aa-164">For more information about using certificates in WCF, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f46aa-165">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f46aa-165">.NET Framework Security</span></span>  
 <span data-ttu-id="f46aa-166">一時的なルート証明書は、不要になったら **[信頼されたルート証明機関]** フォルダーや **[個人]** フォルダーから確実に削除してください。削除するには、証明書を右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f46aa-166">Be sure to delete any temporary root authority certificates from the **Trusted Root Certification Authorities** and **Personal** folders by right-clicking the certificate, then clicking **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f46aa-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="f46aa-167">See Also</span></span>  
 [<span data-ttu-id="f46aa-168">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="f46aa-168">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="f46aa-169">方法 : MMC スナップインを使用して証明書を参照する</span><span class="sxs-lookup"><span data-stu-id="f46aa-169">How to: View Certificates with the MMC Snap-in</span></span>](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [<span data-ttu-id="f46aa-170">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="f46aa-170">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
