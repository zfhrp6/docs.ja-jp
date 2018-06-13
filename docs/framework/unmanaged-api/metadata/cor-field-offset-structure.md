---
title: COR_FIELD_OFFSET 構造体
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c4a5c8efc87940b7df0bfd532beaa67931a8c81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442119"
---
# <a name="corfieldoffset-structure"></a><span data-ttu-id="3c7db-102">COR_FIELD_OFFSET 構造体</span><span class="sxs-lookup"><span data-stu-id="3c7db-102">COR_FIELD_OFFSET Structure</span></span>
<span data-ttu-id="3c7db-103">指定したフィールドのクラス内の相対位置を格納します。</span><span class="sxs-lookup"><span data-stu-id="3c7db-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c7db-104">構文</span><span class="sxs-lookup"><span data-stu-id="3c7db-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="3c7db-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="3c7db-105">Members</span></span>  
  
|<span data-ttu-id="3c7db-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="3c7db-106">Member</span></span>|<span data-ttu-id="3c7db-107">説明</span><span class="sxs-lookup"><span data-stu-id="3c7db-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="3c7db-108">`mdFieldDef`フィールドを表すメタデータ トークン。</span><span class="sxs-lookup"><span data-stu-id="3c7db-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="3c7db-109">そのクラス内のフィールドをオフセットします。</span><span class="sxs-lookup"><span data-stu-id="3c7db-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c7db-110">コメント</span><span class="sxs-lookup"><span data-stu-id="3c7db-110">Remarks</span></span>  
 <span data-ttu-id="3c7db-111">[Imetadataimport::getclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md)と[imetadataemit::setclasslayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md)メソッドが型のパラメーターを受け取る`COR_FIELD_OFFSET`です。</span><span class="sxs-lookup"><span data-stu-id="3c7db-111">[IMetaDataImport::GetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c7db-112">要件</span><span class="sxs-lookup"><span data-stu-id="3c7db-112">Requirements</span></span>  
 <span data-ttu-id="3c7db-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3c7db-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c7db-114">**ヘッダー:** CorHdr.h、CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3c7db-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="3c7db-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c7db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c7db-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c7db-116">See Also</span></span>  
 [<span data-ttu-id="3c7db-117">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="3c7db-117">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="3c7db-118">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c7db-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="3c7db-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c7db-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
