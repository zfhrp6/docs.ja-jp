---
title: "Windows Communication Foundation のプライバシー情報"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, privacy information
- WCF, privacy information
- privacy information [WCF]
ms.assetid: c9553724-f3e7-45cb-9ea5-450a22d309d9
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d0172b91393e4e9e373a247c33be938a3160e14
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="windows-communication-foundation-privacy-information"></a><span data-ttu-id="a3760-102">Windows Communication Foundation のプライバシー情報</span><span class="sxs-lookup"><span data-stu-id="a3760-102">Windows Communication Foundation Privacy Information</span></span>
<span data-ttu-id="a3760-103">マイクロソフトは、エンド ユーザーのプライバシー保護に力を入れています。</span><span class="sxs-lookup"><span data-stu-id="a3760-103">Microsoft is committed to protecting end-users' privacy.</span></span> <span data-ttu-id="a3760-104">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] (バージョン 3.0) を使用してアプリケーションを作成した場合、アプリケーションがエンド ユーザーのプライバシーに影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-104">When you build an application using [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], version 3.0, your application may impact your end-users' privacy.</span></span> <span data-ttu-id="a3760-105">たとえば、アプリケーションが明示的にユーザーの連絡先情報を収集することがあります。つまり、アプリケーションがインターネットを経由して Web サイトに情報を要求したり、情報を送信したりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="a3760-105">For example, your application may explicitly collect user contact information, or it may request or send information over the Internet to your Web site.</span></span> <span data-ttu-id="a3760-106">マイクロソフトの技術をアプリケーションに組み込んでいる場合、その技術にプライバシーに影響を与える可能性がある独自の動作が存在することがあります。</span><span class="sxs-lookup"><span data-stu-id="a3760-106">If you embed Microsoft technology in your application, that technology may have its own behavior that might affect privacy.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="a3760-107"> では、アプリケーションの作成者またはエンド ユーザーが選択しない限り、アプリケーションからマイクロソフトに情報を送信することはありません。</span><span class="sxs-lookup"><span data-stu-id="a3760-107"> does not send any information to Microsoft from your application unless you or the end-user choose to send it to us.</span></span>  
  
## <a name="wcf-in-brief"></a><span data-ttu-id="a3760-108">WCF の概要</span><span class="sxs-lookup"><span data-stu-id="a3760-108">WCF in Brief</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="a3760-109"> とは、Microsoft .NET Framework を使用した分散メッセージング フレームワークで、これによって開発者は、分散アプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-109"> is a distributed messaging framework using the Microsoft .NET Framework that allows developers to build distributed applications.</span></span> <span data-ttu-id="a3760-110">2 つのアプリケーション間で交換されるメッセージには、ヘッダーと本文情報が入ります。</span><span class="sxs-lookup"><span data-stu-id="a3760-110">Messages communicated between two applications contain header and body information.</span></span>  
  
 <span data-ttu-id="a3760-111">ヘッダーには、アプリケーションが使用するサービスに応じて、メッセージ ルーティング、セキュリティ情報、トランザクションなどの情報が追加されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-111">Headers may contain message routing, security information, transactions, and more depending on the services used by the application.</span></span> <span data-ttu-id="a3760-112">メッセージは、通常、既定で暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-112">Messages are typically encrypted by default.</span></span> <span data-ttu-id="a3760-113">ただし、`BasicHttpBinding` を使用する場合は例外です。このバインディングは、セキュリティで保護されていない従来の Web サービスで使用するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="a3760-113">The one exception is when using the `BasicHttpBinding`, which was designed for use with non-secured, legacy Web services.</span></span> <span data-ttu-id="a3760-114">アプリケーションの設計者であるユーザーには最終設計に対する責任があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-114">As the application designer, you are responsible for the final design.</span></span> <span data-ttu-id="a3760-115">SOAP 本文のメッセージには、アプリケーション固有のデータが入りますが、アプリケーション定義の個人情報などのデータは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] の暗号化機能または機密性保護機能を使用してセキュリティで保護できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-115">Messages in the SOAP body contain application-specific data; however, this data, such as application-defined personal information, can be secured by using [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] encryption or confidentiality features.</span></span> <span data-ttu-id="a3760-116">次のセクションでは、プライバシーに影響を与える可能性がある機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="a3760-116">The following sections describe the features that potentially impact privacy.</span></span>  
  
