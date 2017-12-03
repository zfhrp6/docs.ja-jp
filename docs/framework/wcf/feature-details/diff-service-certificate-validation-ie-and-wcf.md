---
title: "Internet Explorer と WCF で実行されるサービス証明書の検証の相違点"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service certificate validation [WCF]
- certificates [WCF], service certificate validation
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b74886f05ca6dc38c724e02cd091c6dd212c554f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="differences-between-service-certificate-validation-done-by-internet-explorer-and-wcf"></a><span data-ttu-id="4ee7d-102">Internet Explorer と WCF で実行されるサービス証明書の検証の相違点</span><span class="sxs-lookup"><span data-stu-id="4ee7d-102">Differences Between Service Certificate Validation Done by Internet Explorer and WCF</span></span>
<span data-ttu-id="4ee7d-103">HTTPS を使用した場合、Internet Explorer と [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ではサービス証明書の検証方法に違いがあるため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントからサービス エンドポイントに正常にメッセージを送信できても、サービスのヘルプ ページや Web サービス記述言語 (WSDL: Web Services Description Language) に Internet Explorer からアクセスできないことがあります。</span><span class="sxs-lookup"><span data-stu-id="4ee7d-103">Because of difference between the way Internet Explorer and [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] validate service certificates when HTTPS is used, it is possible that Internet Explorer will not be able to access the Help page or Web Services Description Language (WSDL) of a service even though a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client is able to successfully send messages to the service endpoints.</span></span> <span data-ttu-id="4ee7d-104">これは、サービス証明書の拡張使用法フラグに `ServerAuthentication` オブジェクト識別子 (OID: Object Identifier) があるかどうかを Internet Explorer がチェックするのに対し、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] はそのような制限を適用しないためです。</span><span class="sxs-lookup"><span data-stu-id="4ee7d-104">This is because Internet Explorer checks whether the service certificate has the `ServerAuthentication` object identifiers (OID) in the enhanced usage flags, whereas [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not enforce such a constraint.</span></span> <span data-ttu-id="4ee7d-105">Internet Explorer がサービス ヘルプ ページまたはサービスの WSDL にアクセスできる場合を使用して、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービス メタデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4ee7d-105">If Internet Explorer is unable to access the service Help page or the WSDL for the service, use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to access the service metadata.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ee7d-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ee7d-106">See Also</span></span>  
 [<span data-ttu-id="4ee7d-107">HTTPS、SSL over TCP、および SOAP セキュリティ間証明書検証の相違点</span><span class="sxs-lookup"><span data-stu-id="4ee7d-107">Certificate Validation Differences Between HTTPS, SSL over TCP, and SOAP Security</span></span>](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)  
 [<span data-ttu-id="4ee7d-108">方法: メタデータを取得し、準拠サービスの実装</span><span class="sxs-lookup"><span data-stu-id="4ee7d-108">How to: Retrieve Metadata and Implement a Compliant Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
