---
title: トランザクション プロトコル バージョン 1.0
ms.date: 03/30/2017
ms.assetid: 034679af-0002-402e-98a8-ef73dcd71bb6
ms.openlocfilehash: d510a74560369a132822e980e7812ca4deff55a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506699"
---
# <a name="transaction-protocols-version-10"></a><span data-ttu-id="632fa-102">トランザクション プロトコル バージョン 1.0</span><span class="sxs-lookup"><span data-stu-id="632fa-102">Transaction Protocols version 1.0</span></span>
<span data-ttu-id="632fa-103">Windows Communication Foundation (WCF) バージョン 1 は、Ws-atomic Transaction プロトコルおよび Ws-coordination プロトコルの version 1.0 を実装します。</span><span class="sxs-lookup"><span data-stu-id="632fa-103">Windows Communication Foundation (WCF) version 1 implements version 1.0 of the WS-Atomic Transaction and WS-Coordination protocols.</span></span> <span data-ttu-id="632fa-104">バージョン 1.1 の詳細については、次を参照してください。[トランザクション プロトコル](../../../../docs/framework/wcf/feature-details/transaction-protocols.md)です。</span><span class="sxs-lookup"><span data-stu-id="632fa-104">For more information about version 1.1, see [Transaction Protocols](../../../../docs/framework/wcf/feature-details/transaction-protocols.md).</span></span>  
  
|<span data-ttu-id="632fa-105">仕様/ドキュメント</span><span class="sxs-lookup"><span data-stu-id="632fa-105">Specification/Document</span></span>|<span data-ttu-id="632fa-106">Link</span><span class="sxs-lookup"><span data-stu-id="632fa-106">Link</span></span>|  
|-----------------------------|----------|  
|<span data-ttu-id="632fa-107">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="632fa-107">WS-Coordination</span></span>|http://msdn.microsoft.com/ws/2005/08/ws-coordination/|  
|<span data-ttu-id="632fa-108">WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="632fa-108">WS-AtomicTransaction</span></span>|http://msdn.microsoft.com/ws/2005/08/ws-atomictransaction/|  
  
 <span data-ttu-id="632fa-109">これらのプロトコル仕様の相互運用性は、アプリケーション間とトランザクション マネージャー間の 2 つのレベルで必要です (次の図を参照)。</span><span class="sxs-lookup"><span data-stu-id="632fa-109">Interoperability on these protocol specifications is required at two levels: between applications and between transaction managers (see the following figure).</span></span> <span data-ttu-id="632fa-110">仕様では、相互運用性の両方のレベルについて、メッセージ形式とメッセージ交換が詳細に説明されます。</span><span class="sxs-lookup"><span data-stu-id="632fa-110">Specifications describe in great detail the message formats and message exchange for both interoperability levels.</span></span> <span data-ttu-id="632fa-111">アプリケーション間での交換に必要な一定のセキュリティ、信頼性、およびエンコーディングは、通常のアプリケーションによる交換にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="632fa-111">Certain security, reliability, and encodings for application-to-application exchange apply as they do for regular application exchange.</span></span> <span data-ttu-id="632fa-112">ただし、トランザクション マネージャー間で適切な相互運用性を実現するには、特定のバインディングを使用するという合意が必要となります。通常、バインディングはユーザーによって構成されないためです。</span><span class="sxs-lookup"><span data-stu-id="632fa-112">However, successful interoperability between transaction managers requires agreement on the particular binding, because it is usually not configured by the user.</span></span>  
  
 <span data-ttu-id="632fa-113">ここでは、WS-AtomicTransaction (WS-AT) 仕様のセキュリティに関する構成と、トランザクション マネージャー間の通信に使用されるセキュリティで保護されたバインディングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="632fa-113">This topic describes a composition of the WS-Atomic Transaction (WS-AT) specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="632fa-114">このドキュメントで説明されているアプローチは、IBM、IONA、Sun Microsystems などを含む WS-AT および WS-Coordination の各種の実装でテスト済みのものです。</span><span class="sxs-lookup"><span data-stu-id="632fa-114">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination including IBM, IONA, Sun Microsystems, and others.</span></span>  
  
 <span data-ttu-id="632fa-115">次の図は、2 つのトランザクション マネージャー (Transaction Manager 1 と Transaction Manager 2)、および 2 つのアプリケーション (Application 1 と Application 2) 間の相互運用性を示しています。</span><span class="sxs-lookup"><span data-stu-id="632fa-115">The following figure depicts the interoperability between two transaction managers, Transaction Manager 1 and Transaction Manager 2, and two applications, Application 1 and Application 2.</span></span>  
  
 <span data-ttu-id="632fa-116">![トランザクション プロトコル](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "トランザクション")</span><span class="sxs-lookup"><span data-stu-id="632fa-116">![Transaction Protocols](../../../../docs/framework/wcf/feature-details/media/transactionmanagers.gif "TransactionManagers")</span></span>  
  
 <span data-ttu-id="632fa-117">1 つのイニシエーター (I) と 1 つの参加要素 (P) を持つ、一般的な WS-Coordination/WS-AtomicTransaction のシナリオを考えます。</span><span class="sxs-lookup"><span data-stu-id="632fa-117">Consider a typical WS-Coordination/WS-Atomic Transaction scenario with one Initiator (I) and one Participant (P).</span></span> <span data-ttu-id="632fa-118">イニシエーターと参加要素の両方にトランザクション マネージャー (それぞれ ITM および PTM と呼びます) があります。</span><span class="sxs-lookup"><span data-stu-id="632fa-118">Both Initiator and Participant have Transaction Managers, (ITM and PTM, respectively).</span></span> <span data-ttu-id="632fa-119">2 フェーズ コミットは、このトピックでは 2PC と呼びます。</span><span class="sxs-lookup"><span data-stu-id="632fa-119">Two-phase commit is referred to as 2PC in this topic.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="632fa-120">1.CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="632fa-120">1. CreateCoordinationContext</span></span>|<span data-ttu-id="632fa-121">12.アプリケーション メッセージ応答</span><span class="sxs-lookup"><span data-stu-id="632fa-121">12. Application Message Response</span></span>|  
