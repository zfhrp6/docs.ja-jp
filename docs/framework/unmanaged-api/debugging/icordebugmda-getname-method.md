---
title: ICorDebugMDA::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c9f76f2c3b2ecf3ac5805dea8f8243f0b74ad48
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417834"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="e9e08-102">ICorDebugMDA::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="e9e08-102">ICorDebugMDA::GetName Method</span></span>
<span data-ttu-id="e9e08-103">によって表されるマネージ デバッグ アシスタント (MDA) の名前を含む文字列を取得[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="e9e08-103">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9e08-104">構文</span><span class="sxs-lookup"><span data-stu-id="e9e08-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9e08-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e9e08-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="e9e08-106">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="e9e08-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="e9e08-107">[out]名前の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e9e08-107">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="e9e08-108">[out]名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="e9e08-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9e08-109">コメント</span><span class="sxs-lookup"><span data-stu-id="e9e08-109">Remarks</span></span>  
 <span data-ttu-id="e9e08-110">MDA 名は、一意の値です。</span><span class="sxs-lookup"><span data-stu-id="e9e08-110">MDA names are unique values.</span></span> <span data-ttu-id="e9e08-111">`GetName`メソッドは、便利な機能およびする代わりに、XML ストリームを取得するスキーマに基づいて、ストリームから名前を抽出します。</span><span class="sxs-lookup"><span data-stu-id="e9e08-111">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9e08-112">要件</span><span class="sxs-lookup"><span data-stu-id="e9e08-112">Requirements</span></span>  
 <span data-ttu-id="e9e08-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e9e08-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9e08-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9e08-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9e08-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9e08-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9e08-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9e08-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9e08-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9e08-117">See Also</span></span>  
 [<span data-ttu-id="e9e08-118">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9e08-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="e9e08-119">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="e9e08-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
