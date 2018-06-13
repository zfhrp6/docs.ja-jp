---
title: GetAssemblyIdentityFromFile 関数
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ea151417a1cb53104ec29fff1e76e21f82ec9bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431644"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="ce92f-102">GetAssemblyIdentityFromFile 関数</span><span class="sxs-lookup"><span data-stu-id="ce92f-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="ce92f-103">ポインターを取得、`IUnknown`指定したオブジェクト`IID`のアセンブリにある指定したファイル パス。</span><span class="sxs-lookup"><span data-stu-id="ce92f-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce92f-104">構文</span><span class="sxs-lookup"><span data-stu-id="ce92f-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce92f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ce92f-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="ce92f-106">[in]要求されたアセンブリに有効なパスです。</span><span class="sxs-lookup"><span data-stu-id="ce92f-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="ce92f-107">[in]`IID`のインターフェイスを返します。</span><span class="sxs-lookup"><span data-stu-id="ce92f-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="ce92f-108">[out]返されたインターフェイス ポインター。</span><span class="sxs-lookup"><span data-stu-id="ce92f-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce92f-109">要件</span><span class="sxs-lookup"><span data-stu-id="ce92f-109">Requirements</span></span>  
 <span data-ttu-id="ce92f-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ce92f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce92f-111">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ce92f-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ce92f-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce92f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce92f-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="ce92f-113">See Also</span></span>  
 <span data-ttu-id="ce92f-114"><<!--zzxref:IUnknown --> `IUnknown`></span><span class="sxs-lookup"><span data-stu-id="ce92f-114"><<!--zzxref:IUnknown --> `IUnknown`></span></span>  
 [<span data-ttu-id="ce92f-115">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="ce92f-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
