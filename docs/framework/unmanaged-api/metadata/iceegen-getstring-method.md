---
title: ICeeGen::GetString メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f7ac5ef95ca3705b11cfda51d7fd1aca7400abc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443074"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="72495-102">ICeeGen::GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="72495-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="72495-103">指定の相対仮想アドレスに格納された文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="72495-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="72495-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="72495-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72495-105">構文</span><span class="sxs-lookup"><span data-stu-id="72495-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72495-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="72495-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="72495-107">[in]返される文字列の相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="72495-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="72495-108">[out]返される文字列。</span><span class="sxs-lookup"><span data-stu-id="72495-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72495-109">要件</span><span class="sxs-lookup"><span data-stu-id="72495-109">Requirements</span></span>  
 <span data-ttu-id="72495-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="72495-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72495-111">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="72495-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72495-112">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="72495-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72495-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72495-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72495-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="72495-114">See Also</span></span>  
 [<span data-ttu-id="72495-115">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="72495-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
