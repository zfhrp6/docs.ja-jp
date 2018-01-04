---
title: "CorThreadSafetyOptions 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorThreadSafetyOptions
api_location: mscoree.dll
api_type: COM
f1_keywords: CorThreadSafetyOptions
helpviewer_keywords: CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e017732882841e1cb2b5f00b1c51e22bba11ae73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="dd683-102">CorThreadSafetyOptions 列挙型</span><span class="sxs-lookup"><span data-stu-id="dd683-102">CorThreadSafetyOptions Enumeration</span></span>
<span data-ttu-id="dd683-103">スレッド セーフのオプションを選択するためのフラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="dd683-103">Specifies flags to select options for thread safety.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd683-104">構文</span><span class="sxs-lookup"><span data-stu-id="dd683-104">Syntax</span></span>  
  
```  
typedef enum CorThreadSafetyOptions {  
    MDThreadSafetyDefault       = 0x00000000,  
    MDThreadSafetyOff           = 0x00000000,  
    MDThreadSafetyOn            = 0x00000001,  
} CorThreadSafetyOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="dd683-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="dd683-105">Members</span></span>  
  
|<span data-ttu-id="dd683-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="dd683-106">Member</span></span>|<span data-ttu-id="dd683-107">説明</span><span class="sxs-lookup"><span data-stu-id="dd683-107">Description</span></span>|  
|------------|-----------------|  
|`MDThreadSatetyDefault`|<span data-ttu-id="dd683-108">既定値です。</span><span class="sxs-lookup"><span data-stu-id="dd683-108">Default value.</span></span> <span data-ttu-id="dd683-109">`MDThreadSatetyOff` と同じ。</span><span class="sxs-lookup"><span data-stu-id="dd683-109">Same as `MDThreadSatetyOff`.</span></span>|  
|`MDThreadSatetyOff`|<span data-ttu-id="dd683-110">リーダー/ライター ロックを設定できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="dd683-110">Indicates that a reader/writer lock cannot be set.</span></span>|  
|`MDThreadSatetyOn`|<span data-ttu-id="dd683-111">リーダー/ライター ロックを設定できることを示します。</span><span class="sxs-lookup"><span data-stu-id="dd683-111">Indicates that a reader/writer lock can be set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd683-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="dd683-112">Requirements</span></span>  
 <span data-ttu-id="dd683-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dd683-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd683-114">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="dd683-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="dd683-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd683-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd683-116">参照</span><span class="sxs-lookup"><span data-stu-id="dd683-116">See Also</span></span>  
 [<span data-ttu-id="dd683-117">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="dd683-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
