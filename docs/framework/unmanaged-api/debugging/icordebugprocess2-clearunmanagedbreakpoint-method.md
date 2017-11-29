---
title: "ICorDebugProcess2::ClearUnmanagedBreakpoint メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ca1514eaa916f5e607e49b5a5713763f855d937
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a><span data-ttu-id="c1922-102">ICorDebugProcess2::ClearUnmanagedBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="c1922-102">ICorDebugProcess2::ClearUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="c1922-103">削除前に設定した、指定されたアドレスのブレークポイント。</span><span class="sxs-lookup"><span data-stu-id="c1922-103">Removes a previously set breakpoint at the given address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1922-104">構文</span><span class="sxs-lookup"><span data-stu-id="c1922-104">Syntax</span></span>  
  
```  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1922-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c1922-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="c1922-106">[in]A`CORDB_ADDRESS`ブレークポイントが設定されたアドレスを指定する値。</span><span class="sxs-lookup"><span data-stu-id="c1922-106">[in] A `CORDB_ADDRESS` value that specifies the address at which the breakpoint was set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1922-107">コメント</span><span class="sxs-lookup"><span data-stu-id="c1922-107">Remarks</span></span>  
 <span data-ttu-id="c1922-108">指定されたブレークポイントが設定されている以前に以前の呼び出しによって[icordebugprocess 2::setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1922-108">The specified breakpoint would have been previously set by an earlier call to [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="c1922-109">`ClearUnmanagedBreakpoint`デバッグ中のプロセスの実行中に、メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c1922-109">The `ClearUnmanagedBreakpoint` method can be called while the process being debugged is running.</span></span>  
  
 <span data-ttu-id="c1922-110">`ClearUnmanagedBreakpoint`メソッドでは、マネージのみのモードで、デバッガーがアタッチされている場合、または指定したアドレスにブレークポイントが存在しない場合はエラー コードが返されます。</span><span class="sxs-lookup"><span data-stu-id="c1922-110">The `ClearUnmanagedBreakpoint` method returns a failure code if the debugger is attached in managed-only mode or if no breakpoint exists at the specified address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1922-111">要件</span><span class="sxs-lookup"><span data-stu-id="c1922-111">Requirements</span></span>  
 <span data-ttu-id="c1922-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c1922-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1922-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1922-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1922-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1922-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1922-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1922-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
