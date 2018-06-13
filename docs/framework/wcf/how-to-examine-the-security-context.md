---
title: '方法 : セキュリティ コンテキストを調べる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 8ff6969095a49dcae8b1d59b5b0ab28a8af24274
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33499477"
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="d29ee-102">方法 : セキュリティ コンテキストを調べる</span><span class="sxs-lookup"><span data-stu-id="d29ee-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="d29ee-103">Windows Communication Foundation (WCF) サービスをプログラムするときにサービスのセキュリティ コンテキストでは、クライアントの資格情報とサービスで認証するために使用するクレームの詳細を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="d29ee-103">When programming Windows Communication Foundation (WCF) services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="d29ee-104">これは、<xref:System.ServiceModel.ServiceSecurityContext> クラスのプロパティを使用することで可能になります。</span><span class="sxs-lookup"><span data-stu-id="d29ee-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="d29ee-105">たとえば、<xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> プロパティまたは <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> プロパティを使用すると、現在のクライアントの ID を取得できます。</span><span class="sxs-lookup"><span data-stu-id="d29ee-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="d29ee-106">クライアントが匿名であるかどうかを確認するには、<xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="d29ee-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="d29ee-107">また、<xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> プロパティにあるクレームのコレクションを反復処理することによって、クライアントのためにどのようなクレームが作成されているのかを確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="d29ee-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="d29ee-108">現在のセキュリティ コンテキストを取得するには</span><span class="sxs-lookup"><span data-stu-id="d29ee-108">To get the current security context</span></span>  
  
-   <span data-ttu-id="d29ee-109">現在のセキュリティ コンテキストを取得するためには、静的プロパティ <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d29ee-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="d29ee-110">参照から現在のコンテキストの任意のプロパティを調べます。</span><span class="sxs-lookup"><span data-stu-id="d29ee-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="d29ee-111">呼び出し元の ID を確認するには</span><span class="sxs-lookup"><span data-stu-id="d29ee-111">To determine the identity of the caller</span></span>  
  
1.  <span data-ttu-id="d29ee-112"><xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> プロパティおよび <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> プロパティの値を表示します。</span><span class="sxs-lookup"><span data-stu-id="d29ee-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="d29ee-113">呼び出し元のクレームを解析するには</span><span class="sxs-lookup"><span data-stu-id="d29ee-113">To parse the claims of a caller</span></span>  
  
1.  <span data-ttu-id="d29ee-114">現在の <xref:System.IdentityModel.Policy.AuthorizationContext> クラスを返します。</span><span class="sxs-lookup"><span data-stu-id="d29ee-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="d29ee-115"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> プロパティを使用して、現在のサービス セキュリティ コンテキストを返し、次に `AuthorizationContext` プロパティを使用して <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> を返します。</span><span class="sxs-lookup"><span data-stu-id="d29ee-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2.  <span data-ttu-id="d29ee-116"><xref:System.IdentityModel.Claims.ClaimSet> クラスの <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> プロパティによって返された <xref:System.IdentityModel.Policy.AuthorizationContext> オブジェクトのコレクションを解析します。</span><span class="sxs-lookup"><span data-stu-id="d29ee-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d29ee-117">例</span><span class="sxs-lookup"><span data-stu-id="d29ee-117">Example</span></span>  
 <span data-ttu-id="d29ee-118">次の例では、現在のセキュリティ コンテキストの <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> プロパティおよび <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> プロパティの値、<xref:System.IdentityModel.Claims.Claim.ClaimType%2A> プロパティの値、クレームのリソース値、および現在のセキュリティ コンテキストのすべてのクレームの <xref:System.IdentityModel.Claims.Claim.Right%2A> プロパティを表示します。</span><span class="sxs-lookup"><span data-stu-id="d29ee-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d29ee-119">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="d29ee-119">Compiling the Code</span></span>  
 <span data-ttu-id="d29ee-120">コードでは、次の名前空間を使用します。</span><span class="sxs-lookup"><span data-stu-id="d29ee-120">The code uses the following namespaces:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="d29ee-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d29ee-121">See Also</span></span>  
 [<span data-ttu-id="d29ee-122">サービスのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="d29ee-122">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="d29ee-123">サービス ID と認証</span><span class="sxs-lookup"><span data-stu-id="d29ee-123">Service Identity and Authentication</span></span>](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
