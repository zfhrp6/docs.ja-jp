---
title: ICeeGen::GetMethodBuffer メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a093b18f72cc99c53951b3dc588ce0cff3c7fefd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442609"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="a160b-102">ICeeGen::GetMethodBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="a160b-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="a160b-103">指定の相対仮想アドレスのメソッドを適切なサイズのバッファーを取得します。</span><span class="sxs-lookup"><span data-stu-id="a160b-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="a160b-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a160b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a160b-105">構文</span><span class="sxs-lookup"><span data-stu-id="a160b-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a160b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a160b-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="a160b-107">[in]バッファーを取得するメソッドの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="a160b-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="a160b-108">[out]返されたバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a160b-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a160b-109">要件</span><span class="sxs-lookup"><span data-stu-id="a160b-109">Requirements</span></span>  
 <span data-ttu-id="a160b-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a160b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a160b-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a160b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a160b-112">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="a160b-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a160b-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a160b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a160b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a160b-114">See Also</span></span>  
 [<span data-ttu-id="a160b-115">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a160b-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
