---
title: "ICeeGen::AllocateMethodBuffer メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.AllocateMethodBuffer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be288bedf12649b4356c68135868b9415840c4d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="b8984-102">ICeeGen::AllocateMethodBuffer メソッド</span><span class="sxs-lookup"><span data-stu-id="b8984-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="b8984-103">メソッドで指定されたサイズのバッファーを作成し、メソッドの相対仮想アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="b8984-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="b8984-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="b8984-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8984-105">構文</span><span class="sxs-lookup"><span data-stu-id="b8984-105">Syntax</span></span>  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8984-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b8984-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="b8984-107">[in]作成するためのバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="b8984-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="b8984-108">[out]返されるバッファー。</span><span class="sxs-lookup"><span data-stu-id="b8984-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="b8984-109">[out]メソッドの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="b8984-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8984-110">要件</span><span class="sxs-lookup"><span data-stu-id="b8984-110">Requirements</span></span>  
 <span data-ttu-id="b8984-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b8984-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8984-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b8984-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8984-113">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="b8984-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8984-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8984-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8984-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8984-115">See Also</span></span>  
 [<span data-ttu-id="b8984-116">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b8984-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
