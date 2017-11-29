---
title: "CorDebugIlToNativeMappingTypes 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugIlToNativeMappingTypes
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugIlToNativeMappingTypes
helpviewer_keywords: CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03046ebb678df64ad3d151aaadba313645417979
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="f1a3a-102">CorDebugIlToNativeMappingTypes 列挙型</span><span class="sxs-lookup"><span data-stu-id="f1a3a-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="f1a3a-103">COR_DEBUG_IL_TO_NATIVE_MAP 構造体のインスタンスによって表されるネイティブの命令の特定の範囲が特別なコード領域に対応するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="f1a3a-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1a3a-104">構文</span><span class="sxs-lookup"><span data-stu-id="f1a3a-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="f1a3a-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="f1a3a-105">Members</span></span>  
  
|<span data-ttu-id="f1a3a-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f1a3a-106">Member</span></span>|<span data-ttu-id="f1a3a-107">説明</span><span class="sxs-lookup"><span data-stu-id="f1a3a-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="f1a3a-108">特別なコード領域には、ネイティブ命令の範囲は対応していません。</span><span class="sxs-lookup"><span data-stu-id="f1a3a-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="f1a3a-109">ネイティブ命令の範囲は、プロローグに対応します。</span><span class="sxs-lookup"><span data-stu-id="f1a3a-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="f1a3a-110">ネイティブ命令の範囲は、エピローグに対応します。</span><span class="sxs-lookup"><span data-stu-id="f1a3a-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1a3a-111">要件</span><span class="sxs-lookup"><span data-stu-id="f1a3a-111">Requirements</span></span>  
 <span data-ttu-id="f1a3a-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f1a3a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1a3a-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1a3a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1a3a-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1a3a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1a3a-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1a3a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a3a-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1a3a-116">See Also</span></span>  
 [<span data-ttu-id="f1a3a-117">GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="f1a3a-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)  
 [<span data-ttu-id="f1a3a-118">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="f1a3a-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
