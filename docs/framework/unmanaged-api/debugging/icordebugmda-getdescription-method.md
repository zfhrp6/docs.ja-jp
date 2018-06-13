---
title: ICorDebugMDA::GetDescription メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2fdace527194228dd6004a991950a80d23275650
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413297"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="5c0d3-102">ICorDebugMDA::GetDescription メソッド</span><span class="sxs-lookup"><span data-stu-id="5c0d3-102">ICorDebugMDA::GetDescription Method</span></span>
<span data-ttu-id="5c0d3-103">によって表されるマネージ デバッグ アシスタント (MDA) の説明を含む文字列を取得[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c0d3-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c0d3-104">構文</span><span class="sxs-lookup"><span data-stu-id="5c0d3-104">Syntax</span></span>  
  
```  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c0d3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5c0d3-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="5c0d3-106">[in]説明を格納する文字列バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="5c0d3-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5c0d3-107">[out]文字列バッファーに返されるバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5c0d3-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="5c0d3-108">[out]MDA の説明を含む文字列バッファー。</span><span class="sxs-lookup"><span data-stu-id="5c0d3-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c0d3-109">コメント</span><span class="sxs-lookup"><span data-stu-id="5c0d3-109">Remarks</span></span>  
 <span data-ttu-id="5c0d3-110">文字列は長さ 0 を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5c0d3-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c0d3-111">要件</span><span class="sxs-lookup"><span data-stu-id="5c0d3-111">Requirements</span></span>  
 <span data-ttu-id="5c0d3-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c0d3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c0d3-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c0d3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c0d3-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c0d3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c0d3-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c0d3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c0d3-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c0d3-116">See Also</span></span>  
 [<span data-ttu-id="5c0d3-117">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c0d3-117">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="5c0d3-118">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="5c0d3-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
