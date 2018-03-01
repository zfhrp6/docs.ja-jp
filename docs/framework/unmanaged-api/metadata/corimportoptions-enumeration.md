---
title: "CorImportOptions 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e9af7bbb6dd7cfa488f72ec99f9cfd848f04e72f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="dede3-102">CorImportOptions 列挙型</span><span class="sxs-lookup"><span data-stu-id="dede3-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="dede3-103">現在のスコープ外のアセンブリのインポート中の動作を制御するフラグ値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="dede3-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dede3-104">構文</span><span class="sxs-lookup"><span data-stu-id="dede3-104">Syntax</span></span>  
  
```  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="dede3-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="dede3-105">Members</span></span>  
  
|<span data-ttu-id="dede3-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="dede3-106">Member</span></span>|<span data-ttu-id="dede3-107">説明</span><span class="sxs-lookup"><span data-stu-id="dede3-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="dede3-108">削除されたレコードをスキップするには既定の動作を示します。</span><span class="sxs-lookup"><span data-stu-id="dede3-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="dede3-109">すべてのメタデータを列挙することを示します。</span><span class="sxs-lookup"><span data-stu-id="dede3-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="dede3-110">削除されたものも含めて、すべての Typedef が列挙されることを示します。</span><span class="sxs-lookup"><span data-stu-id="dede3-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="dede3-111">削除されたものも含めて、すべての MethodDefs が列挙されることを示します。</span><span class="sxs-lookup"><span data-stu-id="dede3-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="dede3-112">削除されたものも含めて、すべての FieldDefs が列挙されることを示します。</span><span class="sxs-lookup"><span data-stu-id="dede3-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="dede3-113">削除されたものも含めて、すべての PropertyDefs が列挙されることを示します。</span><span class="sxs-lookup"><span data-stu-id="dede3-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="dede3-114">削除されたものも含めて、すべての EventDefs が列挙されることを示します。</span><span class="sxs-lookup"><span data-stu-id="dede3-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="dede3-115">削除されたものも含めて、すべてのカスタム属性を列挙することを示します。</span><span class="sxs-lookup"><span data-stu-id="dede3-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="dede3-116">削除されたものも含めて、すべてのエクスポートされた型が列挙されることを示します。</span><span class="sxs-lookup"><span data-stu-id="dede3-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dede3-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="dede3-117">Requirements</span></span>  
 <span data-ttu-id="dede3-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dede3-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dede3-119">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="dede3-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="dede3-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dede3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dede3-121">参照</span><span class="sxs-lookup"><span data-stu-id="dede3-121">See Also</span></span>  
 [<span data-ttu-id="dede3-122">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="dede3-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
