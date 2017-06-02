---
title: "インターネット プロトコル バージョン 6 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "IPv6、強化"
  - "IPv4"
  - "IPv6"
  - "インターネット プロトコル バージョン 6、強化"
  - "インターネット プロトコル バージョン 6"
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# インターネット プロトコル バージョン 6
Internet Protocol version 6 \(IPv6\) は、インターネットでのネットワーク層の標準プロトコル新しいスイートです。  IPv6、住所の枯渇、セキュリティ、自動設定、拡張性に関連してインターネット プロトコル Suite 現在のバージョンの複数の問題 \(IPv4 と呼ぶこともあります\) 決済する場合などに設計されています。  IPv6 は、新しい種類のピアツーピアおよび移動式アプリケーションを含む、アプリケーションを有効にするには、インターネット機能を展開します。  次に、期限内に IPv4 プロトコルの主な問題点です:  
  
-   住所領域のまとめます。枯渇。  
  
     これは、ネットワーク アドレスの訳者 \(NATs\) を使用して一つのパブリック IP アドレスにそのマップの複数の個人住所を導きました。  このメカニズムによって作成された主要な問題エンドツーエンドの接続および間接費の不足を処理します。  
  
-   階層の例の不足。  
  
     固有の定義済クラスの組織では、IPv4 が true の階層にサポートを持たないされます。  偽りのネットワーク トポロジをマップする方法で IP アドレスを含めることが不可能です。  この重要な設計上の欠陥には、工順テーブルの必要性をインターネットのすべての場所で IPv4 パケットの出荷を作成します。  
  
-   複合ネットワークのコンフィギュレーション。  
  
     IPv4 によって、住所が静的に割り当てる DHCP などのコンフィギュレーションのセキュリティを使用します。  理想的な状況では、ホストは DHCP の下部組織の管理に依存必要はありません。  代わりに、ネットワークのある区分に基づいて自体をコンフィギュレーションできます。  
  
-   ビルトインな認証および機密の不足。  
  
     IPv4 は、交換されたデータの認証または暗号化を提供するすべてのメカニズムにサポートは必要ではありません。  これは IPv6 に変更されます。  選択すると、IPv6 サポートする必要があります。  
  
 新しいプロトコルのスイートは、次の基本条件を満たす必要があります:  
  
-   間接費と、大規模な工順と住所。  
  
-   さまざまな接続ステータスの自動設定。  
  
-   ビルトインな認証および機密。  
  
 詳細については、「[IPv6 アドレス指定](../../../docs/framework/network-programming/ipv6-addressing.md)」、「[IPv6 のルーティング](../../../docs/framework/network-programming/ipv6-routing.md)」、「[IPv6 の自動構成](../../../docs/framework/network-programming/ipv6-auto-configuration.md)」、「[IPv6 の有効化と無効化](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md)」、および「[方法: IPv6 のサポートを有効にするようにコンピューター構成ファイルを変更する](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)」を参照してください。  
  
## 参照  
 次は、インターネット技術的なサービス委員会の拠点に表示できる、選択した RFC のドキュメントです \([http:\/\/www.ietf.org](http://www.ietf.org/)\) :  
  
-   将来のインターネット アーキテクチャに対する 1287 RFC。  
  
-   RFC 1454 の IP の次のバージョンの提案を比較。  
  
-   RFC 2373 の IP アドレスのバージョン 6 のアーキテクチャ。  
  
-   RFC 2374 の IPv6 の Aggregatable のグローバルなユニキャストの住所形式。  
  
 、の [Technet の IPv6 の領域](http://go.microsoft.com/fwlink/?LinkID=179658)IPv6 関連情報を確認できます。  
  
## 参照  
 [IPv6 のソケットのサンプル](http://go.microsoft.com/fwlink/?LinkID=179568)   
 [ネットワーク プログラミングのサンプル](../../../docs/framework/network-programming/network-programming-samples.md)   
 [ソケット](../../../docs/framework/network-programming/sockets.md)