---
title: "ICLRStrongName::StrongNameHashSize メソッド"
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
- ICLRStrongName.StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: acc2812567ce2d47d3f06c000fc387708c2e8acb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="f82cd-102">ICLRStrongName::StrongNameHashSize メソッド</span><span class="sxs-lookup"><span data-stu-id="f82cd-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="f82cd-103">指定したハッシュ アルゴリズムを使用して、ハッシュに必要なバッファー サイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="f82cd-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f82cd-104">構文</span><span class="sxs-lookup"><span data-stu-id="f82cd-104">Syntax</span></span>  
  
```  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f82cd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f82cd-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="f82cd-106">[in]バッファー サイズを計算するために使用するハッシュ アルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="f82cd-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="f82cd-107">[out]返されたバッファーのサイズ (バイト)。</span><span class="sxs-lookup"><span data-stu-id="f82cd-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f82cd-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="f82cd-108">Return Value</span></span>  
 <span data-ttu-id="f82cd-109">`S_OK`メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="f82cd-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f82cd-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="f82cd-110">Requirements</span></span>  
 <span data-ttu-id="f82cd-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f82cd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f82cd-112">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f82cd-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f82cd-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="f82cd-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f82cd-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f82cd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f82cd-115">参照</span><span class="sxs-lookup"><span data-stu-id="f82cd-115">See Also</span></span>  
 [<span data-ttu-id="f82cd-116">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f82cd-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
