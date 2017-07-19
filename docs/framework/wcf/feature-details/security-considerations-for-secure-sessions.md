---
title: "セキュリティで保護されたセッションに関するセキュリティの検討 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
caps.latest.revision: 14
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 14
---
# セキュリティで保護されたセッションに関するセキュリティの検討
セキュリティで保護されたセッションを実装する場合に、セキュリティに影響を及ぼす次の項目について考慮する必要があります。セキュリティの考慮事項[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[セキュリティの考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)」および「[セキュリティのベスト プラクティス](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)」を参照してください。  
  
## セキュリティで保護されたセッションとメタデータ  
 セキュリティで保護されたセッションが確立され、<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> プロパティが `false` に設定されると、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] はサービス エンドポイントの Web サービス記述言語 \(WSDL: Web Services Description Language\) ドキュメントにメタデータの一部として `mssp:MustNotSendCancel` アサーションを出力します。`mssp:MustNotSendCancel` アサーションは、クライアントに対してセキュリティで保護されたセッションのキャンセル要求にサービスが応答しないことを通知します。<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> プロパティが `true` に設定されている場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は WSDL ドキュメントに `mssp:MustNotSendCancel` アサーションを出力しません。セキュリティで保護されたセッションが必要でなくなった場合、クライアントはサービスに対してキャンセル要求を送る必要があります。[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用してクライアントを生成した場合、クライアント コードは、`mssp:MustNotSendCancel` アサーションが存在するかどうかに対して適切に反応するようになります。  
  
## セキュリティ保護されたメッセージ交換とカスタム トークン  
 WS\-SecureConversation 仕様での定義方法に起因する、カスタム トークンと派生キーの混在に関する問題があります。仕様では、派生トークンを参照するオプション要素の `wsse:SecurityTokenReference` について次のような記述があります。「`/wsc:DerivedKeyToken/wsse:SecurityTokenReference` このオプション要素は、派生用のセキュリティ コンテキスト トークン、セキュリティ トークン、または共有キーやシークレットの指定に使用されます。指定されていない場合、受信者はメッセージのコンテキストから共有キーを判断できると想定されます。コンテキストを判断できない場合は、`wsc:UnknownDerivationSource` などのエラーが発生します。」  
  
 つまり、カスタム トークンを派生させるには、`SecurityTokenReference` 要素にその句型をラップする必要があります。派生をオフにするオプションもありますが、キーを派生させるオプションが既定となっています。キーをラップしなかった場合、派生キー トークンのシリアル化は実行されますが、その逆シリアル化を試みると例外がスローされます。  
  
## 参照  
 [方法 : WSFederationHttpBinding のセキュリティで保護されたセッションを無効にする](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)   
 [セキュリティの考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)   
 [セキュリティのベスト プラクティス](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)