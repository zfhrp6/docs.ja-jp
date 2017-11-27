---
title: "方法 : 双方向フェデレーション バインディングを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a682b84a90e64e0242a3490986cb526c7f028b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="2b6c3-102">方法 : 双方向フェデレーション バインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="2b6c3-102">How to: Create a Duplex Federated Binding</span></span>
<span data-ttu-id="2b6c3-103"><xref:System.ServiceModel.WSFederationHttpBinding> はデータグラムと要求/応答メッセージの交換コントラクトのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="2b6c3-104">双方向メッセージ交換コントラクトを使用するには、カスタム バインディングを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="2b6c3-105">次の手順は、構成の中でそれを行う方法を説明します。HTTP と TCP トランスポートにはメッセージ モード セキュリティを、TCP トランスポートには混合モード セキュリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="2b6c3-106">このトピックの最後に 3 つのバインディングすべてのサンプル コードがあります。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>  
  
 <span data-ttu-id="2b6c3-107">バインディングはコード内でも作成できます。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-107">You can also create the binding in code.</span></span> <span data-ttu-id="2b6c3-108">詳細については、バインド要素スタックを作成する、次を参照してください。[する方法: SecurityBindingElement を使用してカスタム バインディングを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)です。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="2b6c3-109">HTTP で双方向カスタム フェデレーション バインディングを作成するには</span><span class="sxs-lookup"><span data-stu-id="2b6c3-109">To create a duplex federated custom binding with HTTP</span></span>  
  
1.  <span data-ttu-id="2b6c3-110">[\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)構成ファイルのノードを作成、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>  
  
2.  <span data-ttu-id="2b6c3-111">内部、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)要素を作成、 [\<バインディング >](../../../../docs/framework/misc/binding.md)を持つ要素、`name`属性に設定`FederationDuplexHttpMessageSecurityBinding`です。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>  
  
3.  <span data-ttu-id="2b6c3-112">内部、 [\<バインディング >](../../../../docs/framework/misc/binding.md)要素を作成、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)を持つ要素、`authenticationMode`属性に設定`SecureConversation`です。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-112">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4.  <span data-ttu-id="2b6c3-113">内部、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素を作成、 [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)を持つ要素、`authenticationMode`属性に設定`IssuedTokenForCertificate`または`IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5.  <span data-ttu-id="2b6c3-114">次の[\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素を空、作成[ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)要素。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>  
  
6.  <span data-ttu-id="2b6c3-115">次の[ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)要素を空、作成[ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)要素。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>  
  
7.  <span data-ttu-id="2b6c3-116">次の[ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)要素を空、作成[ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)要素。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="2b6c3-117">TCP メッセージ セキュリティ モードで双方向カスタム フェデレーション バインディングを作成するには</span><span class="sxs-lookup"><span data-stu-id="2b6c3-117">To create a duplex federated custom binding with TCP message security mode</span></span>  
  
1.  <span data-ttu-id="2b6c3-118">[\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)構成ファイルのノードを作成、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>   
  
2.  <span data-ttu-id="2b6c3-119">内部、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)要素を作成、 [\<バインディング >](../../../../docs/framework/misc/binding.md)を持つ要素、`name`属性に設定`FederationDuplexTcpMessageSecurityBinding`です。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>  
  
3.  <span data-ttu-id="2b6c3-120">内部、 [\<バインディング >](../../../../docs/framework/misc/binding.md)要素を作成、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)を持つ要素、`authenticationMode`属性に設定`SecureConversation`です。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-120">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4.  <span data-ttu-id="2b6c3-121">内部、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素を作成、 [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)を持つ要素、`authenticationMode`属性に設定`IssuedTokenForCertificate`または`IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5.  <span data-ttu-id="2b6c3-122">次の[\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素を空、作成[ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)要素。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="2b6c3-123">TCP 混合セキュリティ モードで双方向カスタム フェデレーション バインディングを作成するには</span><span class="sxs-lookup"><span data-stu-id="2b6c3-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>  
  
1.  <span data-ttu-id="2b6c3-124">[\<バインド >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)構成ファイルのノードを作成、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>   
  
2.  <span data-ttu-id="2b6c3-125">内部、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)要素を作成、 [\<バインディング >](../../../../docs/framework/misc/binding.md)を持つ要素、`name`属性に設定`FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`です。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>  
  
3.  <span data-ttu-id="2b6c3-126">内部、 [\<バインディング >](../../../../docs/framework/misc/binding.md)要素を作成、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)を持つ要素、`authenticationMode`属性に設定`SecureConversation`です。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-126">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4.  <span data-ttu-id="2b6c3-127">内部、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素を作成、 [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)を持つ要素、`authenticationMode`属性に設定`IssuedTokenForCertificate`または`IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="2b6c3-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5.  <span data-ttu-id="2b6c3-128">次の[\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)要素を空、作成[ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)要素。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>  
  
6.  <span data-ttu-id="2b6c3-129">次の[ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)要素を空、作成[ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md)要素。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>  
  
## <a name="code-sample"></a><span data-ttu-id="2b6c3-130">コード サンプル</span><span class="sxs-lookup"><span data-stu-id="2b6c3-130">Code Sample</span></span>  
  
#### <a name="sample-with-3-bindings"></a><span data-ttu-id="2b6c3-131">3 つのバインディングの例</span><span class="sxs-lookup"><span data-stu-id="2b6c3-131">Sample with 3 Bindings</span></span>  
  
1.  <span data-ttu-id="2b6c3-132">次のコードを構成ファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="2b6c3-132">Insert the following code into your configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b6c3-133">例</span><span class="sxs-lookup"><span data-stu-id="2b6c3-133">Example</span></span>  
  
```xml  
<bindings>  
   <customBinding>  
      <binding name="FederationDuplexHttpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <compositeDuplex />  
          <oneWay />  
          <httpTransport />  
       </binding>  
<!-- duplex over https is not supported -->  
       <binding name="FederationDuplexTcpMessageSecurityBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />  
          </security>  
          <tcpTransport />  
       </binding>              
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">  
<!-- duplex contract requires secure conversation with require cancellation = true -->  
          <security authenticationMode="SecureConversation">  
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />  
          </security>  
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->  
          <sslStreamSecurity />  
          <tcpTransport />  
       </binding>              
    </customBinding>  
</bindings>  
```
