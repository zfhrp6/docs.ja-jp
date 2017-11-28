---
title: "WCF での承認"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a0c2afafa1d645ec0e95b7b41ff8389873969c89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="85fb1-102">WCF での承認</span><span class="sxs-lookup"><span data-stu-id="85fb1-102">Authorization in WCF</span></span>
<span data-ttu-id="85fb1-103">承認は、サービスやファイルなどのリソースへのアクセスと権限を制御するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="85fb1-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="85fb1-104">このセクションの各トピックでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] でこの基本タスクを実行するさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="85fb1-104">The topics in this section show you how to perform this basic task in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85fb1-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="85fb1-105">In This Section</span></span>  
 [<span data-ttu-id="85fb1-106">アクセス制御機構</span><span class="sxs-lookup"><span data-stu-id="85fb1-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="85fb1-107">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の承認機構の概要と推奨される使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="85fb1-107">Provides a brief outline of the authorization mechanisms in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], and suggested uses.</span></span>  
  
 [<span data-ttu-id="85fb1-108">方法: PrincipalPermissionAttribute クラスでアクセスを制限する</span><span class="sxs-lookup"><span data-stu-id="85fb1-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="85fb1-109"><xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用してサービスへのアクセスを制限するプロセスを示します。</span><span class="sxs-lookup"><span data-stu-id="85fb1-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="85fb1-110">方法: サービスで ASP.NET ロール プロバイダーを使用</span><span class="sxs-lookup"><span data-stu-id="85fb1-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="85fb1-111">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] のロール プロバイダー機能を使用できるようにサービスを構成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="85fb1-111">Walks through the configuration of a service to enable it to use the role provider feature of [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span></span>  
  
 [<span data-ttu-id="85fb1-112">方法: サービスで ASP.NET の承認マネージャー ロール プロバイダーを使用</span><span class="sxs-lookup"><span data-stu-id="85fb1-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="85fb1-113"> は、承認マネージャーを使って Web サイトの承認を管理できます。</span><span class="sxs-lookup"><span data-stu-id="85fb1-113"> can use the Authorization Manager to manage authorization for a Web site.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="85fb1-114"> は、これとほぼ同じ方法でクライアントの承認に [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] と承認マネージャーの組み合わせを利用できます。</span><span class="sxs-lookup"><span data-stu-id="85fb1-114"> can similarly leverage the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="85fb1-115">クレームと Id モデルによる承認の管理</span><span class="sxs-lookup"><span data-stu-id="85fb1-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="85fb1-116">ID モデル インフラストラクチャをクレーム ベースの承認に使用する際の基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="85fb1-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="85fb1-117">委任と偽装</span><span class="sxs-lookup"><span data-stu-id="85fb1-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="85fb1-118">委任と偽装の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="85fb1-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="85fb1-119">参照</span><span class="sxs-lookup"><span data-stu-id="85fb1-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="85fb1-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="85fb1-120">Related Sections</span></span>  
 [<span data-ttu-id="85fb1-121">認証</span><span class="sxs-lookup"><span data-stu-id="85fb1-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="85fb1-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="85fb1-122">See Also</span></span>  
 [<span data-ttu-id="85fb1-123">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="85fb1-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="85fb1-124">Windows Server App Fabric のセキュリティ モデル</span><span class="sxs-lookup"><span data-stu-id="85fb1-124">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
