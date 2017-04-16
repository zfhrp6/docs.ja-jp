---
title: "WCF 配信の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# WCF 配信の概要
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスから配信フィードを公開することができます。配信は、サーバーがフィードと呼ばれる相互運用可能な形式でアプリケーション データの一部を公開するためのアプリケーション統合の機構です。フィードはアプリケーション データのコレクションであり、フィード レベルのメタデータ \(タイトル、作成者、URL、およびその他のメタデータ\) と一連のフィード アイテムから構成されます。フィード内で、フィード アイテムは通常、発生の逆順に並べられます。フィード アイテムは、アイテム レベルのメタデータの標準セット \(タイトル、URL、作成日時、カテゴリ、およびその他のアイテム レベルのメタデータ\) と任意の大きさのアプリケーション固有のデータから構成されます。最も一般的な配信フィードは、RSS \(Really Simple Syndication\) 2.0 と Atom 1.0 であり、どちらも [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] でサポートされています。  
  
## オブジェクト モデル  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、<xref:System.ServiceModel.Syndication.SyndicationFeed>、<xref:System.ServiceModel.Syndication.SyndicationItem>、<xref:System.ServiceModel.Syndication.SyndicationPerson>、<xref:System.ServiceModel.Syndication.SyndicationLink> など、配信専用の一連のクラスが定義されており、フィード、フィード アイテム、および関連するメタデータを形式に依存しない方法で処理できます。また [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、<xref:System.ServiceModel.Syndication.Atom10FeedFormatter> や <xref:System.ServiceModel.Syndication.RSS20FeedFormatter> など、WCF REST プログラミング モデル上で配信をサポートするために構築されるインフラストラクチャ クラスも定義されています。フィード フォーマッタ クラスは、オブジェクト モデルの RSS 2.0 と Atom 1.0 に対する双方向のシリアル化をサポートしています。  
  
## シナリオ  
 現在、配信はブログで広く使用されています。ブログの作成者は、さまざまな種類の情報を定期的に公開します。たとえば、文字、画像、音声などの情報です。多くの新聞や雑誌でも、配信を使用してニュースや記事を公開しています。このようなフィードを定期受信することで、ユーザーはこれらのサイトから発信されるすべての最新情報を得ることができます。配信は一般的にブログや出版社で使用されますが、一連の情報を公開する任意のアプリケーションで使用することもできます。たとえば、配信フィードを使用したバグ データベースの公開が考えられます。この場合は、`CodeDefects` という操作を公開する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスを作成できます。この操作では、調べたいバグを報告した人の電子メール アドレスを指定するパラメーターを使用できます。クライアントは、http:\/\/someserver\/bugDatabase\/CodeDefects?user\=johndoe という URL を使用して、この操作を呼び出すことができます。  
  
## 配信フォーマット  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の配信プラットフォームでは、RSS 2.0 と Atom 1.0 をサポートしています。  
  
## 参照  
 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)