---
title: EnumImportTypes メソッド
ms.date: 03/30/2017
api_name:
- EnumImportTypes
- IALink.EnumImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumImportTypes
helpviewer_keywords:
- EnumImportTypes method
ms.assetid: 83a0e4e7-ec06-40cb-9b63-700b9695bb04
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90319886dfe149a3d2d76451c1a8526299cf5b89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33401649"
---
# <a name="enumimporttypes-method"></a><span data-ttu-id="13272-102">EnumImportTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="13272-102">EnumImportTypes Method</span></span>
<span data-ttu-id="13272-103">それぞれのスコープ内の各種類を列挙します。</span><span class="sxs-lookup"><span data-stu-id="13272-103">Enumerates each type in each scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13272-104">構文</span><span class="sxs-lookup"><span data-stu-id="13272-104">Syntax</span></span>  
  
```  
HRESULT EnumImportTypes(  
    HALINKENUM   hEnum,  
    DWORD        dwMax,  
    mdTypeDef    aTypeDefs[],  
    DWORD*       pdwCount  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13272-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="13272-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="13272-106">列挙子のハンドルです。</span><span class="sxs-lookup"><span data-stu-id="13272-106">Handle for enumerator.</span></span>  
  
 `dwMax`  
 <span data-ttu-id="13272-107">取得する型の最大数。</span><span class="sxs-lookup"><span data-stu-id="13272-107">Maximum number of types to retrieve.</span></span>  
  
 `aTypeDefs`  
 <span data-ttu-id="13272-108">型を超えないように、トークンを受け取ります`dwMax`です。</span><span class="sxs-lookup"><span data-stu-id="13272-108">Recieves type tokens, not to exceed `dwMax`.</span></span>  
  
 `pdwCount`  
 <span data-ttu-id="13272-109">型の実際の数を受け取る`aTypeDefs`です。</span><span class="sxs-lookup"><span data-stu-id="13272-109">Receives actual number of type in `aTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13272-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="13272-110">Return Value</span></span>  
 <span data-ttu-id="13272-111">メソッドが成功した場合は、S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="13272-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13272-112">要件</span><span class="sxs-lookup"><span data-stu-id="13272-112">Requirements</span></span>  
 <span data-ttu-id="13272-113">Alink.h が必要です。</span><span class="sxs-lookup"><span data-stu-id="13272-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13272-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="13272-114">See Also</span></span>  
 [<span data-ttu-id="13272-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13272-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="13272-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="13272-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="13272-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="13272-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
