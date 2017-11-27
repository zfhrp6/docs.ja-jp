---
title: "GetCLRIdentityManager 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCLRIdentityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: GetCLRIdentityManager
helpviewer_keywords: GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ddc0395b6fd659ecd6a26a3132fccc65bbb961fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="d17bb-102">GetCLRIdentityManager 関数</span><span class="sxs-lookup"><span data-stu-id="d17bb-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="d17bb-103">共通言語ランタイム (CLR) に必要な id を管理できるようにするインターフェイスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="d17bb-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="d17bb-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="d17bb-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d17bb-105">構文</span><span class="sxs-lookup"><span data-stu-id="d17bb-105">Syntax</span></span>  
  
```  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d17bb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d17bb-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="d17bb-107">[in]A `REFIID` (インターフェイス識別子) を指定するどのインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="d17bb-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="d17bb-108">この値は、IID_ICLRAssemblyIdentityManager または IID_ICLRHostBindingPolicyManager のいずれかにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d17bb-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="d17bb-109">[out]いずれかのアドレスへのポインター、 [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)または[ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d17bb-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d17bb-110">コメント</span><span class="sxs-lookup"><span data-stu-id="d17bb-110">Remarks</span></span>  
 <span data-ttu-id="d17bb-111">呼び出す、 [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)へのポインターを取得する関数、`GetCLRIdentityManager`関数。</span><span class="sxs-lookup"><span data-stu-id="d17bb-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d17bb-112">要件</span><span class="sxs-lookup"><span data-stu-id="d17bb-112">Requirements</span></span>  
 <span data-ttu-id="d17bb-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d17bb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d17bb-114">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d17bb-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d17bb-115">**ライブラリ:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="d17bb-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="d17bb-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d17bb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d17bb-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d17bb-117">See Also</span></span>  
 [<span data-ttu-id="d17bb-118">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="d17bb-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
