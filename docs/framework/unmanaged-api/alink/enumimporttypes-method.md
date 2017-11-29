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
ms.openlocfilehash: df6efbc86ff958cb8a715c81f86ea1112629fe67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="f4d25-102">EnumImportTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="f4d25-102">EnumImportTypes Method</span></span>
<span data-ttu-id="f4d25-103">それぞれのスコープ内の各種類を列挙します。</span><span class="sxs-lookup"><span data-stu-id="f4d25-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4d25-104">構文</span><span class="sxs-lookup"><span data-stu-id="f4d25-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f4d25-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f4d25-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="f4d25-106">列挙子のハンドルです。</span><span class="sxs-lookup"><span data-stu-id="f4d25-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="f4d25-107">取得する型の最大数。</span><span class="sxs-lookup"><span data-stu-id="f4d25-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="f4d25-108">型を超えないように、トークンを受け取ります`dwMax`です。</span><span class="sxs-lookup"><span data-stu-id="f4d25-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="f4d25-109">型の実際の数を受け取る`aTypeDefs`です。</span><span class="sxs-lookup"><span data-stu-id="f4d25-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f4d25-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="f4d25-110">Return Value</span></span>  
 <span data-ttu-id="f4d25-111">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="f4d25-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4d25-112">要件</span><span class="sxs-lookup"><span data-stu-id="f4d25-112">Requirements</span></span>  
 <span data-ttu-id="f4d25-113">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="f4d25-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d25-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4d25-114">See Also</span></span>  
 [<span data-ttu-id="f4d25-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4d25-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f4d25-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f4d25-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f4d25-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="f4d25-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
