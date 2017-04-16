---
title: "基本的なプログラミング ライフサイクル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "サービスの作成 [WCF]"
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
caps.latest.revision: 36
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 36
---
# 基本的なプログラミング ライフサイクル
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] では、アプリケーションは、同一のコンピューター上、インターネット上、異なるアプリケーション プラットフォーム上のいずれに存在しても、通信できます。ここでは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] アプリケーションを構築するために必要な作業について説明します。実際に動作するサンプル アプリケーションについては、「[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。  
  
## 基本的な作業  
 基本的な作業は、次の順序で行います。  
  
1.  サービス コントラクトを定義します。サービス コントラクトでは、サービスの署名、交換するデータ、およびコントラクトに必要なその他のデータを指定します。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][サービス コントラクトの設計](../../../docs/framework/wcf/designing-service-contracts.md).  
  
2.  コントラクトを実装します。サービス コントラクトを実装するには、そのコントラクトを実装するクラスを作成し、ランタイムに必要なカスタム動作を指定します。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][サービス コントラクトの実装](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
3.  エンドポイントおよびその他の動作情報を指定して、サービスを構成します。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][サービスの構成](../../../docs/framework/wcf/configuring-services.md).  
  
4.  サービスをホストします。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][ホスティング サービス](../../../docs/framework/wcf/hosting-services.md).  
  
5.  クライアント アプリケーションを構築します。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][クライアントを構築する](../../../docs/framework/wcf/building-clients.md).  
  
 このセクションのトピックではこの順に従って説明しますが、手順を最初から実行しないシナリオもあります。たとえば、既存のサービスを使用するクライアントを構築する場合は、手順 5. から開始します。また、既存のクライアント アプリケーションが使用するサービスを構築する場合は、手順 5. を省略できます。  
  
 サービス コントラクトの開発について理解したら、「[拡張機能の概要](../../../docs/framework/wcf/introduction-to-extensibility.md)」にも目を通します。サービスで問題が発生した場合は、「[WCF トラブルシューティング クイックスタート](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)」をチェックし、同様の問題が他のサービスで発生していないかどうかを確認してください。  
  
## 参照  
 [サービス コントラクトの実装](../../../docs/framework/wcf/implementing-service-contracts.md)