---
title: EBindPolicyLevels 列挙型
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1da1d368725ab0a2334080c1caa7d4e25f5f3bab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431124"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="b863d-102">EBindPolicyLevels 列挙型</span><span class="sxs-lookup"><span data-stu-id="b863d-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="b863d-103">適用またはアセンブリのポリシーを変更するレベルを指定するフラグを提供します。</span><span class="sxs-lookup"><span data-stu-id="b863d-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b863d-104">構文</span><span class="sxs-lookup"><span data-stu-id="b863d-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b863d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b863d-105">Members</span></span>  
  
|<span data-ttu-id="b863d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b863d-106">Member</span></span>|<span data-ttu-id="b863d-107">説明</span><span class="sxs-lookup"><span data-stu-id="b863d-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="b863d-108">ポリシーが、管理者レベルで適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="b863d-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="b863d-109">ポリシーが、アプリケーション レベルで適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="b863d-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="b863d-110">ポリシーが、ホスト レベルで適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="b863d-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="b863d-111">ポリシー レベルのフラグを指定しません。</span><span class="sxs-lookup"><span data-stu-id="b863d-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="b863d-112">パブリッシャー レベルでポリシーを適用する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="b863d-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="b863d-113">ポリシーをさまざまなレベルで適用できる必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="b863d-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="b863d-114">ポリシーが、.NET Framework アセンブリの実装間で移植性をサポートするように指定します。</span><span class="sxs-lookup"><span data-stu-id="b863d-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="b863d-115">参照してください、 [ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)構成ファイルの要素。</span><span class="sxs-lookup"><span data-stu-id="b863d-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="b863d-116">共通言語ランタイム (CLR) のポリシーを統合する必要がありますを指定します。</span><span class="sxs-lookup"><span data-stu-id="b863d-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b863d-117">コメント</span><span class="sxs-lookup"><span data-stu-id="b863d-117">Remarks</span></span>  
 <span data-ttu-id="b863d-118">この列挙体は、のメソッドに渡される、 [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)アプリケーション ポリシーの変更を指定するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="b863d-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b863d-119">要件</span><span class="sxs-lookup"><span data-stu-id="b863d-119">Requirements</span></span>  
 <span data-ttu-id="b863d-120">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b863d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b863d-121">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b863d-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b863d-122">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b863d-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b863d-123">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b863d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b863d-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="b863d-124">See Also</span></span>  
 [<span data-ttu-id="b863d-125">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b863d-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="b863d-126">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="b863d-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
