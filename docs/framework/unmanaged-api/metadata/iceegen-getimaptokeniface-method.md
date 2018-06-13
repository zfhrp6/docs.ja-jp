---
title: ICeeGen::GetIMapTokenIface メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIMapTokenIface
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIMapTokenIface
helpviewer_keywords:
- GetIMapTokenIface method [.NET Framework metadata]
- ICeeGen::GetIMapTokenIface method [.NET Framework metadata]
ms.assetid: 847a5531-c37d-49cd-8844-9e54b5d86cf7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 627ae1f3da053af9a1bf9962e5b46cfb8b5046cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442754"
---
# <a name="iceegengetimaptokeniface-method"></a><span data-ttu-id="af03d-102">ICeeGen::GetIMapTokenIface メソッド</span><span class="sxs-lookup"><span data-stu-id="af03d-102">ICeeGen::GetIMapTokenIface Method</span></span>
<span data-ttu-id="af03d-103">指定したトークンによって参照されているインターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="af03d-103">Gets the interface referenced by the specified token.</span></span>  
  
 <span data-ttu-id="af03d-104">このメソッドは、古いは使用できません。</span><span class="sxs-lookup"><span data-stu-id="af03d-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af03d-105">構文</span><span class="sxs-lookup"><span data-stu-id="af03d-105">Syntax</span></span>  
  
```  
HRESULT GetIMapTokenIface (  
    [in, out] IUnknown   **pIMapToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="af03d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="af03d-106">Parameters</span></span>  
 `pIMapToken`  
 <span data-ttu-id="af03d-107">[入力、出力].返されるインターフェイスのメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="af03d-107">[in, out] The metadata token for the interface to be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af03d-108">要件</span><span class="sxs-lookup"><span data-stu-id="af03d-108">Requirements</span></span>  
 <span data-ttu-id="af03d-109">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="af03d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af03d-110">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="af03d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af03d-111">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="af03d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="af03d-112">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af03d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af03d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="af03d-113">See Also</span></span>  
 [<span data-ttu-id="af03d-114">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="af03d-114">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
