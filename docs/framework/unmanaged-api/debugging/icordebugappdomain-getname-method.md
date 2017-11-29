---
title: "ICorDebugAppDomain::GetName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 590bfb5d7d8cac8e322bddfe6258ad9bf377dad6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomaingetname-method"></a><span data-ttu-id="88699-102">ICorDebugAppDomain::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="88699-102">ICorDebugAppDomain::GetName Method</span></span>
<span data-ttu-id="88699-103">アプリケーション ドメインの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="88699-103">Gets the name of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88699-104">構文</span><span class="sxs-lookup"><span data-stu-id="88699-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="88699-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="88699-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="88699-106">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="88699-106">[in] The size of the `szName` array.</span></span> <span data-ttu-id="88699-107">この値をクエリ モードでこのメソッドを格納する 0 に設定します。</span><span class="sxs-lookup"><span data-stu-id="88699-107">Set this value to zero to put this method in query mode.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="88699-108">[out]名前またはで実際に返される文字数のサイズへのポインター`szName`です。</span><span class="sxs-lookup"><span data-stu-id="88699-108">[out] A pointer to the size of the name or the number of characters actually returned in `szName`.</span></span> <span data-ttu-id="88699-109">クエリ モードでこの値により、バッファーのサイズを呼び出し元に名前を割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="88699-109">In query mode, this value lets the caller know how large a buffer to allocate for the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="88699-110">[out]アプリケーション ドメインの名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="88699-110">[out] An array that stores the name of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88699-111">コメント</span><span class="sxs-lookup"><span data-stu-id="88699-111">Remarks</span></span>  
 <span data-ttu-id="88699-112">デバッガーは、`GetName`メソッドを 1 回、名前に必要なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="88699-112">A debugger calls the `GetName` method once to get the size of a buffer needed for the name.</span></span> <span data-ttu-id="88699-113">デバッガーはバッファーを割り当てたし、メソッドを呼び出して、再度バッファーが満杯にします。</span><span class="sxs-lookup"><span data-stu-id="88699-113">The debugger allocates the buffer, and then calls the method a second time to fill the buffer.</span></span> <span data-ttu-id="88699-114">最初の呼び出しで、名前のサイズを取得すると呼びます*クエリ モード*です。</span><span class="sxs-lookup"><span data-stu-id="88699-114">The first call, to get the size of the name, is referred to as *query mode*.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88699-115">要件</span><span class="sxs-lookup"><span data-stu-id="88699-115">Requirements</span></span>  
 <span data-ttu-id="88699-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="88699-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88699-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88699-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88699-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88699-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88699-119">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88699-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
