---
title: "ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyIdentityManager.GetCLRAssemblyReferenceList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList
helpviewer_keywords:
- GetClrAssemblyReferenceList method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList method [.NET Framework hosting]
ms.assetid: cb5ffae5-287b-4a87-9ca8-7ce3ae0601b7
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eefe5ff68c7bd428c18729dcbd792b4c3cb64c2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrassemblyidentitymanagergetclrassemblyreferencelist-method"></a><span data-ttu-id="ff8e8-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList メソッド</span><span class="sxs-lookup"><span data-stu-id="ff8e8-102">ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList Method</span></span>
<span data-ttu-id="ff8e8-103">インターフェイス ポインターを取得、 [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)部分アセンブリ id の指定された一覧からのインスタンス。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-103">Gets an interface pointer to an [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff8e8-104">構文</span><span class="sxs-lookup"><span data-stu-id="ff8e8-104">Syntax</span></span>  
  
```  
HRESULT  GetCLRAssemblyReferenceList (  
    [in] LPCWSTR *ppwzAssemblyReferences,  
    [in] DWORD    dwNumOfReferences,  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ff8e8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ff8e8-105">Parameters</span></span>  
 `ppwzAssemblyReferences`  
 <span data-ttu-id="ff8e8-106">[in]フォームでの null で終わる文字列の配列"name、プロパティの値... ="部分のアセンブリ id の一覧を指定します。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-106">[in] An array of null-terminated strings in the form "name, property=value..." that specify a list of partial assembly identities.</span></span>  
  
 `dwNumOfReferences`  
 <span data-ttu-id="ff8e8-107">[in]内の項目数`ppwzAssemblyReferences`です。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-107">[in] The number of items in `ppwzAssemblyReferences`.</span></span>  
  
 `ppReferenceList`  
 <span data-ttu-id="ff8e8-108">[out]インターフェイス ポインター、`ICLRAssemblyReferenceList`で指定されたアセンブリの一覧については、アセンブリの id データを格納しているオブジェクト`ppwzAssemblyReferences`です。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-108">[out] An interface pointer to an `ICLRAssemblyReferenceList` object that contains the assembly identity data for the list of assemblies specified in `ppwzAssemblyReferences`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ff8e8-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="ff8e8-109">Return Value</span></span>  
  
|<span data-ttu-id="ff8e8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ff8e8-110">HRESULT</span></span>|<span data-ttu-id="ff8e8-111">説明</span><span class="sxs-lookup"><span data-stu-id="ff8e8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ff8e8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ff8e8-112">S_OK</span></span>|<span data-ttu-id="ff8e8-113">メソッドが正常に返されます。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="ff8e8-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ff8e8-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ff8e8-115">共通言語ランタイム (CLR) が、プロセスに読み込まれていませんまたは CLR は、状態をマネージ コードを実行またはできないの呼び出しは正常に処理します。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ff8e8-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ff8e8-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ff8e8-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-117">The call timed out.</span></span>|  
|<span data-ttu-id="ff8e8-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ff8e8-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ff8e8-119">呼び出し元は、ロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ff8e8-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ff8e8-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ff8e8-121">イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ff8e8-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ff8e8-122">E_FAIL</span></span>|<span data-ttu-id="ff8e8-123">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ff8e8-124">メソッドには、E_FAIL が返された場合、CLR は、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ff8e8-125">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ff8e8-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="ff8e8-126">Requirements</span></span>  
 <span data-ttu-id="ff8e8-127">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff8e8-128">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ff8e8-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff8e8-129">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ff8e8-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff8e8-130">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff8e8-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff8e8-131">参照</span><span class="sxs-lookup"><span data-stu-id="ff8e8-131">See Also</span></span>  
 [<span data-ttu-id="ff8e8-132">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff8e8-132">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="ff8e8-133">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ff8e8-133">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
