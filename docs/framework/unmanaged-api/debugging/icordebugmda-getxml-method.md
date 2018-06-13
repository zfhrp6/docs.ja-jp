---
title: ICorDebugMDA::GetXML メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 874462e37aa10af589f39ed099de899ff7155d24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414646"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="6006a-102">ICorDebugMDA::GetXML メソッド</span><span class="sxs-lookup"><span data-stu-id="6006a-102">ICorDebugMDA::GetXML Method</span></span>
<span data-ttu-id="6006a-103">によって表されるマネージ デバッグ アシスタント (MDA) に関連付けられているすべての XML ストリームを取得[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="6006a-103">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6006a-104">構文</span><span class="sxs-lookup"><span data-stu-id="6006a-104">Syntax</span></span>  
  
```  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6006a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6006a-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="6006a-106">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6006a-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6006a-107">[out]XML ストリームの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6006a-107">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="6006a-108">[out]XML ストリームを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="6006a-108">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="6006a-109">配列を空にすることがあります。</span><span class="sxs-lookup"><span data-stu-id="6006a-109">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6006a-110">コメント</span><span class="sxs-lookup"><span data-stu-id="6006a-110">Remarks</span></span>  
 <span data-ttu-id="6006a-111">`GetXML`メソッドことができます、関連付けられている XML ストリームのサイズに応じてパフォーマンスに影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6006a-111">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6006a-112">要件</span><span class="sxs-lookup"><span data-stu-id="6006a-112">Requirements</span></span>  
 <span data-ttu-id="6006a-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6006a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6006a-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6006a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6006a-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6006a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6006a-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6006a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6006a-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6006a-117">See Also</span></span>  
 [<span data-ttu-id="6006a-118">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6006a-118">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [<span data-ttu-id="6006a-119">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="6006a-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