## <a name="messaging"></a><span data-ttu-id="a3760-117">メッセージング</span><span class="sxs-lookup"><span data-stu-id="a3760-117">Messaging</span></span>  
 <span data-ttu-id="a3760-118">各 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] メッセージには、メッセージの送信先と応答の返信先を指定するアドレス ヘッダーがあります。</span><span class="sxs-lookup"><span data-stu-id="a3760-118">Each [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] message has an address header that specifies the message destination and where the reply should go.</span></span>  
  
 <span data-ttu-id="a3760-119">エンドポイント アドレスのアドレス構成要素は、エンドポイントを識別する URI (Uniform Resource Identifier) です。</span><span class="sxs-lookup"><span data-stu-id="a3760-119">The address component of an endpoint address is a Uniform Resource Identifier (URI) that identifies the endpoint.</span></span> <span data-ttu-id="a3760-120">このアドレスは、ネットワーク アドレスまたは論理アドレスのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="a3760-120">The address can be a network address or a logical address.</span></span> <span data-ttu-id="a3760-121">アドレスには、コンピューター名 (ホスト名、完全修飾ドメイン名) と IP アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-121">The address may include machine name (hostname, fully qualified domain name) and an IP address.</span></span> <span data-ttu-id="a3760-122">また、エンドポイント アドレスには、グローバル一意識別子 (GUID)、または各アドレスを識別するために使用される一時アドレス指定用に GUID のコレクションを入れることもできます。</span><span class="sxs-lookup"><span data-stu-id="a3760-122">The endpoint address may also contain a globally unique identifier (GUID), or a collection of GUIDs for temporary addressing used to discern each address.</span></span> <span data-ttu-id="a3760-123">各メッセージには、GUID 形式のメッセージ ID があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-123">Each message contains a message ID that is a GUID.</span></span> <span data-ttu-id="a3760-124">この機能は、WS-Addressing 参照仕様に準拠します。</span><span class="sxs-lookup"><span data-stu-id="a3760-124">This feature follows the WS-Addressing reference standard.</span></span>  
  
 <span data-ttu-id="a3760-125">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] メッセージング レイヤーは個人情報をローカル コンピューターに書き込みません。</span><span class="sxs-lookup"><span data-stu-id="a3760-125">The [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] messaging layer does not write any personal information to the local machine.</span></span> <span data-ttu-id="a3760-126">ただし、サービスの開発者が個人情報を公開するサービスを作成した場合は、ネットワーク レベルで個人情報を公開することがあります。このような例として、エンドポイント名に個人名を使用している場合や、エンドポイントの Web サービス記述言語に個人情報を追加しても、https を使用して WSDL にアクセスすることをクライアントに要求しない場合などがあります。</span><span class="sxs-lookup"><span data-stu-id="a3760-126">However, it might propagate personal information at the network level if a service developer has created a service that exposes such information (for example, by using a person's name in an endpoint name, or including personal information in the endpoint's Web Services Description Language but not requiring clients to use https to access the WSDL).</span></span> <span data-ttu-id="a3760-127">また、開発者が実行されている場合、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)ツールの出力の個人情報を公開するエンドポイントに対してツールには、その情報が含まれ、出力ファイルに書き込まれた、ローカルのハード ディスクです。</span><span class="sxs-lookup"><span data-stu-id="a3760-127">Also, if a developer runs the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool against an endpoint that exposes personal information, the tool's output could contain that information, and the output file is written to the local hard disk.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="a3760-128">ホスト</span><span class="sxs-lookup"><span data-stu-id="a3760-128">Hosting</span></span>  
 <span data-ttu-id="a3760-129">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のホスト機能によって、アプリケーションを必要に応じて開始したり、複数のアプリケーション間でポートを共有したりできます。</span><span class="sxs-lookup"><span data-stu-id="a3760-129">The hosting feature in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] allows applications to start on demand or to enable port sharing between multiple applications.</span></span> <span data-ttu-id="a3760-130">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のアプリケーションは、[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 同様、インターネット インフォメーション サービス (IIS) でホストできます。</span><span class="sxs-lookup"><span data-stu-id="a3760-130">An [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application can be hosted in Internet Information Services (IIS), similar to [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)].</span></span>  
  
 <span data-ttu-id="a3760-131">ホストでは、特定の情報をネットワークに公開せず、コンピューター上にデータを格納しません。</span><span class="sxs-lookup"><span data-stu-id="a3760-131">Hosting does not expose any specific information on the network and it does not keep data on the machine.</span></span>  
  
## <a name="message-security"></a><span data-ttu-id="a3760-132">メッセージのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="a3760-132">Message Security</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="a3760-133"> のセキュリティは、メッセージング アプリケーションにセキュリティ機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="a3760-133"> security provides the security capabilities for messaging applications.</span></span> <span data-ttu-id="a3760-134">提供するセキュリティ機能には、認証と承認があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-134">The security functions provided include authentication and authorization.</span></span>  
  
 <span data-ttu-id="a3760-135">認証は、クライアントとサービスとの間で資格情報を交換することによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-135">Authentication is performed by passing credentials between the clients and services.</span></span> <span data-ttu-id="a3760-136">認証は、次のように、トランスポート レベルのセキュリティまたは SOAP メッセージ レベルのセキュリティで実行できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-136">Authentication can be either through transport-level security or through SOAP message-level security, as follows:</span></span>  
  
-   <span data-ttu-id="a3760-137">SOAP メッセージ セキュリティでは、発行者に応じて、ユーザー名とパスワード、X.509 証明書、Kerberos チケット、SAML トークンのような資格情報を使用して認証が実行されます。このすべての資格情報は、個人情報を含んでいる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-137">In SOAP message security, authentication is performed through credentials like username/passwords, X.509 certificates, Kerberos tickets, and SAML tokens, all of which might contain personal information, depending on the issuer.</span></span>  
  
-   <span data-ttu-id="a3760-138">トランスポート セキュリティでは、HTTP 認証方式 (Basic、Digest、Negotiate、Integrated Windows Authorization、NTLM、None、および Anonymous) のような従来のトランスポート認証機構によって認証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-138">Using transport security, authentication is done through traditional transport authentication mechanisms like HTTP authentication schemes (Basic, Digest, Negotiate, Integrated Windows Authorization, NTLM, None, and Anonymous), and form authentication.</span></span>  
  
 <span data-ttu-id="a3760-139">認証によって、通信するエンドポイント間にセキュリティで保護されたセッションを確立できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-139">Authentication can result in a secure session established between the communicating endpoints.</span></span> <span data-ttu-id="a3760-140">このセッションは、セキュリティ セッションの有効期間が切れるまで有効な GUID によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-140">The session is identified by a GUID that lasts the lifetime of the security session.</span></span> <span data-ttu-id="a3760-141">格納されるデータと格納場所を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="a3760-141">The following table shows what is kept and where.</span></span>  
  
|<span data-ttu-id="a3760-142">データ</span><span class="sxs-lookup"><span data-stu-id="a3760-142">Data</span></span>|<span data-ttu-id="a3760-143">ストレージ</span><span class="sxs-lookup"><span data-stu-id="a3760-143">Storage</span></span>|  
|----------|-------------|  
|<span data-ttu-id="a3760-144">ユーザー名、X.509 証明書、Kerberos トークンなどのプレゼンテーション資格情報、および資格情報への参照</span><span class="sxs-lookup"><span data-stu-id="a3760-144">Presentation credentials, such as username, X.509 certificates, Kerberos tokens, and references to credentials.</span></span>|<span data-ttu-id="a3760-145">Windows 証明書ストアなど、標準の Windows 資格情報管理機構</span><span class="sxs-lookup"><span data-stu-id="a3760-145">Standard Windows credential management mechanisms such as the Windows certificate store.</span></span>|  
|<span data-ttu-id="a3760-146">ユーザー名とパスワードなど、ユーザーのメンバーシップ情報</span><span class="sxs-lookup"><span data-stu-id="a3760-146">User membership information, such as usernames and passwords.</span></span>|[!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]<span data-ttu-id="a3760-147"> メンバーシップ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="a3760-147"> membership providers.</span></span>|  
|<span data-ttu-id="a3760-148">クライアントに対するサービスの認証に使用されるサービスの ID 情報</span><span class="sxs-lookup"><span data-stu-id="a3760-148">Identity information about the service used to authenticate the service to clients.</span></span>|<span data-ttu-id="a3760-149">サービスのエンドポイント アドレス</span><span class="sxs-lookup"><span data-stu-id="a3760-149">Endpoint address of the service.</span></span>|  
|<span data-ttu-id="a3760-150">呼び出し元情報</span><span class="sxs-lookup"><span data-stu-id="a3760-150">Caller information.</span></span>|<span data-ttu-id="a3760-151">監査ログ</span><span class="sxs-lookup"><span data-stu-id="a3760-151">Auditing logs.</span></span>|  
  
## <a name="auditing"></a><span data-ttu-id="a3760-152">監査</span><span class="sxs-lookup"><span data-stu-id="a3760-152">Auditing</span></span>  
 <span data-ttu-id="a3760-153">監査では、認証イベントと承認イベントの成功と失敗を記録します。</span><span class="sxs-lookup"><span data-stu-id="a3760-153">Auditing records the success and failure of authentication and authorization events.</span></span> <span data-ttu-id="a3760-154">監査レコードには、サービス URI、アクション URI、および呼び出し元の ID が入ります。</span><span class="sxs-lookup"><span data-stu-id="a3760-154">Auditing records contain the following data: service URI, action URI, and the caller's identification.</span></span>  
  
 <span data-ttu-id="a3760-155">また、監査では、管理者がメッセージ ログの設定 (オンまたはオフ) を変更した時刻を記録します。その理由は、メッセージ ログが、ヘッダーと本文のアプリケーション固有のデータをログに記録する可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="a3760-155">Auditing also records when the administrator modifies the configuration of message logging (turning it on or off), because message logging may log application-specific data in headers and bodies.</span></span> <span data-ttu-id="a3760-156">[!INCLUDE[wxp](../../../includes/wxp-md.md)] の場合、レコードはアプリケーション イベント ログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-156">For [!INCLUDE[wxp](../../../includes/wxp-md.md)], a record is logged in the application event log.</span></span> <span data-ttu-id="a3760-157">[!INCLUDE[wv](../../../includes/wv-md.md)] と [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] の場合、レコードは、セキュリティ イベント ログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-157">For [!INCLUDE[wv](../../../includes/wv-md.md)] and [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], a record is logged in the security event log.</span></span>  
  
## <a name="transactions"></a><span data-ttu-id="a3760-158">トランザクション</span><span class="sxs-lookup"><span data-stu-id="a3760-158">Transactions</span></span>  
 <span data-ttu-id="a3760-159">トランザクション機能は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のアプリケーションにトランザクション サービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="a3760-159">The transactions feature provides transactional services to a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] application.</span></span>  
  
 <span data-ttu-id="a3760-160">トランザクションの伝達で使用されるトランザクション ヘッダーには、GUID 形式のトランザクション ID または登録リスト ID を追加できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-160">Transaction headers used in transaction propagation may contain Transaction IDs or Enlistment IDs, which are GUIDs.</span></span>  
  
 <span data-ttu-id="a3760-161">トランザクション機能では、Microsoft 分散トランザクション コーディネーター (MSDTC) トランザクション マネージャー (Windows コンポーネントの 1 つ) を使用して、トランザクション状態を管理します。</span><span class="sxs-lookup"><span data-stu-id="a3760-161">The Transactions feature uses the Microsoft Distributed Transaction Coordinator (MSDTC) Transaction Manager (a Windows component) to manage transaction state.</span></span> <span data-ttu-id="a3760-162">既定では、トランザクション マネージャー間の通信は暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-162">By default, communications between Transactions Managers are encrypted.</span></span> <span data-ttu-id="a3760-163">トランザクション マネージャーは、エンドポイント参照、トランザクション ID、および登録リスト ID を永続状態の一部としてログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-163">Transaction Managers may log endpoint references, Transaction IDs, and Enlistment IDs as part of their durable state.</span></span> <span data-ttu-id="a3760-164">この状態の有効期間は、トランザクション マネージャーのログ ファイルの有効期間によって決まります。</span><span class="sxs-lookup"><span data-stu-id="a3760-164">The lifetime of this state is determined by the lifetime of the Transaction Manager’s log file.</span></span> <span data-ttu-id="a3760-165">MSDTC サービスがこのログを所有し、管理します。</span><span class="sxs-lookup"><span data-stu-id="a3760-165">The MSDTC service owns and maintains this log.</span></span>  
  
 <span data-ttu-id="a3760-166">トランザクション機能は、WS-Coordination 仕様と WS-AtomicTransaction 仕様を実装します。</span><span class="sxs-lookup"><span data-stu-id="a3760-166">The Transactions feature implements the WS-Coordination and WS-Atomic Transaction standards.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="a3760-167">信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="a3760-167">Reliable Sessions</span></span>  
 <span data-ttu-id="a3760-168">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] の信頼できるセッションは、トランスポートまたは中継局のエラーが発生した場合でもメッセージの転送を実現します。</span><span class="sxs-lookup"><span data-stu-id="a3760-168">Reliable sessions in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] provide the transfer of messages when transport or intermediary failures occur.</span></span> <span data-ttu-id="a3760-169">信頼できるセッションは、基になるトランスポート (たとえば、ワイヤレス ネットワーク上の TCP 接続) が切断している場合やメッセージを紛失した場合 (HTTP プロキシでの送受信メッセージの破棄) でも、正確に 1 回のメッセージ転送を実行します。</span><span class="sxs-lookup"><span data-stu-id="a3760-169">They provide an exactly-once transfer of messages even when the underlying transport disconnects (for example, a TCP connection on a wireless network) or loses a message (an HTTP proxy dropping an outgoing or incoming message).</span></span> <span data-ttu-id="a3760-170">また、メッセージが送信された順序を維持するので、メッセージの並べ替え (マルチパス ルーティングの場合に発生する可能性がある) を回復できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-170">Reliable sessions also recover message reordering (as may happen in the case of multipath routing), preserving the order in which the messages were sent.</span></span>  
  
 <span data-ttu-id="a3760-171">信頼できるセッションは、WS-ReliableMessaging (WS-RM) プロトコルを使用して実装されています。</span><span class="sxs-lookup"><span data-stu-id="a3760-171">Reliable sessions are implemented using the WS-ReliableMessaging (WS-RM) protocol.</span></span> <span data-ttu-id="a3760-172">これによって追加される WS-RM ヘッダーには、特定の信頼できるセッションに関連付けられたすべてのメッセージの識別に使用されるセッション情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a3760-172">They add WS-RM headers that contain session information, which is used to identify all messages associated with a particular reliable session.</span></span> <span data-ttu-id="a3760-173">各 WS-RM セッションには、GUID 形式の識別子があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-173">Each WS-RM session has an identifier, which is a GUID.</span></span>  
  
 <span data-ttu-id="a3760-174">エンド ユーザーのコンピューターに保持される個人情報はありません。</span><span class="sxs-lookup"><span data-stu-id="a3760-174">No personal information is retained on the end-user's machine.</span></span>  
  
