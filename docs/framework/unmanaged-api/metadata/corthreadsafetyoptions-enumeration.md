---
title: CorThreadSafetyOptions 列挙型
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3407fcac420b8129dd39eabf84aec84b58651944
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442843"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="f7cd8-102">CorThreadSafetyOptions 列挙型</span><span class="sxs-lookup"><span data-stu-id="f7cd8-102">CorThreadSafetyOptions Enumeration</span></span>
<span data-ttu-id="f7cd8-103">スレッド セーフのオプションを選択するためのフラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="f7cd8-103">Specifies flags to select options for thread safety.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7cd8-104">構文</span><span class="sxs-lookup"><span data-stu-id="f7cd8-104">Syntax</span></span>  
  
```  
typedef enum CorThreadSafetyOptions {  
    MDThreadSafetyDefault       = 0x00000000,  
    MDThreadSafetyOff           = 0x00000000,  
    MDThreadSafetyOn            = 0x00000001,  
} CorThreadSafetyOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="f7cd8-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="f7cd8-105">Members</span></span>  
  
|<span data-ttu-id="f7cd8-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f7cd8-106">Member</span></span>|<span data-ttu-id="f7cd8-107">説明</span><span class="sxs-lookup"><span data-stu-id="f7cd8-107">Description</span></span>|  
|------------|-----------------|  
|`MDThreadSatetyDefault`|<span data-ttu-id="f7cd8-108">既定値です。</span><span class="sxs-lookup"><span data-stu-id="f7cd8-108">Default value.</span></span> <span data-ttu-id="f7cd8-109">`MDThreadSatetyOff` と同じ。</span><span class="sxs-lookup"><span data-stu-id="f7cd8-109">Same as `MDThreadSatetyOff`.</span></span>|  
|`MDThreadSatetyOff`|<span data-ttu-id="f7cd8-110">リーダー/ライター ロックを設定できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="f7cd8-110">Indicates that a reader/writer lock cannot be set.</span></span>|  
|`MDThreadSatetyOn`|<span data-ttu-id="f7cd8-111">リーダー/ライター ロックを設定できることを示します。</span><span class="sxs-lookup"><span data-stu-id="f7cd8-111">Indicates that a reader/writer lock can be set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7cd8-112">要件</span><span class="sxs-lookup"><span data-stu-id="f7cd8-112">Requirements</span></span>  
 <span data-ttu-id="f7cd8-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f7cd8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7cd8-114">**ヘッダー:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f7cd8-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f7cd8-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7cd8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7cd8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7cd8-116">See Also</span></span>  
 [<span data-ttu-id="f7cd8-117">メタデータ列挙型</span><span class="sxs-lookup"><span data-stu-id="f7cd8-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
