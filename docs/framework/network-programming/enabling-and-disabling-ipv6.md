---
title: "IPv6 の有効化と無効化 | Microsoft Docs"
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
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# IPv6 の有効化と無効化
IPv6 をサポートする移動、オペレーティング システムとネットワーキングのクラスが正しくコンフィギュレーションされていることを確認するオペレーティング システムのバージョンを IPv6 プロトコルを使用するには、確認します。  
  
## コンフィギュレーションの手順  
 次の表に、さまざまなコンポーネントの一覧  
  
|オペレーティング システム IPv6 有効になるか。|IPv6 有効になるネットワーキングのクラスや。|説明|  
|--------------------------------|------------------------------|--------|  
|いいえ|いいえ|IPv6 の住所を分析できます。|  
|いいえ|はい|IPv6 の住所を分析できます。|  
|はい|いいえ|IPv6 の住所を分析し、名前の決済方法のマークを付けられない古い形式を使用して IPv6 の住所を決済できます。|  
|はい|はい|これらのマークされた古いを含むすべての方法を使用して IPv6 の住所を分析および決済できます。|  
  
 System.Net の名前空間のすべてのクラスの IPv6 のサポートを有効にするには、アプリケーションのコンピュータのコンフィギュレーション ファイルまたはコンフィギュレーション ファイルを変更する必要があるので注意してください。  アプリケーション用にコンフィギュレーション ファイルにコンピュータ上のコンフィギュレーション ファイルの優先順位があります。  
  
 Ipv6 サポートを有効にするコンピュータでコンフィギュレーション ファイルを *machine.config*は、変更方法の例では、[方法: Ipv6 サポートを有効にするコンピュータでコンフィギュレーション ファイルを変更します。](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)表示されます。  、IPv6 のサポートされているオペレーティング システムで有効であることを確認します。  
  
 .NET Framework にコンフィギュレーション ファイルで次のように設定されているコンポーネントの Switch があります。  
  
```  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 .NET Framework Version 1.1 が、以前の **ipv6 enabled**、コンポーネントの Switch の値はかどうか <xref:System.Net.Dns?displayProperty=fullName> クラスの返品 IPv6 の住所のメンバ指定します。  
  
 .NET Framework Version 2.0 と後で、<xref:System.Net.Dns?displayProperty=fullName> クラスのメンバについては、Windows が IPv6 をサポート \(たとえば、<xref:System.Net.Dns.GetHostEntry%2A?displayProperty=fullName> 方法\)、1 種類の制限の IPv6 の住所を返します。  DNS <xref:System.Net.Dns?displayProperty=fullName> の古い形式のメンバは、\(たとえば、<xref:System.Net.Dns.Resolve%2A?displayProperty=fullName> 方法\) ipv6 によって有効にした設定のコンフィギュレーション ファイルの値を読み、確認します。  
  
## 参照  
 [インターネット プロトコル バージョン 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)   
 [ソケット](../../../docs/framework/network-programming/sockets.md)   
 [ネットワーク設定スキーマ](../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [\<ipv6\> 要素 \(ネットワーク設定\)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)