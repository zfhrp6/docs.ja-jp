---
title: CorSaveSize 列挙型
ms.date: 03/30/2017
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66f9f95b0cf19acb677daf7f7401d21cc81864a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447608"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="855da-102">CorSaveSize 列挙型</span><span class="sxs-lookup"><span data-stu-id="855da-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="855da-103">保存操作のサイズの照会で要求される精度のレベルを示す値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="855da-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="855da-104">構文</span><span class="sxs-lookup"><span data-stu-id="855da-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="855da-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="855da-105">Members</span></span>  
  
|<span data-ttu-id="855da-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="855da-106">Member</span></span>|<span data-ttu-id="855da-107">説明</span><span class="sxs-lookup"><span data-stu-id="855da-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="855da-108">戻り値が正確であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="855da-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="855da-109">戻り値を推定することを指定します。</span><span class="sxs-lookup"><span data-stu-id="855da-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="855da-110">破棄できる型を削除するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="855da-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="855da-111">要件</span><span class="sxs-lookup"><span data-stu-id="855da-111">Requirements</span></span>  
 <span data-ttu-id="855da-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="855da-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="855da-113">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="855da-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="855da-114">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="855da-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="855da-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="855da-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="855da-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="855da-116">See Also</span></span>  
 [<span data-ttu-id="855da-117">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="855da-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
