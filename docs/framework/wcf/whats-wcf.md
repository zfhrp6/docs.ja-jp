---
title: Windows Communication Foundation とは
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: e49b393b9dd09a513066a6cb3612ad9f938e9adb
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="what-is-windows-communication-foundation"></a>Windows Communication Foundation とは
Windows Communication Foundation (WCF) は、サービス指向アプリケーションを構築するためのフレームワークです。 WCF を使用して、できるデータを送信する非同期メッセージとして 1 つのサービス エンドポイントから別です。 サービス エンドポイントには、IIS でホストされている、継続的に使用可能なサービスの一部を使用したり、アプリケーションでホストされているサービスを使用できます。 エンドポイントには、サービス エンドポイントからデータを要求するサービスのクライアントを使用できます。 メッセージは XML として送信された 1 文字または 1 語の簡単なものでも、バイナリ データのストリームのような複雑なものでも構いません。 サンプル シナリオをいくつか挙げます。  
  
-   ビジネス トランザクションを処理するセキュリティ保護サービス。  
  
-   トラフィック レポートやその他のモニタリング サービスなど、現在のデータを他のサービスに提供するサービス。  
  
-   2 人のユーザーがリアル タイムで通信したりデータを交換したりできるチャット サービス。  
  
-   データの 1 つ以上のサービスをポーリングし、論理プレゼンテーションで表示するダッシュボード アプリケーション。  
  
-   Windows Workflow Foundation を WCF サービスに使用した、実装されたワークフローの公開。  
  
-   最新のデータ フィードのサービスをポーリングする Silverlight アプリケーション。  
  
 このようなアプリケーションを作成すると、WCF の存在する前に考えられるが、WCF によりエンドポイントの開発より簡単になります。 要約すると、WCF は Web サービスと Web サービス クライアントの作成を管理しやすいアプローチを提供する設計されています。  
  
## <a name="features-of-wcf"></a>WCF の機能  
 WCF には、次の機能セットが含まれています。 詳細については、次を参照してください。 [WCF 機能の詳細](../../../docs/framework/wcf/feature-details/index.md)です。  
  
-   **サービス指向**  
  
     WS 標準を使用する 1 つの結果は、WCF を使用すると、作成する*サービス指向*アプリケーションです。 サービス指向アーキテクチャ (SOA) は、データの送受信に Web サービスを使用します。 このサービスを使用する一般的な長所は、1 つのアプリケーションから別のアプリケーションへハードコーディングせずに、疎結合にできるということです。 疎結合リレーションシップでは、必須のコントラクトが一致していれば、任意のプラットフォームで作成した任意のクライアントを任意のサービスに接続できます。  
  
-   **相互運用性**  
  
     WCF では、Web サービスの相互運用性の最新の業界標準を実装します。 サポートされている標準の詳細については、次を参照してください。[相互運用性との統合](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md)です。  
  
-   **複数のメッセージ パターン**  
  
     メッセージは複数のパターンの 1 つを使用して交換されます。 最も一般的なパターンは要求/応答パターンです。このパターンでは 1 つのエンドポイントが 2 番目のエンドポイントからデータを要求し、 2 番目のエンドポイントが応答します。 その他にも一方向のメッセージなどのパターンがあります。一方向のメッセージでは、1 つのエンドポイントが応答を期待せずにメッセージを送信します。 より複雑なパターンとして、2 つのエンドポイントが接続を確立し、インスタント メッセージング プログラムのようにデータをやり取りする双方向交換パターンがあります。 異なるメッセージ交換を実装する方法の詳細について WCF を使用したパターンを参照してください[コントラクト](../../../docs/framework/wcf/feature-details/contracts.md)です。  
  
-   **サービス メタデータ**  
  
     WCF では、WSDL、XML スキーマ、Ws-policy などの業界標準で指定された形式を使用してサービス メタデータの公開をサポートします。 自動的に生成し、WCF サービスにアクセスするためのクライアントを構成するのには、このメタデータを使用できます。 メタデータは HTTP や HTTPS 上で、または Web サービス メタデータ交換標準を使用して公開できます。 詳細については、次を参照してください。[メタデータ](../../../docs/framework/wcf/feature-details/metadata.md)です。  
  
-   **データ コントラクト**  
  
     WCF を使用してビルドされるため、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]を適用するコントラクトを指定するコードに対応したメソッドも含まれています。 汎用的な型のコントラクトの 1 つにデータ コントラクトがあります。 本質的に、Visual C# または Visual Basic を使用してサービスをコード化した場合、データを処理する最も簡単な方法は、データ エンティティを表すクラスにデータ エンティティに属するプロパティを作成する方法です。 WCF には、この簡単な方法でデータを操作するための包括的なシステムが含まれています。 データを表すクラスを作成すると、設計したデータ型にクライアントが準拠できるメタデータがサービスによって自動生成されます。 詳細については、「[データコントラクトの使用](../../../docs/framework/wcf/feature-details/using-data-contracts.md)」を参照してください。  
  
-   **セキュリティ**  
  
     メッセージを暗号化してプライバシーを保護し、メッセージを受信する前にユーザーが自身を認証することを必須化することができます。 SSL や WS-SecureConversation などよく知られた標準を使用してセキュリティを実装できます。 詳細については、[セキュリティ](../../../docs/framework/wcf/feature-details/security.md)に関するページをご覧ください。  
  