|<span data-ttu-id="632fa-122">2.CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="632fa-122">2. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="632fa-123">13.Commit (完了)</span><span class="sxs-lookup"><span data-stu-id="632fa-123">13. Commit (Completion)</span></span>|  
|<span data-ttu-id="632fa-124">3.Register (完了)</span><span class="sxs-lookup"><span data-stu-id="632fa-124">3. Register (Completion)</span></span>|<span data-ttu-id="632fa-125">14.Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="632fa-125">14. Prepare (2PC)</span></span>|  
|<span data-ttu-id="632fa-126">4.RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="632fa-126">4. RegisterResponse</span></span>|<span data-ttu-id="632fa-127">15.Prepare (2PC)</span><span class="sxs-lookup"><span data-stu-id="632fa-127">15. Prepare (2PC)</span></span>|  
|<span data-ttu-id="632fa-128">5.アプリケーション メッセージ</span><span class="sxs-lookup"><span data-stu-id="632fa-128">5. Application Message</span></span>|<span data-ttu-id="632fa-129">16.Prepared (2PC)</span><span class="sxs-lookup"><span data-stu-id="632fa-129">16. Prepared (2PC)</span></span>|  
|<span data-ttu-id="632fa-130">6.CreateCoordinationContext with Context</span><span class="sxs-lookup"><span data-stu-id="632fa-130">6. CreateCoordinationContext with Context</span></span>|<span data-ttu-id="632fa-131">17.Prepared (2PC)</span><span class="sxs-lookup"><span data-stu-id="632fa-131">17. Prepared (2PC)</span></span>|  
|<span data-ttu-id="632fa-132">7.Register (永続的)</span><span class="sxs-lookup"><span data-stu-id="632fa-132">7. Register (Durable)</span></span>|<span data-ttu-id="632fa-133">18.Committed (完了)</span><span class="sxs-lookup"><span data-stu-id="632fa-133">18. Committed (Completion)</span></span>|  
|<span data-ttu-id="632fa-134">8.RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="632fa-134">8. RegisterResponse</span></span>|<span data-ttu-id="632fa-135">19.Commit (2PC)</span><span class="sxs-lookup"><span data-stu-id="632fa-135">19. Commit (2PC)</span></span>|  
|<span data-ttu-id="632fa-136">9.CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="632fa-136">9. CreateCoordinationContextResponse</span></span>|<span data-ttu-id="632fa-137">20.Commit (2PC)</span><span class="sxs-lookup"><span data-stu-id="632fa-137">20. Commit (2PC)</span></span>|  
|<span data-ttu-id="632fa-138">10.Register (永続的)</span><span class="sxs-lookup"><span data-stu-id="632fa-138">10. Register (Durable)</span></span>|<span data-ttu-id="632fa-139">21.Committed (2PC)</span><span class="sxs-lookup"><span data-stu-id="632fa-139">21. Committed (2PC)</span></span>|  
|<span data-ttu-id="632fa-140">11.RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="632fa-140">11. RegisterResponse</span></span>|<span data-ttu-id="632fa-141">22.Committed (2PC)</span><span class="sxs-lookup"><span data-stu-id="632fa-141">22. Committed (2PC)</span></span>|  
  
 <span data-ttu-id="632fa-142">このドキュメントでは、WS-AtomicTransaction 仕様のセキュリティに関する構成と、トランザクション マネージャー間の通信に使用されるセキュリティで保護されたバインディングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="632fa-142">This document describes a composition of the WS-AtomicTransaction specification with security and describes the secure binding used for communication between transaction managers.</span></span> <span data-ttu-id="632fa-143">このドキュメントで説明されているアプローチは、WS-AT および WS-Coordination の各種の実装でテスト済みのものです。</span><span class="sxs-lookup"><span data-stu-id="632fa-143">The approach described in this document has been successfully tested with other implementations of WS-AT and WS-Coordination.</span></span>  
  
 <span data-ttu-id="632fa-144">この図および表では、セキュリティの観点から見た次の 4 つのクラスのメッセージを示しています。</span><span class="sxs-lookup"><span data-stu-id="632fa-144">The figure and table illustrate four classes of messages from the viewpoint of security:</span></span>  
  
-   <span data-ttu-id="632fa-145">アクティベーション メッセージ (CreateCoordinationContext と CreateCoordinationContextResponse)</span><span class="sxs-lookup"><span data-stu-id="632fa-145">Activation messages (CreateCoordinationContext and CreateCoordinationContextResponse).</span></span>  
  