## <a name="queued-channels"></a><span data-ttu-id="a3760-175">キューに置かれたチャネル</span><span class="sxs-lookup"><span data-stu-id="a3760-175">Queued Channels</span></span>  
 <span data-ttu-id="a3760-176">キューは、送信元アプリケーションが送ったメッセージを受信側アプリケーションに代わって保存しておき、後で受信側アプリケーションに転送します。</span><span class="sxs-lookup"><span data-stu-id="a3760-176">Queues store messages from a sending application on behalf of a receiving application and later forward these messages to the receiving application.</span></span> <span data-ttu-id="a3760-177">受信側アプリケーションが一時的な場合なども、キューによって、送信元アプリケーションから受信側アプリケーションへのメッセージの転送を確実に実行できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-177">They help ensure the transfer of messages from sending applications to receiving applications when, for example, the receiving application is transient.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="a3760-178"> では、トランスポートとして Microsoft メッセージ キュー (MSMQ) を使用することによってキューをサポートします。</span><span class="sxs-lookup"><span data-stu-id="a3760-178"> provides support for queuing by using Microsoft Message Queuing (MSMQ) as a transport.</span></span>  
  
 <span data-ttu-id="a3760-179">キューに置かれたチャネル機能では、ヘッダーをメッセージに追加しません。</span><span class="sxs-lookup"><span data-stu-id="a3760-179">The queued channels feature does not add headers to a message.</span></span> <span data-ttu-id="a3760-180">代わりに、適切なメッセージ キューのメッセージ プロパティ セットを備えたメッセージ キューのメッセージを作成し、メッセージ キューのメソッドを呼び出して、メッセージ キューのキューにメッセージを追加します。</span><span class="sxs-lookup"><span data-stu-id="a3760-180">Instead it creates a Message Queuing message with appropriate Message Queuing message properties set, and invokes Message Queuing methods to put the message in the Message Queuing queue.</span></span> <span data-ttu-id="a3760-181">メッセージ キューは、Windows に付属しているオプション コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="a3760-181">Message Queuing is an optional component that ships with Windows.</span></span>  
  
 <span data-ttu-id="a3760-182">キューに置かれたチャネル機能では、キュー インフラストラクチャとしてメッセージ キューを使用するので、この機能によってエンド ユーザーのコンピューターに保持される情報はありません。</span><span class="sxs-lookup"><span data-stu-id="a3760-182">No information is retained on the end-user's machine by the queued channels feature, because it uses Message Queuing as the queuing infrastructure.</span></span>  
  
## <a name="com-integration"></a><span data-ttu-id="a3760-183">COM+ 統合</span><span class="sxs-lookup"><span data-stu-id="a3760-183">COM+ Integration</span></span>  
 <span data-ttu-id="a3760-184">この機能は、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のサービスと互換性のあるサービスを作成するために既存の COM 機能と COM+ 機能をラップします。</span><span class="sxs-lookup"><span data-stu-id="a3760-184">This feature wraps existing COM and COM+ functionality to create services that are compatible with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="a3760-185">この機能は、特定のヘッダーを使用せず、エンド ユーザーのコンピューターにデータを保持しません。</span><span class="sxs-lookup"><span data-stu-id="a3760-185">This feature does not use specific headers and it does not retain data on the end-user's machine.</span></span>  
  
