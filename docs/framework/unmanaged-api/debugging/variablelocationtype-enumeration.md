---
title: VariableLocationType 列挙型
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cc7a299e6be328095c0368acf0a4b767fb74d01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423950"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="e5158-102">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="e5158-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="e5158-103">変数のネイティブの場所の種類を示します。</span><span class="sxs-lookup"><span data-stu-id="e5158-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5158-104">構文</span><span class="sxs-lookup"><span data-stu-id="e5158-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="e5158-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="e5158-105">Members</span></span>  
  
|<span data-ttu-id="e5158-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e5158-106">Member</span></span>|<span data-ttu-id="e5158-107">説明</span><span class="sxs-lookup"><span data-stu-id="e5158-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="e5158-108">変数は、レジスタには。</span><span class="sxs-lookup"><span data-stu-id="e5158-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="e5158-109">変数は、レジスタの相対メモリの場所には。</span><span class="sxs-lookup"><span data-stu-id="e5158-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="e5158-110">変数は、登録または登録の相対メモリの場所に格納されません。</span><span class="sxs-lookup"><span data-stu-id="e5158-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5158-111">コメント</span><span class="sxs-lookup"><span data-stu-id="e5158-111">Remarks</span></span>  
 <span data-ttu-id="e5158-112">メンバー、`VariableLocationType`列挙体は、によって返される、 [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="e5158-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5158-113">要件</span><span class="sxs-lookup"><span data-stu-id="e5158-113">Requirements</span></span>  
 <span data-ttu-id="e5158-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e5158-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5158-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5158-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5158-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5158-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5158-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5158-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5158-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5158-118">See Also</span></span>  
 [<span data-ttu-id="e5158-119">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="e5158-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
