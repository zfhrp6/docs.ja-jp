---
title: "WMI クラスの参照"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7a74f1d7e70b8664df5022d6f9f42cf04b88f930
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="wmi-class-reference"></a><span data-ttu-id="2544c-102">WMI クラスの参照</span><span class="sxs-lookup"><span data-stu-id="2544c-102">WMI Class Reference</span></span>
<span data-ttu-id="2544c-103">このセクションでは、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] WMI プロバイダーが公開しているすべての WMI クラスを示します。</span><span class="sxs-lookup"><span data-stu-id="2544c-103">This section lists all the WMI classes exposed by the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] WMI provider.</span></span>  
  
## <a name="accessing-wmi-instances"></a><span data-ttu-id="2544c-104">WMI インスタンスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="2544c-104">Accessing WMI Instances</span></span>  
 <span data-ttu-id="2544c-105">WMI オブジェクト リファレンスに記載されているクラスはすべて、インスタンスを直接生成することはできません。ただし Service、AppDomain、Contract、ServiceAppDomain、ServiceToEndpointAssociation、Endpoint の各クラスを除きます。</span><span class="sxs-lookup"><span data-stu-id="2544c-105">All the classes listed in the WMI Object Reference cannot be directly instantiated, except for Service, AppDomain, Contract, ServiceAppDomain, ServiceToEndpointAssociation and Endpoint.</span></span> <span data-ttu-id="2544c-106">他のインスタンスには、これらのトップ レベル クラスのプロパティからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2544c-106">To access other instances, you can access the properties of the previously mentioned top level classes.</span></span> <span data-ttu-id="2544c-107">たとえば TransportBindingElement のインスタンスには、Endpoint のインスタンスから、Binding、BindingElements の順にたどってアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2544c-107">For example, you can access the TransportBindingElement instance from the Endpoint instance -> Binding -> BindingElements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2544c-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2544c-108">In This Section</span></span>  
 [<span data-ttu-id="2544c-109">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="2544c-109">ActivityTransfer</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/activitytransfer.md)  
  
 [<span data-ttu-id="2544c-110">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="2544c-110">AppDomainInfo</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md)  
  
 [<span data-ttu-id="2544c-111">AspNetCompatibilityRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="2544c-111">AspNetCompatibilityRequirementsAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/aspnetcompatibilityrequirementsattribute.md)  
  
 [<span data-ttu-id="2544c-112">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-112">AsymmetricSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/asymmetricsecuritybindingelement.md)  
  
 <span data-ttu-id="2544c-113">「Behavior クラス」</span><span class="sxs-lookup"><span data-stu-id="2544c-113">"Behavior class"</span></span>  
  
 [<span data-ttu-id="2544c-114">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-114">BinaryMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/binarymessageencodingbindingelement.md)  
  
 [<span data-ttu-id="2544c-115">バインド</span><span class="sxs-lookup"><span data-stu-id="2544c-115">Binding</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/binding.md)  
  
 [<span data-ttu-id="2544c-116">BindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-116">BindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/bindingelement.md)  
  
 [<span data-ttu-id="2544c-117">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="2544c-117">CallbackBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/callbackbehavior.md)  
  
 [<span data-ttu-id="2544c-118">チャネル クラス</span><span class="sxs-lookup"><span data-stu-id="2544c-118">Channel class</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/channel-class.md)  
  
 [<span data-ttu-id="2544c-119">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2544c-119">ChannelPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/channelpoolsettings.md)  
  
 [<span data-ttu-id="2544c-120">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="2544c-120">ClientCredentials</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/clientcredentials.md)  
  
 [<span data-ttu-id="2544c-121">ClientViaBehavior</span><span class="sxs-lookup"><span data-stu-id="2544c-121">ClientViaBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md)  
  
 [<span data-ttu-id="2544c-122">CompositeDuplexBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-122">CompositeDuplexBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/compositeduplexbindingelement.md)  
  
 [<span data-ttu-id="2544c-123">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-123">ConnectionOrientedTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/connectionorientedtransportbindingelement.md)  
  
 [<span data-ttu-id="2544c-124">コントラクト</span><span class="sxs-lookup"><span data-stu-id="2544c-124">Contract</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/contract.md)  
  
 [<span data-ttu-id="2544c-125">CustomBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-125">CustomBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/custombindingelement.md)  
  
 [<span data-ttu-id="2544c-126">Deliveryrequirementsattribute は</span><span class="sxs-lookup"><span data-stu-id="2544c-126">DeliveryRequirementsAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/deliveryrequirementsattribute.md)  
  
 [<span data-ttu-id="2544c-127">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="2544c-127">Endpoint</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md)  
  
 [<span data-ttu-id="2544c-128">HttpsTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-128">HttpsTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/httpstransportbindingelement.md)  
  
 [<span data-ttu-id="2544c-129">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-129">HttpTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/httptransportbindingelement.md)  
  
 [<span data-ttu-id="2544c-130">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2544c-130">LocalServiceSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/localservicesecuritysettings.md)  
  
 [<span data-ttu-id="2544c-131">MatchAllEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="2544c-131">MatchAllEndpointBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/matchallendpointbehavior.md)  
  
 [<span data-ttu-id="2544c-132">MessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-132">MessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/messageencodingbindingelement.md)  
  
 [<span data-ttu-id="2544c-133">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="2544c-133">MsmqBindingElementBase</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqbindingelementbase.md)  
  
 [<span data-ttu-id="2544c-134">MsmqIntegrationBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-134">MsmqIntegrationBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqintegrationbindingelement.md)  
  
 [<span data-ttu-id="2544c-135">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-135">MsmqTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqtransportbindingelement.md)  
  
 [<span data-ttu-id="2544c-136">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-136">MtomMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/mtommessageencodingbindingelement.md)  
  
 [<span data-ttu-id="2544c-137">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="2544c-137">MustUnderstandBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/mustunderstandbehavior.md)  
  
 [<span data-ttu-id="2544c-138">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2544c-138">NamedPipeConnectionPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/namedpipeconnectionpoolsettings.md)  
  
 [<span data-ttu-id="2544c-139">NamedPipeTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-139">NamedPipeTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/namedpipetransportbindingelement.md)  
  
 [<span data-ttu-id="2544c-140">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-140">OneWayBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/onewaybindingelement.md)  
  
 <span data-ttu-id="2544c-141">「操作クラス」</span><span class="sxs-lookup"><span data-stu-id="2544c-141">"Operation class"</span></span>  
  
 [<span data-ttu-id="2544c-142">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="2544c-142">OperationBehaviorAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/operationbehaviorattribute.md)  
  
 [<span data-ttu-id="2544c-143">PeerCustomResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-143">PeerCustomResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peercustomresolverbindingelement.md)  
  
 [<span data-ttu-id="2544c-144">PeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-144">PeerResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peerresolverbindingelement.md)  
  
 [<span data-ttu-id="2544c-145">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2544c-145">PeerSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peersecuritysettings.md)  
  
 [<span data-ttu-id="2544c-146">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-146">PeerTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peertransportbindingelement.md)  
  
 [<span data-ttu-id="2544c-147">PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2544c-147">PeerTransportSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peertransportsecuritysettings.md)  
  
 [<span data-ttu-id="2544c-148">PnrpPeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-148">PnrpPeerResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/pnrppeerresolverbindingelement.md)  
  
 [<span data-ttu-id="2544c-149">PrivacyNoticeBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-149">PrivacyNoticeBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/privacynoticebindingelement.md)  
  
 [<span data-ttu-id="2544c-150">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-150">ReliableSessionBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/reliablesessionbindingelement.md)  
  
 [<span data-ttu-id="2544c-151">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-151">SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md)  
  
 [<span data-ttu-id="2544c-152">サービス</span><span class="sxs-lookup"><span data-stu-id="2544c-152">Service</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/service.md)  
  
 [<span data-ttu-id="2544c-153">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="2544c-153">ServiceAppDomain</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/serviceappdomain.md)  
  
 [<span data-ttu-id="2544c-154">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="2544c-154">ServiceAuthorizationBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/serviceauthorizationbehavior.md)  
  
 [<span data-ttu-id="2544c-155">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="2544c-155">ServiceBehaviorAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicebehaviorattribute.md)  
  
 [<span data-ttu-id="2544c-156">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="2544c-156">ServiceCredentials</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicecredentials.md)  
  
 [<span data-ttu-id="2544c-157">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="2544c-157">ServiceDebugBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicedebugbehavior.md)  
  
 [<span data-ttu-id="2544c-158">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="2544c-158">ServiceMetadataBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicemetadatabehavior.md)  
  
 [<span data-ttu-id="2544c-159">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="2544c-159">ServiceSecurityAuditBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicesecurityauditbehavior.md)  
  
 [<span data-ttu-id="2544c-160">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="2544c-160">ServiceThrottlingBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicethrottlingbehavior.md)  
  
 [<span data-ttu-id="2544c-161">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="2544c-161">ServiceTimeoutsBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicetimeoutsbehavior.md)  
  
 [<span data-ttu-id="2544c-162">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="2544c-162">ServiceToEndpointAssociation</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicetoendpointassociation.md)  
  
 [<span data-ttu-id="2544c-163">SslStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-163">SslStreamSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/sslstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="2544c-164">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-164">SymmetricSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)  
  
 [<span data-ttu-id="2544c-165">SynchronousReceiveBehavior</span><span class="sxs-lookup"><span data-stu-id="2544c-165">SynchronousReceiveBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/synchronousreceivebehavior.md)  
  
 [<span data-ttu-id="2544c-166">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2544c-166">TcpConnectionPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tcpconnectionpoolsettings.md)  
  
 [<span data-ttu-id="2544c-167">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-167">TcpTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tcptransportbindingelement.md)  
  
 [<span data-ttu-id="2544c-168">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-168">TextMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/textmessageencodingbindingelement.md)  
  
 [<span data-ttu-id="2544c-169">TraceListener</span><span class="sxs-lookup"><span data-stu-id="2544c-169">TraceListener</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tracelistener.md)  
  
 [<span data-ttu-id="2544c-170">TraceListenerArgument</span><span class="sxs-lookup"><span data-stu-id="2544c-170">TraceListenerArgument</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tracelistenerargument.md)  
  
 [<span data-ttu-id="2544c-171">TransactedBatchingBehavior</span><span class="sxs-lookup"><span data-stu-id="2544c-171">TransactedBatchingBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactedbatchingbehavior.md)  
  
 [<span data-ttu-id="2544c-172">TransactionFlowAttribute</span><span class="sxs-lookup"><span data-stu-id="2544c-172">TransactionFlowAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactionflowattribute.md)  
  
 [<span data-ttu-id="2544c-173">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-173">TransactionFlowBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactionflowbindingelement.md)  
  
 [<span data-ttu-id="2544c-174">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-174">TransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transportbindingelement.md)  
  
 [<span data-ttu-id="2544c-175">TransportSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-175">TransportSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transportsecuritybindingelement.md)  
  
 [<span data-ttu-id="2544c-176">UseManagedPresentationBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-176">UseManagedPresentationBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/usemanagedpresentationbindingelement.md)  
  
 [<span data-ttu-id="2544c-177">WindowsStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2544c-177">WindowsStreamSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/windowsstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="2544c-178">WSAT_TraceEvent</span><span class="sxs-lookup"><span data-stu-id="2544c-178">WSAT_TraceEvent</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-traceevent.md)  
  
 [<span data-ttu-id="2544c-179">WSAT_TraceProvider</span><span class="sxs-lookup"><span data-stu-id="2544c-179">WSAT_TraceProvider</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-traceprovider.md)  
  
 [<span data-ttu-id="2544c-180">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="2544c-180">WSAT_TraceRecord</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-tracerecord.md)  
  
 [<span data-ttu-id="2544c-181">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="2544c-181">XmlDictionaryReaderQuotas</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/xmldictionaryreaderquotas.md)  
  
 [<span data-ttu-id="2544c-182">XmlSerializerOperationBehavior</span><span class="sxs-lookup"><span data-stu-id="2544c-182">XmlSerializerOperationBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/xmlserializeroperationbehavior.md)
