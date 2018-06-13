---
title: ICLRStrongName::StrongNameFreeBuffer メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfc4cb503c7d94345ede34de1788667857946e0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433139"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="66a33-102">ICLRStrongName::StrongNameFreeBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="66a33-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="66a33-103">など、厳密な名前のメソッドを前回呼び出したときに割り当てられたメモリを解放[iclrstrongname::strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)、 [iclrstrongname::strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)、または[Iclrstrongname::strongnamesignaturegeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="66a33-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66a33-104">構文</span><span class="sxs-lookup"><span data-stu-id="66a33-104">Syntax</span></span>  
  
```  
HRESULT StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66a33-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="66a33-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="66a33-106">[in]解放するメモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="66a33-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66a33-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="66a33-107">Return Value</span></span>  
 <span data-ttu-id="66a33-108">`S_OK` メソッドが正常に完了した場合それ以外の場合、失敗を示す HRESULT 値 (を参照してください[の共通 HRESULT 値](http://go.microsoft.com/fwlink/?LinkId=213878)一覧)。</span><span class="sxs-lookup"><span data-stu-id="66a33-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66a33-109">要件</span><span class="sxs-lookup"><span data-stu-id="66a33-109">Requirements</span></span>  
 <span data-ttu-id="66a33-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="66a33-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66a33-111">**ヘッダー:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="66a33-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="66a33-112">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="66a33-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66a33-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66a33-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a33-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="66a33-114">See Also</span></span>  
 [<span data-ttu-id="66a33-115">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="66a33-115">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
