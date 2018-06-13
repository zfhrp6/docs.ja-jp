---
title: IAssemblyEnum::GetNextAssembly メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 977336f9ff5e65905018f7f93ade74e27625f514
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430770"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="57675-102">IAssemblyEnum::GetNextAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="57675-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="57675-103">ポインターを取得[IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)これに含まれている[IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="57675-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57675-104">構文</span><span class="sxs-lookup"><span data-stu-id="57675-104">Syntax</span></span>  
  
```  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57675-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="57675-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="57675-106">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="57675-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="57675-107">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="57675-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="57675-108">[out]返された`IAssemblyName`ポインター。</span><span class="sxs-lookup"><span data-stu-id="57675-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="57675-109">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="57675-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="57675-110">`dwFlags` 0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="57675-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57675-111">要件</span><span class="sxs-lookup"><span data-stu-id="57675-111">Requirements</span></span>  
 <span data-ttu-id="57675-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="57675-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57675-113">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="57675-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="57675-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57675-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57675-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="57675-115">See Also</span></span>  
 [<span data-ttu-id="57675-116">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="57675-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="57675-117">IAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="57675-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
