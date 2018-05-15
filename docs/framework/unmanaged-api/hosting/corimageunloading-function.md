---
title: _CorImageUnloading 関数
ms.date: 03/30/2017
api_name:
- _CorImageUnloading
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorImageUnloading
helpviewer_keywords:
- _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ebd7ef3b329eae8e35b680f3d8c74864e2a0f4d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="corimageunloading-function"></a><span data-ttu-id="ccaf3-102">_CorImageUnloading 関数</span><span class="sxs-lookup"><span data-stu-id="ccaf3-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="ccaf3-103">マネージ モジュール イメージがアンロードされたときに、ローダーに通知します。</span><span class="sxs-lookup"><span data-stu-id="ccaf3-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="ccaf3-104">この関数は実装されていません。</span><span class="sxs-lookup"><span data-stu-id="ccaf3-104">This function is not implemented.</span></span> <span data-ttu-id="ccaf3-105">呼び出された場合、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="ccaf3-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccaf3-106">構文</span><span class="sxs-lookup"><span data-stu-id="ccaf3-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccaf3-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ccaf3-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="ccaf3-108">[in]アンロードするイメージの開始位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ccaf3-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccaf3-109">要件</span><span class="sxs-lookup"><span data-stu-id="ccaf3-109">Requirements</span></span>  
 <span data-ttu-id="ccaf3-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="ccaf3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccaf3-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ccaf3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ccaf3-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="ccaf3-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ccaf3-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccaf3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccaf3-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ccaf3-114">See Also</span></span>  
 [<span data-ttu-id="ccaf3-115">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="ccaf3-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
