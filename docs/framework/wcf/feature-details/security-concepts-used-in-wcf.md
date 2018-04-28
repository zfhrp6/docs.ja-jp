---
title: WCF で使用されるセキュリティの概要
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
caps.latest.revision: 15
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 72712e0934646a39c1e03a38716179384051003a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="security-concepts-used-in-wcf"></a><span data-ttu-id="0d953-102">WCF で使用されるセキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="0d953-102">Security Concepts Used in WCF</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="0d953-103"> のセキュリティは、各種のセキュリティ インフラストラクチャで既に使用され展開されている概念の上に構築されています。</span><span class="sxs-lookup"><span data-stu-id="0d953-103"> security is built upon concepts already in use and deployed in various security infrastructures.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="0d953-104"> は、これらのインフラストラクチャの一部 (SSL (Secure Sockets Layer) over HTTP (HTTPS) など) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0d953-104"> supports some of those infrastructures, such as Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="0d953-105">ただし、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、新しい相互運用可能なセキュリティ標準 (WS-Security など) を SOAP エンコード メッセージに実装することで、既存のセキュリティ インフラストラクチャをサポートする以上の機能を実現しています。</span><span class="sxs-lookup"><span data-stu-id="0d953-105">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] goes beyond supporting existing security infrastructures by implementing newer interoperable security standards (such as WS-Security) over SOAP-encoded messages.</span></span> <span data-ttu-id="0d953-106">既存の機構と新規の相互運用可能な標準のどちらを使用する場合でも、背後にあるセキュリティ概念に変わりはありません。</span><span class="sxs-lookup"><span data-stu-id="0d953-106">Whether you are using existing mechanisms or new interoperable standards, the security concepts behind both are the same.</span></span> <span data-ttu-id="0d953-107">既存のインフラストラクチャおよび新しい標準を支える概念を理解することが、アプリケーションにとって最善のセキュリティ モデルを実装するための要になります。</span><span class="sxs-lookup"><span data-stu-id="0d953-107">Understanding the concepts behind existing infrastructures and the newer standards is central to implementing the best security model for an application.</span></span>  
  
