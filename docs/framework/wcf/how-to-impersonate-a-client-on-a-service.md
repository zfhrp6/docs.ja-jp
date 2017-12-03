---
title: "方法 : サービスでクライアントに偽装する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de7bfb7d926f9aa75ccfcfe8a550a0dbae4e12ef
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-impersonate-a-client-on-a-service"></a><span data-ttu-id="8dd15-102">方法 : サービスでクライアントに偽装する</span><span class="sxs-lookup"><span data-stu-id="8dd15-102">How to: Impersonate a Client on a Service</span></span>
<span data-ttu-id="8dd15-103">[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] サービスでクライアントを偽装すると、サービスはクライアントの代理としてアクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="8dd15-103">Impersonating a client on a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service enables the service to perform actions on behalf of the client.</span></span> <span data-ttu-id="8dd15-104">コンピューター上のディレクトリやファイルへのアクセス、または SQL Server データベースへのアクセスなど、アクセス制御リスト (ACL) のチェックを受けるアクションでは、ACL のチェックがクライアントのユーザー アカウントに対して行われます。</span><span class="sxs-lookup"><span data-stu-id="8dd15-104">For actions subject to access control list (ACL) checks, such as access to directories and files on a machine or access to a SQL Server database, the ACL check is against the client user account.</span></span> <span data-ttu-id="8dd15-105">ここでは、Windows ドメインのクライアントで、クライアント偽装レベルを設定できるようにするために必要な基本的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="8dd15-105">This topic shows the basic steps required to enable a client in a Windows domain to set a client impersonation level.</span></span> <span data-ttu-id="8dd15-106">このパターンの実施例については、「 [Impersonating the Client](../../../docs/framework/wcf/samples/impersonating-the-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dd15-106">For a working example of this, see [Impersonating the Client](../../../docs/framework/wcf/samples/impersonating-the-client.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="8dd15-107">クライアントの権限借用を参照してください[委任と偽装](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)です。</span><span class="sxs-lookup"><span data-stu-id="8dd15-107"> client impersonation, see [Delegation and Impersonation](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8dd15-108">クライアントとサービスが同じコンピューター上で実行されており、クライアントがシステム アカウント ( `Local System` や `Network Service`など) で実行されているときに、ステートレスなセキュリティ コンテキスト トークンを使用してセキュリティで保護されたセッションを確立した場合、クライアントを偽装することはできません。</span><span class="sxs-lookup"><span data-stu-id="8dd15-108">When the client and service are running on the same computer and the client is running under a system account (that is, `Local System` or `Network Service`), the client cannot be impersonated when a secure session is established with stateful Security Context tokens.</span></span> <span data-ttu-id="8dd15-109">通常、WinForms アプリケーションやコンソール アプリケーションは、現在ログインしているアカウントで実行されるため、既定でそのアカウントを偽装できます。</span><span class="sxs-lookup"><span data-stu-id="8dd15-109">A WinForms or console application typically is run under the currently logged in account, so that account can be impersonated by default.</span></span> <span data-ttu-id="8dd15-110">ただし、クライアントが [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ページであり、そのページが [!INCLUDE[iis601](../../../includes/iis601-md.md)] または IIS 7.0 でホストされている場合、既定では、クライアントは `Network Service` アカウントで実行されます。</span><span class="sxs-lookup"><span data-stu-id="8dd15-110">However, when the client is an [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page and that page is hosted in [!INCLUDE[iis601](../../../includes/iis601-md.md)] or IIS 7.0, then the client does run under the `Network Service` account by default.</span></span> <span data-ttu-id="8dd15-111">セキュリティで保護されたセッションをサポートするシステム提供のすべてのバインディングは、ステートフルなセキュリティ コンテキスト トークンを既定で使用します。</span><span class="sxs-lookup"><span data-stu-id="8dd15-111">All of the system-provided bindings that support secure sessions use a stateless Security Context token by default.</span></span> <span data-ttu-id="8dd15-112">ただし、クライアントが [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] ページであり、ステートフルなセキュリティ コンテキスト トークンを使用する、セキュリティで保護されたセッションを使用している場合は、クライアントを偽装できません。</span><span class="sxs-lookup"><span data-stu-id="8dd15-112">However, if the client is an [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] page and secure sessions with stateful Security Context tokens are used, the client cannot be impersonated.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="8dd15-113">セキュリティで保護されたセッションでステートフルなセキュリティ コンテキスト トークンを使用して、参照してください[する方法: セキュリティで保護されたセッションのセキュリティ コンテキスト トークンを作成](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)です。</span><span class="sxs-lookup"><span data-stu-id="8dd15-113"> using stateful Security Context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a><span data-ttu-id="8dd15-114">サービスにキャッシュされた Windows トークンでクライアントの偽装を有効にするには</span><span class="sxs-lookup"><span data-stu-id="8dd15-114">To enable impersonation of a client from a cached Windows token on a service</span></span>  
  
1.  <span data-ttu-id="8dd15-115">サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="8dd15-115">Create the service.</span></span> <span data-ttu-id="8dd15-116">この基本的な手順のチュートリアルについては、「 [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8dd15-116">For a tutorial of this basic procedure, see [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md).</span></span>  
  
2.  <span data-ttu-id="8dd15-117">Windows 認証を使用してセッションを作成するバインディング ( <xref:System.ServiceModel.NetTcpBinding> や <xref:System.ServiceModel.WSHttpBinding>など) を使用します。</span><span class="sxs-lookup"><span data-stu-id="8dd15-117">Use a binding that uses Windows authentication and creates a session, such as <xref:System.ServiceModel.NetTcpBinding> or <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3.  <span data-ttu-id="8dd15-118">サービスのインターフェイスの実装を作成するときには、クライアントの偽装を必要とするメソッドに <xref:System.ServiceModel.OperationBehaviorAttribute> クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="8dd15-118">When creating the implementation of the service's interface, apply the <xref:System.ServiceModel.OperationBehaviorAttribute> class to the method that requires client impersonation.</span></span> <span data-ttu-id="8dd15-119"><xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> プロパティを <xref:System.ServiceModel.ImpersonationOption.Required>に設定します。</span><span class="sxs-lookup"><span data-stu-id="8dd15-119">Set the <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> property to <xref:System.ServiceModel.ImpersonationOption.Required>.</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a><span data-ttu-id="8dd15-120">クライアントに許可される偽装レベルを設定するには</span><span class="sxs-lookup"><span data-stu-id="8dd15-120">To set the allowed impersonation level on the client</span></span>  
  
1.  <span data-ttu-id="8dd15-121">[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、サービス クライアント コードを作成します。</span><span class="sxs-lookup"><span data-stu-id="8dd15-121">Create service client code by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="8dd15-122">[WCF クライアントを使用してサービスにアクセスする](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)です。</span><span class="sxs-lookup"><span data-stu-id="8dd15-122"> [Accessing Services Using a WCF Client](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).</span></span>  
  
2.  <span data-ttu-id="8dd15-123">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントの作成後、 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> クラスの <xref:System.ServiceModel.Security.WindowsClientCredential> プロパティを <xref:System.Security.Principal.TokenImpersonationLevel> 列挙値の 1 つに設定します。</span><span class="sxs-lookup"><span data-stu-id="8dd15-123">After creating the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client, set the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property of the <xref:System.ServiceModel.Security.WindowsClientCredential> class to one of the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration values.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8dd15-124"><xref:System.Security.Principal.TokenImpersonationLevel.Delegation>を使用するには、ネゴシエート Kerberos 認証 ( *"マルチレッグ"* Kerberos または *"マルチステップ"* Kerberos と呼ぶこともあります) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8dd15-124">To use <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, negotiated Kerberos authentication (sometimes called *multi-leg* or *multi-step* Kerberos) must be used.</span></span> <span data-ttu-id="8dd15-125">これを実装する方法については、次を参照してください。[セキュリティのベスト プラクティス](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)です。</span><span class="sxs-lookup"><span data-stu-id="8dd15-125">For a description of how to implement this, see [Best Practices for Security](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="8dd15-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="8dd15-126">See Also</span></span>  
 <xref:System.ServiceModel.OperationBehaviorAttribute>  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 [<span data-ttu-id="8dd15-127">クライアントの偽装</span><span class="sxs-lookup"><span data-stu-id="8dd15-127">Impersonating the Client</span></span>](../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 [<span data-ttu-id="8dd15-128">委任と偽装</span><span class="sxs-lookup"><span data-stu-id="8dd15-128">Delegation and Impersonation</span></span>](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
