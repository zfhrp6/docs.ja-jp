---
title: "WCF での認証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 432ed9debeffad82125b567508ed46b46d4b8821
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="authentication-in-wcf"></a>WCF での認証
以下のトピックでは、Windows 認証、X.509 証明書、ユーザー名とパスワードなど、認証を提供する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のさまざまな機構を示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法 : ASP.NET メンバーシップ プロバイダーを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 ASP.NET の機能には、メンバーシップとロール プロバイダー、認証のためのユーザー名とパスワードの組み合わせを格納するデータベース、および承認のためのユーザー ロールがあります。 ここでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが同じデータベースを使用してユーザーの認証と承認を行うしくみについて説明します。  
  
 [方法 : カスタム ユーザー名およびパスワード検証を使用する](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 カスタム ユーザー名およびパスワード検証を統合する方法を示します。  
  
 [サービス ID と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 追加の保護手段として、クライアントは、予期されるを指定してサービスを認証できます*identity*サービス。 予想される ID とサービスから返される ID が一致しない場合、認証は失敗します。  
  
 [セキュリティ ネゴシエーションとタイムアウト](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> クラスの <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> プロパティの使用方法について説明します。  
  
 [Windows 認証エラーのデバッグ](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 Windows 認証の使用時に発生する一般的な問題について重点的に説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>関連項目  
 [一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a>参照  
 [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Windows Server App Fabric のセキュリティ モデル](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
