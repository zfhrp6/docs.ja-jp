---
title: "_CorImageUnloading 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _CorImageUnloading
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: _CorImageUnloading
helpviewer_keywords: _CorImageUnloading function [.NET Framework hosting]
ms.assetid: b4367214-6dac-4280-aa11-fd487ff30bc4
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90df58e2765cdecf4a1ec22cf5540e5cfa9530a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corimageunloading-function"></a><span data-ttu-id="05777-102">_CorImageUnloading 関数</span><span class="sxs-lookup"><span data-stu-id="05777-102">_CorImageUnloading Function</span></span>
<span data-ttu-id="05777-103">マネージ モジュール イメージがアンロードされたときに、ローダーに通知します。</span><span class="sxs-lookup"><span data-stu-id="05777-103">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 <span data-ttu-id="05777-104">この関数は実装されていません。</span><span class="sxs-lookup"><span data-stu-id="05777-104">This function is not implemented.</span></span> <span data-ttu-id="05777-105">呼び出された場合、E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="05777-105">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05777-106">構文</span><span class="sxs-lookup"><span data-stu-id="05777-106">Syntax</span></span>  
  
```  
STDAPI (VOID) _CorImageUnloading(   
   [in] PVOID* ImageBase  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05777-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="05777-107">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="05777-108">[in]アンロードするイメージの開始位置へのポインター。</span><span class="sxs-lookup"><span data-stu-id="05777-108">[in] A pointer to the starting location of the image to unload.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05777-109">要件</span><span class="sxs-lookup"><span data-stu-id="05777-109">Requirements</span></span>  
 <span data-ttu-id="05777-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="05777-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05777-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="05777-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="05777-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="05777-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05777-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05777-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05777-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="05777-114">See Also</span></span>  
 [<span data-ttu-id="05777-115">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="05777-115">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
