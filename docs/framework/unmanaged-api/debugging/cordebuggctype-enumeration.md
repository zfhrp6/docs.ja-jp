---
title: CorDebugGCType 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugGCType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGCType
helpviewer_keywords:
- CorDebugGCType enumeration [.NET Framework debugging]
ms.assetid: 880ca92a-42d4-42a5-9b9c-c2848eb39c6a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e74f564a483d80fd6312cf015802750d48e73ca7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403995"
---
# <a name="cordebuggctype-enumeration"></a><span data-ttu-id="1c8b8-102">CorDebugGCType 列挙型</span><span class="sxs-lookup"><span data-stu-id="1c8b8-102">CorDebugGCType Enumeration</span></span>
<span data-ttu-id="1c8b8-103">ガベージ コレクターがワークステーションまたはサーバーのどちらで実行されているかを示します。</span><span class="sxs-lookup"><span data-stu-id="1c8b8-103">Indicates whether the garbage collector is running on a workstation or a server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c8b8-104">構文</span><span class="sxs-lookup"><span data-stu-id="1c8b8-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGCType {  
    CorDebugWorkstationGC  = 0,  
    CorDebugServerGC       = ( CorDebugWorkstationGC + 1 )  
} CorDebugGCType;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c8b8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1c8b8-105">Parameters</span></span>  
  
## <a name="members"></a><span data-ttu-id="1c8b8-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1c8b8-106">Members</span></span>  
  
|<span data-ttu-id="1c8b8-107">メンバー名</span><span class="sxs-lookup"><span data-stu-id="1c8b8-107">Member name</span></span>|<span data-ttu-id="1c8b8-108">説明</span><span class="sxs-lookup"><span data-stu-id="1c8b8-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebugWorkstationGC`|<span data-ttu-id="1c8b8-109">ガベージ コレクターは、ワークステーション上で実行されています。</span><span class="sxs-lookup"><span data-stu-id="1c8b8-109">The garbage collector is running on a workstation.</span></span>|  
|`CorDebugServerGC`|<span data-ttu-id="1c8b8-110">ガベージ コレクターは、サーバーで実行します。</span><span class="sxs-lookup"><span data-stu-id="1c8b8-110">The garbage collector is running on a server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c8b8-111">コメント</span><span class="sxs-lookup"><span data-stu-id="1c8b8-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c8b8-112">要件</span><span class="sxs-lookup"><span data-stu-id="1c8b8-112">Requirements</span></span>  
 <span data-ttu-id="1c8b8-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1c8b8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c8b8-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1c8b8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1c8b8-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c8b8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c8b8-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c8b8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c8b8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="1c8b8-117">See Also</span></span>  
 [<span data-ttu-id="1c8b8-118">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="1c8b8-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
