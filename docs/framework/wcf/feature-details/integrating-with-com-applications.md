---
title: "COM アプリケーションとの統合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 130a7cda170721f34a5b44f3361bd591d6375267
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="integrating-with-com-applications"></a>COM アプリケーションとの統合
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス モニカーを使用することによって既存のコードに直接統合できます。 サービス モニカーは Office VBA、Visual Basic 6.0、または Visual C++ 6.0 などの幅広い COM ベースの開発環境で使用可能です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [COM アプリケーションとの統合の概要](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 統合プロセスの主要部分の概要を説明します。  
  
 [方法 : サービス モニカーを登録および構成する](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス モニカーを COM アプリケーションで使用するには、必要な属性型を COM に登録し、必要なバインディング構成を使用して COM アプリケーションとモニカーを構成します。  
  
 [方法 : 未登録で Windows Communication Foundation のサービス モニカーを使用する](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 WSDL (Web Services Definition Language) ドキュメントの形式で、または WS-MetadataExchange エンドポイントからコントラクトの定義を取得する方法を説明します。  
  
 [方法 : WSDL コントラクトと共にサービス モニカーを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL モニカーを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のサンプルを呼び出す方法を説明します。  
  
 [方法 : Metadata Exchange コントラクトと共にサービス モニカーを使用する](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 Mex エンドポイントを指定する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] モニカーを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のサンプルを呼び出す方法を説明します。  
  
 [方法 : チャネルのセキュリティ資格情報を指定する](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス モニカーは、チャネル資格情報を指定するためのさまざまな代替メソッドの使用を許可する `IChannelCredentials` インターフェイスをサポートします。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a>参照  
 [COM+ アプリケーションとの統合](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
