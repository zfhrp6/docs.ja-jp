---
title: "CorSaveSize 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSaveSize
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSaveSize
helpviewer_keywords: CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 34d4d42c7cf385bca77de37dce52689778aa5b1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="4c7ff-102">CorSaveSize 列挙型</span><span class="sxs-lookup"><span data-stu-id="4c7ff-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="4c7ff-103">保存操作のサイズの照会で要求される精度のレベルを示す値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="4c7ff-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c7ff-104">構文</span><span class="sxs-lookup"><span data-stu-id="4c7ff-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="4c7ff-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="4c7ff-105">Members</span></span>  
  
|<span data-ttu-id="4c7ff-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4c7ff-106">Member</span></span>|<span data-ttu-id="4c7ff-107">説明</span><span class="sxs-lookup"><span data-stu-id="4c7ff-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="4c7ff-108">戻り値が正確であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c7ff-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="4c7ff-109">戻り値を推定することを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c7ff-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="4c7ff-110">破棄できる型を削除するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="4c7ff-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4c7ff-111">要件</span><span class="sxs-lookup"><span data-stu-id="4c7ff-111">Requirements</span></span>  
 <span data-ttu-id="4c7ff-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4c7ff-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c7ff-113">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="4c7ff-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4c7ff-114">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="4c7ff-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4c7ff-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c7ff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c7ff-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c7ff-116">See Also</span></span>  
 [<span data-ttu-id="4c7ff-117">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="4c7ff-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
