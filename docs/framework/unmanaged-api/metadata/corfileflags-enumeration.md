---
title: "CorFileFlags 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFileFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFileFlags
helpviewer_keywords: CorFileFlags enumeration [.NET Framework metadata]
ms.assetid: d16703fd-518f-412e-92cb-74433d11032e
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bf123f734f73ecfe726a80099de6ec06b0ced06b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corfileflags-enumeration"></a><span data-ttu-id="21e8a-102">CorFileFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="21e8a-102">CorFileFlags Enumeration</span></span>
<span data-ttu-id="21e8a-103">呼び出しで定義されているファイルの種類を記述する値を含む[imetadataassemblyemit::definefile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="21e8a-103">Contains values that describe the type of file defined in a call to [IMetaDataAssemblyEmit::DefineFile](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-definefile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e8a-104">構文</span><span class="sxs-lookup"><span data-stu-id="21e8a-104">Syntax</span></span>  
  
```  
typedef enum CorFileFlags {  
  
    ffContainsMetaData      =   0x0000,  
    ffContainsNoMetaData    =   0x0001  
  
} CorFileFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="21e8a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="21e8a-105">Members</span></span>  
  
|<span data-ttu-id="21e8a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="21e8a-106">Member</span></span>|<span data-ttu-id="21e8a-107">説明</span><span class="sxs-lookup"><span data-stu-id="21e8a-107">Description</span></span>|  
|------------|-----------------|  
|`ffContainsMetaData`|<span data-ttu-id="21e8a-108">ファイルがリソース ファイルでないことを示します。</span><span class="sxs-lookup"><span data-stu-id="21e8a-108">Indicates that the file is not a resource file.</span></span>|  
|`ffContainsNoMetaData`|<span data-ttu-id="21e8a-109">場合によっては、リソース ファイル、ファイルにメタデータが含まれていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="21e8a-109">Indicates that the file, possibly a resource file, does not contain metadata.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21e8a-110">要件</span><span class="sxs-lookup"><span data-stu-id="21e8a-110">Requirements</span></span>  
 <span data-ttu-id="21e8a-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="21e8a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e8a-112">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="21e8a-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="21e8a-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21e8a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21e8a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="21e8a-114">See Also</span></span>  
 [<span data-ttu-id="21e8a-115">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="21e8a-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
