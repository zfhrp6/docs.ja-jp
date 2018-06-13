---
title: ICorDebugStringValue::GetString メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63d3df561a3b48a4b26426235455ef1a074512f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417967"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="393e5-102">ICorDebugStringValue::GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="393e5-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="393e5-103">この ICorDebugStringValue によって参照される文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="393e5-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="393e5-104">構文</span><span class="sxs-lookup"><span data-stu-id="393e5-104">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]   
        WCHAR       szString[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="393e5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="393e5-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="393e5-106">[in] `szString` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="393e5-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="393e5-107">[out]返される文字数へのポインター、`szString`配列。</span><span class="sxs-lookup"><span data-stu-id="393e5-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="393e5-108">[out]取得した文字列を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="393e5-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="393e5-109">要件</span><span class="sxs-lookup"><span data-stu-id="393e5-109">Requirements</span></span>  
 <span data-ttu-id="393e5-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="393e5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="393e5-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="393e5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="393e5-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="393e5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="393e5-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="393e5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
