---
title: EContextType 列挙型
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a261d9164e8714531eab1fe9fc8148304e6d5bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432883"
---
# <a name="econtexttype-enumeration"></a><span data-ttu-id="7f8cb-102">EContextType 列挙型</span><span class="sxs-lookup"><span data-stu-id="7f8cb-102">EContextType Enumeration</span></span>
<span data-ttu-id="7f8cb-103">現在実行中のスレッドのセキュリティ コンテキストをについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7f8cb-103">Describes the security context of the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f8cb-104">構文</span><span class="sxs-lookup"><span data-stu-id="7f8cb-104">Syntax</span></span>  
  
```  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a><span data-ttu-id="7f8cb-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="7f8cb-105">Members</span></span>  
  
|<span data-ttu-id="7f8cb-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="7f8cb-106">Member</span></span>|<span data-ttu-id="7f8cb-107">説明</span><span class="sxs-lookup"><span data-stu-id="7f8cb-107">Description</span></span>|  
|------------|-----------------|  
|`eCurrentContext`|<span data-ttu-id="7f8cb-108">共通言語ランタイム (CLR) の呼び出し時に現在のスレッドのコンテキストを示す、 [ihostsecuritymanager::getsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)メソッド、またはへの呼び出しで CLR によって要求されたコンテキスト、 [Ihostsecuritymanager::setsecuritycontext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="7f8cb-108">Indicates the context on the current thread at the time the common language runtime (CLR) calls the [IHostSecurityManager::GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md) method, or the context requested by the CLR in a call to the [IHostSecurityManager::SetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-setsecuritycontext-method.md) method.</span></span>|  
|`eRestrictedContext`|<span data-ttu-id="7f8cb-109">対象では、ホストは、ガベージ コレクターでは、またはクラスまたはモジュール コンス トラクターなど、低い特権コンテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="7f8cb-109">Indicates a context over which the host has lower privileges, such as the garbage collector, or class or module constructors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f8cb-110">コメント</span><span class="sxs-lookup"><span data-stu-id="7f8cb-110">Remarks</span></span>  
 <span data-ttu-id="7f8cb-111">いずれかの CLR が用意されて、`EContextType`値への呼び出しのパラメーター値として、`IHostSecurityManager::GetSecurityContext`と`IHostSecurityManager::SetSecurityContext`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="7f8cb-111">The CLR supplies one of the `EContextType` values as a parameter value in calls to the `IHostSecurityManager::GetSecurityContext` and `IHostSecurityManager::SetSecurityContext` methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f8cb-112">要件</span><span class="sxs-lookup"><span data-stu-id="7f8cb-112">Requirements</span></span>  
 <span data-ttu-id="7f8cb-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7f8cb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f8cb-114">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7f8cb-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f8cb-115">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f8cb-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f8cb-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f8cb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f8cb-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7f8cb-117">See Also</span></span>  
 [<span data-ttu-id="7f8cb-118">IHostSecurityContext インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f8cb-118">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="7f8cb-119">IHostSecurityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7f8cb-119">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 [<span data-ttu-id="7f8cb-120">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="7f8cb-120">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