-   **複数のトランスポートとエンコーディング**  
  
     メッセージは複数の組み込みトランスポート プロトコルおよびエンコーディングのいずれかを使用して送信できます。 最も一般的なプロトコルとエンコーディングは、テキスト エンコードを使用して、World Wide Web 上のハイパー テキスト転送プロトコル (HTTP) を使用して SOAP メッセージを送信します。 また、WCF over TCP、メッセージを送信する機能が名前付きパイプ、MSMQ です。 これらのメッセージはテキストとしてエンコードするか、最適化されたバイナリ形式を使用することができます。  バイナリ データは MTOM 標準を使用することで効率的に送信できます。 提供されているトランスポートまたはエンコーディングのいずれもニーズを満たさない場合は、独自のカスタム トランスポートまたはエンコーディングを作成できます。 トランスポートと WCF でサポートされているエンコーディングの詳細については、次を参照してください。[トランスポート](../../../docs/framework/wcf/feature-details/transports.md)です。  
  
-   **キューに置かれた信頼性のあるメッセージ**  
  
     WCF では、Ws-reliable Messaging 経由で実装され、MSMQ を使用して、信頼できるセッションを使用した信頼性の高いメッセージ交換をサポートします。 WCF で信頼性があり、キューに置かれたメッセージングのサポートの詳細については、次を参照してください。[キューと信頼できるセッション](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)です。  
  
-   **非揮発性メッセージ**  
  
     非揮発性メッセージは、通信の中断によって失われることがないメッセージです。 非揮発性メッセージ パターンのメッセージは常にデータベースに保存されます。 中断が発生した場合、接続復旧時にデータベースでメッセージの交換を再開できます。 Windows Workflow Foundation (WF) を使用して非揮発性メッセージを作成することもできます。 詳細については、次を参照してください。[ワークフロー サービス](../../../docs/framework/wcf/feature-details/workflow-services.md)です。  
  
-   **トランザクション**  
  
     WCF では、WS-AtomicTtransactions、<xref:System.Transactions> 名前空間の API、および Microsoft 分散トランザクション コーディネーターの 3 つのトランザクション モデルの 1 つを使用したトランザクションもサポートしています。  WCF でのサポートを参照してくださいトランザクションの詳細については[トランザクション](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md)です。  
  
-   **AJAX および REST サポート**  
  
     REST は、進化し続ける Web 2.0 テクノロジの一例です。 WCF は、SOAP エンベロープにラップされていない「書式なし」の XML データを処理するように設定します。 WCF は、ATOM (一般的な RSS 標準)、でも非 XML の形式など、JavaScript Object Notation (JSON) などの特定の XML 形式をサポートするために拡張することもできます。  
  
-   **機能拡張**  
  
     WCF アーキテクチャには、機能拡張ポイントの数があります。 追加の機能が必要になった場合、サービスの動作をカスタマイズできる多数のエントリ ポイントがあります。 詳細については、使用可能な機能拡張ポイントを参照してください[WCF の拡張](../../../docs/framework/wcf/extending/index.md)です。  
  
## <a name="wcf-integration-with-other-microsoft-technologies"></a>WCF と他のマイクロソフト テクノロジと統合  
 WCF は、柔軟なプラットフォームです。 この柔軟性を活かしてもいくつかの他の Microsoft 製品に WCF が使用されます。 WCF の基礎を理解すると、使用する場合はこれらの製品即時の利点があります。  
  
 WCF とペアにする最初のテクノロジは、Windows Workflow Foundation (WF) でした。 ワークフロー「アクティビティ」としてワークフローの手順をカプセル化することによってアプリケーションの開発を簡略化します。 最初のバージョンの Windows Workflow Foundation では、開発者は、ワークフローのホストを作成する必要があります。 Windows Workflow Foundation の次のバージョンは、WCF と統合されました。 任意のワークフローを簡単に、WCF サービスでホストを許可します。WF/WCF のプロジェクトの種類を自動的に選択してこれを行うで[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]です。  
  
 また、Microsoft BizTalk Server R2 を通信テクノロジとして WCF を利用します。 BizTalk は、1 つの標準化形式のデータを受け取り、別の形式に変換するように設計されています。 メッセージは、厳密なマッピングか、またはワークフロー エンジンなどの BizTalk 機能の 1 つを使用してメッセージを変換できる、中央管理のメッセージ ボックスに配信する必要があります。 BizTalk では、メッセージ ボックスにメッセージを配信 WCF 行基幹業務 (LOB) アダプターを使用できます。  
  
 Microsoft Silverlight は開発者がストリーミング ビデオなどメディアを多用する Web サイトを作成できる、相互運用が可能で充実した Web アプリケーションを作成するためのプラットフォームです。 バージョン 2 以降では、Silverlight が組み込まれている WCF を通信テクノロジに Silverlight アプリケーションが WCF エンドポイントを接続します。  
  
 [!INCLUDE[dublin](../../../includes/dublin-md.md)]アプリケーション サーバーは展開および WCF の通信を使用してアプリケーションを管理するために特別に作成します。 [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] WCF 対応アプリケーション向けに設計された豊富なツールと構成オプションが含まれています。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel>  
 [Windows Communication Foundation の基本概念](../../../docs/framework/wcf/fundamental-concepts.md)  
 [Windows Communication Foundation のアーキテクチャ](../../../docs/framework/wcf/architecture.md)  
 [ガイドラインとベスト プラクティス](../../../docs/framework/wcf/guidelines-and-best-practices.md)  
 [チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [ドキュメントのガイド](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [基本的な WCF プログラミング](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Windows Communication Foundation サンプル](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)
