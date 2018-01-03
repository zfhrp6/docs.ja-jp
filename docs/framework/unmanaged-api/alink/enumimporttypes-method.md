---
title: "EnumImportTypes メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location: alink.dll
api_type: COM
f1_keywords: EnumImportTypes
helpviewer_keywords: EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08644816d3fa11ade5a8ebee1573e8f66d526101
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="a1e36-102">EnumImportTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="a1e36-102">EnumImportTypes Method</span></span>
<span data-ttu-id="a1e36-103">それぞれのスコープ内の各種類を列挙します。</span><span class="sxs-lookup"><span data-stu-id="a1e36-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1e36-104">構文</span><span class="sxs-lookup"><span data-stu-id="a1e36-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1e36-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a1e36-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="a1e36-106">列挙子のハンドルです。</span><span class="sxs-lookup"><span data-stu-id="a1e36-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="a1e36-107">取得する型の最大数。</span><span class="sxs-lookup"><span data-stu-id="a1e36-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="a1e36-108">型を超えないように、トークンを受け取ります`dwMax`です。</span><span class="sxs-lookup"><span data-stu-id="a1e36-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="a1e36-109">型の実際の数を受け取る`aTypeDefs`です。</span><span class="sxs-lookup"><span data-stu-id="a1e36-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1e36-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="a1e36-110">Return Value</span></span>  
 <span data-ttu-id="a1e36-111">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="a1e36-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1e36-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="a1e36-112">Requirements</span></span>  
 <span data-ttu-id="a1e36-113">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="a1e36-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e36-114">参照</span><span class="sxs-lookup"><span data-stu-id="a1e36-114">See Also</span></span>  
 [<span data-ttu-id="a1e36-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1e36-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="a1e36-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a1e36-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="a1e36-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="a1e36-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
