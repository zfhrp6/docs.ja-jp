---
title: "コントラクト | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コントラクト [WCF]"
  - "WCF [WCF], コントラクト"
  - "Windows Communication Foundation [WCF], コントラクト"
ms.assetid: c8364183-4ac1-480b-804a-c5e6c59a5d7d
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# コントラクト
ここでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] コントラクトを定義および実装する方法について説明します。  サービス コントラクトでは、エンドポイントが外部と何をやりとりするかが指定されます。  具体的には、要求\/応答、一方向、双方向など、基本的なメッセージ交換パターン \(MEP\) に編成された一連のメッセージに関する記述です。  サービス コントラクトがメッセージ交換の論理的に関連したセットであるとすると、サービス操作は単一のメッセージ交換です。  たとえば、`Hello` という操作では、1 つのメッセージを受け取り、呼び出し元があいさつを通知できるようにする必要があり、メッセージを返すことができます \(マナーが悪ければ返さない場合もあり得ます\)。  
  
 コントラクトおよび [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のその他の中心的概念[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[Windows Communication Foundation の基本概念](../../../../docs/framework/wcf/fundamental-concepts.md)」を参照してください。  ここでは、サービス コントラクトを理解することに重点を置きます。  サービス コントラクトを使用してサービスに接続するクライアントを構築する方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[WCF クライアントの概要](../../../../docs/framework/wcf/wcf-client-overview.md)」を参照してください。  クライアント チャネル、クライアント アーキテクチャ、およびその他クライアントに関する問題[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[クライアント](../../../../docs/framework/wcf/feature-details/clients.md)」を参照してください。  
  
## 概要  
 ここでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの設計および実装に関する大まかな概念的位置付けについて説明します。  サブトピックでは、設計と実装の仕様についてより詳しく説明します。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションを設計および実装する前に、次の準備をしておくことをお勧めします。  
  
-   サービス コントラクトの概要、しくみ、および作成方法について理解する。  
  
-   コントラクトとは、実行時の構成またはホスト環境でサポートされていない可能性のある最小限の要件を記述するものであることを理解する。  
  
## サービス コントラクト  
 サービス コントラクトとは、以下の項目に関する記述です。  
  
-   サービスでの操作のグループ化  
  
-   交換するメッセージに関する操作のシグネチャ  
  
-   交換するメッセージのデータ型  
  
-   操作の場所  
  
-   サービスとの正常な通信をサポートするために使用するプロトコルとシリアル化形式  
  
 たとえば、注文情報の種類に関する入力を受け入れ、発注 ID を含めた成功または失敗の情報を返す `CreateOrder` 操作が含まれた発注書コントラクトがあるとします。  このコントラクトには、発注 ID を受け入れ、注文ステータス情報を返す `GetOrderStatus` 操作も含まれている場合があります。  この種のサービス コントラクトの場合、以下を明示します。  
  
-   発注書コントラクトが `CreateOrder` 操作と `GetOrderStatus` 操作で構成されていること。  
  
-   これらの操作によって、入力メッセージと出力メッセージが指定されていること。  
  
-   これらのメッセージが伝達できるデータ。  
  
-   メッセージを正常に処理するために必要な通信インフラストラクチャに関する明確な記述。  たとえば、正常な通信を確立するためにセキュリティが必要かどうか、また、どのような形式のセキュリティが必要かなどの詳細を記述します。  
  
 このような種類の情報を他のさまざまなプラットフォーム上 \(マイクロソフト以外のプラットフォームも含む\) のアプリケーションに伝達するために、XML サービス コントラクトは、[Web Services Description Language \(WSDL\)](http://go.microsoft.com/fwlink/?LinkId=87004) や [XML Schema \(XSD\)](http://go.microsoft.com/fwlink/?LinkId=87005) などの標準 XML 形式で公開されます。  多くのプラットフォームの開発者は、このパブリック コントラクト情報を使用して、サービスと通信できるアプリケーションを作成できます。これは、開発者が仕様の言語を理解しているだけでなく、これらの言語はサービスがサポートするパブリックな形式、書式、およびプロトコルを記述することで相互運用できるように設計されているためです。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] がこの種の情報を処理する方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[メタデータ](../../../../docs/framework/wcf/feature-details/metadata.md)」を参照してください。  
  
 コントラクトはさまざまな方法で表現できます。ただし、WSDL と XSD は、利用しやすい方法でサービスを記述する優れた言語ではあるものの直接使用するのが難しいため、どのような場合でも、サービス コントラクトの実装ではなく、サービスを記述するだけです。  そのため、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションでは、マネージ属性、マネージ インターフェイス、およびマネージ クラスを使用して、サービスの構造の定義と実装の両方を行います。  
  
 マネージ型で定義されたコントラクトは、特に他のプラットフォーム上のクライアントやその他のサービス実装側が必要とする場合に、メタデータ \(WSDL および XSD\) として変換 \(*エクスポート*とも呼ばれます\) できます。  これにより、どのクライアント アプリケーションに対してもパブリック メタデータを使用して記述できる、簡単なプログラミング モデルが実現します。  基になる SOAP メッセージの詳細 \(トランスポートとセキュリティ関連の情報など\) は、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に残しておくことができます。WCF は、サービス コントラクト型システムと XML 型システム間で必要な変換を自動的に実行します。  
  
 コントラクトの設計[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[サービス コントラクトの設計](../../../../docs/framework/wcf/designing-service-contracts.md)」を参照してください。  コントラクトの実装[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[サービス コントラクトの実装](../../../../docs/framework/wcf/implementing-service-contracts.md)」を参照してください。  
  
 さらに、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には、メッセージ レベルでサービス コントラクト全体を開発できる機能も備わっています。  メッセージ レベルでサービス コントラクトを開発する方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[メッセージ コントラクトの使用](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)」を参照してください。  SOAP XML 以外でサービスを開発する方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[POX アプリケーションとの相互運用性](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md)」を参照してください。  
  
### 要件の階層の理解  
 サービス コントラクトは、操作をグループ化し、MEP、メッセージの種類、およびメッセージに格納されているデータ型を指定します。さらに、実装でコントラクトをサポートするために必要な実行時の動作のカテゴリ \(メッセージの暗号化と署名を要求するなど\) を示します。  ただし、サービス コントラクト自体は、これらの要件を満たす方法を正確に指定するわけではなく、これらの要件が必要であることを示すだけです。  暗号化の種類やメッセージに署名する方法は、準拠サービスの実装と構成によって決まります。  
  
 コントラクトに必要なのは、サービス コントラクトの実装と、動作を追加するための実行時の構成に関するものであるという点に注意してください。  使用するサービスを公開するために満たす必要のある要件のセットは、上記の要件のセットを基に作成されます。  コントラクトが実装の要件を作成しても、実装ではサービスの実行を可能にするために、さらに多くの構成とバインディングを必要とする場合があります。  また、ホスト アプリケーションも、サービス構成とバインディングによって追加されるすべての要件をサポートする必要があります。  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービス アプリケーションを設計、実装、構成、およびホストする際には、この追加要件のプロセスに注意することが重要です。  たとえば、コントラクトでセッションをサポートする必要があることが指定されている場合があります。  その場合、コントラクトの要件をサポートするようにバインディングを構成する必要があります。そうしないと、サービス実装は機能しなくなります。  また、サービスが統合 Windows 認証を必要としており、インターネット インフォメーション サービス \(IIS\) でホストされる場合、サービスが存在する Web アプリケーションでは、統合 Windows 認証を有効にし、匿名サポートを無効にしておく必要があります。  各種サービス ホスト アプリケーションの機能と影響[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[ホスト](../../../../docs/framework/wcf/feature-details/hosting.md)」を参照してください。  
  
## 参照  
 [エンドポイント : アドレス、バインディング、およびコントラクト](../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)   
 [サービス コントラクトの設計](../../../../docs/framework/wcf/designing-service-contracts.md)   
 [サービス コントラクトの実装](../../../../docs/framework/wcf/implementing-service-contracts.md)