## <a name="com-service-moniker"></a><span data-ttu-id="a3760-186">COM サービス モニカー</span><span class="sxs-lookup"><span data-stu-id="a3760-186">COM Service Moniker</span></span>  
 <span data-ttu-id="a3760-187">この機能は、標準の [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントにアンマネージ ラッパーを提供します。</span><span class="sxs-lookup"><span data-stu-id="a3760-187">This provides an unmanaged wrapper to a standard [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="a3760-188">この機能は、ネットワーク上で特定のヘッダーを使用せず、コンピューターにデータを保持しません。</span><span class="sxs-lookup"><span data-stu-id="a3760-188">This feature does not have specific headers on the wire nor does it persist data on the machine.</span></span>  
  
## <a name="peer-channel"></a><span data-ttu-id="a3760-189">ピア チャネル</span><span class="sxs-lookup"><span data-stu-id="a3760-189">Peer Channel</span></span>  
 <span data-ttu-id="a3760-190">ピア チャネルによって、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] を使用したマルチパーティ アプリケーションの展開が可能になります。</span><span class="sxs-lookup"><span data-stu-id="a3760-190">A peer channel enables development of multiparty applications using [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="a3760-191">マルチパーティ メッセージングはメッシュのコンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-191">Multiparty messaging occurs in the context of a mesh.</span></span> <span data-ttu-id="a3760-192">メッシュは、ノードが参加できる名前によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-192">Meshes are identified by a name that nodes can join.</span></span> <span data-ttu-id="a3760-193">ピア チャネル内の各ノードは、ユーザー指定のポートで TCP リスナーを作成し、メッシュ内の他のノードとの接続を確立することによって、回復力を確保します。</span><span class="sxs-lookup"><span data-stu-id="a3760-193">Each node in the peer channel creates a TCP listener at a user-specified port and establishes connections with other nodes in the mesh to ensure resiliency.</span></span> <span data-ttu-id="a3760-194">メッシュ内の他のノードに接続するため、ノードは、リスナー アドレスやコンピューターの IP アドレスなど一部のデータをメッシュ内の他のノードと交換します。</span><span class="sxs-lookup"><span data-stu-id="a3760-194">To connect to other nodes in the mesh, nodes also exchange some data, including the listener address and the machine's IP addresses, with other nodes in the mesh.</span></span> <span data-ttu-id="a3760-195">メッシュ内で送信されるメッセージに送信者に関するセキュリティ情報を入れ、メッセージのなりすましと改ざんを防止することができます。</span><span class="sxs-lookup"><span data-stu-id="a3760-195">Messages sent around in the mesh can contain security information that pertains to the sender to prevent message spoofing and tampering.</span></span>  
  
 <span data-ttu-id="a3760-196">エンド ユーザーのコンピューターに個人情報は格納されません。</span><span class="sxs-lookup"><span data-stu-id="a3760-196">No personal information is stored on the end-user's machine.</span></span>  
  
## <a name="it-professional-experience"></a><span data-ttu-id="a3760-197">IT 専門家向けの機能</span><span class="sxs-lookup"><span data-stu-id="a3760-197">IT Professional Experience</span></span>  
  
### <a name="tracing"></a><span data-ttu-id="a3760-198">トレース</span><span class="sxs-lookup"><span data-stu-id="a3760-198">Tracing</span></span>  
 <span data-ttu-id="a3760-199">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] インフラストラクチャの診断機能は、トランスポート レイヤーとサービス モデル レイヤーを経由するメッセージ、およびこのメッセージに関連付けられたアクティビティとイベントをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="a3760-199">The diagnostics feature of the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastructure logs messages that pass through the transport and service model layers, and the activities and events associated with these messages.</span></span> <span data-ttu-id="a3760-200">この機能は既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="a3760-200">This feature is turned off by default.</span></span> <span data-ttu-id="a3760-201">この機能はアプリケーションの構成ファイルを使用して有効にし、トレース動作は、実行時に [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] WMI プロバイダーを使用して変更できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-201">It is enabled using the application’s configuration file and the tracing behavior may be modified using the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] WMI provider at run time.</span></span> <span data-ttu-id="a3760-202">有効にすると、トレース インフラストラクチャは、メッセージ、アクティビティ、および処理イベントを含んだ診断トレースを構成済みリスナーに出力します。</span><span class="sxs-lookup"><span data-stu-id="a3760-202">When enabled, the tracing infrastructure emits a diagnostic trace that contains messages, activities, and processing events to configured listeners.</span></span> <span data-ttu-id="a3760-203">出力の形式と場所は、管理者が選択するリスナー構成によって決まりますが、通常は XML 形式のファイルです。</span><span class="sxs-lookup"><span data-stu-id="a3760-203">The format and location of the output are determined by the administrator’s listener configuration choices, but is typically an XML formatted file.</span></span> <span data-ttu-id="a3760-204">管理者は、トレース ファイルでアクセス制御リスト (ACL) を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-204">The administrator is responsible for setting the access control list (ACL) on the trace files.</span></span> <span data-ttu-id="a3760-205">特に、Windows アクティベーション システム (WAS) でホストするとき、管理者は、ファイルがパブリック仮想ルート ディレクトリから提供されていないことを確認する必要があります (提供されることを望まない場合)。</span><span class="sxs-lookup"><span data-stu-id="a3760-205">In particular, when hosted by Windows Activation System (WAS), the administrator should make sure the files are not served from the public virtual root directory if that is not desired.</span></span>  
  
 <span data-ttu-id="a3760-206">トレースには、メッセージ ログとサービス モデル診断トレースの 2 種類があります。この 2 種類のトレースについて次のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="a3760-206">There are two types of tracing: Message logging and Service Model diagnostic tracing, described in the following section.</span></span> <span data-ttu-id="a3760-207">この 2 つのトレースは、それぞれ <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> と <xref:System.ServiceModel> というトレース ソースから構成されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-207">Each type is configured through its own trace source: <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> and <xref:System.ServiceModel>.</span></span> <span data-ttu-id="a3760-208">このログ トレース ソースは両方とも、アプリケーションにローカルなデータを取り込みます。</span><span class="sxs-lookup"><span data-stu-id="a3760-208">Both of these logging trace sources capture data that is local to the application.</span></span>  
  
### <a name="message-logging"></a><span data-ttu-id="a3760-209">メッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="a3760-209">Message Logging</span></span>  
 <span data-ttu-id="a3760-210">メッセージ ログのトレース ソース (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) によって管理者は、システムを通過するメッセージをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-210">The message logging trace source (<xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A>) allows an administrator to log the messages that flow through the system.</span></span> <span data-ttu-id="a3760-211">ユーザーは構成によって、メッセージ全体またはメッセージ ヘッダーだけをログに記録するかどうか、トランスポート レイヤーまたはサービス モデル レイヤーでログに記録するかどうか、および形式が正しくないメッセージをログに記録するかどうかを設定できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-211">Through configuration, the user may decide to log entire messages or message headers only, whether to log at the transport and/or service model layers, and whether to include malformed messages.</span></span> <span data-ttu-id="a3760-212">また、ユーザーは、フィルター処理を設定して、ログに記録するメッセージを制限できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-212">Also, the user may configure filtering to restrict which messages are logged.</span></span>  
  
 <span data-ttu-id="a3760-213">既定では、メッセージ ログは無効になっています。</span><span class="sxs-lookup"><span data-stu-id="a3760-213">By default, message logging is disabled.</span></span> <span data-ttu-id="a3760-214">ローカル コンピューターの管理者は、アプリケーション レベルの管理者がメッセージ ログを有効にするのを防止できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-214">The local machine administrator can prevent the application-level administrator from turning message logging on.</span></span>  
  
#### <a name="encrypted-and-decrypted-message-logging"></a><span data-ttu-id="a3760-215">暗号化および復号化されるメッセージ ログ</span><span class="sxs-lookup"><span data-stu-id="a3760-215">Encrypted and Decrypted Message Logging</span></span>  
 <span data-ttu-id="a3760-216">メッセージは、以下に説明するようにログに記録され、暗号化および復号化されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-216">Messages are logged, encrypted, or decrypted, as described in the following terms.</span></span>  
  
 <span data-ttu-id="a3760-217">トランスポート ログ</span><span class="sxs-lookup"><span data-stu-id="a3760-217">Transport Logging</span></span>  
 <span data-ttu-id="a3760-218">トランスポート レベルで送受信されるメッセージをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="a3760-218">Logs messages received and sent at the transport level.</span></span> <span data-ttu-id="a3760-219">このメッセージは、すべてのヘッダーを含んでいて、ネットワーク上に送信される前と受信されるときに暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-219">These messages contain all headers, and may be encrypted before being sent on the wire and when being received.</span></span>  
  
 <span data-ttu-id="a3760-220">メッセージがネットワーク上に送信される前と受信されるときに暗号化される場合、そのメッセージは暗号化されたままログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-220">If messages are encrypted before being sent on the wire and when they are received, they are logged encrypted as well.</span></span> <span data-ttu-id="a3760-221">例外は、セキュリティ プロトコル (https) を使用する場合です。メッセージは、ネットワーク上で暗号化されている場合でも、送信前と受信後は復号化された状態でログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-221">An exception is when a security protocol is used (https): they are then logged decrypted before being sent and after being received even if they are encrypted on the wire.</span></span>  
  
 <span data-ttu-id="a3760-222">サービス ログ</span><span class="sxs-lookup"><span data-stu-id="a3760-222">Service Logging</span></span>  
 <span data-ttu-id="a3760-223">チャネル ヘッダー処理が実行された後、ユーザー コードを入力する直前と直後に、サービス モデル レベルで送受信されるメッセージをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="a3760-223">Logs messages received or sent at the service model level, after channel header processing has occurred, just before and after entering user code.</span></span>  
  
 <span data-ttu-id="a3760-224">このレベルでログに記録されるメッセージは、ネットワーク上でセキュリティ保護され、暗号化されている場合でも復号化されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-224">Messages logged at this level are decrypted even if they were secured and encrypted on the wire.</span></span>  
  
 <span data-ttu-id="a3760-225">形式が正しくないメッセージのログ</span><span class="sxs-lookup"><span data-stu-id="a3760-225">Malformed Message Logging</span></span>  
 <span data-ttu-id="a3760-226">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] インフラストラクチャが認識できないまたは処理できないメッセージをログに記録します。</span><span class="sxs-lookup"><span data-stu-id="a3760-226">Logs messages that the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastructure cannot understand or process.</span></span>  
  
 <span data-ttu-id="a3760-227">メッセージは、暗号化の有無を問わず、そのままの状態でログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-227">Messages are logged as-is, that is, encrypted or not</span></span>  
  
 <span data-ttu-id="a3760-228">メッセージが復号化された状態または暗号化されていない状態でログに記録される場合、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] では既定で、メッセージをログに記録する前にセキュリティ キーと個人情報の可能性がある情報をメッセージから削除します。</span><span class="sxs-lookup"><span data-stu-id="a3760-228">When messages are logged in decrypted or unencrypted form, by default [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] removes security keys and potentially personal information from the messages before logging them.</span></span> <span data-ttu-id="a3760-229">次のセクションでは、削除される情報と削除が実行される状況について説明します。</span><span class="sxs-lookup"><span data-stu-id="a3760-229">The next sections describe what information is removed, and when.</span></span> <span data-ttu-id="a3760-230">キーと個人情報の可能性がある情報をログに記録するには、コンピューターの管理者とアプリケーションを配置するユーザーの両方が、所定の構成操作を実行して既定の動作を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-230">The machine administrator and application deployer must both take certain configuration actions to change the default behavior to log keys and potentially personal information.</span></span>  
  