-   <span data-ttu-id="632fa-146">登録メッセージ (Register と RegisterResponse)</span><span class="sxs-lookup"><span data-stu-id="632fa-146">Registration messages (Register and RegisterResponse)</span></span>  
  
-   <span data-ttu-id="632fa-147">プロトコル メッセージ (Prepare、Rollback、Commit、Aborted など)</span><span class="sxs-lookup"><span data-stu-id="632fa-147">Protocol messages (Prepare, Rollback, Commit, Aborted, and so on).</span></span>  
  
-   <span data-ttu-id="632fa-148">アプリケーション メッセージ</span><span class="sxs-lookup"><span data-stu-id="632fa-148">Application messages.</span></span>  
  
 <span data-ttu-id="632fa-149">最初の 3 つのメッセージ クラスはトランザクション マネージャーのメッセージと考えられます。これらのクラスのバインディング構成については、後の「アプリケーション メッセージ交換」で説明します。</span><span class="sxs-lookup"><span data-stu-id="632fa-149">The first three message classes are considered Transaction Manager messages and their binding configuration is described in the "Application Message Exchange" later in this topic.</span></span> <span data-ttu-id="632fa-150">4 番目のメッセージ クラスは、アプリケーション間のメッセージであり、後の「メッセージの例」で説明します。</span><span class="sxs-lookup"><span data-stu-id="632fa-150">The fourth class of message is application to application messages and is described in the "Message Examples" section later in this topic.</span></span> <span data-ttu-id="632fa-151">このセクションでは、これらのクラスの各 WCF によって使用されるプロトコル バインディングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="632fa-151">This section describes the protocol bindings used for each of these classes by WCF.</span></span>  
  
 <span data-ttu-id="632fa-152">このドキュメントでは、次の XML 名前空間と関連付けられたプレフィックスが使用されます。</span><span class="sxs-lookup"><span data-stu-id="632fa-152">The following XML Namespaces and associated prefixes are used throughout this document.</span></span>  
  
|<span data-ttu-id="632fa-153">プレフィックス</span><span class="sxs-lookup"><span data-stu-id="632fa-153">Prefix</span></span>|<span data-ttu-id="632fa-154">名前空間の URI</span><span class="sxs-lookup"><span data-stu-id="632fa-154">Namespace URI</span></span>|  
|------------|-------------------|  
|<span data-ttu-id="632fa-155">s11</span><span class="sxs-lookup"><span data-stu-id="632fa-155">s11</span></span>|http://schemas.xmlsoap.org/soap/envelope|  
|<span data-ttu-id="632fa-156">wsa</span><span class="sxs-lookup"><span data-stu-id="632fa-156">wsa</span></span>|http://www.w3.org/2004/08/addressing|  
|<span data-ttu-id="632fa-157">wscoor</span><span class="sxs-lookup"><span data-stu-id="632fa-157">wscoor</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wscoor|  
|<span data-ttu-id="632fa-158">wsat</span><span class="sxs-lookup"><span data-stu-id="632fa-158">wsat</span></span>|http://schemas.xmlsoap.org/ws/2004/10/wsat|  
|<span data-ttu-id="632fa-159">t</span><span class="sxs-lookup"><span data-stu-id="632fa-159">t</span></span>|http://schemas.xmlsoap.org/ws/2005/02/trust|  
|<span data-ttu-id="632fa-160">o</span><span class="sxs-lookup"><span data-stu-id="632fa-160">o</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd|  
|<span data-ttu-id="632fa-161">xsd</span><span class="sxs-lookup"><span data-stu-id="632fa-161">xsd</span></span>|http://www.w3.org/2001/XMLSchema|  
  
## <a name="transaction-manager-bindings"></a><span data-ttu-id="632fa-162">トランザクション マネージャー バインディング</span><span class="sxs-lookup"><span data-stu-id="632fa-162">Transaction Manager Bindings</span></span>  
 <span data-ttu-id="632fa-163">R1001 : トランザクション マネージャーは、SOAP 1.1、WS-Addressing 2004/08 for WS-AtomicTransaction、および WS-Coordination メッセージ交換を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="632fa-163">R1001: Transaction Managers must use SOAP 1.1 and WS-Addressing 2004/08 for WS-Atomic Transaction and WS-Coordination message exchanges.</span></span>  
  
 <span data-ttu-id="632fa-164">アプリケーション メッセージは、後で説明するように、これらのバインディングに制限されません。</span><span class="sxs-lookup"><span data-stu-id="632fa-164">Application messages are not constrained to these bindings and are described later.</span></span>  
  
