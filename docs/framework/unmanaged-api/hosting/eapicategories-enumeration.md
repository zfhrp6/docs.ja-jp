---
title: EApiCategories 列挙型
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f25348410387a7b0e03ef897e8534336baeb126a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432210"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="fc3bd-102">EApiCategories 列挙型</span><span class="sxs-lookup"><span data-stu-id="fc3bd-102">EApiCategories Enumeration</span></span>
<span data-ttu-id="fc3bd-103">部分的に信頼されたコードでの実行をブロックするホスト機能のカテゴリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-103">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc3bd-104">構文</span><span class="sxs-lookup"><span data-stu-id="fc3bd-104">Syntax</span></span>  
  
```  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a><span data-ttu-id="fc3bd-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="fc3bd-105">Members</span></span>  
  
|<span data-ttu-id="fc3bd-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="fc3bd-106">Member</span></span>|<span data-ttu-id="fc3bd-107">説明</span><span class="sxs-lookup"><span data-stu-id="fc3bd-107">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="fc3bd-108">指定するすべてのマネージ クラスとその他の対象となるメンバー`EApiCategories`フィールドは、部分的に信頼されたコードでの実行をブロックします。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-108">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="fc3bd-109">マネージ クラスとメンバーを作成、操作、および外部プロセスの破棄を部分的に信頼されるコードで実行をブロックすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-109">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="fc3bd-110">マネージ クラスとメンバーを作成、操作、および外部スレッドの破棄を部分的に信頼されるコードで実行をブロックすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="fc3bd-111">部分的に信頼されたコードでの実行中止にメモリをリーク可能性がある可能性があるマネージ型とメンバーがブロックされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-111">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="fc3bd-112">部分信頼コードでの実行をブロックするマネージ コードのカテゴリがないを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-112">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="fc3bd-113">共通言語ランタイム (CLR) のセキュリティ インフラストラクチャが部分的に信頼されたコードによって使用されるからブロックされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-113">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="fc3bd-114">部分的に信頼されたコードでの実行、マネージ クラスとメンバーが影響を与える機能ホストされたプロセスがブロックされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-114">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="fc3bd-115">部分的に信頼されたコードでの実行、マネージ クラスとメンバーが影響を与える機能ホスト プロセス内のスレッドがブロックされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-115">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="fc3bd-116">部分的に信頼されたコードでの実行、マネージ クラスと共有の状態を公開するメンバーがブロックされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-116">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="fc3bd-117">共通言語ランタイム クラスとロックを保持するためにユーザー コードを許可するメンバーを部分的に信頼されるコードで実行をブロックすることを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-117">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="fc3bd-118">部分的に信頼されたコードでの実行、マネージ クラスとを許可または対話操作を必要とするメンバーがブロックされることを指定します。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-118">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc3bd-119">コメント</span><span class="sxs-lookup"><span data-stu-id="fc3bd-119">Remarks</span></span>  
 <span data-ttu-id="fc3bd-120">[Iclrhostprotectionmanager::setprotectedcategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md)メソッドが型のパラメーターを受け取る`EApiCategories`です。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-120">The [ICLRHostProtectionManager::SetProtectedCategories](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="fc3bd-121">`EApiCategories`列挙と`SetProtectedCategories`メソッドは直接関連するマネージ<xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType>クラスです。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-121">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="fc3bd-122">マネージ クラスが使用されて、<xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType>列挙型、値が対応に直接、`EApiCategories`によって記述されたカテゴリに対応する機能を公開するマネージ型とメンバーをマークする、値`EApiCategories`です。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-122">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc3bd-123">要件</span><span class="sxs-lookup"><span data-stu-id="fc3bd-123">Requirements</span></span>  
 <span data-ttu-id="fc3bd-124">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fc3bd-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc3bd-125">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc3bd-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc3bd-126">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc3bd-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc3bd-127">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc3bd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc3bd-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc3bd-128">See Also</span></span>  
 [<span data-ttu-id="fc3bd-129">ICLRHostProtectionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="fc3bd-129">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="fc3bd-130">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="fc3bd-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
