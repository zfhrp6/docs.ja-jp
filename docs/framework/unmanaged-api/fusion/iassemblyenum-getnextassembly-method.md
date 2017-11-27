---
title: "IAssemblyEnum::GetNextAssembly メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyEnum.GetNextAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cef1624d0432d571edfddfa772f31366e23074f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="7dbe3-102">IAssemblyEnum::GetNextAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="7dbe3-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="7dbe3-103">ポインターを取得[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)これに含まれている[IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="7dbe3-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dbe3-104">構文</span><span class="sxs-lookup"><span data-stu-id="7dbe3-104">Syntax</span></span>  
  
```  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7dbe3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7dbe3-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="7dbe3-106">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="7dbe3-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="7dbe3-107">`pvReserved`null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7dbe3-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="7dbe3-108">[out]返された`IAssemblyName`ポインター。</span><span class="sxs-lookup"><span data-stu-id="7dbe3-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="7dbe3-109">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="7dbe3-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="7dbe3-110">`dwFlags`0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7dbe3-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7dbe3-111">要件</span><span class="sxs-lookup"><span data-stu-id="7dbe3-111">Requirements</span></span>  
 <span data-ttu-id="7dbe3-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="7dbe3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7dbe3-113">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7dbe3-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7dbe3-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7dbe3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dbe3-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="7dbe3-115">See Also</span></span>  
 [<span data-ttu-id="7dbe3-116">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7dbe3-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="7dbe3-117">IAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7dbe3-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
