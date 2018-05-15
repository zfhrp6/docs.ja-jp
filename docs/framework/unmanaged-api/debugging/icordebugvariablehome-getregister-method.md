---
title: ICorDebugVariableHome::GetRegister メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e06c98067fea9368ac8f750d9187636d2ca9a8c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="b2f94-102">ICorDebugVariableHome::GetRegister メソッド</span><span class="sxs-lookup"><span data-stu-id="b2f94-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="b2f94-103">場所の種類を持つ変数を格納するレジスタを取得`VLT_REGISTER`、およびロケーションの型の変数のベース レジスタ`VLT_REGISTER_RELATIVE`です。</span><span class="sxs-lookup"><span data-stu-id="b2f94-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2f94-104">構文</span><span class="sxs-lookup"><span data-stu-id="b2f94-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2f94-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b2f94-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="b2f94-106">[out]CorDebugRegister 列挙値の場所の種類を持つ変数のレジスタを示す`VLT_REGISTER`、およびロケーションの型の変数のベース レジスタ`VLT_REGISTER_RELATIVE`です。</span><span class="sxs-lookup"><span data-stu-id="b2f94-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2f94-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="b2f94-107">Return Value</span></span>  
 <span data-ttu-id="b2f94-108">メソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="b2f94-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="b2f94-109">[値]</span><span class="sxs-lookup"><span data-stu-id="b2f94-109">Value</span></span>|<span data-ttu-id="b2f94-110">説明</span><span class="sxs-lookup"><span data-stu-id="b2f94-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="b2f94-111">によって示されるレジスタには、変数、`pRegister`引数。</span><span class="sxs-lookup"><span data-stu-id="b2f94-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="b2f94-112">変数は、レジスタまたはレジスタの相対位置ではありません。</span><span class="sxs-lookup"><span data-stu-id="b2f94-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2f94-113">要件</span><span class="sxs-lookup"><span data-stu-id="b2f94-113">Requirements</span></span>  
 <span data-ttu-id="b2f94-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="b2f94-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2f94-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2f94-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2f94-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2f94-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2f94-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2f94-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2f94-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2f94-118">See Also</span></span>  
 [<span data-ttu-id="b2f94-119">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="b2f94-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [<span data-ttu-id="b2f94-120">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b2f94-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
