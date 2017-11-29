---
title: "WCF の拡張"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3faa09a550bdc32437aeac864f09ec7711bdaf97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="extending-wcf"></a>WCF の拡張
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、実行時コンポーネントを変更し、拡張することによって、サービス ベースのアプリケーションを正確に制御および拡張できます。 このセクションのトピックでは、その拡張アーキテクチャについて詳しく説明します。 基本的なプログラミングの詳細については、次を参照してください。[基本的な WCF プログラミング](../../../../docs/framework/wcf/basic-wcf-programming.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [拡張 ServiceHost とサービス モデル レイヤー](../../../../docs/framework/wcf/extending/extending-servicehost-and-the-service-model-layer.md)  
 サービス モデル レイヤーには、基になるチャネルから受信メッセージを取得し、そのメッセージをアプリケーション コードでのメソッド呼び出しに変換し、結果を呼び出し元に送信するという役割があります。  サービス モデル拡張は、ディスパッチャーの機能、カスタム動作、メッセージとパラメーターの途中受信、およびその他の拡張機能に関連する実行や通信の動作と機能を変更または実装します。  
  
 [バインディングの拡張](../../../../docs/framework/wcf/extending/extending-bindings.md)  
 バインディングはエンドポイントに接続するために必要な通信の詳細設定を記述するオブジェクトです。 バインディングの拡張やカスタム バインディングは、アプリケーションの各種機能をサポートするために必要なカスタム通信機能を実装します。  
  
 [チャネル レイヤーの拡張](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)  
 チャネル レイヤーは、サービス モデル レイヤーより下に位置し、クライアントとサービス間のメッセージの交換を担います。 チャネル拡張は、セキュリティなどの新しいプロトコル機能を実装できます。 また、SOAP メッセージを伝達する新しいネットワーク トランスポートの実装など、トランスポート機能も実装できます。  
  
 [セキュリティの拡張](../../../../docs/framework/wcf/extending/extending-security.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のセキュリティは、転送セキュリティ (整合性、機密性、および認証)、アクセス制御 (承認)、および監査で構成されます。 `IdentityModel` 名前空間にある各クラスは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でアクセス制御のために使用されます。 セキュリティ アーキテクチャを理解することによって、カスタムのアクセス制御システムに対応したカスタムのクレーム タイプを作成できます。  
  
 [メタデータ システムの拡張](../../../../docs/framework/wcf/extending/extending-the-metadata-system.md)  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のメタデータ システムは複数のクラスのグループおよびインターフェイスで、サービス ベースのアプリケーションを実装するために必要なメタデータを表します。 クラスを変更または拡張するか、WSDL (Web サービス記述言語) の拡張子やカスタム WS-PolicyAttachments アサーションなどのカスタム メタデータをエクスポート/インポートするインターフェイスを実装して構成します。  
  
 [拡張エンコーダーとシリアライザー](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
 エンコーダーとシリアライザーは、データをある形式から別の形式に変換します。 このセクションのトピックでは、提供されたクラスを特別な要件に合わせて拡張する方法を説明します。  
  
## <a name="reference"></a>参照  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a>関連項目  
 [基本的な WCF プログラミング](../../../../docs/framework/wcf/basic-wcf-programming.md)  
  
 [WCF 機能の詳細](../../../../docs/framework/wcf/feature-details/index.md)  
  
 [ガイドラインとベスト プラクティス](../../../../docs/framework/wcf/guidelines-and-best-practices.md)
