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
# <a name="internet-protocol-version-6"></a><span data-ttu-id="8c37c-102">インターネット プロトコル バージョン 6</span><span class="sxs-lookup"><span data-stu-id="8c37c-102">Internet Protocol Version 6</span></span>
<span data-ttu-id="8c37c-103">インターネット プロトコル バージョン 6 (IPv6) は、インターネットのネットワーク層の標準プロトコルの新しいスイートです。</span><span class="sxs-lookup"><span data-stu-id="8c37c-103">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="8c37c-104">IPv6 は、アドレスの不足、セキュリティ、自動構成、拡張性などに関して、インターネット プロトコル スイートの現在のバージョン (IPv4) が抱える多くの問題を解決するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="8c37c-104">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="8c37c-105">IPv6 は、インターネットの機能を拡張して、ピア ツー ピア アプリケーションやモバイル アプリケーションなどの新しい種類のアプリケーションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="8c37c-105">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="8c37c-106">現在の IPv4 プロトコルの主な問題を次に示します。</span><span class="sxs-lookup"><span data-stu-id="8c37c-106">The following are the main issues of the current IPv4 protocol:</span></span>  
  
-   <span data-ttu-id="8c37c-107">アドレス空間の急減。</span><span class="sxs-lookup"><span data-stu-id="8c37c-107">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="8c37c-108">これが、複数のプライベート アドレスを 1 つのパブリック IP アドレスにマップするネットワーク アドレス変換器 (NAT) の使用につながってきました。</span><span class="sxs-lookup"><span data-stu-id="8c37c-108">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="8c37c-109">このメカニズムによって生じた主な問題は、処理オーバーヘッドとエンド ツー エンドの接続の欠如です。</span><span class="sxs-lookup"><span data-stu-id="8c37c-109">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
-   <span data-ttu-id="8c37c-110">階層サポートの不足。</span><span class="sxs-lookup"><span data-stu-id="8c37c-110">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="8c37c-111">IPv4 固有の定義済みクラス組織により、IPv4 には真の階層サポートが不足しています。</span><span class="sxs-lookup"><span data-stu-id="8c37c-111">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="8c37c-112">真にネットワーク トポロジをマップする方法で IP アドレスを構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="8c37c-112">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="8c37c-113">この重大な設計上の欠陥により、IPv4 パケットをインターネット上の任意の場所に配信するために大規模なルーティング テーブルが必要となっています。</span><span class="sxs-lookup"><span data-stu-id="8c37c-113">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
-   <span data-ttu-id="8c37c-114">複雑なネットワーク構成。</span><span class="sxs-lookup"><span data-stu-id="8c37c-114">Complex network configuration.</span></span>  
  
     <span data-ttu-id="8c37c-115">IPv4 では、アドレスを静的に、または DHCP などの構成プロトコルを使用して割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c37c-115">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="8c37c-116">理想的な状況では、ホストは DHCP インフラストラクチャの管理に依存する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8c37c-116">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="8c37c-117">代わりに、ホストが配置されているネットワーク セグメントに基づいてホスト自身で構成できます。</span><span class="sxs-lookup"><span data-stu-id="8c37c-117">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
-   <span data-ttu-id="8c37c-118">組み込み認証と機密性の不足。</span><span class="sxs-lookup"><span data-stu-id="8c37c-118">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="8c37c-119">IPv4 では、交換されるデータの認証または暗号化を提供する任意のメカニズムのサポートは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="8c37c-119">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="8c37c-120">IPv6 ではこれが変わります。</span><span class="sxs-lookup"><span data-stu-id="8c37c-120">This changes with IPv6.</span></span> <span data-ttu-id="8c37c-121">インターネット プロトコル セキュリティ (IPSec) は、IPv6 のサポート要件です。</span><span class="sxs-lookup"><span data-stu-id="8c37c-121">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="8c37c-122">新しいプロトコル スイートは、次の基本的な要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="8c37c-122">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
-   <span data-ttu-id="8c37c-123">大規模なルーティングと低いオーバーヘッドでのアドレス指定。</span><span class="sxs-lookup"><span data-stu-id="8c37c-123">Large-scale routing and addressing with low overhead.</span></span>  
  
