---
title: "EBindPolicyLevels 列挙型"
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
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 52e4d4522c7401aba198deed7853ccca71752d83
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="347ad-102">EBindPolicyLevels 列挙型</span><span class="sxs-lookup"><span data-stu-id="347ad-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="347ad-103">適用またはアセンブリのポリシーを変更するレベルを指定するフラグを提供します。</span><span class="sxs-lookup"><span data-stu-id="347ad-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="347ad-104">構文</span><span class="sxs-lookup"><span data-stu-id="347ad-104">Syntax</span></span>  
  
```  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a><span data-ttu-id="347ad-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="347ad-105">Members</span></span>  
  
|<span data-ttu-id="347ad-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="347ad-106">Member</span></span>|<span data-ttu-id="347ad-107">説明</span><span class="sxs-lookup"><span data-stu-id="347ad-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="347ad-108">ポリシーが、管理者レベルで適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="347ad-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="347ad-109">ポリシーが、アプリケーション レベルで適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="347ad-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="347ad-110">ポリシーが、ホスト レベルで適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="347ad-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="347ad-111">ポリシー レベルのフラグを指定しません。</span><span class="sxs-lookup"><span data-stu-id="347ad-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="347ad-112">パブリッシャー レベルでポリシーを適用する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="347ad-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="347ad-113">ポリシーをさまざまなレベルで適用できる必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="347ad-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="347ad-114">ポリシーが、.NET Framework アセンブリの実装間で移植性をサポートするように指定します。</span><span class="sxs-lookup"><span data-stu-id="347ad-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="347ad-115">参照してください、 [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)構成ファイルの要素。</span><span class="sxs-lookup"><span data-stu-id="347ad-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="347ad-116">共通言語ランタイム (CLR) のポリシーを統合する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="347ad-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="347ad-117">コメント</span><span class="sxs-lookup"><span data-stu-id="347ad-117">Remarks</span></span>  
 <span data-ttu-id="347ad-118">この列挙体は、のメソッドに渡される、 [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)アプリケーション ポリシーの変更を指定するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="347ad-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="347ad-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="347ad-119">Requirements</span></span>  
 <span data-ttu-id="347ad-120">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="347ad-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="347ad-121">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="347ad-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="347ad-122">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="347ad-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="347ad-123">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="347ad-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="347ad-124">参照</span><span class="sxs-lookup"><span data-stu-id="347ad-124">See Also</span></span>  
 [<span data-ttu-id="347ad-125">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="347ad-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="347ad-126">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="347ad-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
