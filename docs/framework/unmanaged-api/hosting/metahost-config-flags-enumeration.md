---
title: "METAHOST_CONFIG_FLAGS 列挙体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: METAHOST_CONFIG_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: METAHOST_CONFIG_FLAGS
helpviewer_keywords: METAHOST_CONFIG_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 6f1e389f-ed99-4d6a-a0ba-72d7d869a01d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5743356cdb2a99c4c5eb0c958bc5ca0815146d4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="metahostconfigflags-enumeration"></a><span data-ttu-id="250bc-102">METAHOST_CONFIG_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="250bc-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="250bc-103">返される、可能なフラグについて説明します、`pdwConfigFlags`のパラメーター、 [iclrmetahostpolicy::getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)メソッド、および設定することを示します、`useLegacyV2RuntimeActivationPolicy`属性、 [ \<スタートアップ > 要素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)構成ファイルのです。</span><span class="sxs-lookup"><span data-stu-id="250bc-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="250bc-104">構文</span><span class="sxs-lookup"><span data-stu-id="250bc-104">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="250bc-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="250bc-105">Members</span></span>  
  
|<span data-ttu-id="250bc-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="250bc-106">Member</span></span>|<span data-ttu-id="250bc-107">説明</span><span class="sxs-lookup"><span data-stu-id="250bc-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="250bc-108">`useLegacyV2RuntimeActivationPolicy`属性に存在しません、 [\<スタートアップ > 要素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="250bc-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="250bc-109">`useLegacyV2RuntimeActivationPolicy`属性が存在し、設定を`true`です。</span><span class="sxs-lookup"><span data-stu-id="250bc-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="250bc-110">`useLegacyV2RuntimeActivationPolicy`属性が存在し、設定を`false`です。</span><span class="sxs-lookup"><span data-stu-id="250bc-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="250bc-111">戻り値をこのマスクを適用`pdwConfigFlags`に関連する値を取得する`useLegacyV2RuntimeActivationPolicy`です。</span><span class="sxs-lookup"><span data-stu-id="250bc-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="250bc-112">コメント</span><span class="sxs-lookup"><span data-stu-id="250bc-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="250bc-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="250bc-113">Requirements</span></span>  
 <span data-ttu-id="250bc-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="250bc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="250bc-115">**ヘッダー:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="250bc-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="250bc-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="250bc-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="250bc-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="250bc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="250bc-118">参照</span><span class="sxs-lookup"><span data-stu-id="250bc-118">See Also</span></span>  
 [<span data-ttu-id="250bc-119">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="250bc-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="250bc-120">GetRequestedRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="250bc-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)  
 [<span data-ttu-id="250bc-121">\<スタートアップ > 要素</span><span class="sxs-lookup"><span data-stu-id="250bc-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
