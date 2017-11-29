---
title: "ICLRAssemblyIdentityManager::IsStronglyNamed メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.IsStronglyNamed
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::IsStronglyNamed
helpviewer_keywords:
- IsStronglyNamed method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::IsStronglyNamed method [.NET Framework hosting]
ms.assetid: 954bd386-2076-4d00-9d46-38c728aa9cab
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d0cb0bcaf5d19ec088511e64baffff9031911b32
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="25a81-102">ICLRAssemblyIdentityManager::IsStronglyNamed メソッド</span><span class="sxs-lookup"><span data-stu-id="25a81-102">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>
<span data-ttu-id="25a81-103">指定したアセンブリは厳密な名前かどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="25a81-103">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25a81-104">構文</span><span class="sxs-lookup"><span data-stu-id="25a81-104">Syntax</span></span>  
  
```  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25a81-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="25a81-105">Parameters</span></span>  
 `pwzAssemblyIdentity`  
 <span data-ttu-id="25a81-106">[in]評価するアセンブリの非透過の標準アセンブリの id データ。</span><span class="sxs-lookup"><span data-stu-id="25a81-106">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="25a81-107">[out]`true`によってアセンブリが参照されている場合は、`pwzAssemblyIdentity`パラメーターが強く、それ以外の名前付き`false`します。</span><span class="sxs-lookup"><span data-stu-id="25a81-107">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25a81-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="25a81-108">Return Value</span></span>  
  
|<span data-ttu-id="25a81-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="25a81-109">HRESULT</span></span>|<span data-ttu-id="25a81-110">説明</span><span class="sxs-lookup"><span data-stu-id="25a81-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="25a81-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="25a81-111">S_OK</span></span>|<span data-ttu-id="25a81-112">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="25a81-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="25a81-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="25a81-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="25a81-114">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="25a81-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="25a81-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="25a81-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="25a81-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="25a81-116">The call timed out.</span></span>|  
|<span data-ttu-id="25a81-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="25a81-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="25a81-118">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="25a81-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="25a81-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="25a81-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="25a81-120">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="25a81-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="25a81-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="25a81-121">E_FAIL</span></span>|<span data-ttu-id="25a81-122">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="25a81-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="25a81-123">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="25a81-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="25a81-124">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="25a81-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25a81-125">要件</span><span class="sxs-lookup"><span data-stu-id="25a81-125">Requirements</span></span>  
 <span data-ttu-id="25a81-126">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="25a81-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25a81-127">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="25a81-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="25a81-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="25a81-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25a81-129">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25a81-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25a81-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="25a81-130">See Also</span></span>  
 [<span data-ttu-id="25a81-131">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25a81-131">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
