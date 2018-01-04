---
title: "サービスおよびクライアントのセキュリティ保護"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 52e07a83f5a1b84abc46f00e6fd6e80e4b9a2622
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="securing-services-and-clients"></a>サービスおよびクライアントのセキュリティ保護
ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] でのセキュリティのプログラミングについて説明します。 一般に、これには、システムが提供する適切なバインディングを選択すること、セキュリティ要素のプロパティを適切に設定すること、サービス側/クライアント側で使う資格情報の検索方法にまつわる、サービスの動作に関するプロパティを適切に設定することなどが含まれます。 ように、これらの手法はほとんどのシナリオでは、ほとんどのユーザーのセキュリティ要件をカバー[一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)です。 シナリオには、多くの機能が必要とする場合が初めて表示[のカスタム バインディングのセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); ソリューションが明らかなかどうかは、次を参照してください。[拡張セキュリティ](../../../../docs/framework/wcf/extending/extending-security.md)です。 作成する (またはとの相互運用) は豊富な要求を使用するシステムでは、トピックを参照してください。[承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [WCF セキュリティのプログラミング](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 メッセージを保護するために使うプログラミング モデルの概要  
  
 [トランスポート セキュリティの概要](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 トランスポート層を介してやり取りするメッセージを保護する方法の概要  
  
 [メッセージのセキュリティ](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のメッセージ レベル セキュリティを使用する理由の要約  
  
 [セキュリティで保護されたセッション](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セッションのセキュリティを保護する際の考慮事項  
  
 [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 X.509 証明書を使用する際に必要となる主なタスクの解説  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a>関連項目  
 [セキュリティの概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [セキュリティの拡張](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [バインディングとセキュリティ](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [カスタム バインドを使用したセキュリティ機能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [セキュリティの拡張](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [承認](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>参照  
 [基本的な WCF プログラミング](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Windows Server App Fabric のセキュリティ モデル](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
