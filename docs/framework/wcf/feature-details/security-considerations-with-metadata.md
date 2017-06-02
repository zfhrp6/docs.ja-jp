---
title: "メタデータを使用する場合のセキュリティ上の考慮事項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
caps.latest.revision: 10
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 10
---
# メタデータを使用する場合のセキュリティ上の考慮事項
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のメタデータの機能を使用するときは、サービス メタデータの公開、取得、および使用によって生じるセキュリティへの影響を考慮する必要があります。  
  
## メタデータを公開する場合と公開しない場合  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、既定ではメタデータを公開しない設定になっています。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのメタデータを公開するには、メタデータ エンドポイントをサービスに追加することにより、メタデータの公開を明示的に指定する必要があります \(「[メタデータの公開](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)」を参照\)。  メタデータの公開を無効のままにしておけば、攻撃者にとっては侵入経路が少ないことになり、したがって情報漏洩の危険を減らすことができます。  メタデータを公開する必要のないサービスもあります。  必要ないのであれば無効のままにしておくようお勧めします。  この状態でも、[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用すれば、サービス アセンブリから直接、メタデータやクライアント コードを生成できます。  Svcutil.exe を使用してメタデータをエクスポートする方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : Svcutil.exe を使用してコンパイル済みのサービス コードからメタデータをエクスポートする](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)」を参照してください。  
  
## セキュリティ保護されたバインディングによるメタデータの公開  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に組み込まれた既定のメタデータ バインディングはセキュリティ保護されておらず、メタデータへの匿名アクセスを許可するようになっています。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが公開するサービス メタデータにはサービスに関する詳細な記述があるので、故意または過失により、重要な情報が漏洩するおそれがあります。  たとえば、一般に公開するべきではない、インフラストラクチャ操作に関する情報が入った状態で発行される可能性があるのです。  権限のないアクセスを拒否する方法として、メタデータ エンドポイントで、セキュリティ保護されたバインディングを使う、というものがあります。  メタデータ エンドポイントは HTTP\/GET 要求に応答しますが、ここに SSL \(Secure Sockets Layer\) を使用すれば、メタデータを保護できます。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [方法 : セキュリティで保護されたメタデータ エンドポイント](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md).  
  
 メタデータ エンドポイントを保護することで、正当なユーザーが、改ざんやなりすましを恐れずに安全にサービス メタデータを取得できる手段も提供されます。  
  
## 信頼できるメタデータのみを使用  
 サービス メタデータを使用すると、サービスの呼び出しに必要なランタイム コンポーネントを自動構築できます。  たとえば、設計時には、クライアント アプリケーションを開発するためにメタデータを利用できます。また、実行時には、メタデータを利用して、クライアントがサービス呼び出しのために使用するバインディングを動的に更新できます。  
  
 サービス メタデータを取得する際、セキュリティ保護された方法を使わないと、改ざんやなりすましのおそれがあります。  メタデータが改ざんされると、知らない間に悪質なサービスに接続されたり、セキュリティ上問題のある設定に切り替えられたり、XML 構造が破壊されたりすることがあります。  メタデータ ドキュメントはかなりの容量になることがあるので、多くの場合、ファイル システムに保存することになります。  改ざんやなりすましを防ぐために、サービス メタデータを要求するときには、できるだけセキュリティで保護されたバインディングを使用してください。  
  
## 安全な技術を使ってメタデータを処理  
 サービス メタデータは多くの場合、MEX \(WS\-Metadata Exchange\) などの標準的なプロトコルを使用して、ネットワーク経由で伝送されます。  メタデータの形式を見ると、多くの場合、他のメタデータを参照する旨の記述ができるようになっています。  <xref:System.ServiceModel.Description.MetadataExchangeClient> 型は、Web サービス記述言語 \(WSDL\) ドキュメント、XML スキーマ、および MEX ドキュメント内の参照を自動的に処理します。  取得したメタデータから生成される <xref:System.ServiceModel.Description.MetadataSet> オブジェクトのサイズは、使用されている <xref:System.ServiceModel.Description.MetadataExchangeClient> インスタンスの <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> の値と、この <xref:System.ServiceModel.Description.MetadataExchangeClient> インスタンスが使用するバインディングの `MaxReceivedMessageSize` の値に比例します。  動作環境に合わせてこのクォータ値を適切に設定してください。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、サービス メタデータは XML の形で処理されます。  XML ドキュメントを処理するアプリケーションは、悪質な XML 構造が現れても破綻しないようになっていなければなりません。  XML を処理するときは、`XmlDictionaryReader` に適切なクォータ値を設定して使用すると共に、<xref:System.Xml.XmlReader> インスタンスに対する <xref:System.Xml.XmlReaderSettings> オブジェクトの <xref:System.XML.XmlReaderSettings.ProhibitDtd%2A> プロパティを `true` に設定してください。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のメタデータ システムは、メタデータ拡張をアプリケーションの構成ファイルに登録することにより、容易に拡張できるようになっています \(「[メタデータ システムの拡張](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)」を参照\)。  メタデータ拡張はどのようなコードでも実行できるので、適切なアクセス制御リスト \(ACL\) でアプリケーション構成ファイルを保護し、信頼できるメタデータ拡張以外は登録しないようにする必要があります。  
  
## 生成されたクライアントの検証  
 信頼できないソースから取得したメタデータを基にクライアント コードを生成した場合、これがクライアント アプリケーションのセキュリティ ポリシーに合致しているかどうか検証する必要があります。  動作を検証するための専用クライアントを使うか、あるいはツールが生成したコードを目視で検査してください。  動作を検証するためのクライアントを実装する例については、「[クライアント検証](../../../../docs/framework/wcf/samples/client-validation.md)」を参照してください。  
  
## アプリケーション構成ファイルの保護  
 サービスのアプリケーション構成ファイルでは、メタデータを公開する方法、および公開の有無を制御できます。  攻撃者が設定を変更できないように、適切なアクセス制御リスト \(ACL\) でアプリケーション構成ファイルを保護することをお勧めします。  
  
## 参照  
 [方法 : セキュリティで保護されたメタデータ エンドポイント](../../../../docs/framework/wcf/feature-details/how-to-secure-metadata-endpoints.md)   
 [セキュリティ](../../../../docs/framework/wcf/feature-details/security.md)