---
title: ICorDebugAppDomain::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84f895e749fc8f2520dbce3caf9e6c11fda78a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405770"
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="c5582-102">ICorDebugAppDomain::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="c5582-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="c5582-103">アプリケーション ドメインの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="c5582-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5582-104">構文</span><span class="sxs-lookup"><span data-stu-id="c5582-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5582-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c5582-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c5582-106">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="c5582-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="c5582-107">この値をクエリ モードでこのメソッドを格納する 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="c5582-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c5582-108">[out]名前またはで実際に返される文字数のサイズへのポインター`szName`です。</span><span class="sxs-lookup"><span data-stu-id="c5582-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="c5582-109">クエリ モードでこの値により、バッファーのサイズを呼び出し元に名前を割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="c5582-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="c5582-110">[out]アプリケーション ドメインの名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="c5582-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5582-111">コメント</span><span class="sxs-lookup"><span data-stu-id="c5582-111">Remarks</span></span>  
 <span data-ttu-id="c5582-112">デバッガーは、`GetName`メソッドを 1 回、名前に必要なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="c5582-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="c5582-113">デバッガーはバッファーを割り当てたし、メソッドを呼び出して、再度バッファーが満杯にします。</span><span class="sxs-lookup"><span data-stu-id="c5582-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="c5582-114">最初の呼び出しで、名前のサイズを取得すると呼びます*クエリ モード*です。</span><span class="sxs-lookup"><span data-stu-id="c5582-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5582-115">要件</span><span class="sxs-lookup"><span data-stu-id="c5582-115">Requirements</span></span>  
 <span data-ttu-id="c5582-116">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c5582-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5582-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5582-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5582-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5582-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5582-119">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5582-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
