---
title: '方法 : 署名の検証に使用する証明機関の証明書チェーンを指定する (WCF)'
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
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29637ea7f0a1e533a6735ebfa6f428fe20039e48
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a><span data-ttu-id="fd511-102">方法 : 署名の検証に使用する証明機関の証明書チェーンを指定する (WCF)</span><span class="sxs-lookup"><span data-stu-id="fd511-102">How to: Specify the Certificate Authority Certificate Chain Used to Verify Signatures (WCF)</span></span>
<span data-ttu-id="fd511-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は、X.509 証明書を使用して署名された SOAP メッセージを受信すると、その X.509 証明書が信頼された証明機関によって発行されたものかどうかを既定で検証します。</span><span class="sxs-lookup"><span data-stu-id="fd511-103">When [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] receives a SOAP message signed using an X.509 certificate, by default it verifies that the X.509 certificate was issued by a trusted certification authority.</span></span> <span data-ttu-id="fd511-104">これは、証明書ストアを検索し、その証明機関の証明書が信頼された証明書として指定されているかどうかを確認することによって行われます。</span><span class="sxs-lookup"><span data-stu-id="fd511-104">This is done by looking in a certificate store and determining if the certificate for that certification authority has been designated as trusted.</span></span> <span data-ttu-id="fd511-105">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でこれを確認するには、証明機関証明書チェーンを適切な証明書ストアにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd511-105">In order for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to make this determination, the certification authority certificate chain must be installed in the correct certificate store.</span></span>  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a><span data-ttu-id="fd511-106">証明機関証明書チェーンをインストールするには</span><span class="sxs-lookup"><span data-stu-id="fd511-106">To install a certification authority certificate chain</span></span>  
  
-   <span data-ttu-id="fd511-107">SOAP メッセージの受信者が信頼する必要のある X.509 証明書の発行元の各証明機関について、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で X.509 証明書の取得元として構成されている証明書ストアに、証明機関証明書チェーンをインストールします。</span><span class="sxs-lookup"><span data-stu-id="fd511-107">For each certification authority that a SOAP message recipient intends to trust X.509 certificates issued from, install the certification authority certificate chain into the certificate store that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is configured to retrieve X.509 certificates from.</span></span>  
  
     <span data-ttu-id="fd511-108">たとえば、SOAP メッセージの受信者がマイクロソフトによって発行された X.509 証明書を信頼する必要がある場合は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] で X.509 証明書の検索先として設定されている証明書ストアに、マイクロソフトの証明機関証明書チェーンをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fd511-108">For instance, if a SOAP message recipient intends to trust X.509 certificates issued by Microsoft, the certification authority certificate chain for Microsoft must be installed in the certificate store that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is set up to look for X.509 certificates from.</span></span> <span data-ttu-id="fd511-109">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が X.509 証明書を検索する証明書ストアは、コードまたは構成で指定できます。</span><span class="sxs-lookup"><span data-stu-id="fd511-109">The certificate store in which [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] looks for X.509 certificates can be specified in code or configuration.</span></span> <span data-ttu-id="fd511-110">これを使用してコードで指定するなど、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>メソッドまたは構成など、いくつかの方法で、 [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="fd511-110">For example, this can be specified in code using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method or in configuration a few ways, including the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .</span></span>  
  
     <span data-ttu-id="fd511-111">Windows には、信頼された証明機関の既定の証明書チェーンのセットが用意されているため、一部の CA については証明書チェーンをインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="fd511-111">Because Windows ships with a set of default certificate chains for trusted certificate authorities, it may not be necessary to install the certificate chain for all certificate authorities.</span></span>  
  
    1.  <span data-ttu-id="fd511-112">証明機関証明書チェーンをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="fd511-112">Export the certification authority certificate chain.</span></span>  
  
         <span data-ttu-id="fd511-113">正確なエクスポート方法は、証明機関によって異なります。</span><span class="sxs-lookup"><span data-stu-id="fd511-113">Exactly how this is done depends on the certification authority.</span></span> <span data-ttu-id="fd511-114">証明機関で Microsoft 証明書サービスが実行されている場合は、選択**CA 証明書、証明書チェーン、または CRL のダウンロード**を選択し**ダウンロードの CA 証明書**です。</span><span class="sxs-lookup"><span data-stu-id="fd511-114">If the certification authority is running Microsoft Certificate Services, select **Download a CA certificate, certificate chain, or CRL**, and then choose **Download CA certificate**.</span></span>  
  
    2.  <span data-ttu-id="fd511-115">証明機関証明書チェーンをインポートします。</span><span class="sxs-lookup"><span data-stu-id="fd511-115">Import the certification authority certificate chain.</span></span>  
  
         <span data-ttu-id="fd511-116">Microsoft 管理コンソール (MMC: Microsoft Management Console) で、証明書スナップインを開きます。</span><span class="sxs-lookup"><span data-stu-id="fd511-116">In the Microsoft Management Console (MMC), open the Certificates snap-in.</span></span> <span data-ttu-id="fd511-117">証明書のストアが[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]選択から X.509 証明書を取得するように構成、**の信頼されたルート****証明機関**フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="fd511-117">For the certificate store that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is configured to retrieve X.509 certificates from, select the **Trusted Root** **Certification Authorities**folder.</span></span> <span data-ttu-id="fd511-118">下にある、**信頼されたルート証明機関**フォルダーを右クリックし、**証明書**フォルダーをポイント**すべてのタスク**、順にクリック**インポート**.</span><span class="sxs-lookup"><span data-stu-id="fd511-118">Under the **Trusted Root Certification Authorities** folder, right-click the **Certificates**folder, point to **All Tasks**, and then click **Import**.</span></span> <span data-ttu-id="fd511-119">手順 a. でエクスポートしたファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="fd511-119">Provide the file exported in step a.</span></span>  
  
         <span data-ttu-id="fd511-120">詳細については、MMC で、証明書スナップインを使用して、次を参照してください。[する方法: MMC スナップインで証明書の表示](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)です。</span><span class="sxs-lookup"><span data-stu-id="fd511-120">For more information about using the Certificates snap-in with MMC, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd511-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="fd511-121">See Also</span></span>  
 [<span data-ttu-id="fd511-122">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="fd511-122">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
