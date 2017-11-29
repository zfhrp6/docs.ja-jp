---
title: "COR_FIELD_OFFSET 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_FIELD_OFFSET
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_FIELD_OFFSET
helpviewer_keywords: COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8e821a9d4ffa5054f687eff7360bc8d7cefb9f09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="f1227-102">COR_FIELD_OFFSET 構造体</span><span class="sxs-lookup"><span data-stu-id="f1227-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="f1227-103">指定したフィールドのクラス内の相対位置を格納します。</span><span class="sxs-lookup"><span data-stu-id="f1227-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1227-104">構文</span><span class="sxs-lookup"><span data-stu-id="f1227-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="f1227-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="f1227-105">Members</span></span>  
  
|<span data-ttu-id="f1227-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f1227-106">Member</span></span>|<span data-ttu-id="f1227-107">説明</span><span class="sxs-lookup"><span data-stu-id="f1227-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="f1227-108">`mdFieldDef`フィールドを表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="f1227-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="f1227-109">そのクラス内のフィールドをオフセットします。</span><span class="sxs-lookup"><span data-stu-id="f1227-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1227-110">コメント</span><span class="sxs-lookup"><span data-stu-id="f1227-110">Remarks</span></span>  
 <span data-ttu-id="f1227-111">[Imetadataimport::getclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)と[imetadataemit::setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)メソッドが型のパラメーターを受け取る`COR_FIELD_OFFSET`です。</span><span class="sxs-lookup"><span data-stu-id="f1227-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1227-112">要件</span><span class="sxs-lookup"><span data-stu-id="f1227-112">Requirements</span></span>  
 <span data-ttu-id="f1227-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f1227-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1227-114">**ヘッダー:** CorHdr.h、CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="f1227-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="f1227-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1227-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1227-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1227-116">See Also</span></span>  
 [<span data-ttu-id="f1227-117">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="f1227-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="f1227-118">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1227-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="f1227-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1227-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
