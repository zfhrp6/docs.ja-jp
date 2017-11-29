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
ms.openlocfilehash: 35b909f7b73657c8862c2d0645e5c5766df8beb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="metahostconfigflags-enumeration"></a><span data-ttu-id="01e9d-102">METAHOST_CONFIG_FLAGS 列挙体</span><span class="sxs-lookup"><span data-stu-id="01e9d-102">METAHOST_CONFIG_FLAGS Enumeration</span></span>
<span data-ttu-id="01e9d-103">返される、可能なフラグについて説明します、`pdwConfigFlags`のパラメーター、 [iclrmetahostpolicy::getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)メソッド、および設定することを示します、`useLegacyV2RuntimeActivationPolicy`属性、 [ \<スタートアップ > 要素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)構成ファイルのです。</span><span class="sxs-lookup"><span data-stu-id="01e9d-103">Describes the possible flags returned in the `pdwConfigFlags` parameter of the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method, indicating the presence and setting of the `useLegacyV2RuntimeActivationPolicy` attribute in the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) of the configuration file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01e9d-104">構文</span><span class="sxs-lookup"><span data-stu-id="01e9d-104">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET  = 0x00,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE   = 0x01,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE  = 0x02,  
    METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK   = 0x03  
} METAHOST_CONFIG_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="01e9d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="01e9d-105">Members</span></span>  
  
|<span data-ttu-id="01e9d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="01e9d-106">Member</span></span>|<span data-ttu-id="01e9d-107">説明</span><span class="sxs-lookup"><span data-stu-id="01e9d-107">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_UNSET`|<span data-ttu-id="01e9d-108">`useLegacyV2RuntimeActivationPolicy`属性に存在しません、 [\<スタートアップ > 要素](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)です。</span><span class="sxs-lookup"><span data-stu-id="01e9d-108">The `useLegacyV2RuntimeActivationPolicy` attribute was not present in the [\<startup> Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md).</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_TRUE`|<span data-ttu-id="01e9d-109">`useLegacyV2RuntimeActivationPolicy`属性が存在し、設定を`true`です。</span><span class="sxs-lookup"><span data-stu-id="01e9d-109">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `true`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_FALSE`|<span data-ttu-id="01e9d-110">`useLegacyV2RuntimeActivationPolicy`属性が存在し、設定を`false`です。</span><span class="sxs-lookup"><span data-stu-id="01e9d-110">The `useLegacyV2RuntimeActivationPolicy` attribute was present and set to `false`.</span></span>|  
|`METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK`|<span data-ttu-id="01e9d-111">戻り値をこのマスクを適用`pdwConfigFlags`に関連する値を取得する`useLegacyV2RuntimeActivationPolicy`です。</span><span class="sxs-lookup"><span data-stu-id="01e9d-111">Apply this mask to the value returned in `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01e9d-112">コメント</span><span class="sxs-lookup"><span data-stu-id="01e9d-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01e9d-113">要件</span><span class="sxs-lookup"><span data-stu-id="01e9d-113">Requirements</span></span>  
 <span data-ttu-id="01e9d-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="01e9d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01e9d-115">**ヘッダー:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="01e9d-115">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="01e9d-116">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="01e9d-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01e9d-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01e9d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01e9d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="01e9d-118">See Also</span></span>  
 [<span data-ttu-id="01e9d-119">ホスティングの列挙体</span><span class="sxs-lookup"><span data-stu-id="01e9d-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [<span data-ttu-id="01e9d-120">GetRequestedRuntime メソッド</span><span class="sxs-lookup"><span data-stu-id="01e9d-120">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)  
 [<span data-ttu-id="01e9d-121">\<スタートアップ > 要素</span><span class="sxs-lookup"><span data-stu-id="01e9d-121">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