### <a name="transaction-manager-https-binding"></a><span data-ttu-id="632fa-165">トランザクション マネージャー HTTPS バインディング</span><span class="sxs-lookup"><span data-stu-id="632fa-165">Transaction Manager HTTPS Binding</span></span>  
 <span data-ttu-id="632fa-166">トランザクション マネージャー HTTPS バインディングは、セキュリティを実現してトランザクション ツリー内の送信者と受信者の各ペア間で信頼を確立するトランスポート セキュリティにのみ依存します。</span><span class="sxs-lookup"><span data-stu-id="632fa-166">The transaction manager HTTPS binding relies solely on transport security to achieve security and establish trust between each sender-receiver pair in the transaction tree.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="632fa-167">HTTPS トランスポート構成</span><span class="sxs-lookup"><span data-stu-id="632fa-167">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="632fa-168">トランザクション マネージャー ID を確立するために X.509 証明書が使用されます。</span><span class="sxs-lookup"><span data-stu-id="632fa-168">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="632fa-169">クライアントおよびサーバーの承認が必要です。クライアントおよびサーバーの承認は、以下のような実装詳細の状態にしておきます。</span><span class="sxs-lookup"><span data-stu-id="632fa-169">Client/server authentication is required, and client/server authorization is left as an implementation detail:</span></span>  
  
-   <span data-ttu-id="632fa-170">R1111 : ネットワーク経由で示された X.509 証明書は、発信元コンピューターの完全修飾ドメイン名 (FQDN) と一致するサブジェクト名を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="632fa-170">R1111: X.509 certificates presented over the wire must have a subject name that matches the fully qualified domain name (FQDN) of the originating machine.</span></span>  
  
-   <span data-ttu-id="632fa-171">B1112 : X.509 のサブジェクト名のチェックが成功するには、システム内の送信者と受信者の各ペア間で、DNS が機能している必要があります。</span><span class="sxs-lookup"><span data-stu-id="632fa-171">B1112: DNS must be functional between each sender-receiver pair in the system for X.509 subject name checks to succeed.</span></span>  
  
#### <a name="activation-and-registration-binding-configuration"></a><span data-ttu-id="632fa-172">アクティベーションと登録のバインド構成</span><span class="sxs-lookup"><span data-stu-id="632fa-172">Activation and Registration Binding Configuration</span></span>  
 <span data-ttu-id="632fa-173">WCF では、HTTPS 経由での相関関係と共に、要求/応答の二重バインディングが必要です。</span><span class="sxs-lookup"><span data-stu-id="632fa-173">WCF requires request/reply duplex binding with correlation over HTTPS.</span></span> <span data-ttu-id="632fa-174">(関連付けと要求/応答メッセージ交換パターンの詳細については、WS-AtomicTransaction 仕様のセクション 8 を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="632fa-174">(For more information about correlation and descriptions of the request/reply message exchange patterns, see WS-Atomic Transaction, Section 8.)</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="632fa-175">2PC プロトコルのバインド構成</span><span class="sxs-lookup"><span data-stu-id="632fa-175">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="632fa-176">WCF では、HTTPS 経由で一方向 (データグラム) メッセージをサポートします。</span><span class="sxs-lookup"><span data-stu-id="632fa-176">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="632fa-177">メッセージ間の関連付けは、実装詳細の状態にしておきます。</span><span class="sxs-lookup"><span data-stu-id="632fa-177">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="632fa-178">B2131: 実装をサポートする必要があります`wsa:ReferenceParameters`WCF の 2 pc メッセージの関連付けを実現するために WS アドレス指定」の説明に従ってします。</span><span class="sxs-lookup"><span data-stu-id="632fa-178">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
### <a name="transaction-manager-mixed-security-binding"></a><span data-ttu-id="632fa-179">トランザクション マネージャーによる混合セキュリティ バインディング</span><span class="sxs-lookup"><span data-stu-id="632fa-179">Transaction Manager Mixed Security Binding</span></span>  
 <span data-ttu-id="632fa-180">これは、代替 (混在モード) をトランスポート セキュリティと組み合わせて使用 Ws-coordination 発行済みトークンの id を確立するためのモデルをバインドします。</span><span class="sxs-lookup"><span data-stu-id="632fa-180">This is an alternate (mixed mode) binding that uses transport security combined with the  WS-Coordination Issued Token model for identity establishment purposes.</span></span>  <span data-ttu-id="632fa-181">2 つのバインディングを区別する要素は、アクティベーションと登録のみです。</span><span class="sxs-lookup"><span data-stu-id="632fa-181">Activation and Registration are the only elements that differ between the two bindings.</span></span>  
  
#### <a name="https-transport-configuration"></a><span data-ttu-id="632fa-182">HTTPS トランスポート構成</span><span class="sxs-lookup"><span data-stu-id="632fa-182">HTTPS Transport Configuration</span></span>  
 <span data-ttu-id="632fa-183">トランザクション マネージャー ID を確立するために X.509 証明書が使用されます。</span><span class="sxs-lookup"><span data-stu-id="632fa-183">X.509 certificates are used to establish Transaction Manager Identity.</span></span> <span data-ttu-id="632fa-184">クライアントおよびサーバーの承認が必要です。クライアントおよびサーバーの承認は、以下のような実装詳細の状態にしておきます。</span><span class="sxs-lookup"><span data-stu-id="632fa-184">Client/Server authentication is required, and client/server authorization is left as an implementation detail.</span></span>  
  
#### <a name="activation-message-binding-configuration"></a><span data-ttu-id="632fa-185">アクティベーション メッセージのバインド構成</span><span class="sxs-lookup"><span data-stu-id="632fa-185">Activation Message Binding Configuration</span></span>  
 <span data-ttu-id="632fa-186">アクティベーション メッセージは通常、アプリケーションとローカルのトランザクション マネージャー間で発生するため、相互運用には参加しません。</span><span class="sxs-lookup"><span data-stu-id="632fa-186">Activation Messages usually do not participate in interoperability because they typically occur between an application and its local Transaction Manager.</span></span>  
  
 <span data-ttu-id="632fa-187">B1221: 双方向の HTTPS バインドを使用する WCF (」に記載[メッセージング プロトコル](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) アクティベーション メッセージにします。</span><span class="sxs-lookup"><span data-stu-id="632fa-187">B1221: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)) for Activation messages.</span></span> <span data-ttu-id="632fa-188">要求および応答メッセージは、WS-Addressing 2004/08 を使用して関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="632fa-188">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="632fa-189">WS-AtomicTransaction 仕様のセクション 8 では、関連付けとメッセージ交換のパターンについて詳細に説明されています。</span><span class="sxs-lookup"><span data-stu-id="632fa-189">WS-Atomic Transaction specification, Section 8, describes further details about correlation and the message exchange patterns.</span></span>  
  
