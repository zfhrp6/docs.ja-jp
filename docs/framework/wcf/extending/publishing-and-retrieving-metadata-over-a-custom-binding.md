---
title: カスタム バインディングを介したメタデータの公開と取得
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 528f7662ee3a1f956427e5e42f540816f55027f8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803885"
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>カスタム バインディングを介したメタデータの公開と取得
<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> は、サービスにメタデータ エンドポイントを追加するためのサポートを提供します。 これらのメタデータ エンドポイントがある URL に HTTP GET 要求に応答できる、 `?wsdl` querystring および Ws-metadataexchange (MEX) 仕様で定義された Ws-transfer GET 要求にします。 MEX エンドポイントは、<xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> コントラクトを実装します。  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>カスタム バインドを介したメタデータの公開  
 HTTP GET メタデータ エンドポイントと HTTPS GET メタデータ エンドポイントを有効にするには、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> プロパティまたは <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> プロパティを `true` に設定します。 これらのエンドポイントのバインディングは構成できません。  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>コントラクト、ただしで使用できますも含み、カスタムのバインディングを使用するため、任意のエンドポイント<xref:System.ServiceModel.Description.IMetadataExchange>エンドポイントは、他の Windows Communication Foundation (WCF) サービス エンドポイントと同じです。 システム指定のバインディングの構成を変更する方法または <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> の構成方法を理解している場合は、<xref:System.ServiceModel.Description.IMetadataExchange> エンドポイントで使用されるバインディングを構成できます。  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>カスタム バインドを介したメタデータの取得  
 メタデータは、標準の HTTP 要求または HTTPS GET 要求を使用して HTTP Get および HTTPS Get メタデータ エンドポイントから取得できます。  
  
 WCF でサポートされている標準の MEX バインディングのいずれかを使用することができます、通常、MEX メタデータ エンドポイントからメタデータを取得します。 詳細については、「<xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>」を参照してください。 <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> 型および Svcutil.exe ツールでは、指定したメタデータ エンドポイントのアドレスに基づいて、標準の MEX バインディングの 1 つが自動的に選択されます。  
  
 MEX メタデータ エンドポイントで標準の MEX バインディングとは異なるバインディングを使用する場合は、コードを使用するか、<xref:System.ServiceModel.Description.MetadataExchangeClient> クライアント エンドポイント構成を提供することにより、<xref:System.ServiceModel.Description.IMetadataExchange> で使用されるバインディングを構成できます。 Svcutil.exe ツールは、構成ファイルから、メタデータ エンドポイント アドレスの URI スキームと同じ名前を持つ <xref:System.ServiceModel.Description.IMetadataExchange> クライアント エンドポイント構成を自動的に読み込みます。  
  
## <a name="security"></a>セキュリティ  
 カスタム バインディングを介してメタデータを公開する場合、メタデータに必要なセキュリティ サポートをそのカスタム バインディングが提供することを確認してください。 たとえば、情報の漏えいを防止し、メタデータを取得するための権限がクライアントにあることを確認するには、認証および暗号化を要求するように <xref:System.ServiceModel.Description.IMetadataExchange> エンドポイントを構成することによってメタデータとアプリケーションのセキュリティを強化します。 サンプル[カスタム セキュリティで保護されたメタデータ エンドポイント](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)このシナリオを示します。  
  
## <a name="see-also"></a>関連項目  
 [サービスのセキュリティ保護](../../../../docs/framework/wcf/securing-services.md)  
 [WS-MetadataExchange のバインディング](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)  
 [方法 : カスタム WS-Metadata Exchange バインディングを構成する](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [方法 : MEX 以外のバインディングを介してメタデータを取得する](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