## <a name="introduction-to-security-for-wcf-web-services"></a><span data-ttu-id="0d953-108">WCF Web サービスのセキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="0d953-108">Introduction to Security for WCF Web Services</span></span>  
 <span data-ttu-id="0d953-109">Microsoft Patterns and Practices グループは、ここからダウンロードされる WCF セキュリティ ガイダンスで、詳細なホワイト ペーパーを書き込みました。 [WCF セキュリティ ガイド](http://go.microsoft.com/fwlink/?LinkId=210210)です。</span><span class="sxs-lookup"><span data-stu-id="0d953-109">The Microsoft Patterns and Practices group wrote an in-depth whitepaper on WCF security guidance which is available for download here: [WCF Security Guide](http://go.microsoft.com/fwlink/?LinkId=210210).</span></span> <span data-ttu-id="0d953-110">このホワイト ペーパーでは、Web サービス、WCF セキュリティの主な概念、イントラネット アプリケーション シナリオ、およびインターネット アプリケーション シナリオに関連するセキュリティの基本概念について説明しています。</span><span class="sxs-lookup"><span data-stu-id="0d953-110">This whitepaper describes the fundamental security concepts as they relate to web services, key WCF security concepts, intranet application scenarios, and internet application scenarios.</span></span>  
  
## <a name="industry-wide-security-specifications"></a><span data-ttu-id="0d953-111">業界標準のセキュリティ仕様</span><span class="sxs-lookup"><span data-stu-id="0d953-111">Industry-Wide Security Specifications</span></span>  
  
### <a name="public-key-infrastructure"></a><span data-ttu-id="0d953-112">公開キー基盤</span><span class="sxs-lookup"><span data-stu-id="0d953-112">Public Key Infrastructure</span></span>  
 <span data-ttu-id="0d953-113">公開キー基盤 (PKI: Public Key Infrastructure) は、デジタル証明書、証明機関、およびその他の登録機関で構成されるシステムです。PKI では、公開キー暗号化を使用して、電子取引に関与する各当事者の検証と認証を行います。</span><span class="sxs-lookup"><span data-stu-id="0d953-113">Public Key Infrastructure (PKI) is a system of digital certificates, certification authorities, and other registration authorities that verify and authenticate each party involved in an electronic transaction through the use of public key cryptography.</span></span> <span data-ttu-id="0d953-114">詳細については、次を参照してください。 [Windows Server 2008 R2 の証明書サービス](http://go.microsoft.com/fwlink/?LinkId=210211)です。</span><span class="sxs-lookup"><span data-stu-id="0d953-114">For more information, see [Windows Server 2008 R2 Certificate Services](http://go.microsoft.com/fwlink/?LinkId=210211).</span></span>  
  
### <a name="kerberos-protocol"></a><span data-ttu-id="0d953-115">Kerberos プロトコル</span><span class="sxs-lookup"><span data-stu-id="0d953-115">Kerberos Protocol</span></span>  
 <span data-ttu-id="0d953-116">*Kerberos プロトコル*仕様は、Windows ドメインでユーザーを認証するためのセキュリティ機構を作成します。</span><span class="sxs-lookup"><span data-stu-id="0d953-116">The *Kerberos protocol* is a specification for creating a security mechanism that authenticates users on a Windows domain.</span></span> <span data-ttu-id="0d953-117">ユーザーはドメイン内の他のエンティティと、セキュリティで保護されたコンテキストを確立できます。</span><span class="sxs-lookup"><span data-stu-id="0d953-117">It allows a user to establish a secure context with other entities within a domain.</span></span> <span data-ttu-id="0d953-118">Windows 2000 以降のプラットフォームでは、Kerberos プロトコルが既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="0d953-118">Windows 2000 and later platforms use the Kerberos protocol by default.</span></span> <span data-ttu-id="0d953-119">システムの機構を理解することは、イントラネット クライアントと対話するサービスを作成する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="0d953-119">Understanding the mechanisms of the system is useful when creating a service that will interact with intranet clients.</span></span> <span data-ttu-id="0d953-120">さらに、以降、 *Web Services Security Kerberos Binding*広くが発行すると、ことができます、Kerberos プロトコルを使用するインターネット クライアントと通信 (つまり、Kerberos プロトコルは、相互運用可能な)。</span><span class="sxs-lookup"><span data-stu-id="0d953-120">In addition, since the *Web Services Security Kerberos Binding* is widely published, you can use the Kerberos protocol to communicate with Internet clients (that is, the Kerberos protocol is interoperable).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="0d953-121"> Kerberos プロトコルが Windows に実装されている方法を参照してください。 [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212)です。</span><span class="sxs-lookup"><span data-stu-id="0d953-121"> how the Kerberos protocol is implemented in Windows, see  [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkId=210212).</span></span>  
  
### <a name="x509-certificates"></a><span data-ttu-id="0d953-122">X.509 証明書</span><span class="sxs-lookup"><span data-stu-id="0d953-122">X.509 Certificates</span></span>  
 <span data-ttu-id="0d953-123">X.509 証明書は、セキュリティ アプリケーションで使用される主要な資格情報の形式です。</span><span class="sxs-lookup"><span data-stu-id="0d953-123">X.509 certificates are a primary credential form used in security applications.</span></span> <span data-ttu-id="0d953-124">詳細については、X.509 証明書を参照してください[X.509 公開キー証明書](http://go.microsoft.com/fwlink/?LinkId=210213)です。</span><span class="sxs-lookup"><span data-stu-id="0d953-124">For more information on X.509 certificates see [X.509 Public Key Certificates](http://go.microsoft.com/fwlink/?LinkId=210213).</span></span> <span data-ttu-id="0d953-125">X.509 証明書は証明書ストア内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="0d953-125">X.509 certificates are stored within a certificate store.</span></span> <span data-ttu-id="0d953-126">Windows を実行しているコンピューターには、それぞれ目的が異なる数種類の証明書ストアがあります。</span><span class="sxs-lookup"><span data-stu-id="0d953-126">A computer running Windows has several kinds of certificate stores, each with a different purpose.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="0d953-127"> 別のストアを参照してください[証明書ストア](http://go.microsoft.com/fwlink/?LinkID=87787)です。</span><span class="sxs-lookup"><span data-stu-id="0d953-127"> the different stores, see [Certificate Stores](http://go.microsoft.com/fwlink/?LinkID=87787).</span></span>  
  
## <a name="web-services-security-specifications"></a><span data-ttu-id="0d953-128">Web サービスのセキュリティ仕様</span><span class="sxs-lookup"><span data-stu-id="0d953-128">Web Services Security Specifications</span></span>  
 <span data-ttu-id="0d953-129">システム定義のバインディングでは、一般に使用されるさまざまな Web サービスのセキュリティ仕様をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0d953-129">The system-defined bindings support many commonly used web services security specifications.</span></span> <span data-ttu-id="0d953-130">システム指定のバインディングと、web サービス仕様の完全な一覧については、サポートを参照してください:[システム指定の相互運用性バインディングでサポートされる Web サービス プロトコル](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)</span><span class="sxs-lookup"><span data-stu-id="0d953-130">For a complete list of system-provided bindings and the web services specifications they support see: [Web Services Protocols Supported by System-Provided Interoperability Bindings](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)</span></span>  
  
## <a name="access-control-mechanisms"></a><span data-ttu-id="0d953-131">アクセス制御機構</span><span class="sxs-lookup"><span data-stu-id="0d953-131">Access Control Mechanisms</span></span>  
 <span data-ttu-id="0d953-132">WCF には、サービスや操作へのアクセスを制御するさまざまな方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="0d953-132">WCF provides a number of ways to control access to a service or operation.</span></span> <span data-ttu-id="0d953-133">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="0d953-133">Among them are</span></span>  
  
1.  <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2.  <span data-ttu-id="0d953-134">ASP.NET メンバーシップ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="0d953-134">ASP.NET Membership Provider</span></span>  
  
3.  <span data-ttu-id="0d953-135">ASP.NET ロール プロバイダー</span><span class="sxs-lookup"><span data-stu-id="0d953-135">ASP.NET Role Provider</span></span>  
  
4.  <span data-ttu-id="0d953-136">承認マネージャー</span><span class="sxs-lookup"><span data-stu-id="0d953-136">Authorization Manager</span></span>  
  
5.  <span data-ttu-id="0d953-137">ID モデル</span><span class="sxs-lookup"><span data-stu-id="0d953-137">Identity Model</span></span>  
  
 <span data-ttu-id="0d953-138">詳細については、これらのトピックを参照してください、[アクセス制御機構](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)</span><span class="sxs-lookup"><span data-stu-id="0d953-138">For more information on these topics see, [Access Control Mechanisms](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d953-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d953-139">See Also</span></span>  
 [<span data-ttu-id="0d953-140">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="0d953-140">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="0d953-141">Windows Server App Fabric のセキュリティ モデル</span><span class="sxs-lookup"><span data-stu-id="0d953-141">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
