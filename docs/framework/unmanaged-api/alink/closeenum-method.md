---
title: "CloseEnum メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CloseEnum
- IALink.CloseEnum
api_location: alink.dll
api_type: COM
f1_keywords: CloseEnum
helpviewer_keywords: CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 89f5b7069af0bfdfd732ed1ab4935771a565a20f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="closeenum-method"></a><span data-ttu-id="a2ce6-102">CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="a2ce6-102">CloseEnum Method</span></span>
<span data-ttu-id="a2ce6-103">指定の列挙体を閉じるし、関連付けられているリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="a2ce6-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2ce6-104">構文</span><span class="sxs-lookup"><span data-stu-id="a2ce6-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2ce6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a2ce6-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="a2ce6-106">終了する列挙体のハンドルです。</span><span class="sxs-lookup"><span data-stu-id="a2ce6-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2ce6-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="a2ce6-107">Return Value</span></span>  
 <span data-ttu-id="a2ce6-108">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="a2ce6-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2ce6-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="a2ce6-109">Requirements</span></span>  
 <span data-ttu-id="a2ce6-110">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="a2ce6-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ce6-111">参照</span><span class="sxs-lookup"><span data-stu-id="a2ce6-111">See Also</span></span>  
 [<span data-ttu-id="a2ce6-112">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2ce6-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="a2ce6-113">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2ce6-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="a2ce6-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="a2ce6-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
