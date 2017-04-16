---
title: "IPv6 および Teredo を使用した NAT トラバーサル | Microsoft Docs"
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
ms.assetid: 568cd245-3300-49ef-a995-d81bf845d961
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# IPv6 および Teredo を使用した NAT トラバーサル
ネットワーク アドレス変換 \(NAT\) の横断をサポートする改善が行われた。  これらの変更は、IPv6 と Teredo 用に設計されていますが、技術にトンネルを掘る他の IP に、適用されるです。  これらの改善は <xref:System.Net> および関連する名前空間のクラスに影響します。  
  
 技術にトンネルを掘る IP の使用を計画するこれらの変更は、クライアントとサーバー アプリケーションに影響を与える可能性があります。  
  
 サポート NAT.横断への変更は、.NET Framework Version 4.を使用してアプリケーションにのみ使用できます。  これらの機能は、.NET Framework の以前のバージョンでは使用できません。  
  
## 概要  
 Internet Protocol version 4 \(IPv4\) は、32 ビットのコードと IPv4 の住所をで定義します。  したがって、IPv4 は、約 40億固有の IP アドレス \(2^32\) がサポートされます。  90 時間に配置されたインターネット上のコンピュータおよびネットワーク デバイスの数として IPv4 の住所領域の限度が明確になります。  
  
 IPv4 の有効期間を延長するために使用されている技術の 1 が、単一の固有パブリック IP アドレスが複数のプライベート IP アドレス \(プライベート イントラネット\) を表すように NAT を展開します。  NAT.デバイスの後のプライベート IP アドレスは、パブリック IPv4 の住所を共有します。  NAT.デバイスは、専用のハードウェア デバイス \(低な無線アクセス ポイントおよびルーターなど\) または NAT を提供するサービスを実行しているコンピュータである場合があります。  この、各種の IP アドレスのデバイスまたはサービスは、インターネットをプライベート イントラネット間の IP のネットワーク パケットを変換します。  
  
 この設定は、プライベート イントラネットで実行されるインターネット他の IP アドレス \(通常は\) サーバーに要求を送信クライアント アプリケーションの場合によくあります。  応答を送信または応答することがわかっている戻す場合 NAT.サーバーまたはデバイスがクライアントのマッピングその要求を保持することができます。  ただし、この設定は NAT.デバイスの後でプライベート イントラネットで実行されるサービスを提供するとともにそばパケット聴覚を立て、対応するアプリケーションの問題を提起します。  これはピアツーピア アプリケーション用に、ケースです。  
  
 IPv6 プロトコルは 128 ビットのコードと IPv4 の住所をで定義します。  したがって、IPv6 は非常に大きな 3.2 x 10^38 個の固有 IP アドレス　\(2^128 個\) をサポートします。  この住所領域のサイズによって、一意な住所が許可されるインターネットに関連するすべてのデバイスにできます。  この問題があります。  世界の大部分はまだ IPv4 のみ使用します。  特に、既存のルーター複数の会社と小世帯と、組織が使用する無線アクセス ポイントは IPv6 はサポートされません。  これらの顧客に使用するインターネット サービス プロバイダが IPv6 のサポートをサポートしていませんとコンフィギュレーションしていません。  
  
 複数の IPv6 の切り替えテクノロジは IPv4 のパケットの IPv6 の住所にトンネルを掘るは、セキュリティ面。  これらのテクノロジには、他の IPv6 のネットワークに到達するため IPv6 のネットワーク ホストが IP4 をスキャンする必要がある場合 6to4、ISATAP とユニキャストの IPv6 のトラフィックに住所指定およびホストでホストの自動トンネリングを提供する Teredo のトンネルが含まれます。  パケットの IPv6 は IPv4 のパケットとしてトンネルを掘られて送信されます。  NAT.デバイスを使用して IPv6 の住所の NAT.横断ようにするトンネリング テクノロジが使用されます。  
  
 Teredo は IPv4 のネットワークに IPv6 の接続が移動 IPv6 の切り替えテクノロジの 1 つです。  Teredo は、インターネット技術的な委員会 \(IETF\) が発行される RFC 4380 に記載されます。  Windows XP SP2 が範囲 2001:0::\/32 パブリック IPv6 の住所を提供する仮想の Teredo アダプタに、後でサポートを提供します。  この IPv6 の住所は、インターネットからフォワードに接続そば聴覚を立てるには、リッスン サービスに接続する IPv6 によって有効にするクライアントに提供できます。  これは、問題をからアプリケーションで IPv6 の Teredo の住所を使用してに接続できるため、アプリケーションを NAT.デバイスの後のコンピュータ住所をリリースします。  
  
