---
title: "WIF API リファレンス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a027d902-9314-4bfd-b172-4e81847b1d68
caps.latest.revision: 4
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ef439ff502fc39074d36f63d139fd23e42471d42
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="wif-api-reference"></a>WIF API リファレンス
Windows Identity Foundation (WIF) クラスは、`mscorlib` (mscorlib.dll)、`System.IdentityModel` (System.IdentityModel.dll)、`System.IdentityModel.Services` (System.IdentityModel.Services.dll)、および `System.ServiceModel` (System.ServiceModel.dll) というアセンブリに分割されています。 このトピックでは、WIF 名前空間のリンクを紹介し、各名前空間に含まれるクラスについて簡単に説明します。  
  
> [!IMPORTANT]
>  `System.IdentityModel`、<xref:System.IdentityModel.Claims?displayProperty=fullName>、および <xref:System.IdentityModel.Policy?displayProperty=fullName> という <xref:System.IdentityModel.Selectors?displayProperty=fullName> 名前空間には、WCF クレーム ベースの ID モデルを実装するクラスが含まれます。 .NET Framework 4.5 以降、WCF クレーム ベース ID モデルは WIF に置き換えられています。 WIF に基づいてソリューションをビルドする際は、これら 3 つの名前空間でクラスを使用しないでください。  
  
 <xref:System.IdentityModel?displayProperty=fullName>  
 クッキーの変換、セキュリティ トークン サービス、および特殊な XML ディクショナリ リーダーを表すクラスが含まれます。  
  
 <xref:System.IdentityModel.Configuration?displayProperty=fullName>  
 Windows Identity Foundation (WIF) を使用して構築されたアプリケーションとサービスの構成を提供するクラスが含まれます。 この名前空間のクラスは、[\<identityConfiguration>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) 要素の設定を表しています。  
  
 <xref:System.IdentityModel.Metadata?displayProperty=fullName>  
 フェデレーション メタデータ ドキュメントの要素を表すクラスが含まれます。  
  
 <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName>  
 WS-Trust 成果物を表すクラスが含まれます。  
  
 <xref:System.IdentityModel.Services?displayProperty=fullName>  
 受動的な (WS-Federation) シナリオで使用されるクラスが含まれます。 また、[\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) 要素の設定を表すクラスもいくつか含まれています。 この要素の設定で、アプリケーションの WS-Federation を構成します。 `System.IdentityModel.Services.Configuration` 名前空間には、WS-Federation の構成に使用されるほとんどのクラスが含まれます。  
  
 <xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>  
 WS-Federation プロトコルを使用する WIF アプリケーションに構成を提供するクラスが含まれます。 この名前空間内のクラスは、[\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) 要素の設定を表します。 また、`System.IdentityModel.Services` 名前空間には、WS-Federation の構成に使用されるいくつかのクラスが含まれます。  
  
 <xref:System.IdentityModel.Services.Tokens?displayProperty=fullName>  
 Web ファーム シナリオの特殊なセキュリティ トークン ハンドラーが含まれます。  
  
 <xref:System.IdentityModel.Tokens?displayProperty=fullName>  
 セキュリティ トークン、セキュリティ トークン ハンドラー、およびその他のセキュリティ トークンの成果物を表すクラスが含まれます。  
  
 <xref:System.Security.Claims?displayProperty=fullName>  
 クレーム、クレーム ベースの ID、クレーム ベースの原則、およびその他のクレーム ベースの ID モデル成果物を表すクラスが含まれます。  
  
 <xref:System.ServiceModel.Security?displayProperty=fullName>  
 アクティブな (WS-Trust) シナリオで使用される WCF のコントラクト、チャネル、サービス ホスト、およびその他の成果物を表すクラスが含まれています。 この名前空間には、Windows Communication Foundation (WCF) 固有で、WIF が使用していないクラスも含まれています。  
  
## <a name="see-also"></a>関連項目  
 [WIF 構成のリファレンス](../../../docs/framework/security/wif-configuration-reference.md)   
 [WIF 3.5 と WIF 4.5 間での名前空間マッピング](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)

