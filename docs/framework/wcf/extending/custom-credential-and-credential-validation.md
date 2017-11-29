---
title: "カスタム資格情報と資格情報の検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3ca7726f3a6a0c5faaab1cbbd0b31125ce0c1d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="custom-credential-and-credential-validation"></a>カスタム資格情報と資格情報の検証
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のセキュリティは、サービスとクライアント間の資格情報の交換に基づきます。 セキュリティ シナリオの多くは、Windows (Kerberos)、ユーザー名とパスワード、証明書などの共通の資格情報の種類を使用して満たされます。 ただし、新しい種類の資格情報が必要な場合があります。このセクションのこのトピックでは、その新しい種類の処理方法と検証方法について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: カスタム証明書検証を使用するサービスを作成します。](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クラスを継承することで <xref:System.IdentityModel.Selectors.X509CertificateValidator> の検証をカスタマイズする方法について説明します。  
  
 [チュートリアル: カスタムのクライアントとサービスの資格情報の作成](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 拡張する方法を示します、<xref:System.ServiceModel.Description.ClientCredentials>と<xref:System.ServiceModel.Description.ServiceCredentials>資格情報の種類を新規に対応するクラス。 これは、カスタム資格情報の種類の作成を実現するトピック シリーズの 1 番目です。  
  
 [方法: カスタム セキュリティ トークン プロバイダーを作成します。](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 セキュリティ トークン プロバイダーを作成して新しい資格情報の種類を処理し、その資格情報の新しいトークンを返す方法を説明します。 これは、シリーズの 2 番目のトピックです。  
  
 [方法: カスタム セキュリティ トークン認証システムを作成します。](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 カスタム認証システムを作成して新しい資格情報の種類を認証する方法を説明します。 これは、シリーズの 3 番目のトピックです。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a>関連項目  
 [認証](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [フェデレーションと発行済みトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>関連項目  
 [セキュリティ](../../../../docs/framework/wcf/feature-details/security.md)
