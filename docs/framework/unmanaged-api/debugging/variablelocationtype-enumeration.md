---
title: "VariableLocationType 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7ea476ef32b807823108aa2836778da576618214
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="c098c-102">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="c098c-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="c098c-103">変数のネイティブの場所の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="c098c-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c098c-104">構文</span><span class="sxs-lookup"><span data-stu-id="c098c-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="c098c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c098c-105">Members</span></span>  
  
|<span data-ttu-id="c098c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c098c-106">Member</span></span>|<span data-ttu-id="c098c-107">説明</span><span class="sxs-lookup"><span data-stu-id="c098c-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="c098c-108">変数は、レジスタには。</span><span class="sxs-lookup"><span data-stu-id="c098c-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="c098c-109">変数は、レジスタの相対メモリの場所には。</span><span class="sxs-lookup"><span data-stu-id="c098c-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="c098c-110">変数は、登録または登録の相対メモリの場所に格納されません。</span><span class="sxs-lookup"><span data-stu-id="c098c-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c098c-111">コメント</span><span class="sxs-lookup"><span data-stu-id="c098c-111">Remarks</span></span>  
 <span data-ttu-id="c098c-112">メンバー、`VariableLocationType`列挙体は、によって返される、 [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c098c-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c098c-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="c098c-113">Requirements</span></span>  
 <span data-ttu-id="c098c-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c098c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c098c-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c098c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c098c-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c098c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c098c-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c098c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c098c-118">参照</span><span class="sxs-lookup"><span data-stu-id="c098c-118">See Also</span></span>  
 [<span data-ttu-id="c098c-119">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="c098c-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
