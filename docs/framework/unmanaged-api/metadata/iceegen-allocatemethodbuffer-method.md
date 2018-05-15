---
title: ICeeGen::AllocateMethodBuffer メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.AllocateMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f56376d4400f4e24aefe2d1e5d4ad504b1d281cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="96503-102">ICeeGen::AllocateMethodBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="96503-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="96503-103">メソッドで指定されたサイズのバッファーを作成し、メソッドの相対仮想アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="96503-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="96503-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="96503-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96503-105">構文</span><span class="sxs-lookup"><span data-stu-id="96503-105">Syntax</span></span>  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96503-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="96503-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="96503-107">[in]作成するためのバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="96503-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="96503-108">[out]返されるバッファー。</span><span class="sxs-lookup"><span data-stu-id="96503-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="96503-109">[out]メソッドの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="96503-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96503-110">要件</span><span class="sxs-lookup"><span data-stu-id="96503-110">Requirements</span></span>  
 <span data-ttu-id="96503-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="96503-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96503-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="96503-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96503-113">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="96503-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96503-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96503-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96503-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="96503-115">See Also</span></span>  
 [<span data-ttu-id="96503-116">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="96503-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