#### <a name="information-removed-from-message-headers-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="a3760-231">復号化されたまたは暗号化されていないメッセージをログに記録するときにメッセージ ヘッダーから削除される情報</span><span class="sxs-lookup"><span data-stu-id="a3760-231">Information Removed from Message Headers When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="a3760-232">メッセージが復号化された状態または暗号化されていない状態でログに記録される場合、既定ではメッセージがログに記録される前に、セキュリティ キーと個人情報の可能性がある情報がメッセージ ヘッダーとメッセージ本文から削除されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-232">When messages are logged in decrypted/unencrypted form, security keys and potentially personal information are removed by default from message headers and message bodies before they are logged.</span></span> <span data-ttu-id="a3760-233">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] によってキーおよび個人情報の可能性がある情報と見なされる部分を次のリストに示します。</span><span class="sxs-lookup"><span data-stu-id="a3760-233">The following list shows what [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] considers keys and potentially personal information.</span></span>  
  
 <span data-ttu-id="a3760-234">削除されるキー :</span><span class="sxs-lookup"><span data-stu-id="a3760-234">Keys that are removed:</span></span>  
  
 <span data-ttu-id="a3760-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span><span class="sxs-lookup"><span data-stu-id="a3760-235">\- For xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"</span></span>  
  
 <span data-ttu-id="a3760-236">wst:BinarySecret</span><span class="sxs-lookup"><span data-stu-id="a3760-236">wst:BinarySecret</span></span>  
  
 <span data-ttu-id="a3760-237">wst:Entropy</span><span class="sxs-lookup"><span data-stu-id="a3760-237">wst:Entropy</span></span>  
  
 <span data-ttu-id="a3760-238">\-Xmlns:wsse ="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd"と xmlns:wsse ="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="a3760-238">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="a3760-239">wsse:Password</span><span class="sxs-lookup"><span data-stu-id="a3760-239">wsse:Password</span></span>  
  
 <span data-ttu-id="a3760-240">wsse:Nonce</span><span class="sxs-lookup"><span data-stu-id="a3760-240">wsse:Nonce</span></span>  
  
 <span data-ttu-id="a3760-241">削除される個人情報の可能性がある情報 :</span><span class="sxs-lookup"><span data-stu-id="a3760-241">Potentially personal information that is removed:</span></span>  
  
 <span data-ttu-id="a3760-242">\-Xmlns:wsse ="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd"と xmlns:wsse ="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span><span class="sxs-lookup"><span data-stu-id="a3760-242">\- For xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.1.xsd" and xmlns:wsse="http://docs.oasis-open.org/wss/2005/xx/oasis-2005xx-wss-wssecurity-secext-1.1.xsd"</span></span>  
  
 <span data-ttu-id="a3760-243">wsse:Username</span><span class="sxs-lookup"><span data-stu-id="a3760-243">wsse:Username</span></span>  
  
 <span data-ttu-id="a3760-244">wsse:BinarySecurityToken</span><span class="sxs-lookup"><span data-stu-id="a3760-244">wsse:BinarySecurityToken</span></span>  
  
 <span data-ttu-id="a3760-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span><span class="sxs-lookup"><span data-stu-id="a3760-245">\- For xmlns:saml="urn:oasis:names:tc:SAML:1.0:assertion" the items in bold (below) are removed:</span></span>  
  
 <span data-ttu-id="a3760-246">\<アサーション</span><span class="sxs-lookup"><span data-stu-id="a3760-246">\<Assertion</span></span>  
  
 <span data-ttu-id="a3760-247">MajorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="a3760-247">MajorVersion="1"</span></span>  
  
 <span data-ttu-id="a3760-248">MinorVersion="1"</span><span class="sxs-lookup"><span data-stu-id="a3760-248">MinorVersion="1"</span></span>  
  
 <span data-ttu-id="a3760-249">AssertionId="[ID]"</span><span class="sxs-lookup"><span data-stu-id="a3760-249">AssertionId="[ID]"</span></span>  
  
 <span data-ttu-id="a3760-250">Issuer="[string]"</span><span class="sxs-lookup"><span data-stu-id="a3760-250">Issuer="[string]"</span></span>  
  
 <span data-ttu-id="a3760-251">IssueInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="a3760-251">IssueInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="a3760-252">\<条件で NotBefore"[dateTime]"NotOnOrAfter を = ="[dateTime]"></span><span class="sxs-lookup"><span data-stu-id="a3760-252">\<Conditions NotBefore="[dateTime]" NotOnOrAfter="[dateTime]"></span></span>  
  
 <span data-ttu-id="a3760-253">\<AudienceRestrictionCondition></span><span class="sxs-lookup"><span data-stu-id="a3760-253">\<AudienceRestrictionCondition></span></span>  
  
 <span data-ttu-id="a3760-254">\<Audience > [uri]\</Audience > +</span><span class="sxs-lookup"><span data-stu-id="a3760-254">\<Audience>[uri]\</Audience>+</span></span>  
  
 <span data-ttu-id="a3760-255">\</AudienceRestrictionCondition>\*</span><span class="sxs-lookup"><span data-stu-id="a3760-255">\</AudienceRestrictionCondition>\*</span></span>  
  
 <span data-ttu-id="a3760-256">\<DoNotCacheCondition />\*</span><span class="sxs-lookup"><span data-stu-id="a3760-256">\<DoNotCacheCondition />\*</span></span>  
  
 <span data-ttu-id="a3760-257"><\!-基本型を抽象化</span><span class="sxs-lookup"><span data-stu-id="a3760-257"><\!-- abstract base type</span></span>  
  
 <span data-ttu-id="a3760-258">\<条件/> \*</span><span class="sxs-lookup"><span data-stu-id="a3760-258">\<Condition />\*</span></span>  
  
 -->  
  
 <span data-ttu-id="a3760-259">\</Conditions>?</span><span class="sxs-lookup"><span data-stu-id="a3760-259">\</Conditions>?</span></span>  
  
 <span data-ttu-id="a3760-260">\<アドバイス ></span><span class="sxs-lookup"><span data-stu-id="a3760-260">\<Advice></span></span>  
  
 <span data-ttu-id="a3760-261">\<AssertionIDReference > [ID]\</AssertionIDReference > \*</span><span class="sxs-lookup"><span data-stu-id="a3760-261">\<AssertionIDReference>[ID]\</AssertionIDReference>\*</span></span>  
  
 <span data-ttu-id="a3760-262">\<アサーション > [アサーション]\</Assertion > \*</span><span class="sxs-lookup"><span data-stu-id="a3760-262">\<Assertion>[assertion]\</Assertion>\*</span></span>  
  
 <span data-ttu-id="a3760-263">[any]\*</span><span class="sxs-lookup"><span data-stu-id="a3760-263">[any]\*</span></span>  
  
 <span data-ttu-id="a3760-264">\</Advice>?</span><span class="sxs-lookup"><span data-stu-id="a3760-264">\</Advice>?</span></span>  
  
 <span data-ttu-id="a3760-265"><\!--抽象基本型</span><span class="sxs-lookup"><span data-stu-id="a3760-265"><\!-- Abstract base types</span></span>  
  
 <span data-ttu-id="a3760-266">\<ステートメント/> \*</span><span class="sxs-lookup"><span data-stu-id="a3760-266">\<Statement />\*</span></span>  
  
 <span data-ttu-id="a3760-267">\<SubjectStatement></span><span class="sxs-lookup"><span data-stu-id="a3760-267">\<SubjectStatement></span></span>  
  
 <span data-ttu-id="a3760-268">\<サブジェクト ></span><span class="sxs-lookup"><span data-stu-id="a3760-268">\<Subject></span></span>  
  
 `<NameIdentifier`  
  
 `NameQualifier="[string]"?`  
  
 `Format="[uri]"?`  
  
 `>`  
  
 `[string]`  
  
 `</NameIdentifier>?`  
  
 <span data-ttu-id="a3760-269">\<SubjectConfirmation></span><span class="sxs-lookup"><span data-stu-id="a3760-269">\<SubjectConfirmation></span></span>  
  
 <span data-ttu-id="a3760-270">\<ConfirmationMethod > [anyUri]\</ConfirmationMethod > +</span><span class="sxs-lookup"><span data-stu-id="a3760-270">\<ConfirmationMethod>[anyUri]\</ConfirmationMethod>+</span></span>  
  
 <span data-ttu-id="a3760-271">\<SubjectConfirmationData > [すべて]\</SubjectConfirmationData > ですか?</span><span class="sxs-lookup"><span data-stu-id="a3760-271">\<SubjectConfirmationData>[any]\</SubjectConfirmationData>?</span></span>  
  
 <span data-ttu-id="a3760-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span><span class="sxs-lookup"><span data-stu-id="a3760-272">\<ds:KeyInfo>...\</ds:KeyInfo>?</span></span>  
  
 <span data-ttu-id="a3760-273">\</SubjectConfirmation > ですか?</span><span class="sxs-lookup"><span data-stu-id="a3760-273">\</SubjectConfirmation>?</span></span>  
  
 <span data-ttu-id="a3760-274">\</Subject></span><span class="sxs-lookup"><span data-stu-id="a3760-274">\</Subject></span></span>  
  
 <span data-ttu-id="a3760-275">\</SubjectStatement>\*</span><span class="sxs-lookup"><span data-stu-id="a3760-275">\</SubjectStatement>\*</span></span>  
  
 -->  
  
 <span data-ttu-id="a3760-276">\<AuthenticationStatement</span><span class="sxs-lookup"><span data-stu-id="a3760-276">\<AuthenticationStatement</span></span>  
  
 <span data-ttu-id="a3760-277">AuthenticationMethod="[uri]"</span><span class="sxs-lookup"><span data-stu-id="a3760-277">AuthenticationMethod="[uri]"</span></span>  
  
 <span data-ttu-id="a3760-278">AuthenticationInstant="[dateTime]"</span><span class="sxs-lookup"><span data-stu-id="a3760-278">AuthenticationInstant="[dateTime]"</span></span>  
  
 >  
  
 <span data-ttu-id="a3760-279">[Subject]</span><span class="sxs-lookup"><span data-stu-id="a3760-279">[Subject]</span></span>  
  
 `<SubjectLocality`  
  
 `IPAddress="[string]"?`  
  
 `DNSAddress="[string]"?`  
  
 `/>?`  
  
 <span data-ttu-id="a3760-280"><AuthorityBinding</span><span class="sxs-lookup"><span data-stu-id="a3760-280"><AuthorityBinding</span></span>  
  
 <span data-ttu-id="a3760-281">AuthorityKind="[QName]"</span><span class="sxs-lookup"><span data-stu-id="a3760-281">AuthorityKind="[QName]"</span></span>  
  
 <span data-ttu-id="a3760-282">Location="[uri]"</span><span class="sxs-lookup"><span data-stu-id="a3760-282">Location="[uri]"</span></span>  
  
 <span data-ttu-id="a3760-283">Binding="[uri]"</span><span class="sxs-lookup"><span data-stu-id="a3760-283">Binding="[uri]"</span></span>  
  
 />*  
  
 <span data-ttu-id="a3760-284">\</AuthenticationStatement>\*</span><span class="sxs-lookup"><span data-stu-id="a3760-284">\</AuthenticationStatement>\*</span></span>  
  
 <span data-ttu-id="a3760-285">\<AttributeStatement></span><span class="sxs-lookup"><span data-stu-id="a3760-285">\<AttributeStatement></span></span>  
  
 <span data-ttu-id="a3760-286">[Subject]</span><span class="sxs-lookup"><span data-stu-id="a3760-286">[Subject]</span></span>  
  
 <span data-ttu-id="a3760-287">\<属性</span><span class="sxs-lookup"><span data-stu-id="a3760-287">\<Attribute</span></span>  
  
 <span data-ttu-id="a3760-288">AttributeName="[string]"</span><span class="sxs-lookup"><span data-stu-id="a3760-288">AttributeName="[string]"</span></span>  
  
 <span data-ttu-id="a3760-289">AttributeNamespace="[uri]"</span><span class="sxs-lookup"><span data-stu-id="a3760-289">AttributeNamespace="[uri]"</span></span>  
  
 >  
  
 `<AttributeValue>[any]</AttributeValue>+`  
  
 <span data-ttu-id="a3760-290">\</Attribute>+</span><span class="sxs-lookup"><span data-stu-id="a3760-290">\</Attribute>+</span></span>  
  
 <span data-ttu-id="a3760-291">\</AttributeStatement>\*</span><span class="sxs-lookup"><span data-stu-id="a3760-291">\</AttributeStatement>\*</span></span>  
  
 <span data-ttu-id="a3760-292">\<AuthorizationDecisionStatement</span><span class="sxs-lookup"><span data-stu-id="a3760-292">\<AuthorizationDecisionStatement</span></span>  
  
 <span data-ttu-id="a3760-293">Resource="[uri]"</span><span class="sxs-lookup"><span data-stu-id="a3760-293">Resource="[uri]"</span></span>  
  
 <span data-ttu-id="a3760-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span><span class="sxs-lookup"><span data-stu-id="a3760-294">Decision="[Permit&#124;Deny&#124;Indeterminate]"</span></span>  
  
 >  
  
 <span data-ttu-id="a3760-295">[Subject]</span><span class="sxs-lookup"><span data-stu-id="a3760-295">[Subject]</span></span>  
  
 <span data-ttu-id="a3760-296">\<アクション Namespace ="[uri]"> [文字列]\</Action > +</span><span class="sxs-lookup"><span data-stu-id="a3760-296">\<Action Namespace="[uri]">[string]\</Action>+</span></span>  
  
 <span data-ttu-id="a3760-297">\<Evidence></span><span class="sxs-lookup"><span data-stu-id="a3760-297">\<Evidence></span></span>  
  
 <span data-ttu-id="a3760-298">\<AssertionIDReference > [ID]\</AssertionIDReference > +</span><span class="sxs-lookup"><span data-stu-id="a3760-298">\<AssertionIDReference>[ID]\</AssertionIDReference>+</span></span>  
  
 <span data-ttu-id="a3760-299">\<アサーション > [アサーション]\</Assertion > +</span><span class="sxs-lookup"><span data-stu-id="a3760-299">\<Assertion>[assertion]\</Assertion>+</span></span>  
  
 <span data-ttu-id="a3760-300">\</Evidence>?</span><span class="sxs-lookup"><span data-stu-id="a3760-300">\</Evidence>?</span></span>  
  
 <span data-ttu-id="a3760-301">\</AuthorizationDecisionStatement>\*</span><span class="sxs-lookup"><span data-stu-id="a3760-301">\</AuthorizationDecisionStatement>\*</span></span>  
  
 <span data-ttu-id="a3760-302">\</Assertion></span><span class="sxs-lookup"><span data-stu-id="a3760-302">\</Assertion></span></span>  
  
#### <a name="information-removed-from-message-bodies-when-logging-decryptedunencrypted-messages"></a><span data-ttu-id="a3760-303">復号化されたまたは暗号化されていないメッセージをログに記録するときにメッセージ本文から削除される情報</span><span class="sxs-lookup"><span data-stu-id="a3760-303">Information Removed from Message Bodies When Logging Decrypted/Unencrypted Messages</span></span>  
 <span data-ttu-id="a3760-304">前述のとおり、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] では、復号化されたまたは暗号化されていないメッセージをログに記録する場合、キーと既知の可能性がある個人情報をメッセージ ヘッダーから削除します。</span><span class="sxs-lookup"><span data-stu-id="a3760-304">As previously described, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] removes keys and known potentially personal information from message headers for logged decrypted/unencrypted messages.</span></span> <span data-ttu-id="a3760-305">それに加えて、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] では、次のリストに示す、キー交換に関係するセキュリティ メッセージを記述する本文要素とアクションについて、キーと既知の可能性がある個人情報をメッセージ本文から削除します。</span><span class="sxs-lookup"><span data-stu-id="a3760-305">In addition, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] removes keys and known potentially personal information from message bodies for the body elements and actions in the following list, which describe security messages involved in key exchange.</span></span>  
  
 <span data-ttu-id="a3760-306">次の名前空間の場合 :</span><span class="sxs-lookup"><span data-stu-id="a3760-306">For the following namespaces:</span></span>  
  
 <span data-ttu-id="a3760-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" と xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (有効なアクションがない場合など)</span><span class="sxs-lookup"><span data-stu-id="a3760-307">xmlns:wst="http://schemas.xmlsoap.org/ws/2004/04/trust" and xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust" (for example, if no action available)</span></span>  
  
 <span data-ttu-id="a3760-308">キー交換を伴うこの本文要素について情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-308">Information is removed for these body elements, which involve key exchange:</span></span>  
  
 <span data-ttu-id="a3760-309">wst:RequestSecurityToken</span><span class="sxs-lookup"><span data-stu-id="a3760-309">wst:RequestSecurityToken</span></span>  
  
 <span data-ttu-id="a3760-310">wst:RequestSecurityTokenResponse</span><span class="sxs-lookup"><span data-stu-id="a3760-310">wst:RequestSecurityTokenResponse</span></span>  
  
 <span data-ttu-id="a3760-311">wst:RequestSecurityTokenResponseCollection</span><span class="sxs-lookup"><span data-stu-id="a3760-311">wst:RequestSecurityTokenResponseCollection</span></span>  
  
 <span data-ttu-id="a3760-312">次の各アクションについても情報が削除されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-312">Information is also removed for each of the following Actions:</span></span>  
  
 <span data-ttu-id="a3760-313">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue</span><span class="sxs-lookup"><span data-stu-id="a3760-313">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue</span></span>  
  
 <span data-ttu-id="a3760-314">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue</span><span class="sxs-lookup"><span data-stu-id="a3760-314">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue</span></span>  
  
 <span data-ttu-id="a3760-315">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew</span><span class="sxs-lookup"><span data-stu-id="a3760-315">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Renew</span></span>  
  
 <span data-ttu-id="a3760-316">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew</span><span class="sxs-lookup"><span data-stu-id="a3760-316">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Renew</span></span>  
  
 <span data-ttu-id="a3760-317">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel</span><span class="sxs-lookup"><span data-stu-id="a3760-317">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Cancel</span></span>  
  
 <span data-ttu-id="a3760-318">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel</span><span class="sxs-lookup"><span data-stu-id="a3760-318">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Cancel</span></span>  
  
 <span data-ttu-id="a3760-319">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate</span><span class="sxs-lookup"><span data-stu-id="a3760-319">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Validate</span></span>  
  
 <span data-ttu-id="a3760-320">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate</span><span class="sxs-lookup"><span data-stu-id="a3760-320">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Validate</span></span>  
  
 <span data-ttu-id="a3760-321">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT</span><span class="sxs-lookup"><span data-stu-id="a3760-321">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT</span></span>  
  
 <span data-ttu-id="a3760-322">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT</span><span class="sxs-lookup"><span data-stu-id="a3760-322">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT</span></span>  
  
 <span data-ttu-id="a3760-323">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend</span><span class="sxs-lookup"><span data-stu-id="a3760-323">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Amend</span></span>  
  
 <span data-ttu-id="a3760-324">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend</span><span class="sxs-lookup"><span data-stu-id="a3760-324">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Amend</span></span>  
  
 <span data-ttu-id="a3760-325">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew</span><span class="sxs-lookup"><span data-stu-id="a3760-325">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Renew</span></span>  
  
 <span data-ttu-id="a3760-326">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew</span><span class="sxs-lookup"><span data-stu-id="a3760-326">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Renew</span></span>  
  
 <span data-ttu-id="a3760-327">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel</span><span class="sxs-lookup"><span data-stu-id="a3760-327">http://schemas.xmlsoap.org/ws/2005/02/trust/RST/SCT/Cancel</span></span>  
  
 <span data-ttu-id="a3760-328">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel</span><span class="sxs-lookup"><span data-stu-id="a3760-328">http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/SCT/Cancel</span></span>  
  
 <span data-ttu-id="a3760-329">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT</span><span class="sxs-lookup"><span data-stu-id="a3760-329">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT</span></span>  
  
 <span data-ttu-id="a3760-330">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT</span><span class="sxs-lookup"><span data-stu-id="a3760-330">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT</span></span>  
  
 <span data-ttu-id="a3760-331">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend</span><span class="sxs-lookup"><span data-stu-id="a3760-331">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RST/SCT-Amend</span></span>  
  
 <span data-ttu-id="a3760-332">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend</span><span class="sxs-lookup"><span data-stu-id="a3760-332">http://schemas.xmlsoap.org/ws/2004/04/security/trust/RSTR/SCT-Amend</span></span>  
  
