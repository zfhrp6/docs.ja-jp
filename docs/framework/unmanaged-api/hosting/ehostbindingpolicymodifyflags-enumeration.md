---
title: "EHostBindingPolicyModifyFlags 列挙型"
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
- EHostBindingPolicyModifyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EHostBindingPolicyModifyFlags
helpviewer_keywords:
- EHostBindingPolicyModifyFlags enumeration [.NET Framework hosting]
ms.assetid: 0339af16-ee1d-48ec-837d-a79d9a9c89f8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: eb985cf2f34719b3aed9397155bd9d538b57dc3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ehostbindingpolicymodifyflags-enumeration"></a><span data-ttu-id="29ae2-102">EHostBindingPolicyModifyFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="29ae2-102">EHostBindingPolicyModifyFlags Enumeration</span></span>
<span data-ttu-id="29ae2-103">により、ホストはターゲット アセンブリにはソース アセンブリから、ポリシーの変更を適用するときに、共通言語ランタイム (CLR) を実行する必要がありますのリダイレクトの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="29ae2-103">Allows the host to specify the type of redirection the common language runtime (CLR) should perform when applying policy modifications from a source assembly to a target assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ae2-104">構文</span><span class="sxs-lookup"><span data-stu-id="29ae2-104">Syntax</span></span>  
  
```  
typedef enum _hostBindingPolicyModifyFlags {  
    HOST_BINDING_POLICY_MODIFY_DEFAULT  = 0,  
    HOST_BINDING_POLICY_MODIFY_CHAIN    = 1,  
    HOST_BINDING_POLICY_MODIFY_REMOVE   = 2,  
    HOST_BINDING_POLICY_MODIFY_MAX      = 3  
} EHostBindingPolicyModifyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="29ae2-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="29ae2-105">Members</span></span>  
  
|<span data-ttu-id="29ae2-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="29ae2-106">Member</span></span>|<span data-ttu-id="29ae2-107">説明</span><span class="sxs-lookup"><span data-stu-id="29ae2-107">Description</span></span>|  
|------------|-----------------|  
|`HOST_BINDING_POLICY_MODIFY_CHAIN`|<span data-ttu-id="29ae2-108">CLR が上にターゲット アセンブリのソース アセンブリのポリシー値をチェーンするを指定します。</span><span class="sxs-lookup"><span data-stu-id="29ae2-108">Specifies that the CLR will chain policy values of the source assembly onto those of the target assembly.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_DEFAULT`|<span data-ttu-id="29ae2-109">CLR が既定のアクションを実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="29ae2-109">Specifies that the CLR will perform the default action.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_MAX`|<span data-ttu-id="29ae2-110">CLR が最大値にターゲット アセンブリのポリシー値を設定するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="29ae2-110">Specifies that the CLR will set the policy values of the target assembly to the maximum values.</span></span>|  
|`HOST_BINDING_POLICY_MODIFY_REMOVE`|<span data-ttu-id="29ae2-111">CLR が基になるアセンブリのターゲット アセンブリのポリシー値を置き換えることを指定します。</span><span class="sxs-lookup"><span data-stu-id="29ae2-111">Specifies that the CLR will replace policy values of the target assembly with those of the source assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29ae2-112">コメント</span><span class="sxs-lookup"><span data-stu-id="29ae2-112">Remarks</span></span>  
 <span data-ttu-id="29ae2-113">[Iclrhostbindingpolicymanager::modifyapplicationpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)メソッドが型のパラメーターを受け取る`EHostBindingPolicyModifyFlags`です。</span><span class="sxs-lookup"><span data-stu-id="29ae2-113">The [ICLRHostBindingPolicyManager::ModifyApplicationPolicy](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md) method takes a parameter of type `EHostBindingPolicyModifyFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ae2-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="29ae2-114">Requirements</span></span>  
 <span data-ttu-id="29ae2-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="29ae2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29ae2-116">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="29ae2-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29ae2-117">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="29ae2-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29ae2-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29ae2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ae2-119">参照</span><span class="sxs-lookup"><span data-stu-id="29ae2-119">See Also</span></span>  
 [<span data-ttu-id="29ae2-120">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="29ae2-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="29ae2-121">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="29ae2-121">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
