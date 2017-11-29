---
title: "ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ff0e51327e0e66c2a282ebf46e6036f81d3d568b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="49578-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList メソッド</span><span class="sxs-lookup"><span data-stu-id="49578-102">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>
<span data-ttu-id="49578-103">指定された名前が一覧内のアセンブリの名前に一致するかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="49578-103">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49578-104">構文</span><span class="sxs-lookup"><span data-stu-id="49578-104">Syntax</span></span>  
  
```  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49578-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="49578-105">Parameters</span></span>  
 `pwzAssemblyName`  
 <span data-ttu-id="49578-106">[in]検索対象のアセンブリの名前。</span><span class="sxs-lookup"><span data-stu-id="49578-106">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49578-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="49578-107">Return Value</span></span>  
  
|<span data-ttu-id="49578-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="49578-108">HRESULT</span></span>|<span data-ttu-id="49578-109">説明</span><span class="sxs-lookup"><span data-stu-id="49578-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="49578-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="49578-110">S_OK</span></span>|<span data-ttu-id="49578-111">文字列は、一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="49578-111">The string appears in the list.</span></span>|  
|<span data-ttu-id="49578-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="49578-112">S_FALSE</span></span>|<span data-ttu-id="49578-113">文字列は、一覧には表示されません。</span><span class="sxs-lookup"><span data-stu-id="49578-113">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="49578-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="49578-114">E_FAIL</span></span>|<span data-ttu-id="49578-115">不明な致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="49578-115">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="49578-116">メソッドには、E_FAIL が返された、後に、共通言語ランタイムは、プロセス内で使用可能ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="49578-116">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="49578-117">メソッドのホストに以降の呼び出しでは、HOST_E_CLRNOTAVAILABLE を返します。</span><span class="sxs-lookup"><span data-stu-id="49578-117">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="49578-118">要件</span><span class="sxs-lookup"><span data-stu-id="49578-118">Requirements</span></span>  
 <span data-ttu-id="49578-119">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="49578-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49578-120">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="49578-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="49578-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="49578-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="49578-122">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49578-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49578-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="49578-123">See Also</span></span>  
 [<span data-ttu-id="49578-124">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49578-124">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="49578-125">ICLRAssemblyReferenceList インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49578-125">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [<span data-ttu-id="49578-126">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49578-126">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 [<span data-ttu-id="49578-127">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49578-127">IHostAssemblyStore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)