## NAT.横断と Teredo をサポートする改良  
 改良は NAT.横断をサポートするための <xref:System.Net>、<xref:System.Net.NetworkInformation>と IPv6 と Teredo を使用して <xref:System.Net.Sockets> の名前空間に追加されます。  
  
 複数の方法は <xref:System.Net.NetworkInformation.IPGlobalProperties?displayProperty=fullName> クラスでホストのユニキャストの IP アドレスの一覧を取得するために追加されます。  <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A> 方法がローカル コンピュータの安定したユニキャストの IP アドレスのテーブルを取得する非同期要求されます。  <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A> 方法がローカル コンピュータの安定したユニキャストの IP アドレスのテーブルを取得する保留中非同期要求を終了。  <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A> 方法は、アドレス テーブルを必要に応じて紹介するまで待機するローカル コンピュータの安定したユニキャストの IP アドレスのテーブルを同期取得する要求です。  
  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=fullName> のプロパティが <xref:System.Net.IPAddress> が IPv6 の Teredo 住所であるかどうかを判断するために使用できます。  
  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A> のプロパティを添付これらの新しい <xref:System.Net.NetworkInformation.IPGlobalProperties> クラスの方法を使用して簡単に Teredo の住所を検索するアプリケーションができます。  アプリケーションはリモート アプリケーションにこの情報が含まれている場合に保管場所の Teredo の住所を従業員全体に知らせたくない場合にのみ必要があります。通常  たとえば、ピアツーピア アプリケーションは、アプリケーション配送を有効にする場合は、他に凝視するそれらをようにするマッチメーク サーバーに IPv6 すべての住所を送信する場合があります。  
  
 アプリケーションは保管場所の住所 Teredo のではなく <xref:System.Net.IPAddress.IPv6Any?displayProperty=fullName> のリッスンは、リッスン サービスを設定する必要があります。  したがって、リモート クライアントまたはピアがリッスン サービスのホストに直接 IPv6 の工順がある場合は、クライアントまたはピア IPv6 を使用してに直接接続し、を Teredo パケットにトンネルを掘るに使用する必要がない場合。  
  
 TCP のアプリケーション用に、<xref:System.Net.Sockets.TcpListener?displayProperty=fullName> クラスに NAT.横断を有効にする <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A> の方法があります。  UDP アプリケーションの場合は、<xref:System.Net.Sockets.UdpClient?displayProperty=fullName> クラスに NAT.横断を有効にする <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A> の方法があります。  
  
 <xref:System.Net.Sockets.Socket?displayProperty=fullName> を使用し、関連する <xref:System.Net.Sockets.Socket.GetSocketOption%2A> クラス、および <xref:System.Net.Sockets.Socket.SetSocketOption%2A> 方法がの <xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName> ソケット オプションおよび照会するに使用できるアプリケーションに対して有効または NAT.横断を無効にします。  
  
## 参照  
 <xref:System.Net.IPAddress.IsIPv6Teredo%2A?displayProperty=fullName>   
 <xref:System.Net.NetworkInformation.IPGlobalProperties.BeginGetUnicastAddresses%2A?displayProperty=fullName>   
 <xref:System.Net.NetworkInformation.IPGlobalProperties.EndGetUnicastAddresses%2A?displayProperty=fullName>   
 <xref:System.Net.NetworkInformation.IPGlobalProperties.GetUnicastAddresses%2A?displayProperty=fullName>   
 <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=fullName>   
 <xref:System.Net.Sockets.Socket.SetIPProtectionLevel%2A?displayProperty=fullName>   
 <xref:System.Net.Sockets.TcpListener.AllowNatTraversal%2A?displayProperty=fullName>   
 <xref:System.Net.Sockets.UdpClient.AllowNatTraversal%2A?displayProperty=fullName>