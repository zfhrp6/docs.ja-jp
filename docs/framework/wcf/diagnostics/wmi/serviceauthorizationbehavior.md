---
title: ServiceAuthorizationBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62f3e32e886f49ac8dde6af5c37a4e57373c9576
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="946ef-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="946ef-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="946ef-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="946ef-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="946ef-104">構文</span><span class="sxs-lookup"><span data-stu-id="946ef-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="946ef-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="946ef-105">Methods</span></span>  
 <span data-ttu-id="946ef-106">ServiceAuthorizationBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="946ef-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="946ef-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="946ef-107">Properties</span></span>  
 <span data-ttu-id="946ef-108">ServiceAuthorizationBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="946ef-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="946ef-109">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="946ef-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="946ef-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="946ef-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="946ef-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="946ef-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="946ef-112">受信メッセージによって提供される資格情報を使用してサービスが偽装を試みるかどうかを制御する値。</span><span class="sxs-lookup"><span data-stu-id="946ef-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="946ef-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="946ef-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="946ef-114">データ型: string</span><span class="sxs-lookup"><span data-stu-id="946ef-114">Data type: string</span></span>  
  
 <span data-ttu-id="946ef-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="946ef-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="946ef-116">サーバーでの操作を実行するために使用されるプリンシパル。</span><span class="sxs-lookup"><span data-stu-id="946ef-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="946ef-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="946ef-117">RoleProvider</span></span>  
 <span data-ttu-id="946ef-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="946ef-118">Data type: string</span></span>  
  
 <span data-ttu-id="946ef-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="946ef-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="946ef-120">ASP.NET ロール プロバイダーの名前。</span><span class="sxs-lookup"><span data-stu-id="946ef-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="946ef-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="946ef-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="946ef-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="946ef-122">Data type: string</span></span>  
  
 <span data-ttu-id="946ef-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="946ef-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="946ef-124">カスタム承認で使用される承認マネージャー。</span><span class="sxs-lookup"><span data-stu-id="946ef-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="946ef-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="946ef-125">Requirements</span></span>  
  
|<span data-ttu-id="946ef-126">MOF</span><span class="sxs-lookup"><span data-stu-id="946ef-126">MOF</span></span>|<span data-ttu-id="946ef-127">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="946ef-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="946ef-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="946ef-128">Namespace</span></span>|<span data-ttu-id="946ef-129">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="946ef-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="946ef-130">参照</span><span class="sxs-lookup"><span data-stu-id="946ef-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