#### <a name="no-information-is-removed-from-application-specific-headers-and-body-data"></a><span data-ttu-id="a3760-333">情報が削除されないアプリケーション固有のヘッダーと本文データ</span><span class="sxs-lookup"><span data-stu-id="a3760-333">No Information Is Removed from Application-specific Headers and Body Data</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="a3760-334"> では、アプリケーション固有のヘッダー (クエリ文字列など) と本文データ (クレジット カード番号など) にある個人情報を追跡しません。</span><span class="sxs-lookup"><span data-stu-id="a3760-334"> does not track personal information in application-specific headers (for example, query strings) or body data (for example, credit card number).</span></span>  
  
 <span data-ttu-id="a3760-335">メッセージ ログが有効な場合、アプリケーション固有のヘッダーと本文情報にある個人情報はログに表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-335">When message logging is on, personal information in application-specific headers and body information may be visible in the logs.</span></span> <span data-ttu-id="a3760-336">そのため、この場合もアプリケーションを配置するユーザーが、構成ファイルとログ ファイルに対する ACL を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-336">Again, the application deployer is responsible for setting the ACLs on the configuration and log files.</span></span> <span data-ttu-id="a3760-337">また、この情報を表示しない場合にログを無効にすることや、情報がログに記録された後で、この情報をログ ファイルからフィルターで除外することもできます。</span><span class="sxs-lookup"><span data-stu-id="a3760-337">He also can turn off logging if he does not want this information to be visible, or he may filter out this information from the log files after it is logged.</span></span>  
  
