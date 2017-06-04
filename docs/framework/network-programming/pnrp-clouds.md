---
title: "PNRP クラウド | Microsoft Docs"
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
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
caps.latest.revision: 4
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 4
---
# PNRP クラウド
PNRP 「」クラウドは、ネットワークを通じて互いに通信できる一連のノードを表します。  " 「クラウド ピア メッシュ」および「」ピアツーピア グラフとは」、「同義です。  
  
 ノード間の通信は、異なるクラウドにまたがって行うことはできません。  <xref:System.Net.PeerToPeer.Cloud> インスタンスは、大文字と小文字が区別される名前によって一意に識別されます。  1 つのピアまたはノードを、複数のクラウドに割り当てることができます。  
  
 クラウドは、ネットワーク インターフェイスと密接な関係があります。  別々のサブネットにアタッチされた 2 枚のネットワーク カードを搭載しているマルチホーム コンピューターでは、3 つのクラウドが返されます。インターフェイスごとの各リンクローカル アドレスに対して 1 つずつのクラウドと、1 つのグローバル スコープ クラウドです。  
  
 PNRP の使用は 3 範囲は互いに検索できるコンピュータ グループ範囲にある「」を曇らせます:  
  
-   グローバルなクラウドは、グローバルな IPv6 の住所の範囲とグローバル アドレスに対応し、全体の IPv6 のインターネットすべてのコンピュータを表します。  単一のグローバルなクラウドだけです。  
  
-   ローカルのリンク クラウド リンクはローカルの IPv6 の住所の範囲とリンク ローカルの住所に対応します。  ローカルのリンク クラウドは、ローカルに関連付けられているサブネットとして通常同じである特定のリンクではです。  複数のローカルのリンク クラウドがあります。  
  
 3 番目のクラウド、サービス拠点特定のクラウドは、サービスの拠点 IPv6 の住所の範囲とサービス拠点ローカルの住所に対応します。  このクラウドは、PNRP でサポートされているが、非難されています。  
  
## クラウド  
 PNRP のクラウドは <xref:System.Net.PeerToPeer.Cloud> クラスのインスタンスで表されます。  クラウド グループは <xref:System.Net.PeerToPeer.CloudCollection> の enumerable クラスのインスタンスを表しますピアを使用します。  期限内なピアにわかる <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> の静的な方法を呼び出し、PNRP のクラウドの集合取得できます。  
  
 個々のクラウドに 256 文字は Unicode の文字列として表示される一意の名前があります。  これらの名前は、前の範囲とともに、クラウド クラスの固有インスタンスの製造に使用されます。  キューブのインスタンスは耐久性がある使用する XML され、再構築することができます。  
  
 一度クラウドのインスタンスが作成されます既知のピアのメッシュを作成する場合は、または派生、ピアの名前は、に登録できます。  
  
## 参照  
 <xref:System.Net.PeerToPeer.Cloud>   
 [Peer Name Resolution Protocol](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)