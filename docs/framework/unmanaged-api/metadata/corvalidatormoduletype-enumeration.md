---
title: "CorValidatorModuleType 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorValidatorModuleType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorValidatorModuleType
helpviewer_keywords: CorValidatorModuleType enumeration [.NET Framework metadata]
ms.assetid: 748f1ab2-fbcb-4f55-89ec-8d23d81ebc80
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fa7ca08398358dcf00a986c356de365e9caafc4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="corvalidatormoduletype-enumeration"></a><span data-ttu-id="3fcd1-102">CorValidatorModuleType 列挙型</span><span class="sxs-lookup"><span data-stu-id="3fcd1-102">CorValidatorModuleType Enumeration</span></span>
<span data-ttu-id="3fcd1-103">モジュールの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="3fcd1-103">Specifies the type of a module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fcd1-104">構文</span><span class="sxs-lookup"><span data-stu-id="3fcd1-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    ValidatorModuleTypeInvalid  = 0x0,  
    ValidatorModuleTypeMin      = 0x00000001,  
    ValidatorModuleTypePE       = 0x00000001,  
    ValidatorModuleTypeObj      = 0x00000002,  
    ValidatorModuleTypeEnc      = 0x00000003,  
    ValidatorModuleTypeIncr     = 0x00000004,  
    ValidatorModuleTypeMax      = 0x00000004  
} CorValidatorModuleType;  
```  
  
## <a name="members"></a><span data-ttu-id="3fcd1-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="3fcd1-105">Members</span></span>  
  
|<span data-ttu-id="3fcd1-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="3fcd1-106">Member</span></span>|<span data-ttu-id="3fcd1-107">説明</span><span class="sxs-lookup"><span data-stu-id="3fcd1-107">Description</span></span>|  
|------------|-----------------|  
|`ValidatorModuleTypeInvalid`|<span data-ttu-id="3fcd1-108">モジュールは、無効な型です。</span><span class="sxs-lookup"><span data-stu-id="3fcd1-108">The module is an invalid type.</span></span>|  
|`ValidatorModuleTypeMin`|<span data-ttu-id="3fcd1-109">最小値、`CorValidatorModuleType`列挙型。</span><span class="sxs-lookup"><span data-stu-id="3fcd1-109">The minimum value of the `CorValidatorModuleType` enum.</span></span>|  
|`ValidatorModuleTypePE`|<span data-ttu-id="3fcd1-110">モジュールは、ポータブル実行可能 (PE) ファイルです。</span><span class="sxs-lookup"><span data-stu-id="3fcd1-110">The module is a portable executable (PE) file.</span></span>|  
|`ValidatorModuleTypeObj`|<span data-ttu-id="3fcd1-111">モジュールは、.obj ファイルです。</span><span class="sxs-lookup"><span data-stu-id="3fcd1-111">The module is a .obj file.</span></span>|  
|`ValidatorModuleTypeEnc`|<span data-ttu-id="3fcd1-112">モジュールは、エディット コンティニュのデバッガー セッションです。</span><span class="sxs-lookup"><span data-stu-id="3fcd1-112">The module is an edit-and-continue debugger session.</span></span>|  
|`ValidatorModuleTypeIncr`|<span data-ttu-id="3fcd1-113">モジュールは、いずれかの段階的に構築します。</span><span class="sxs-lookup"><span data-stu-id="3fcd1-113">The module is one that has been incrementally built.</span></span>|  
|`ValidatorModuleTypeMax`|<span data-ttu-id="3fcd1-114">最大値、`CorValidatorModuleType`列挙型。</span><span class="sxs-lookup"><span data-stu-id="3fcd1-114">The maximum value of the `CorValidatorModuleType` enum.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3fcd1-115">要件</span><span class="sxs-lookup"><span data-stu-id="3fcd1-115">Requirements</span></span>  
 <span data-ttu-id="3fcd1-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3fcd1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fcd1-117">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3fcd1-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fcd1-118">**ライブラリ:** MsCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3fcd1-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3fcd1-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fcd1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fcd1-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fcd1-120">See Also</span></span>  
 [<span data-ttu-id="3fcd1-121">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="3fcd1-121">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