-   <span data-ttu-id="632fa-190">R1222 : `CreateCoordinationContext` を受信すると、コーディネーターは、関連付けられている秘密の `SecurityContextToken` を使用して `STx` を発行します。</span><span class="sxs-lookup"><span data-stu-id="632fa-190">R1222: Upon receiving a `CreateCoordinationContext`, the Coordinator must issue a `SecurityContextToken` with associated secret `STx`.</span></span> <span data-ttu-id="632fa-191">このトークンは、WS-Trust の仕様に従って、`t:IssuedTokens` ヘッダー内に返されます。</span><span class="sxs-lookup"><span data-stu-id="632fa-191">This token is returned inside a `t:IssuedTokens` header following WS-Trust specification.</span></span>  
  
-   <span data-ttu-id="632fa-192">R1223 : アクティベーションが既存のコーディネーション コンテキスト内で発生した場合、既存のコンテキストに関連付けられた `t:IssuedTokens` がある `SecurityContextToken` ヘッダーは、`CreateCoordinationContext` メッセージでフローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="632fa-192">R1223: If Activation occurs within an existing Coordination Context, the `t:IssuedTokens` header with the `SecurityContextToken` associated with existing Context must flow on the `CreateCoordinationContext` message.</span></span>  
  
 <span data-ttu-id="632fa-193">新しい`t:IssuedTokens`送信にアタッチするためのヘッダーを生成する必要があります`wscoor:CreateCoordinationContextResponse`メッセージ。</span><span class="sxs-lookup"><span data-stu-id="632fa-193">A new `t:IssuedTokens` header should be generated for attaching to the outgoing `wscoor:CreateCoordinationContextResponse` message.</span></span>  
  
#### <a name="registration-message-binding-configuration"></a><span data-ttu-id="632fa-194">登録メッセージのバインド構成</span><span class="sxs-lookup"><span data-stu-id="632fa-194">Registration Message Binding Configuration</span></span>  
 <span data-ttu-id="632fa-195">B1231: 双方向の HTTPS バインドを使用する WCF (記載[メッセージング プロトコル](../../../../docs/framework/wcf/feature-details/messaging-protocols.md))。</span><span class="sxs-lookup"><span data-stu-id="632fa-195">B1231: WCF uses duplex HTTPS binding (described in [Messaging Protocols](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)).</span></span> <span data-ttu-id="632fa-196">要求および応答メッセージは、WS-Addressing 2004/08 を使用して関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="632fa-196">Request and Reply messages are correlated using WS-Addressing 2004/08.</span></span>  
  
 <span data-ttu-id="632fa-197">WS-AtomicTransaction 仕様のセクション 8 では、関連付けとメッセージ交換のパターンについて詳細に説明されています。</span><span class="sxs-lookup"><span data-stu-id="632fa-197">WS-AtomicTransaction, Section 8, describes further details about correlation and descriptions of the message exchange patterns.</span></span>  
  
 <span data-ttu-id="632fa-198">R1232: 発信`wscoor:Register`メッセージで使用する必要があります、`IssuedTokenOverTransport`で説明されている認証モード[セキュリティ プロトコル](../../../../docs/framework/wcf/feature-details/security-protocols.md)です。</span><span class="sxs-lookup"><span data-stu-id="632fa-198">R1232: Outgoing `wscoor:Register` messages must use the `IssuedTokenOverTransport` authentication mode described in [Security Protocols](../../../../docs/framework/wcf/feature-details/security-protocols.md).</span></span>  
  
 <span data-ttu-id="632fa-199">`wsse:Timestamp`要素を使用して署名する必要があります、`SecurityContextToken``STx`発行します。</span><span class="sxs-lookup"><span data-stu-id="632fa-199">The `wsse:Timestamp` element must be signed using the `SecurityContextToken``STx` issued.</span></span> <span data-ttu-id="632fa-200">この署名は特定のトランザクションに関連付けられたトークンを所有していることの証明であり、トランザクションに登録されている参加要素の認証で使用されます。</span><span class="sxs-lookup"><span data-stu-id="632fa-200">This signature is a proof of possession of the token associated with particular transaction and is used to authenticate a participant enlisting in the transaction.</span></span> <span data-ttu-id="632fa-201">RegistrationResponse メッセージは、HTTPS を使用して返信されます。</span><span class="sxs-lookup"><span data-stu-id="632fa-201">The RegistrationResponse message is sent back over HTTPS.</span></span>  
  