### <a name="service-model-tracing"></a><span data-ttu-id="a3760-338">サービス モデル トレース</span><span class="sxs-lookup"><span data-stu-id="a3760-338">Service Model Tracing</span></span>  
 <span data-ttu-id="a3760-339">サービス モデルのトレース ソース (<xref:System.ServiceModel>) によって、メッセージ処理に関するアクティビティとイベントのトレースを実行できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-339">The Service Model trace source (<xref:System.ServiceModel>) enables tracing of activities and events related to message processing.</span></span> <span data-ttu-id="a3760-340">この機能では、<xref:System.Diagnostics> から .NET Framework 診断機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="a3760-340">This feature uses the .NET Framework diagnostic functionality from <xref:System.Diagnostics>.</span></span> <span data-ttu-id="a3760-341"><xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> プロパティと同様、場所とその ACL は、.NET Framework アプリケーションの構成ファイルを使用してユーザーが設定できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-341">As with the <xref:System.ServiceModel.Configuration.DiagnosticSection.MessageLogging%2A> property, the location and its ACL are user-configurable using .NET Framework application configuration files.</span></span> <span data-ttu-id="a3760-342">メッセージ ログと同様、管理者がトレースを有効にするときに必ずファイルの場所が設定されるので、管理者は ACL を制御できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-342">As with message logging, the file location is always configured when the administrator enables tracing; thus, the administrator controls the ACL.</span></span>  
  
 <span data-ttu-id="a3760-343">スコープ内のメッセージに含まれるメッセージ ヘッダーをトレースします。</span><span class="sxs-lookup"><span data-stu-id="a3760-343">Traces contain message headers when a message is in scope.</span></span> <span data-ttu-id="a3760-344">前のセクションで説明した、メッセージ ヘッダーに含まれる個人情報の可能性がある情報を非表示にする場合と同じ規則が適用されます。既定では、先に示した個人情報はトレース時にヘッダーから削除されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-344">The same rules for hiding potentially personal information in message headers in the previous section apply: the personal information previously identified is removed by default from the headers in traces.</span></span> <span data-ttu-id="a3760-345">個人情報の可能性がある情報をログに記録するには、コンピューターの管理者とアプリケーションを配置するユーザーの両方が構成を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-345">Both the machine administrator and the application deployer must modify the configuration in order to log potentially personal information.</span></span> <span data-ttu-id="a3760-346">ただし、アプリケーション固有のヘッダーにある個人情報はトレース時にログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-346">However, personal information contained in application-specific headers is logged in traces.</span></span> <span data-ttu-id="a3760-347">アプリケーションを配置するユーザーは、構成ファイルとトレース ファイルに対する ACL を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-347">The application deployer is responsible for setting the ACLs on the configuration and trace files.</span></span> <span data-ttu-id="a3760-348">また、この情報を表示しない場合にトレースを無効にすることや、情報がログに記録された後で、この情報をトレース ファイルからフィルターで除外することもできます。</span><span class="sxs-lookup"><span data-stu-id="a3760-348">He also can turn off tracing if he does not want this information to be visible, or he can filter out this information from the trace files after it is logged.</span></span>  
  
 <span data-ttu-id="a3760-349">ServiceModel トレースの一部として、一意な ID (呼び出されたアクティビティ ID、通常は GUID) は、インフラストラクチャのさまざまな部分を通過するメッセージとして、異なる複数のアクティビティを結合します。</span><span class="sxs-lookup"><span data-stu-id="a3760-349">As part of ServiceModel Tracing, Unique IDs (called Activity IDs, and typically a GUID) link different activities together as a message flows through different parts of the infrastructure.</span></span>  
  
