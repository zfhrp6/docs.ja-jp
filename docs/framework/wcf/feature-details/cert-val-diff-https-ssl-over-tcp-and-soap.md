---
title: "HTTPS、SSL Over TCP、SOAP セキュリティ間における証明書検証方法の相違点"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: certificates [WCF], validation differences
ms.assetid: 953a219f-4745-4019-9894-c70704f352e6
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 34be2fbc5b8148d7bfdeb5e5d07e5b73ac89a97e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="certificate-validation-differences-between-https-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="e2dd8-102">HTTPS、SSL Over TCP、SOAP セキュリティ間における証明書検証方法の相違点</span><span class="sxs-lookup"><span data-stu-id="e2dd8-102">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>
<span data-ttu-id="e2dd8-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、HTTP (HTTPS) または TCP を介したトランスポート層セキュリティ (TLS) だけでなく、メッセージ層 (SOAP) セキュリティでも証明書を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-103">You can use certificates in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] with message-layer (SOAP) security in addition to transport-layer security (TLS) over HTTP (HTTPS) or TCP.</span></span> <span data-ttu-id="e2dd8-104">ここでは、このような証明書の検証方法の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-104">This topic describes differences in the way such certificates are validated.</span></span>  
  
## <a name="validation-of-https-client-certificates"></a><span data-ttu-id="e2dd8-105">HTTPS クライアント証明書の検証</span><span class="sxs-lookup"><span data-stu-id="e2dd8-105">Validation of HTTPS Client Certificates</span></span>  
 <span data-ttu-id="e2dd8-106">HTTPS を使用してクライアントとサービス間で通信を行う場合、サービスに対して認証を行うためにクライアントが使用する証明書はチェーン信頼をサポートしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-106">When using HTTPS to communicate between a client and a service, the certificate that the client uses to authenticate to the service must support chain trust.</span></span> <span data-ttu-id="e2dd8-107">つまり、信頼されたルート証明機関にチェーンされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-107">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="e2dd8-108">HTTP レイヤーが発生しない場合、<xref:System.Net.WebException>メッセージで"リモート サーバーがエラーを返しました: (403) アクセス不可"。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-108">If not, the HTTP layer raises a <xref:System.Net.WebException> with the message "The remote server returned an error: (403) Forbidden."</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e2dd8-109">この例外を表示、<xref:System.ServiceModel.Security.MessageSecurityException>です。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-109"> surfaces this exception as a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span>  
  
## <a name="validation-of-https-service-certificates"></a><span data-ttu-id="e2dd8-110">HTTP サービス証明書の検証</span><span class="sxs-lookup"><span data-stu-id="e2dd8-110">Validation of HTTPS Service Certificates</span></span>  
 <span data-ttu-id="e2dd8-111">HTTPS を使用してクライアントとサービス間で通信を行う場合、サーバーが認証に使用する証明書は既定でチェーン信頼をサポートしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-111">When using HTTPS to communicate between a client and a service, the certificate that the server authenticates with must support chain trust by default.</span></span> <span data-ttu-id="e2dd8-112">つまり、信頼されたルート証明機関にチェーンされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-112">That is, it must chain to a trusted root certificate authority.</span></span> <span data-ttu-id="e2dd8-113">証明書が失効しているかどうかを確認するためのオンライン チェックは行われません。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-113">No online check is performed to see whether the certificate has been revoked.</span></span> <span data-ttu-id="e2dd8-114">この動作は、<xref:System.Net.Security.RemoteCertificateValidationCallback> コールバックを登録することによってオーバーライドできます。コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-114">You can override this behavior by registering a <xref:System.Net.Security.RemoteCertificateValidationCallback> callback, as shown in the following code.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#1)] 
 [!code-vb[c_CertificateValidationDifferences#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#1)]  
  
 <span data-ttu-id="e2dd8-115">`ValidateServerCertificate` の署名は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-115">where the signature for `ValidateServerCertificate` is as follows:</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#2)]
 [!code-vb[c_CertificateValidationDifferences#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#2)]  
  
 <span data-ttu-id="e2dd8-116">`ValidateServerCertificate` を実装すると、サービス証明書を検証するために必要であるとクライアント アプリケーションの開発者が考える、すべてのチェックを実行できます。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-116">Implementing `ValidateServerCertificate` can perform any checks that the client application developer deems necessary to validate the service certificate.</span></span>  
  
## <a name="validation-of-client-certificates-in-ssl-over-tcp-or-soap-security"></a><span data-ttu-id="e2dd8-117">SSL over TCP または SOAP セキュリティにおけるクライアント証明書の検証</span><span class="sxs-lookup"><span data-stu-id="e2dd8-117">Validation of Client Certificates in SSL over TCP or SOAP Security</span></span>  
 <span data-ttu-id="e2dd8-118">SSL (Secure Sockets Layer) over TCP またはメッセージ (SOAP) セキュリティを使用する場合、クライアント証明書は <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> クラスの <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> プロパティ値に従って検証されます。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-118">When using Secure Sockets Layer (SSL) over TCP or message (SOAP) security, client certificates are validated according to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="e2dd8-119">プロパティは <xref:System.ServiceModel.Security.X509CertificateValidationMode> の値のいずれかに設定されます。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-119">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span> <span data-ttu-id="e2dd8-120">失効チェックは <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> クラスの <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> プロパティの値に応じて実行されます。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-120">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="e2dd8-121">プロパティは <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> の値のいずれかに設定されます。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-121">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#3)]
 [!code-vb[c_CertificateValidationDifferences#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#3)]  
  
## <a name="validation-of-service-certificate-in-ssl-over-tcp-and-soap-security"></a><span data-ttu-id="e2dd8-122">SSL over TCP および SOAP セキュリティにおけるサービス証明書の検証</span><span class="sxs-lookup"><span data-stu-id="e2dd8-122">Validation of Service Certificate in SSL over TCP and SOAP Security</span></span>  
 <span data-ttu-id="e2dd8-123">SSL over TCP またはメッセージ (SOAP) セキュリティを使用する場合、サービス証明書は <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> クラスの <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> プロパティ値に従って検証されます。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-123">When using SSL over TCP or (SOAP) message security, service certificates are validated according to the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="e2dd8-124">プロパティは <xref:System.ServiceModel.Security.X509CertificateValidationMode> の値のいずれかに設定されます。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-124">The property is set to one of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> values.</span></span>  
  
 <span data-ttu-id="e2dd8-125">失効チェックは <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> クラスの <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> プロパティの値に応じて実行されます。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-125">Revocation checking is performed according to the values of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.RevocationMode%2A> property value of the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> class.</span></span> <span data-ttu-id="e2dd8-126">プロパティは <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> の値のいずれかに設定されます。</span><span class="sxs-lookup"><span data-stu-id="e2dd8-126">The property is set to one of the <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> values.</span></span>  
  
 [!code-csharp[c_CertificateValidationDifferences#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_certificatevalidationdifferences/cs/source.cs#4)]
 [!code-vb[c_CertificateValidationDifferences#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_certificatevalidationdifferences/vb/source.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e2dd8-127">参照</span><span class="sxs-lookup"><span data-stu-id="e2dd8-127">See Also</span></span>  
 <xref:System.Net.Security.RemoteCertificateValidationCallback>  
 [<span data-ttu-id="e2dd8-128">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="e2dd8-128">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
