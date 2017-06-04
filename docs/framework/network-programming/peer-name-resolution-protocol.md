---
title: "Peer Name Resolution Protocol | Microsoft Docs"
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
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# Peer Name Resolution Protocol
ID の名前またはそのほかの型のそれぞれのネットワーク上の場所 \(アドレスとポート、プロトコル\) を決済するピアツーピア環境ピアの使用、特定の名前の決済システム。  ピア以前の名前解決策は、ドメイン ネーム システム内の一時本来 \(DNS\) 接続、他の短所が複雑になります。  
  
 Microsoft® Windows® のピアツーピア ネットワーキングのプラットフォーム ピア決済 Protocol \(PNRP\) 名は、最初に Windows XP に対して作成され、Windows Vista の™で更新される安全で、スケーラブル、動的名前の登録と名前決済のプロトコルこの問題を解決します。  PNRP の作業アプリケーション開発者向けの還付の新しい可能性を作成する従来の名前の決済システムと非常別々に。  
  
 PNRP を使用すると、ピアの名前は、機械の機械、または個々のアプリケーションまたはサービス適用できます。  ピア決済の名前、住所、ポートに公開拡張積荷が含まれます。  このシステムのメリットは、フォールト トレランス、その古い住所を戻さないボトルネックと名前が含まれません;決済 プロトコル携帯電話にユーザーを検索する優秀な解決策をします。  
  
 セキュリティの点で、ピアの名前は保護された \(protected\) または保証のない公開できます \(unprotected\)。  PNRP はからかうに対して安全なピアの名前を保護するために公開キーを使用してインターネット; コンピューターとサービスは、PNRP と名前を付けることができます。  
  
-   ピア名決済プロトコルは、次のプロパティを表示します:  
  
-   配分するとほとんど完全に serverless。  サーバーはブートストラップ プロセスに限られます。  
  
-   サード パーティの介入なしに、名前書をセキュリティ保護します。  DNS 名書とは異なり、PNRP の名前は、当座書と財務の原価を伴わないです。  
  
-   古い住所の決済されないリアルタイムの PNRP の更新。  
  
-   PNRP での名前の解決策は、コンピュータ以外に、サービスの名前決済を許可して、拡張。  
  
## System.Net.PeerToPeer の名前空間  
  
-   PNRP 機能は、.NET Framework Version 3.5 内の <xref:System.Net.PeerToPeer> の名前空間によって定義されます。  これは、使用可能な PNRP のサービスを使用するピアの名前を登録し、解決するために使用できる一連の型を提供します。  
  
-   \(PNRP と注文のピアのリゾルバーは <xref:System.ServiceModel.PeerResolvers> の名前空間に表示される型を使用して作成され、インスタンスを作成できます\)。  
  
-   次のように使用可能な PNRP のサービスを使用する名前を登録し、決済する基本的なタイプがあります:  
  
-   :<xref:System.Net.PeerToPeer.Cloud>範囲など、使用可能な PNRP のクラウドを表す情報を定義します。  
  
-   :<xref:System.Net.PeerToPeer.PeerName>クラウド内のピアを登録し、その後解決するために使用できるピアの名前を定義します。  
  
-   :<xref:System.Net.PeerToPeer.PeerNameRecord>ピアが連絡できるネットワーク エンドポイントを含む、ピアの登録情報を含む PNRP のクラウド レコードを定義します。  
  
-   :<xref:System.Net.PeerToPeer.PeerNameRegistration>方法を含むピア名の登録プロセスを、ピアの名前の登録を開始および停止するに定義します。  
  
-   :<xref:System.Net.PeerToPeer.PeerNameResolver>決済の同期、非同期な方法をエンドポイントに含めるネットワーク ピア名を解決するためのプロセスを定義します。  
  
## 参照  
 <xref:System.ServiceModel.PeerResolvers>   
 <xref:System.Net.PeerToPeer>   
 [ネットワーク プログラミングのサンプル](../../../docs/framework/network-programming/network-programming-samples.md)   
 [サンプルのピアツーピア技術](http://go.microsoft.com/fwlink/?LinkID=179571)