#### <a name="2pc-protocol-binding-configuration"></a><span data-ttu-id="632fa-202">2PC プロトコルのバインド構成</span><span class="sxs-lookup"><span data-stu-id="632fa-202">2PC Protocol Binding Configuration</span></span>  
 <span data-ttu-id="632fa-203">WCF では、HTTPS 経由で一方向 (データグラム) メッセージをサポートします。</span><span class="sxs-lookup"><span data-stu-id="632fa-203">WCF supports one-way (datagram) messages over HTTPS.</span></span> <span data-ttu-id="632fa-204">メッセージ間の関連付けは、実装詳細の状態にしておきます。</span><span class="sxs-lookup"><span data-stu-id="632fa-204">Correlation among the messages is left as an implementation detail.</span></span>  
  
 <span data-ttu-id="632fa-205">B2131: 実装をサポートする必要があります`wsa:ReferenceParameters`WCF の 2 pc メッセージの関連付けを実現するために WS アドレス指定」の説明に従ってします。</span><span class="sxs-lookup"><span data-stu-id="632fa-205">B2131: Implementations must support `wsa:ReferenceParameters` as described in WS-Addressing to achieve correlation of WCF’s 2PC messages.</span></span>  
  
## <a name="application-message-exchange"></a><span data-ttu-id="632fa-206">アプリケーション メッセージ交換</span><span class="sxs-lookup"><span data-stu-id="632fa-206">Application Message Exchange</span></span>  
 <span data-ttu-id="632fa-207">アプリケーションでは、バインディングが次のセキュリティ要件を満たしている限り、アプリケーション間メッセージに任意のバインディングを使用できます。</span><span class="sxs-lookup"><span data-stu-id="632fa-207">Applications are free to use any particular binding for application-to-application messages, as long as the binding meets the following security requirements:</span></span>  
  
-   <span data-ttu-id="632fa-208">R2001 : アプリケーション間メッセージでは、メッセージのヘッダーの `t:IssuedTokens` に加えて `CoordinationContext` ヘッダーをフローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="632fa-208">R2001: Application-to-application messages must flow the `t:IssuedTokens` header along with the `CoordinationContext` in the header of the message.</span></span>  
  
-   <span data-ttu-id="632fa-209">R2002 : `t:IssuedToken` の整合性と機密性が提供される必要があります。</span><span class="sxs-lookup"><span data-stu-id="632fa-209">R2002: Integrity and confidentiality of `t:IssuedToken` must be provided.</span></span>  
  
 <span data-ttu-id="632fa-210">`CoordinationContext` ヘッダーには `wscoor:Identifier` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="632fa-210">The `CoordinationContext` header contains `wscoor:Identifier`.</span></span> <span data-ttu-id="632fa-211">定義`xsd:AnyURI`、絶対と相対 Uri の使用できるように WCF のみがサポート`wscoor:Identifiers`、絶対 Uri であります。</span><span class="sxs-lookup"><span data-stu-id="632fa-211">While the definition of `xsd:AnyURI` allows the use of both absolute and relative URIs, WCF supports only `wscoor:Identifiers`, which are absolute URIs.</span></span>  
  
 <span data-ttu-id="632fa-212">場合、`wscoor:Identifier`の`wscoor:CoordinationContext`相対 uri では、トランザクションの WCF サービスからエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="632fa-212">If the `wscoor:Identifier` of the `wscoor:CoordinationContext` is a relative URI, faults will be returned from transactional WCF services.</span></span>  
  
## <a name="message-examples"></a><span data-ttu-id="632fa-213">メッセージの例</span><span class="sxs-lookup"><span data-stu-id="632fa-213">Message Examples</span></span>  
  
### <a name="createcoordinationcontext-requestresponse-messages"></a><span data-ttu-id="632fa-214">CreateCoordinationContext 要求/応答メッセージ</span><span class="sxs-lookup"><span data-stu-id="632fa-214">CreateCoordinationContext Request/Response Messages</span></span>  
 <span data-ttu-id="632fa-215">次のメッセージは、要求/応答のパターンに従います。</span><span class="sxs-lookup"><span data-stu-id="632fa-215">The following messages follow a request/response pattern.</span></span>  
  
#### <a name="createcoordinationcontext"></a><span data-ttu-id="632fa-216">CreateCoordinationContext</span><span class="sxs-lookup"><span data-stu-id="632fa-216">CreateCoordinationContext</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wscoor/CreateCoordinationContext</Action>  
    <a:MessageID>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</MessageID>  
    <a:ReplyTo>  
      <Address>https://...</a:Address>  
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security>  
      <u:Timestamp>  
        <wsu:Created>2005-12-15T23:36:09.921Z</u:Created>  
        <wsu:Expires>2005-12-15T23:41:09.921Z</u:Expires>  
      </u:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:CreateCoordinationContext>  
      <wscoor:CoordinationType>...</wscoor:CoordinationType>  
    </wscoor:CreateCoordinationContext>  
  </s:Body>  