#### <a name="custom-trace-listeners"></a><span data-ttu-id="a3760-350">カスタム トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="a3760-350">Custom Trace Listeners</span></span>  
 <span data-ttu-id="a3760-351">メッセージ ログとトレースの両方で、カスタム トレース リスナーを構成できます。このリスナーは、ネットワーク上で、リモート データベースなどにトレースとメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-351">For both message logging and tracing, a custom trace listener can be configured, which can send traces and messages on the wire (for example, to a remote database).</span></span> <span data-ttu-id="a3760-352">アプリケーションを配置するユーザーは、カスタム リスナーを構成するか、ユーザーがリスナーを構成できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-352">The application deployer is responsible for configuring custom listeners or enabling users to do so.</span></span> <span data-ttu-id="a3760-353">また、遠隔地で公開される個人情報に対しても責任があり、この遠隔地に ACL を適切に適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3760-353">He is also responsible for any personal information exposed at the remote location, and for properly applying ACLs to this location.</span></span>  
  
### <a name="other-features-for-it-professionals"></a><span data-ttu-id="a3760-354">IT 専門家向けのその他の機能</span><span class="sxs-lookup"><span data-stu-id="a3760-354">Other features for IT Professionals</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="a3760-355"> には、Windows に付属の WMI から [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] インフラストラクチャ構成情報を公開する WMI プロバイダーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="a3760-355"> has a WMI provider that exposes the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastructure configuration information through WMI (shipped with Windows).</span></span> <span data-ttu-id="a3760-356">既定では、WMI インターフェイスは管理者が利用できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-356">By default, the WMI interface is available to administrators.</span></span>  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="a3760-357"> 構成では、.NET Framework 構成のしくみを使用します。</span><span class="sxs-lookup"><span data-stu-id="a3760-357"> configuration uses the .NET Framework configuration mechanism.</span></span> <span data-ttu-id="a3760-358">構成ファイルはコンピューターに保存されます。</span><span class="sxs-lookup"><span data-stu-id="a3760-358">The configuration files are stored on the machine.</span></span> <span data-ttu-id="a3760-359">アプリケーション開発者と管理者が、アプリケーションの要件に応じて構成ファイルと ACL を作成します。</span><span class="sxs-lookup"><span data-stu-id="a3760-359">The application developer and the administrator create the configuration files and ACL for each of the application's requirements.</span></span> <span data-ttu-id="a3760-360">構成ファイルには、エンドポイント アドレスと証明書ストア内の証明書へのリンクを入れることができます。</span><span class="sxs-lookup"><span data-stu-id="a3760-360">A configuration file can contain endpoint addresses and links to certificates in the certificate store.</span></span> <span data-ttu-id="a3760-361">証明書を使用してアプリケーション データを提供し、アプリケーションによって使用される機能の各プロパティを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="a3760-361">The certificates can be used to provide application data to configure various properties of the features used by the application.</span></span>  
  
 <span data-ttu-id="a3760-362">また、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] では、<xref:System.Environment.FailFast%2A> メソッドを呼び出すことによって、.NET Framework のプロセス ダンプ機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="a3760-362">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] also uses the .NET Framework process dump functionality by calling the <xref:System.Environment.FailFast%2A> method.</span></span>  
  
### <a name="it-pro-tools"></a><span data-ttu-id="a3760-363">IT 専門家のツール</span><span class="sxs-lookup"><span data-stu-id="a3760-363">IT Pro Tools</span></span>  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="a3760-364"> には、次の IT 専門家向けのツールも用意されており、Windows SDK に同梱されています。</span><span class="sxs-lookup"><span data-stu-id="a3760-364"> also provides the following IT professional tools, which ship in the Windows SDK.</span></span>  
  
#### <a name="svctraceviewerexe"></a><span data-ttu-id="a3760-365">SvcTraceViewer.exe</span><span class="sxs-lookup"><span data-stu-id="a3760-365">SvcTraceViewer.exe</span></span>  
 <span data-ttu-id="a3760-366">このビューアーは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] トレース ファイルを表示します。</span><span class="sxs-lookup"><span data-stu-id="a3760-366">The viewer displays [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] trace files.</span></span> <span data-ttu-id="a3760-367">このビューアーは、トレースに含まれているすべての情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="a3760-367">The viewer shows whatever information is contained in the traces.</span></span>  
  
#### <a name="svcconfigeditorexe"></a><span data-ttu-id="a3760-368">SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="a3760-368">SvcConfigEditor.exe</span></span>  
 <span data-ttu-id="a3760-369">このエディターでは、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 構成ファイルを作成し、編集できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-369">The editor allows the user to create and edit [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] configuration files.</span></span> <span data-ttu-id="a3760-370">このエディターは、構成ファイルに含まれているすべての情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="a3760-370">The editor shows whatever information is contained in the configuration files.</span></span> <span data-ttu-id="a3760-371">テキスト エディターでも同じ操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-371">The same task can be accomplished with a text editor.</span></span>  
  
#### <a name="servicemodelreg"></a><span data-ttu-id="a3760-372">ServiceModel_Reg</span><span class="sxs-lookup"><span data-stu-id="a3760-372">ServiceModel_Reg</span></span>  
 <span data-ttu-id="a3760-373">このツールでは、コンピューター上の ServiceModel のインストールを管理できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-373">This tool allows the user to manage ServiceModel installs on a machine.</span></span> <span data-ttu-id="a3760-374">このツールは、実行時にコンソール ウィンドウにステータス メッセージを表示し、処理中に [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] インストールの構成に関する情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-374">The tool displays status messages in a console window when it runs and, in the process, may display information about the configuration of the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] installation.</span></span>  
  
#### <a name="wsatconfigexe-and-wsatuidll"></a><span data-ttu-id="a3760-375">WSATConfig.exe と WSATUI.dll</span><span class="sxs-lookup"><span data-stu-id="a3760-375">WSATConfig.exe and WSATUI.dll</span></span>  
 <span data-ttu-id="a3760-376">このツールによって、IT 専門家は [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] で相互運用可能な WS-AtomicTransaction ネットワーク サポートを構成できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-376">These tools allow IT Professionals to configure interoperable WS-AtomicTransaction network support in [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="a3760-377">このツールは、レジストリに格納された最も一般的に使用される WS-AtomicTransaction 設定の値を表示し、ユーザーはこのツールを使用してその値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-377">The tools display and allow the user to change the values of the most commonly used WS-AtomicTransaction settings stored in the registry.</span></span>  
  
## <a name="cross-cutting-features"></a><span data-ttu-id="a3760-378">広範囲に使用できる機能</span><span class="sxs-lookup"><span data-stu-id="a3760-378">Cross-cutting Features</span></span>  
 <span data-ttu-id="a3760-379">次の機能は広範囲に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-379">The following features are cross-cutting.</span></span> <span data-ttu-id="a3760-380">つまり、前述の任意の機能と共に構成できます。</span><span class="sxs-lookup"><span data-stu-id="a3760-380">That is, they can be composed with any of the preceding features.</span></span>  
  
### <a name="service-framework"></a><span data-ttu-id="a3760-381">サービス フレームワーク</span><span class="sxs-lookup"><span data-stu-id="a3760-381">Service Framework</span></span>  
 <span data-ttu-id="a3760-382">ヘッダーには、インスタンス ID を入れることができます。このインスタンス ID は、メッセージを CLR クラスのインスタンスに関連付ける GUID です。</span><span class="sxs-lookup"><span data-stu-id="a3760-382">Headers can contain an instance ID, which is a GUID that associates a message with an instance of a CLR class.</span></span>  
  
 <span data-ttu-id="a3760-383">Web サービス記述言語 (WSDL) には、ポートの定義が入ります。</span><span class="sxs-lookup"><span data-stu-id="a3760-383">The Web Services Description Language (WSDL) contains a definition of the port.</span></span> <span data-ttu-id="a3760-384">各ポートには、エンドポイント アドレス、およびアプリケーションが使用するサービスを表すバインディングがあります。</span><span class="sxs-lookup"><span data-stu-id="a3760-384">Each port has an endpoint address and a binding that represents the services used by the application.</span></span> <span data-ttu-id="a3760-385">WSDL の公開は、構成を使用して無効にできます。</span><span class="sxs-lookup"><span data-stu-id="a3760-385">Exposing WSDL can be turned off using configuration.</span></span> <span data-ttu-id="a3760-386">コンピューターに保持される情報はありません。</span><span class="sxs-lookup"><span data-stu-id="a3760-386">No information is retained on the machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3760-387">参照</span><span class="sxs-lookup"><span data-stu-id="a3760-387">See Also</span></span>  
 [<span data-ttu-id="a3760-388">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a3760-388">Windows Communication Foundation</span></span>](http://msdn.microsoft.com/library/fd327ade-0260-4c40-adbe-b74645ba3277)  
 [<span data-ttu-id="a3760-389">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="a3760-389">Security</span></span>](../../../docs/framework/wcf/feature-details/security.md)
