---
title: CustomDumpItem 構造体
ms.date: 03/30/2017
api_name:
- CustomDumpItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CustomDumpItem
helpviewer_keywords:
- CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f742d219d603488bbade091f7a8192785d3e84f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433097"
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="1a14d-102">CustomDumpItem 構造体</span><span class="sxs-lookup"><span data-stu-id="1a14d-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="1a14d-103">エラー報告でのカスタムのダンプに追加する項目を示します。</span><span class="sxs-lookup"><span data-stu-id="1a14d-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a14d-104">構文</span><span class="sxs-lookup"><span data-stu-id="1a14d-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="1a14d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="1a14d-105">Members</span></span>  
  
|<span data-ttu-id="1a14d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1a14d-106">Member</span></span>|<span data-ttu-id="1a14d-107">説明</span><span class="sxs-lookup"><span data-stu-id="1a14d-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="1a14d-108">[ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)を追加する項目の種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="1a14d-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="1a14d-109">現在使用されていません。</span><span class="sxs-lookup"><span data-stu-id="1a14d-109">Not currently used.</span></span> <span data-ttu-id="1a14d-110">和集合に追加する項目は、ポインターのサイズよりも小さいする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a14d-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="1a14d-111">場合、`struct`は必要に応じて、個別に割り当ててし をポイントします。</span><span class="sxs-lookup"><span data-stu-id="1a14d-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a14d-112">コメント</span><span class="sxs-lookup"><span data-stu-id="1a14d-112">Remarks</span></span>  
 <span data-ttu-id="1a14d-113">[Iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)型のパラメーターを受け取る`CustomDumpItem`です。</span><span class="sxs-lookup"><span data-stu-id="1a14d-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a14d-114">要件</span><span class="sxs-lookup"><span data-stu-id="1a14d-114">Requirements</span></span>  
 <span data-ttu-id="1a14d-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1a14d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a14d-116">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="1a14d-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="1a14d-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="1a14d-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a14d-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a14d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a14d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a14d-119">See Also</span></span>  
 [<span data-ttu-id="1a14d-120">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="1a14d-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