</s11:Envelope>  
```  
  
#### <a name="createcoordinationcontextresponse"></a><span data-ttu-id="632fa-217">CreateCoordinationContextResponse</span><span class="sxs-lookup"><span data-stu-id="632fa-217">CreateCoordinationContextResponse</span></span>  
  
```xml  
<s:Envelope>  
  <!-- Data below is shown in the clear for  
       illustration purposes only. -->  
  <s:Header>  
    <a:Action>./ws/2004/10/wscoor/CreateCoordinationContextResponse </a:Action>  
    <a:RelatesTo>urn:uuid:069f5104-fd88-4264-9f99-60032a82854e</a:RelatesTo>  
    <a:To s:mustUnderstand="1">https://... </a:To>  
    <t:IssuedTokens>  
 <wst:RequestSecurityTokenResponse     
    xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
    xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd"   
    xmlns:wst="http://schemas.xmlsoap.org/ws/2005/02/trust"  
    xmlns:wsc="http://schemas.xmlsoap.org/ws/2005/02/sc"  
    xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy">  
    <wst:TokenType>http://schemas.xmlsoap.org/ws/2005/02/sc/sct</wst:TokenType>  
    <wst:RequestedSecurityToken>  
      <wsc:SecurityContextToken>  
        <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
        </wssu:Identifier>  
      </wsc:SecurityContextToken>   
    </wst:RequestedSecurityToken>  
    <wsp:AppliesTo>  
        http://fabrikam123.com/CCi  
    </wsp:AppliesTo>    
    <wst:RequestedAttachedReference>  
      <wsse:SecurityTokenReference >  
        <wsse:Reference   
           ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
           URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedAttachedReference>  
    <wst:RequestedUnattachedReference>  
      <wsse:SecurityTokenReference>  
        <wsse:Reference   
          ValueType="http://schemas.xmlsoap.org/ws/2005/02/sc/sct"  
          URI="http://fabrikam123.com/SCTi"/>  
      </wsse:SecurityTokenReference>  
    </wst:RequestedUnattachedReference>  
    <wst:RequestedProofToken>  
      <wst:BinarySecret   
        Type="http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey">  
        <!-- base64 encoded value -->  
      </wst:BinarySecret>  
    </wst:RequestedProofToken>  
    <wst:Lifetime>  
      <wssu:Created>2005-10-24T20:19:26.526Z</wssu:Created>  
      <wssu:Expires>2005-10-25T06:24:26.526Z</wssu:Expires>  
    </wst:Lifetime>  
    <wst:KeySize>256</wst:KeySize>  
</wst:RequestSecurityTokenResponse>  
    </t:IssuedTokens>  
    <o:Security xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
      <u:Timestamp u:Id="_0">  
        <u:Created>2005-12-15T23:36:12.015Z</u:Created>  
        <u:Expires>2005-12-15T23:41:12.015Z</u:Expires>  
      </u:Timestamp>  
    </o:Security>  
  </s:Header>  
  <s:Body>  
    <wscoor:CreateCoordinationContextResponse>  
      <wscoor:CoordinationContext>  
        <wscoor:Identifier>  
     http://fabrikam123.com/CCi  
      </wscoor:Identifier>  
        <wscoor:Expires>...</wscoor:Expires>  
        <wscoor:CoordinationType>...</wscoor:CoordinationType>  
        <wscoor:RegistrationService>  
          <a:Address>https://...</a:Address>  
          <a:ReferenceParameters>  
             ...  
          </a:ReferenceParameters>  
        </wscoor:RegistrationService>  
      </wscoor:CoordinationContext>  
    </wscoor:CreateCoordinationContextResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="registration-messages"></a><span data-ttu-id="632fa-218">登録メッセージ</span><span class="sxs-lookup"><span data-stu-id="632fa-218">Registration Messages</span></span>  
 <span data-ttu-id="632fa-219">次のメッセージは、登録メッセージです。</span><span class="sxs-lookup"><span data-stu-id="632fa-219">The following messages are registration messages.</span></span>  
  
#### <a name="register"></a><span data-ttu-id="632fa-220">登録</span><span class="sxs-lookup"><span data-stu-id="632fa-220">Register</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://schemas.xmlsoap.org/ws/2004/10/wscoor/Register</a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e</a:MessageID>  
    <a:ReplyTo>  
      <a:Address>https://...</a:Address>        
    </a:ReplyTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsc:SecurityContextToken>  
      <wssu:Identifier>  
          http://fabrikam123.com/SCTi  
      </wssu:Identifier>  
      </wsc:SecurityContextToken>  
      <!-- supporting signature over the timestamp -->  
      <wsse:Signature xmlns:ds="http://www.w3.org/2000/09/xmldsig#">  
        <ds:SignedInfo>  
          <ds:CanonicalizationMethod Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
          <ds:SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#hmac-sha1"/>  
          <ds:Reference URI="#_0">  
            <ds:Transforms>  
              <ds:Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>  
            </ds:Transforms>  
            <ds:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>  
            <ds:DigestValue>  
              alRzyhjLgoUOYoh8cx4n75eTcUk=  
            </ds:DigestValue>  
          </ds:Reference>  
        </ds:SignedInfo>  
        <ds:SignatureValue>YZYjnVvSOVasAQqQxaaviTSWtqI=</ds:SignatureValue>  
        <ds:KeyInfo>  
          <wsse:SecurityTokenReference  
            xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">  
            <wsse:Reference   
              URI="http://fabrikam123.com/SCTi"/>  
          </wsse:SecurityTokenReference>  
        </ds:KeyInfo>  
      </wsse:Signature>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:Register>  
      <wscoor:ProtocolIdentifier>...</wscoor:ProtocolIdentifier>  
      <wscoor:ParticipantProtocolService>  
        <a:Address>https://... </a:Address>  
      </wscoor:ParticipantProtocolService>  
    </wscoor:Register>  
  </s:Body>  
