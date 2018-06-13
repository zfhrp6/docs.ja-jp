---
title: ICLRStrongName::StrongNameHashSize メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ebf2e0225cf497a0b89a46ecdb3e203d5b9a4cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432015"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="d8e29-102">ICLRStrongName::StrongNameHashSize メソッド</span><span class="sxs-lookup"><span data-stu-id="d8e29-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="d8e29-103">指定したハッシュ アルゴリズムを使用して、ハッシュに必要なバッファー サイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="d8e29-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8e29-104">構文</span><span class="sxs-lookup"><span data-stu-id="d8e29-104">Syntax</span></span>  
  
```  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8e29-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d8e29-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="d8e29-106">[in]バッファー サイズを計算するために使用するハッシュ アルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="d8e29-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="d8e29-107">[out]返されたバッファーのサイズ (バイト)。</span><span class="sxs-lookup"><span data-stu-id="d8e29-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d8e29-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="d8e29-108">Return Value</span></span>  
 <span data-ttu-id="d8e29-109">`S_OK` メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="d8e29-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8e29-110">要件</span><span class="sxs-lookup"><span data-stu-id="d8e29-110">Requirements</span></span>  
 <span data-ttu-id="d8e29-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d8e29-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8e29-112">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d8e29-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d8e29-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="d8e29-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8e29-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8e29-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8e29-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="d8e29-115">See Also</span></span>  
 [<span data-ttu-id="d8e29-116">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d8e29-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
