---
title: ICeeGen::ComputePointer メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.ComputePointer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::ComputePointer
helpviewer_keywords:
- ICeeGen::ComputePointer method [.NET Framework metadata]
- ComputePointer method [.NET Framework metadata]
ms.assetid: b6b95c04-0f2c-4fcc-a8bc-3b1dcbdba731
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1239546072192d6ff9497013ad7b7140ea13085
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443243"
---
# <a name="iceegencomputepointer-method"></a><span data-ttu-id="128ba-102">ICeeGen::ComputePointer メソッド</span><span class="sxs-lookup"><span data-stu-id="128ba-102">ICeeGen::ComputePointer Method</span></span>
<span data-ttu-id="128ba-103">指定されたコードのセクションのバッファーを決定します。</span><span class="sxs-lookup"><span data-stu-id="128ba-103">Determines the buffer for the specified code section.</span></span>  
  
 <span data-ttu-id="128ba-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="128ba-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="128ba-105">構文</span><span class="sxs-lookup"><span data-stu-id="128ba-105">Syntax</span></span>  
  
```  
HRESULT ComputePointer (  
    [in]  HCEESECTION  section,  
    [in]  ULONG        RVA,   
    [out] UCHAR        **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="128ba-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="128ba-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="128ba-107">[in]バッファーを取得するコード セクションです。</span><span class="sxs-lookup"><span data-stu-id="128ba-107">[in] The code section for which to return a buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="128ba-108">[in]ポインターを取得する対象のメソッドの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="128ba-108">[in] The relative virtual address of the method for which to get a pointer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="128ba-109">[out]返されたバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="128ba-109">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="128ba-110">要件</span><span class="sxs-lookup"><span data-stu-id="128ba-110">Requirements</span></span>  
 <span data-ttu-id="128ba-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="128ba-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="128ba-112">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="128ba-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="128ba-113">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="128ba-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="128ba-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="128ba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="128ba-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="128ba-115">See Also</span></span>  
 [<span data-ttu-id="128ba-116">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="128ba-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
