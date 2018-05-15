---
title: CorFileFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorFileFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileFlags
helpviewer_keywords:
- CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ecc2f62a6bb8119b7fe06a82aea827a58d04ecb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="817ff-102">CorFileFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="817ff-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="817ff-103">呼び出しで定義されているファイルの種類を記述する値を含む[imetadataassemblyemit::definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="817ff-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="817ff-104">構文</span><span class="sxs-lookup"><span data-stu-id="817ff-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="817ff-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="817ff-105">Members</span></span>  
  
|<span data-ttu-id="817ff-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="817ff-106">Member</span></span>|<span data-ttu-id="817ff-107">説明</span><span class="sxs-lookup"><span data-stu-id="817ff-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="817ff-108">ファイルがリソース ファイルでないことを示します。</span><span class="sxs-lookup"><span data-stu-id="817ff-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="817ff-109">場合によっては、リソース ファイル、ファイルにメタデータが含まれていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="817ff-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="817ff-110">要件</span><span class="sxs-lookup"><span data-stu-id="817ff-110">Requirements</span></span>  
 <span data-ttu-id="817ff-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="817ff-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="817ff-112">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="817ff-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="817ff-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="817ff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="817ff-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="817ff-114">See Also</span></span>  
 [<span data-ttu-id="817ff-115">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="817ff-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
