---
title: CloseEnum メソッド
ms.date: 03/30/2017
api_name:
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5c3185dc6d488223d5882f543f0c690d82261b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402445"
---
# <a name="closeenum-method"></a><span data-ttu-id="36967-102">CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="36967-102">CloseEnum Method</span></span>
<span data-ttu-id="36967-103">指定の列挙体を閉じるし、関連付けられているリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="36967-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36967-104">構文</span><span class="sxs-lookup"><span data-stu-id="36967-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36967-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="36967-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="36967-106">終了する列挙体のハンドルです。</span><span class="sxs-lookup"><span data-stu-id="36967-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36967-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="36967-107">Return Value</span></span>  
 <span data-ttu-id="36967-108">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="36967-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36967-109">要件</span><span class="sxs-lookup"><span data-stu-id="36967-109">Requirements</span></span>  
 <span data-ttu-id="36967-110">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="36967-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36967-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="36967-111">See Also</span></span>  
 [<span data-ttu-id="36967-112">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="36967-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="36967-113">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="36967-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="36967-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="36967-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
