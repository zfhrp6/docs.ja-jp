---
title: WCF 配信の概要
ms.date: 03/30/2017
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
ms.openlocfilehash: c059ca3ee33b254a60d6b8596b02e1f995fd2ca1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="wcf-syndication-overview"></a>WCF 配信の概要
Windows Communication Foundation (WCF) は、WCF サービスから配信フィードを公開するためのサポートを提供します。 配信は、サーバーがフィードと呼ばれる相互運用可能な形式でアプリケーション データの一部を公開するためのアプリケーション統合の機構です。 フィードはアプリケーション データのコレクションであり、フィード レベルのメタデータ (タイトル、作成者、URL、およびその他のメタデータ) と一連のフィード アイテムから構成されます。 フィード内で、フィード アイテムは通常、発生の逆順に並べられます。 フィード アイテムは、アイテム レベルのメタデータの標準セット (タイトル、URL、作成日時、カテゴリ、およびその他のアイテム レベルのメタデータ) と任意の大きさのアプリケーション固有のデータから構成されます。 配信フィードの 2 つの最も一般的な種類は、RSS Really Simple Syndication () 2.0 と Atom 1.0 では、WCF でサポートされるです。  
  
## <a name="object-model"></a>オブジェクト モデル  
 WCF 形式に依存しない方法で、フィード、フィード アイテム、および関連するメタデータを操作できるように配信固有のクラスのセットの定義: <xref:System.ServiceModel.Syndication.SyndicationFeed>、 <xref:System.ServiceModel.Syndication.SyndicationItem>、 <xref:System.ServiceModel.Syndication.SyndicationPerson>、 <xref:System.ServiceModel.Syndication.SyndicationLink>、およびその他の配信に固有のクラスです。 WCF では、配信のサポートなどを提供する WCF REST プログラミング モデル上に構築されるインフラストラクチャ クラスも定義されて: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>、および<!--zz <xref:System.ServiceModel.Syndication.RSS20FeedFormatter>-->`RSS20FeedFormatter`です。 フィード フォーマッタ クラスは、オブジェクト モデルの RSS 2.0 と Atom 1.0 に対する双方向のシリアル化をサポートしています。  
  
## <a name="scenarios"></a>シナリオ  
 現在、配信はブログで広く使用されています。ブログの作成者は、さまざまな種類の情報を定期的に公開します。 たとえば、文字、画像、音声などの情報です。 多くの新聞や雑誌でも、配信を使用してニュースや記事を公開しています。 このようなフィードを定期受信することで、ユーザーはこれらのサイトから発信されるすべての最新情報を得ることができます。 配信は一般的にブログや出版社で使用されますが、一連の情報を公開する任意のアプリケーションで使用することもできます。たとえば、配信フィードを使用したバグ データベースの公開が考えられます。 呼ばれる操作を公開する WCF サービスを作成する`CodeDefects`です。 この操作では、調べたいバグを報告した人の電子メール アドレスを指定するパラメーターを使用できます。 クライアントは、次の URL を使用して、操作を呼び出す:http://someserver/bugDatabase/CodeDefects?user=johndoeです。  
  
## <a name="syndication-formats"></a>配信フォーマット  
 WCF 配信プラットフォームでは、RSS 2.0 および Atom 1.0 をサポートします。  
  
## <a name="see-also"></a>関連項目  
 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
