---
title: "CustomDumpItem 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CustomDumpItem
api_location: mscoree.dll
api_type: COM
f1_keywords: CustomDumpItem
helpviewer_keywords: CustomDumpItem structure [.NET Framework hosting]
ms.assetid: fd9085ff-7beb-4c38-97f0-037cd8ba4f65
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47fd4e1dd3889cc7eeaa37457b47d9b2fd6dd8b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="customdumpitem-structure"></a><span data-ttu-id="817d7-102">CustomDumpItem 構造体</span><span class="sxs-lookup"><span data-stu-id="817d7-102">CustomDumpItem Structure</span></span>
<span data-ttu-id="817d7-103">エラー報告でのカスタムのダンプに追加する項目を示します。</span><span class="sxs-lookup"><span data-stu-id="817d7-103">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="817d7-104">構文</span><span class="sxs-lookup"><span data-stu-id="817d7-104">Syntax</span></span>  
  
```  
struct {  
    ECustomDumpItemKind itemKind;   
    union {  
        UINT_PTR pReserved;  
    }  
} CustomDumpItem;  
```  
  
## <a name="members"></a><span data-ttu-id="817d7-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="817d7-105">Members</span></span>  
  
|<span data-ttu-id="817d7-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="817d7-106">Member</span></span>|<span data-ttu-id="817d7-107">説明</span><span class="sxs-lookup"><span data-stu-id="817d7-107">Description</span></span>|  
|------------|-----------------|  
|`itemKind`|<span data-ttu-id="817d7-108">[ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)を追加する項目の種類を示す値。</span><span class="sxs-lookup"><span data-stu-id="817d7-108">An [ECustomDumpItemKind](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md) value that indicates the kind of item to be added.</span></span>|  
|`pReserved`|<span data-ttu-id="817d7-109">現在使用されていません。</span><span class="sxs-lookup"><span data-stu-id="817d7-109">Not currently used.</span></span> <span data-ttu-id="817d7-110">和集合に追加する項目は、ポインターのサイズよりも小さいする必要があります。</span><span class="sxs-lookup"><span data-stu-id="817d7-110">Any items added to the union must be no larger than pointer size.</span></span> <span data-ttu-id="817d7-111">場合、`struct`は必要に応じて、個別に割り当ててし をポイントします。</span><span class="sxs-lookup"><span data-stu-id="817d7-111">If a `struct` is required, you must allocate it separately and point to it.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="817d7-112">コメント</span><span class="sxs-lookup"><span data-stu-id="817d7-112">Remarks</span></span>  
 <span data-ttu-id="817d7-113">[Iclrerrorreportingmanager::begincustomdump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)型のパラメーターを受け取る`CustomDumpItem`です。</span><span class="sxs-lookup"><span data-stu-id="817d7-113">[ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) takes a parameter of type `CustomDumpItem`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="817d7-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="817d7-114">Requirements</span></span>  
 <span data-ttu-id="817d7-115">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="817d7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="817d7-116">**ヘッダー:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="817d7-116">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="817d7-117">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="817d7-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="817d7-118">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="817d7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="817d7-119">参照</span><span class="sxs-lookup"><span data-stu-id="817d7-119">See Also</span></span>  
 [<span data-ttu-id="817d7-120">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="817d7-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