-   <span data-ttu-id="8c37c-124">さまざまな接続状況の自動構成。</span><span class="sxs-lookup"><span data-stu-id="8c37c-124">Auto-configuration for various connecting situations.</span></span>  
  
-   <span data-ttu-id="8c37c-125">組み込み認証と機密性。</span><span class="sxs-lookup"><span data-stu-id="8c37c-125">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="8c37c-126">詳細については、「[IPv6 アドレス指定](../../../docs/framework/network-programming/ipv6-addressing.md)」、「[IPv6 のルーティング](../../../docs/framework/network-programming/ipv6-routing.md)」、「[IPv6 の自動構成](../../../docs/framework/network-programming/ipv6-auto-configuration.md)」、「[IPv6 の有効化と無効化](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md)」、および「[方法: IPv6 のサポートを有効にするようにコンピューター構成ファイルを変更する](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c37c-126">For more information, see [IPv6 Addressing](../../../docs/framework/network-programming/ipv6-addressing.md), [IPv6 Routing](../../../docs/framework/network-programming/ipv6-routing.md), [IPv6 Auto-Configuration](../../../docs/framework/network-programming/ipv6-auto-configuration.md), [Enabling and Disabling IPv6](../../../docs/framework/network-programming/enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="8c37c-127">参照</span><span class="sxs-lookup"><span data-stu-id="8c37c-127">References</span></span>  
 <span data-ttu-id="8c37c-128">インターネット技術標準化委員会サイト ([http://www.ietf.org](http://www.ietf.org/)) で検索できる厳選した RFC ドキュメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="8c37c-128">The following are selected RFC documents that you can find at the Internet Engineering Task Force site ([http://www.ietf.org](http://www.ietf.org/)):</span></span>  
  
-   <span data-ttu-id="8c37c-129">RFC 1287、Towards the Future Internet Architecture (将来のインターネットアーキテクチャに向けて)</span><span class="sxs-lookup"><span data-stu-id="8c37c-129">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
-   <span data-ttu-id="8c37c-130">RFC 1454、Comparison of Proposals for Next Version of IP (IP の次のバージョンのための提案の比較)</span><span class="sxs-lookup"><span data-stu-id="8c37c-130">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
-   <span data-ttu-id="8c37c-131">RFC 2373、IP Version 6 Addressing Architecture (IP バージョン 6 のアドレス指定アーキテクチャ)</span><span class="sxs-lookup"><span data-stu-id="8c37c-131">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
-   <span data-ttu-id="8c37c-132">RFC 2374、An IPv6 Aggregatable Global Unicast Address Format (IPv6 の集約可能なグローバル ユニキャスト アドレス形式)</span><span class="sxs-lookup"><span data-stu-id="8c37c-132">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="8c37c-133">[Technet の IPv6 分野](http://go.microsoft.com/fwlink/?LinkID=179658)でも IPv6 関連の情報を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="8c37c-133">You can also find IPv6-related information on the [IPv6 area on Technet](http://go.microsoft.com/fwlink/?LinkID=179658).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c37c-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c37c-134">See Also</span></span>  
 [<span data-ttu-id="8c37c-135">IPv6 ソケットのサンプル</span><span class="sxs-lookup"><span data-stu-id="8c37c-135">IPv6 Sockets Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=179568)  
 [<span data-ttu-id="8c37c-136">ネットワーク プログラミングのサンプル</span><span class="sxs-lookup"><span data-stu-id="8c37c-136">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="8c37c-137">ソケット</span><span class="sxs-lookup"><span data-stu-id="8c37c-137">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
