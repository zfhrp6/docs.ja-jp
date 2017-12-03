---
title: "方法 : 証明書 (WCF) を取得する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b1b7ab4ed91487965ac8b0d78a9a44818cfee9eb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-obtain-a-certificate-wcf"></a><span data-ttu-id="286fe-102">方法 : 証明書 (WCF) を取得する</span><span class="sxs-lookup"><span data-stu-id="286fe-102">How to: Obtain a Certificate (WCF)</span></span>
<span data-ttu-id="286fe-103">X.509 証明書を使用する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] の機能を使用するには、最初に証明書を取得します。</span><span class="sxs-lookup"><span data-stu-id="286fe-103">To use any of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] features of that use X.509 certificates, you just first obtain certificates.</span></span>  
  
### <a name="to-obtain-an-x509-certificate"></a><span data-ttu-id="286fe-104">X.509 証明書を取得するには</span><span class="sxs-lookup"><span data-stu-id="286fe-104">To obtain an X.509 certificate</span></span>  
  
1.  <span data-ttu-id="286fe-105">次のいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="286fe-105">Choose one of the following:</span></span>  
  
    -   <span data-ttu-id="286fe-106">VeriSign, Inc. などの証明機関から証明書を購入します。</span><span class="sxs-lookup"><span data-stu-id="286fe-106">Purchase a certificate from a certification authority, such as VeriSign, Inc.</span></span>  
  
    -   <span data-ttu-id="286fe-107">独自の証明書サービスを設定し、証明機関に証明書への署名を依頼します。</span><span class="sxs-lookup"><span data-stu-id="286fe-107">Set up your own certificate service and have a certification authority sign the certificates.</span></span> [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]<span data-ttu-id="286fe-108">、Windows 2000 Server、Windows 2000 Server Datacenter、および Windows 2000 Datacenter Server にはすべて、公開キー基盤 (PKI) をサポートする証明書サービスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="286fe-108">, Windows 2000 Server, Windows 2000 Server Datacenter, and Windows 2000 Datacenter Server all include certificate services that support public key infrastructure (PKI).</span></span> <span data-ttu-id="286fe-109">Windows Server 2008 を使用して、 [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483)証明機関を管理するロール。</span><span class="sxs-lookup"><span data-stu-id="286fe-109">In Windows Server 2008, use the [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkID=153483) role to manage a certification authority.</span></span>  
  
    -   <span data-ttu-id="286fe-110">独自の証明書サービスを設定し、証明書には署名しません。</span><span class="sxs-lookup"><span data-stu-id="286fe-110">Set up your own certificate service and do not have the certificates signed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="286fe-111">どの方法を使用する場合でも、X.509 証明書を含む SOAP 要求の受信者は、その X.509 証明書を信頼する必要があります。</span><span class="sxs-lookup"><span data-stu-id="286fe-111">Whichever approach you take, the recipient of the SOAP request that contains the X.509 certificate must trust the X.509 certificate.</span></span> <span data-ttu-id="286fe-112">つまり、証明書チェーン内の X.509 証明書または発行者は、信頼されたユーザーの証明書ストア内に存在し、また X.509 証明書は信頼されない証明書ストア内には存在しないということを意味します。</span><span class="sxs-lookup"><span data-stu-id="286fe-112">This means that the X.509 certificate or an issuer in the certificate chain is in the Trusted People certificate store and that the X.509 certificate is not in the Untrusted Certificates store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="286fe-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="286fe-113">See Also</span></span>  
 [<span data-ttu-id="286fe-114">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="286fe-114">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="286fe-115">方法: 開発中に使用するための一時的な証明書を作成</span><span class="sxs-lookup"><span data-stu-id="286fe-115">How to: Create Temporary Certificates for Use During Development</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
