---
title: .NET Framework のネットワーク プログラミング
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: efecd4f2858843a2401e3d69538d87f92475b816
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397898"
---
# <a name="network-programming-in-the-net-framework"></a><span data-ttu-id="f06f6-102">.NET Framework のネットワーク プログラミング</span><span class="sxs-lookup"><span data-stu-id="f06f6-102">Network Programming in the .NET Framework</span></span>
<span data-ttu-id="f06f6-103">Microsoft .NET Framework は、アプリケーションにすばやく簡単に統合できる、複数層の拡張可能なインターネット サービスのマネージ実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-103">The Microsoft .NET Framework provides a layered, extensible, and managed implementation of Internet services that can be quickly and easily integrated into your applications.</span></span> <span data-ttu-id="f06f6-104">ネットワーク アプリケーションは、プラグ可能なプロトコルを基に自動的に新しいインターネット プロトコルを使用するように作成することも、ソケット レベルでネットワークを使用できるように Windows ソケット インターフェイスのマネージ実装を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f06f6-104">Your network applications can build on pluggable protocols to automatically take advantage of new Internet protocols, or they can use a managed implementation of the Windows socket interface to work with the network on the socket level.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f06f6-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f06f6-105">In This Section</span></span>  

 [<span data-ttu-id="f06f6-106">プラグ可能なプロトコルの概要</span><span class="sxs-lookup"><span data-stu-id="f06f6-106">Introducing Pluggable Protocols</span></span>](../../../docs/framework/network-programming/introducing-pluggable-protocols.md)  
 <span data-ttu-id="f06f6-107">必要なアクセス プロトコルに関係なく、インターネット リソースにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-107">Describes how to access an Internet resource without regard to the access protocol that it requires.</span></span>  
  
 [<span data-ttu-id="f06f6-108">データの要求</span><span class="sxs-lookup"><span data-stu-id="f06f6-108">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)  
 <span data-ttu-id="f06f6-109">プラグ可能なプロトコルを使用して、インターネット リソースにデータをアップロードしたり、ダウンロードしたりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-109">Explains how to use pluggable protocols to upload and download data from Internet resources.</span></span>  
  
 [<span data-ttu-id="f06f6-110">プラグ可能なプロトコルのプログラミング</span><span class="sxs-lookup"><span data-stu-id="f06f6-110">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)  
 <span data-ttu-id="f06f6-111">プロトコル固有のクラスを派生させて、プラグ可能なプロトコルを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-111">Explains how to derive protocol-specific classes to implement pluggable protocols.</span></span>  
  
 [<span data-ttu-id="f06f6-112">アプリケーション プロトコルの使用</span><span class="sxs-lookup"><span data-stu-id="f06f6-112">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 <span data-ttu-id="f06f6-113">TCP、UDP、HTTP などのネットワーク プロトコルを利用するアプリケーションのプログラミングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-113">Describes programming applications that take advantage of network protocols such as TCP, UDP, and HTTP.</span></span>  
  
 [<span data-ttu-id="f06f6-114">インターネット プロトコル バージョン 6</span><span class="sxs-lookup"><span data-stu-id="f06f6-114">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 <span data-ttu-id="f06f6-115">インターネット プロトコル スイート (IPv4) の現在のバージョンより優れたインターネット プロトコル Version 6 (IPv6) の利点について説明し、IPv6 のアドレス指定、ルーティングおよび自動構成、および IPv6 を有効/無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-115">Describes the advantages of Internet Protocol version 6 (IPv6) over the current version of the Internet Protocol suite (IPv4), describes IPv6 addressing, routing and auto-configuration, and how to enable and disable IPv6.</span></span>  
  
 [<span data-ttu-id="f06f6-116">インターネット アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="f06f6-116">Configuring Internet Applications</span></span>](../../../docs/framework/network-programming/configuring-internet-applications.md)  
 <span data-ttu-id="f06f6-117">.NET Framework 構成ファイルを使用して、インターネット アプリケーションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-117">Explains how to use the .NET Framework configuration files to configure Internet applications.</span></span>  
  
 [<span data-ttu-id="f06f6-118">.NET Framework のネットワークのトレース</span><span class="sxs-lookup"><span data-stu-id="f06f6-118">Network Tracing in the .NET Framework</span></span>](../../../docs/framework/network-programming/network-tracing.md)  
 <span data-ttu-id="f06f6-119">.NET Framework のネットワークのトレースを使用して、メソッド呼び出しについての情報、およびマネージ アプリケーションによって生成されるネットワーク トラフィックについての情報を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-119">Explains how to use network tracing to get information about method invocations and network traffic generated by a managed application.</span></span>  
  
 [<span data-ttu-id="f06f6-120">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="f06f6-120">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)  
 <span data-ttu-id="f06f6-121"><xref:System.Net.WebClient?displayProperty=nameWithType>、<xref:System.Net.WebRequest?displayProperty=nameWithType>、および <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> クラスを使用するアプリケーションでキャッシュを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-121">Describes how to use caching for applications that use the <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType>, and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.</span></span>  
  
 [<span data-ttu-id="f06f6-122">ネットワーク プログラミングにおけるセキュリティ</span><span class="sxs-lookup"><span data-stu-id="f06f6-122">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)  
 <span data-ttu-id="f06f6-123">標準のインターネット セキュリティと認証の手法を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-123">Describes how to use standard Internet security and authentication techniques.</span></span>  
  
 [<span data-ttu-id="f06f6-124">System.Net クラスのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="f06f6-124">Best Practices for System.Net Classes</span></span>](../../../docs/framework/network-programming/best-practices-for-system-net-classes.md)  
 <span data-ttu-id="f06f6-125">インターネット アプリケーションを最大限に活用するためのヒントとテクニックを紹介します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-125">Provides tips and tricks for getting the most out of your Internet applications.</span></span>  
  
 [<span data-ttu-id="f06f6-126">プロキシを介したインターネットへのアクセス</span><span class="sxs-lookup"><span data-stu-id="f06f6-126">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 <span data-ttu-id="f06f6-127">プロキシの設定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-127">Describes how to configure proxies.</span></span>  
  
 [<span data-ttu-id="f06f6-128">ネットワーク情報</span><span class="sxs-lookup"><span data-stu-id="f06f6-128">NetworkInformation</span></span>](../../../docs/framework/network-programming/networkinformation.md)  
 <span data-ttu-id="f06f6-129">ネットワーク イベント、変更、統計、およびプロパティの情報を収集する方法について説明し、<xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> クラスを使用してリモート ホストに到達可能であるかどうかを判定する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-129">Describes how to gather information about network events, changes, statistics, and properties and also explains how to determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
 [<span data-ttu-id="f06f6-130">バージョン 2.0 での System.Uri 名前空間の変更</span><span class="sxs-lookup"><span data-stu-id="f06f6-130">Changes to the System.Uri namespace in Version 2.0</span></span>](../../../docs/framework/network-programming/changes-to-the-system-uri-namespace-in-version-2-0.md)  
 <span data-ttu-id="f06f6-131">Version 2.0 で正しくない動作を修正し、使いやすさを改善し、セキュリティを強化するために <xref:System.Uri?displayProperty=nameWithType> クラスに加えられたいくつかの変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-131">Describes several changes made to the <xref:System.Uri?displayProperty=nameWithType> class in Version 2.0 to fixed incorrect behavior, enhance usability, and enhance security.</span></span>  
  
 [<span data-ttu-id="f06f6-132">System.Uri での International Resource Identifier のサポート</span><span class="sxs-lookup"><span data-stu-id="f06f6-132">International Resource Identifier Support in System.Uri</span></span>](../../../docs/framework/network-programming/international-resource-identifier-support-in-system-uri.md)  
 <span data-ttu-id="f06f6-133">Version 3.5、3.0 SP1、および 2.0 SP1 で、International Resource Identifier (IRI) および国際化ドメイン名 (IDN) をサポートするために、<xref:System.Uri?displayProperty=nameWithType> クラスに追加された強化機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-133">Describes enhancements to the <xref:System.Uri?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 for International Resource Identifier (IRI) and Internationalized Domain Name (IDN) support.</span></span>  
  
 [<span data-ttu-id="f06f6-134">バージョン 3.5 のソケット パフォーマンスの強化</span><span class="sxs-lookup"><span data-stu-id="f06f6-134">Socket Performance Enhancements in Version 3.5</span></span>](../../../docs/framework/network-programming/socket-performance-enhancements-in-version-3-5.md)  
 <span data-ttu-id="f06f6-135">Version 3.5、3.0 SP1、および 2.0 SP1 で、<xref:System.Net.Sockets.Socket?displayProperty=nameWithType> クラスに追加された一連の強化機能について説明します。これらの機能によって、目的に特化した高パフォーマンスのソケット アプリケーションで使用できる代替非同期パターンが提供されます。</span><span class="sxs-lookup"><span data-stu-id="f06f6-135">Describes a set of enhancements to the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 that provide an alternative asynchronous pattern that can be used by specialized high-performance socket applications.</span></span>  
  
 [<span data-ttu-id="f06f6-136">ピア名解決プロトコル</span><span class="sxs-lookup"><span data-stu-id="f06f6-136">Peer Name Resolution Protocol</span></span>](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)  
 <span data-ttu-id="f06f6-137">Version 3.5 で、ピア名解決プロトコル (PNRP)、サーバーを使用しない動的な名前登録、および名前解決プロトコルをサポートするために追加されたサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-137">Describes support added in Version 3.5 to support the Peer Name Resolution Protocol (PNRP), a serverless and dynamic name registration and name resolution protocol.</span></span> <span data-ttu-id="f06f6-138">これらの新機能は、<xref:System.Net.PeerToPeer?displayProperty=nameWithType> 名前空間によってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f06f6-138">These new features are supported by the <xref:System.Net.PeerToPeer?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="f06f6-139">ピアツーピア コラボレーション</span><span class="sxs-lookup"><span data-stu-id="f06f6-139">Peer-to-Peer Collaboration</span></span>](../../../docs/framework/network-programming/peer-to-peer-collaboration.md)  
 <span data-ttu-id="f06f6-140">Version 3.5 で、PNRP に基づくピア ツー ピア コラボレーションをサポートするために追加されたサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-140">Describes support added in Version 3.5 to support the Peer-to-Peer Collaboration that builds on PNRP.</span></span> <span data-ttu-id="f06f6-141">これらの新機能は、<xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> 名前空間によってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f06f6-141">These new features are supported by the <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="f06f6-142">バージョン 3.5 SP1 における HttpWebRequest の NTLM 認証への変更</span><span class="sxs-lookup"><span data-stu-id="f06f6-142">Changes to NTLM authentication for HttpWebRequest in Version 3.5 SP1</span></span>](../../../docs/framework/network-programming/changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 <span data-ttu-id="f06f6-143">System.Net 名前空間の <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>、<xref:System.Net.HttpListener?displayProperty=nameWithType>、<xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>、および関連クラスによる統合 Windows 認証の処理方法に影響を与える、Version 3.5 SP1 で行われたセキュリティの変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-143">Describes security changes made in Version 3.5 SP1 that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the System.Net namespace.</span></span>  
  
 [<span data-ttu-id="f06f6-144">統合 Windows 認証と拡張保護</span><span class="sxs-lookup"><span data-stu-id="f06f6-144">Integrated Windows Authentication with Extended Protection</span></span>](../../../docs/framework/network-programming/integrated-windows-authentication-with-extended-protection.md)  
 <span data-ttu-id="f06f6-145"><xref:System.Net.HttpWebRequest?displayProperty=nameWithType> 名前空間および関連名前空間の <xref:System.Net.HttpListener?displayProperty=nameWithType>、<xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>、<xref:System.Net.Security.SslStream?displayProperty=nameWithType>、<xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>、<xref:System.Net?displayProperty=nameWithType>、および関連クラスによる統合 Windows 認証の処理方法に影響を与える、拡張保護用の強化機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-145">Describes enhancements for extended protection that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the <xref:System.Net?displayProperty=nameWithType> and related namespaces.</span></span>  
  
 [<span data-ttu-id="f06f6-146">IPv6 および Teredo を使用した NAT トラバーサル</span><span class="sxs-lookup"><span data-stu-id="f06f6-146">NAT Traversal using IPv6 and Teredo</span></span>](../../../docs/framework/network-programming/nat-traversal-using-ipv6-and-teredo.md)  
 <span data-ttu-id="f06f6-147">IPv6 および Teredo を使用する NAT トラバースをサポートするために、<xref:System.Net?displayProperty=nameWithType>、<xref:System.Net.NetworkInformation?displayProperty=nameWithType>、および <xref:System.Net.Sockets?displayProperty=nameWithType> 名前空間に追加された強化機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-147">Describes enhancements added to the <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType>, and <xref:System.Net.Sockets?displayProperty=nameWithType> namespaces to support NAT traversal using IPv6 and Teredo.</span></span>  
  
 [<span data-ttu-id="f06f6-148">Windows ストア アプリのネットワーク分離</span><span class="sxs-lookup"><span data-stu-id="f06f6-148">Network Isolation for Windows Store Apps</span></span>](../../../docs/framework/network-programming/network-isolation-for-windows-store-apps.md)  
 <span data-ttu-id="f06f6-149"><xref:System.Net>、 <xref:System.Net.Http>、および <xref:System.Net.Http.Headers> 名前空間のクラスを [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリケーションで使用したときのネットワーク分離の影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-149">Describes the impact of network isolation when classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces are used in [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="f06f6-150">ネットワーク プログラミングのサンプル</span><span class="sxs-lookup"><span data-stu-id="f06f6-150">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 <span data-ttu-id="f06f6-151"><xref:System.Net>、 <xref:System.Net.Cache>、 <xref:System.Net.Configuration>、 <xref:System.Net.Mail>、 <xref:System.Net.Mime>、 <xref:System.Net.NetworkInformation>、 <xref:System.Net.PeerToPeer>、 <xref:System.Net.Security>、 <xref:System.Net.Sockets> 名前空間のクラスを使用する、ダウンロード可能なネットワーク プログラミング サンプルへのリンク。</span><span class="sxs-lookup"><span data-stu-id="f06f6-151">Links to downloadable network programming samples that use classes in the <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> namespaces.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f06f6-152">参照</span><span class="sxs-lookup"><span data-stu-id="f06f6-152">Reference</span></span>  
 <xref:System.Net?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-153">最近のネットワークで使用されている多くのプロトコル用の単純なプログラミング インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-153">Provides a simple programming interface for many of the protocols used on networks today.</span></span> <span data-ttu-id="f06f6-154">この名前空間の <xref:System.Net.WebRequest?displayProperty=nameWithType> および <xref:System.Net.WebResponse?displayProperty=nameWithType> クラスは、プラグ可能なプロトコルの基礎です。</span><span class="sxs-lookup"><span data-stu-id="f06f6-154">The <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.WebResponse?displayProperty=nameWithType> classes in this namespace are the basis for pluggable protocols.</span></span>  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-155">取得したリソースのキャッシュ ポリシーを <xref:System.Net.WebRequest?displayProperty=nameWithType> クラスおよび <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> クラスを使用して定義するために使用する型および列挙体を定義します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-155">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.</span></span>  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-156">アプリケーションが System.Net 名前空間の構成設定にプログラムでアクセスして更新するために使用するクラス。</span><span class="sxs-lookup"><span data-stu-id="f06f6-156">Classes that applications use to programmatically access and update configuration settings for the System.Net namespaces.</span></span>  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-157">最新の HTTP アプリケーション用のプログラミング インターフェイスを提供するクラス。</span><span class="sxs-lookup"><span data-stu-id="f06f6-157">Classes that provides a programming interface for modern HTTP applications.</span></span>  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-158"><xref:System.Net.Http?displayProperty=nameWithType> 名前空間で使用される HTTP ヘッダーのコレクションのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-158">Provides support for collections of HTTP headers used by the <xref:System.Net.Http?displayProperty=nameWithType> namespace</span></span>  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-159">SMTP プロトコルを使用してメールを作成および送信するクラス。</span><span class="sxs-lookup"><span data-stu-id="f06f6-159">Classes to compose and send mail using the SMTP protocol.</span></span>  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-160">Defines types that are used to represent Multipurpose Internet Mail Exchange (MIME) headers used by classes in the <xref:System.Net.Mail?displayProperty=nameWithType> 名前空間のクラスが、MIME (Multipurpose Internet Mail Exchange) ヘッダーを表すために使用する型を定義します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-160">Defines types that are used to represent Multipurpose Internet Mail Exchange (MIME) headers used by classes in the <xref:System.Net.Mail?displayProperty=nameWithType> namespace.</span></span>  
  
 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-161">ネットワーク イベント、変更、統計、およびプロパティについての情報をプログラムで収集するクラス。</span><span class="sxs-lookup"><span data-stu-id="f06f6-161">Classes to programmatically gather information about network events, changes, statistics, and properties.</span></span>  
  
 <xref:System.Net.PeerToPeer?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-162">ピア名前解決プロトコル (PNRP) のマネージ実装を開発者に提供します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-162">Provides a managed implementation of the Peer Name Resolution Protocol (PNRP) for developers.</span></span>  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-163">ピア ツー ピア コラボレーション インターフェイスのマネージ実装を開発者に提供します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-163">Provides a managed implementation of the Peer-to-Peer Collaboration interface for developers.</span></span>  
  
 <xref:System.Net.Security?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-164">ホスト間の安全な通信のためのネットワーク ストリームを提供するクラス。</span><span class="sxs-lookup"><span data-stu-id="f06f6-164">Classes to provide network streams for secure communications between hosts.</span></span>  
  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-165">ネットワークへのアクセスの制御を支援する必要のある開発者のための、Windows ソケット (Winsock) インターフェイスのマネージ実装が用意されています。</span><span class="sxs-lookup"><span data-stu-id="f06f6-165">Provides a managed implementation of the Windows Sockets (Winsock) interface for developers who need to help control access to the network.</span></span>  
  
 <xref:System.Net.WebSockets?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-166">WebSocket インターフェイスのマネージ実装を開発者に提供します。</span><span class="sxs-lookup"><span data-stu-id="f06f6-166">Provides a managed implementation of the WebSocket interface for developers.</span></span>  
  
 <xref:System.Uri?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-167">URI (Uniform Resource Identifier) のオブジェクト表現を可能にし、URI の一部へ簡単にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="f06f6-167">Provides an object representation of a uniform resource identifier (URI) and easy access to the parts of the URI.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-168">アプリケーションの拡張保護を使用した認証をサポートします。</span><span class="sxs-lookup"><span data-stu-id="f06f6-168">Provides support for authentication using extended protection for applications.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="f06f6-169">アプリケーションの拡張保護を使用した認証の構成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="f06f6-169">Provides support for configuration of authentication using extended protection for applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f06f6-170">参照</span><span class="sxs-lookup"><span data-stu-id="f06f6-170">See Also</span></span>  

 [<span data-ttu-id="f06f6-171">.NET Framework でのトランスポート層セキュリティ (TLS) のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="f06f6-171">Transport Layer Security (TLS) best practices with .NET Framework</span></span>](../../../docs/framework/network-programming/tls.md)  
 [<span data-ttu-id="f06f6-172">ネットワーク プログラミング方法のトピック</span><span class="sxs-lookup"><span data-stu-id="f06f6-172">Network Programming How-to Topics</span></span>](../../../docs/framework/network-programming/network-programming-how-to-topics.md)  
 [<span data-ttu-id="f06f6-173">ネットワーク プログラミングのサンプル</span><span class="sxs-lookup"><span data-stu-id="f06f6-173">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="f06f6-174">MSDN Code Gallery 上の .NET 用のネットワークのサンプル</span><span class="sxs-lookup"><span data-stu-id="f06f6-174">Networking Samples for .NET on MSDN Code Gallery</span></span>](http://code.msdn.microsoft.com/Wiki/View.aspx?ProjectName=nclsamples)  
 [<span data-ttu-id="f06f6-175">HttpClient のサンプル</span><span class="sxs-lookup"><span data-stu-id="f06f6-175">HttpClient Sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=242550)
