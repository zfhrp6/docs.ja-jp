---
title: "インターネット プロトコル バージョン 6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e8ac63cae9d70f0249533848fa472da77f04b807
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="internet-protocol-version-6"></a>インターネット プロトコル バージョン 6
インターネット プロトコル バージョン 6 (IPv6) は、インターネットのネットワーク層の標準プロトコルの新しいスイートです。 IPv6 は、アドレスの不足、セキュリティ、自動構成、拡張性などに関して、インターネット プロトコル スイートの現在のバージョン (IPv4) が抱える多くの問題を解決するために設計されています。 IPv6 は、インターネットの機能を拡張して、ピア ツー ピア アプリケーションやモバイル アプリケーションなどの新しい種類のアプリケーションを有効にします。 現在の IPv4 プロトコルの主な問題を次に示します。  
  
-   アドレス空間の急減。  
  
     これが、複数のプライベート アドレスを 1 つのパブリック IP アドレスにマップするネットワーク アドレス変換器 (NAT) の使用につながってきました。 このメカニズムによって生じた主な問題は、処理オーバーヘッドとエンド ツー エンドの接続の欠如です。  
  
-   階層サポートの不足。  
  
     IPv4 固有の定義済みクラス組織により、IPv4 には真の階層サポートが不足しています。 真にネットワーク トポロジをマップする方法で IP アドレスを構成することはできません。 この重大な設計上の欠陥により、IPv4 パケットをインターネット上の任意の場所に配信するために大規模なルーティング テーブルが必要となっています。  
  
-   複雑なネットワーク構成。  
  
     IPv4 では、アドレスを静的に、または DHCP などの構成プロトコルを使用して割り当てる必要があります。 理想的な状況では、ホストは DHCP インフラストラクチャの管理に依存する必要はありません。 代わりに、ホストが配置されているネットワーク セグメントに基づいてホスト自身で構成できます。  
  
-   組み込み認証と機密性の不足。  
  
     IPv4 では、交換されるデータの認証または暗号化を提供する任意のメカニズムのサポートは必要ありません。 IPv6 ではこれが変わります。 インターネット プロトコル セキュリティ (IPSec) は、IPv6 のサポート要件です。  
  
 新しいプロトコル スイートは、次の基本的な要件を満たす必要があります。  
  
-   大規模なルーティングと低いオーバーヘッドでのアドレス指定。  
  
-   さまざまな接続状況の自動構成。  
  
-   組み込み認証と機密性。  
  
 詳細については、「[IPv6 アドレス指定](../../../docs/framework/network-programming/ipv6-addressing.md)」、「[IPv6 のルーティング](../../../docs/framework/network-programming/ipv6-routing.md)」、「[IPv6 の自動構成](../../../docs/framework/network-programming/ipv6-auto-configuration.md)」、「[IPv6 の有効化と無効化](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md)」、および「[方法: IPv6 のサポートを有効にするようにコンピューター構成ファイルを変更する](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)」を参照してください。  
  
## <a name="references"></a>参照  
 インターネット技術標準化委員会サイト ([http://www.ietf.org](http://www.ietf.org/)) で検索できる厳選した RFC ドキュメントを次に示します。  
  
-   RFC 1287、Towards the Future Internet Architecture (将来のインターネットアーキテクチャに向けて)  
  
-   RFC 1454、Comparison of Proposals for Next Version of IP (IP の次のバージョンのための提案の比較)  
  
-   RFC 2373、IP Version 6 Addressing Architecture (IP バージョン 6 のアドレス指定アーキテクチャ)  
  
-   RFC 2374、An IPv6 Aggregatable Global Unicast Address Format (IPv6 の集約可能なグローバル ユニキャスト アドレス形式)  
  
 [Technet の IPv6 分野](http://go.microsoft.com/fwlink/?LinkID=179658)でも IPv6 関連の情報を見つけることができます。  
  
## <a name="see-also"></a>関連項目  
 [IPv6 ソケットのサンプル](http://go.microsoft.com/fwlink/?LinkID=179568)  
 [ネットワーク プログラミングのサンプル](../../../docs/framework/network-programming/network-programming-samples.md)  
 [ソケット](../../../docs/framework/network-programming/sockets.md)
