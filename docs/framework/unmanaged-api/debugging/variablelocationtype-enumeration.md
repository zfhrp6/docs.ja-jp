---
title: "VariableLocationType 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: VariableLocationType
api_location: mscordbi.dll
api_type: COM
f1_keywords: VariableLocationType
helpviewer_keywords: VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0338a89acdd9c29370bc8e52ed9a099e9330c2cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="d72de-102">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="d72de-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="d72de-103">変数のネイティブの場所の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="d72de-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d72de-104">構文</span><span class="sxs-lookup"><span data-stu-id="d72de-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="d72de-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="d72de-105">Members</span></span>  
  
|<span data-ttu-id="d72de-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d72de-106">Member</span></span>|<span data-ttu-id="d72de-107">説明</span><span class="sxs-lookup"><span data-stu-id="d72de-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="d72de-108">変数は、レジスタには。</span><span class="sxs-lookup"><span data-stu-id="d72de-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="d72de-109">変数は、レジスタの相対メモリの場所には。</span><span class="sxs-lookup"><span data-stu-id="d72de-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="d72de-110">変数は、登録または登録の相対メモリの場所に格納されません。</span><span class="sxs-lookup"><span data-stu-id="d72de-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d72de-111">コメント</span><span class="sxs-lookup"><span data-stu-id="d72de-111">Remarks</span></span>  
 <span data-ttu-id="d72de-112">メンバー、`VariableLocationType`列挙体は、によって返される、 [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="d72de-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d72de-113">要件</span><span class="sxs-lookup"><span data-stu-id="d72de-113">Requirements</span></span>  
 <span data-ttu-id="d72de-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="d72de-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d72de-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d72de-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d72de-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d72de-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d72de-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d72de-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d72de-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="d72de-118">See Also</span></span>  
 [<span data-ttu-id="d72de-119">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="d72de-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
