---
title: ICorDebugThread2::GetActiveFunctions メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7ed7787f0302826cab67664780177f05e551199
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421107"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="90eb3-102">ICorDebugThread2::GetActiveFunctions メソッド</span><span class="sxs-lookup"><span data-stu-id="90eb3-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="90eb3-103">このスレッドのフレームのそれぞれに、アクティブな関数に関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="90eb3-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90eb3-104">構文</span><span class="sxs-lookup"><span data-stu-id="90eb3-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90eb3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="90eb3-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="90eb3-106">[in] `pFunctions` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="90eb3-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="90eb3-107">[out]返されたオブジェクトの数へのポインター、`pFunctions`配列。</span><span class="sxs-lookup"><span data-stu-id="90eb3-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="90eb3-108">返されるオブジェクトの数は、スタック上のマネージ フレームの数と等しくなります。</span><span class="sxs-lookup"><span data-stu-id="90eb3-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="90eb3-109">[入力、出力].このスレッドのフレームでアクティブな関数についての情報を含む各 COR_ACTIVE_FUNCTION オブジェクトの配列。</span><span class="sxs-lookup"><span data-stu-id="90eb3-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="90eb3-110">最初の要素は、リーフ フレームとスタックのルートまでさかのぼりますに使用されます。</span><span class="sxs-lookup"><span data-stu-id="90eb3-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90eb3-111">コメント</span><span class="sxs-lookup"><span data-stu-id="90eb3-111">Remarks</span></span>  
 <span data-ttu-id="90eb3-112">場合`pFunctions`が入力で null`GetActiveFunctions`はスタック上にある関数の数のみを返します。</span><span class="sxs-lookup"><span data-stu-id="90eb3-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="90eb3-113">つまり場合、`pFunctions`が入力で null`GetActiveFunctions`値を返しますでのみ`pcFunctions`です。</span><span class="sxs-lookup"><span data-stu-id="90eb3-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="90eb3-114">`GetActiveFunctions`メソッドは最適化の手法として、スタック トレースでのフレームから同じ情報を取得経由でありがありました ICorDebugILFrame オブジェクトに完全なスタック トレースでのフレームのみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="90eb3-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90eb3-115">要件</span><span class="sxs-lookup"><span data-stu-id="90eb3-115">Requirements</span></span>  
 <span data-ttu-id="90eb3-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="90eb3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90eb3-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90eb3-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90eb3-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90eb3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90eb3-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90eb3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
