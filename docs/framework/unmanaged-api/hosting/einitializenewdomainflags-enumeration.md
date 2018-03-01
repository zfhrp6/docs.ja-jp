---
title: "EInitializeNewDomainFlags 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fa5c9aa050e0f5e634c43080d9caa5011a126529
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="83dba-102">EInitializeNewDomainFlags 列挙体</span><span class="sxs-lookup"><span data-stu-id="83dba-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="83dba-103">ホストがランタイムにアプリケーション ドメインの初期化に関する情報を提供できるようにします。</span><span class="sxs-lookup"><span data-stu-id="83dba-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83dba-104">構文</span><span class="sxs-lookup"><span data-stu-id="83dba-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="83dba-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="83dba-105">Members</span></span>  
  
|<span data-ttu-id="83dba-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="83dba-106">Member</span></span>|<span data-ttu-id="83dba-107">説明</span><span class="sxs-lookup"><span data-stu-id="83dba-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="83dba-108">フラグがありません。</span><span class="sxs-lookup"><span data-stu-id="83dba-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="83dba-109">共通言語ランタイム (CLR) の通知、こと、ホスト変更できなくなりますで、アプリケーション ドメインのセキュリティの状態を<xref:System.AppDomainManager.InitializeNewDomain%2A>メソッドです。</span><span class="sxs-lookup"><span data-stu-id="83dba-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83dba-110">コメント</span><span class="sxs-lookup"><span data-stu-id="83dba-110">Remarks</span></span>  
 <span data-ttu-id="83dba-111">[Iclrdomainmanager::setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)メソッドが型のパラメーターを受け取る`EInitializeNewDomainFlags`です。</span><span class="sxs-lookup"><span data-stu-id="83dba-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83dba-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="83dba-112">Requirements</span></span>  
 <span data-ttu-id="83dba-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="83dba-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83dba-114">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="83dba-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="83dba-115">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83dba-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83dba-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83dba-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83dba-117">参照</span><span class="sxs-lookup"><span data-stu-id="83dba-117">See Also</span></span>  
 [<span data-ttu-id="83dba-118">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="83dba-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="83dba-119">SetAppDomainManagerType メソッド</span><span class="sxs-lookup"><span data-stu-id="83dba-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