</s:Envelope>  
```  
  
#### <a name="register-response"></a><span data-ttu-id="632fa-221">RegisterResponse</span><span class="sxs-lookup"><span data-stu-id="632fa-221">Register Response</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>  
      http://schemas.xmlsoap.org/ws/2004/10/wscoor/RegisterResponse  
    </a:Action>  
    <a:MessageID>urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088d</a:MessageID>  
    <a:RelatesTo>  
      urn:uuid:ed418b86-a75e-4aea-9d4e-a5d0cb5c088e        
    </a:RelatesTo>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp>  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
    </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wscoor:RegisterResponse>  
      <wscoor:CoordinatorProtocolService>  
        <a:Address>https://...</a:Address>  
        <a:ReferenceParameters>  
          ...  
        </a:ReferenceParameters>  
      </wscoor:CoordinatorProtocolService>  
    </wscoor:RegisterResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="two-phase-commit-protocol-messages"></a><span data-ttu-id="632fa-222">2 フェーズ コミット プロトコル メッセージ</span><span class="sxs-lookup"><span data-stu-id="632fa-222">Two Phase Commit Protocol Messages</span></span>  
 <span data-ttu-id="632fa-223">次のメッセージは、2 フェーズ コミット (2PC) プロトコルに関連しています。</span><span class="sxs-lookup"><span data-stu-id="632fa-223">The following message relates to the two-phase commit (2PC) protocol.</span></span>  
  
#### <a name="commit"></a><span data-ttu-id="632fa-224">コミット</span><span class="sxs-lookup"><span data-stu-id="632fa-224">Commit</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <a:Action>http://.../ws/2004/10/wsat/Commit</a:Action>  
    <a:To>https://...</a:To>  
    <wsse:Security   
      s:mustUnderstand="1"   
      xmlns:wsse="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd"  
      xmlns:wssu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
      <wssu:Timestamp wssu:Id="_0" >  
        <wssu:Created>2005-12-15T23:36:13.827Z</wssu:Created>  
        <wssu:Expires>2005-12-15T23:41:13.827Z</wssu:Expires>  
      </wssu:Timestamp>  
   </wsse:Security>  
  </s:Header>  
  <s:Body xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
    <wsat:Commit />  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="application-messages"></a><span data-ttu-id="632fa-225">アプリケーション メッセージ</span><span class="sxs-lookup"><span data-stu-id="632fa-225">Application Messages</span></span>  
 <span data-ttu-id="632fa-226">次のメッセージは、アプリケーション メッセージです。</span><span class="sxs-lookup"><span data-stu-id="632fa-226">The following messages are application messages.</span></span>  
  
#### <a name="application-message-request"></a><span data-ttu-id="632fa-227">アプリケーション メッセージ (要求)</span><span class="sxs-lookup"><span data-stu-id="632fa-227">Application message-Request</span></span>  
  
```xml  
<s:Envelope>  
  <s:Header>  
<!-- Addressing headers, all signed-->  
    <wsse:Security s:mustUnderstand="1">  
      <wssu:Timestamp wssu:Id="timestamp">   
        <wssu:Created>2005-10-25T06:29:18.703Z</wssu:Created>  
        <wssu:Expires>2005-10-25T06:34:18.703Z</wssu:Expires>  
      </wssu:Timestamp>  
      <wsse:BinarySecurityToken   
          wssu:Id="IA_Certificate"   
          ValueType="...#X509v3"   
          EncodingType="...#Base64Binary">  
        <!-- IA certificate -->  
      </wsse:BinarySecurityToken>  
      <e:EncryptedKey Id="encrypted_key">  
            <!-- ephemeral key encrypted for PA certificate -->    
        <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
          <e:DataReference URI="#encrypted_body"/>  
          <e:DataReference URI="#encrypted_CCi"/>  
          <e:DataReference URI="#encrypted_issuedtokens"/>  
        </e:ReferenceList>  
      </e:EncryptedKey>  
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">  
        <!-- signature over Addressing headers, Timestamp, and Body -->  
      </Signature>  
    </wsse:Security>  
    <wsse11:EncryptedHeader >  
     <!-- encrypted wscoor:CoordinationContext header containing CCi -->  
    </wsse11:EncryptedHeader>  
    <wsse11:EncryptedHeader   
      <!-- encrypted wst:IssuedTokens header containing SCTi -->  
      <!-- wst:IssuedTokens header is taken verbatim from message #2 above, omitted for brevity -->  
    </wsse11:EncryptedHeader>  
  </s:Header>  
  <s:Body wssu:Id="body">  
    <!-- encrypted content of the Body element of the application message -->      
    <e:EncryptedData Id="encrypted_body"   
           Type="http://www.w3.org/2001/04/xmlenc#Content"   
           xmlns:e="http://www.w3.org/2001/04/xmlenc#">  
...  
    </e:EncryptedData>  
  </s:Body>  
</s:Envelope>  
```
