---
title: "エンドポイント : アドレス、バインディング、およびコントラクト | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エンドポイント [WCF]"
  - "WCF [WCF], エンドポイント"
  - "Windows Communication Foundation [WCF], エンドポイント"
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# エンドポイント : アドレス、バインディング、およびコントラクト
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスを使用して行われるすべての通信では、サービスの*エンドポイント*が使用されます。エンドポイントは、クライアントが [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスによって提供される機能にアクセスできるようにします。  
  
 各エンドポイントは、次の 4 つのプロパティで構成されます。  
  
-   そのエンドポイントの場所を示すアドレス。  
  
-   クライアントがエンドポイントと通信する方法を指定するバインディング。  
  
-   利用可能な操作を識別するためのコントラクト。  
  
-   エンドポイントのローカル実装の詳細を指定する一連の動作。  
  
 ここでは、エンドポイントの構造と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] オブジェクト モデルでの表現方法について説明します。  
  
## エンドポイントの構造  
 各エンドポイントの構造は次のとおりです。  
  
-   アドレス : アドレスは、エンドポイントを一意に識別し、サービスの潜在的ユーザーにそのエンドポイントの場所を示します。[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] オブジェクト モデルでは、<xref:System.ServiceModel.EndpointAddress> クラスで表されます。<xref:System.ServiceModel.EndpointAddress> クラスには次のものが含まれます。  
  
    -   <xref:System.ServiceModel.EndpointAddress.Uri%2A> プロパティは、サービスのアドレスを表します。  
  
    -   <xref:System.ServiceModel.EndpointAddress.Identity%2A> プロパティは、サービスのセキュリティ ID とオプションのメッセージ ヘッダーのコレクションを表します。オプションのメッセージ ヘッダーは、エンドポイントの識別またはエンドポイントとの対話のための、より詳細なアドレス指定情報を追加するために使用されます。  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [エンドポイント アドレスの指定](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   バインディング : バインディングは、エンドポイントとの通信方法を指定します。バインディングには、以下の項目が含まれます。  
  
    -   使用するトランスポート プロトコル \(例 : TCP や HTTP\)。  
  
    -   メッセージに使用するエンコーディング \(例 : テキストやバイナリ\)。  
  
    -   必要なセキュリティ要件 \(例 : SSL メッセージ セキュリティや SOAP メッセージ セキュリティ\)。  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [WCF のバインディングの概要](../../../../docs/framework/wcf/bindings-overview.md).[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] オブジェクト モデルでは、バインディングは抽象基本クラス <xref:System.ServiceModel.Channels.Binding> で表されます。ほとんどのシナリオでは、システム指定のバインディングを使用できます。詳細については、「[システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)」を参照してください。  
  
-   コントラクト : コントラクトは、エンドポイントがクライアントに公開する機能を示します。コントラクトは、以下の項目を指定します。  
  
    -   クライアントから呼び出すことができる操作。  
  
    -   メッセージの形式。  
  
    -   操作を呼び出すために必要な入力パラメーターまたはデータの型。  
  
    -   クライアントが予期できる処理メッセージまたは応答メッセージの種類。  
  
     コントラクトの定義の詳細については、「[サービス コントラクトの設計](../../../../docs/framework/wcf/designing-service-contracts.md)」を参照してください。  
  
-   動作 : エンドポイントの動作を使用すると、サービス エンドポイントのローカル動作をカスタマイズできます。これを実現するため、エンドポイントの動作は [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ランタイムのビルド プロセスに参加します。エンドポイントの動作の一例は、<xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> プロパティです。これにより、SOAP アドレスまたは Web サービス記述言語 \(WSDL\) アドレスとは異なるリッスン アドレスを指定できます。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).  
  
## エンドポイントの定義  
 サービスのエンドポイントはコードを使用して強制的に指定するか、構成を介して宣言として指定できます。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]「[方法 : 構成にサービス エンドポイントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)」および「[方法 : コード内にサービス エンドポイントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)」を参照してください。  
  
## このセクションの内容  
 このセクションでは、バインディング、エンドポイント、およびアドレスの目的を説明し、バインディングとエンドポイントの構成方法および `ClientVia` 動作と `ListenUri` プロパティの使用方法を示します。  
  
 [アドレス](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でのエンドポイントのアドレス指定の方法について説明します。  
  
 [バインディング](../../../../docs/framework/wcf/feature-details/bindings.md)  
 バインディングを使用して、クライアントとサービスが相互に通信するために必要なトランスポート、エンコーディング、およびプロトコルの詳細を指定する方法について説明します。  
  
 [コントラクト](../../../../docs/framework/wcf/feature-details/contracts.md)  
 コントラクトでサービスのメソッドが定義されるしくみについて説明します。  
  
 [方法 : 構成にサービス エンドポイントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 構成にサービス エンドポイントを作成する方法について説明します。  
  
 [方法 : コード内にサービス エンドポイントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 コード内にサービス エンドポイントを作成する方法について説明します。  
  
 [方法 : Svcutil.exe を使用してコンパイル済みサービス コードを検証する](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用して、サービスをホストせずにサービスの実装と構成でエラーを検出する方法について説明します。  
  
## 参照  
 [サービスの構成](../../../../docs/framework/wcf/configuring-services.md)   
 [バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)