---
title: "ICorDebug::DebugActiveProcess メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.DebugActiveProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c17345caaec71e4d4b057bdcfc2cc395014cbf82
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="453b2-102">ICorDebug::DebugActiveProcess メソッド</span><span class="sxs-lookup"><span data-stu-id="453b2-102">ICorDebug::DebugActiveProcess Method</span></span>
<span data-ttu-id="453b2-103">既存のプロセスにデバッガーをアタッチします。</span><span class="sxs-lookup"><span data-stu-id="453b2-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="453b2-104">構文</span><span class="sxs-lookup"><span data-stu-id="453b2-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="453b2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="453b2-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="453b2-106">[in]デバッガーのアタッチ先となるプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="453b2-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="453b2-107">[in]ブール値に設定されている`true`デバッガーがプロセスの Win32 デバッガーとして動作する必要があります、アンマネージのコールバックのディスパッチ場合はそれ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="453b2-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="453b2-108">[out]デバッガーのアタッチするプロセスを表す"ICorDebugProcess"オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="453b2-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="453b2-109">コメント</span><span class="sxs-lookup"><span data-stu-id="453b2-109">Remarks</span></span>  
 <span data-ttu-id="453b2-110">相互運用機能デバッグは、IA 64 ベースおよび AMD64 ベースのプラットフォームなど Win9x と x86 以外のプラットフォームではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="453b2-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="453b2-111">要件</span><span class="sxs-lookup"><span data-stu-id="453b2-111">Requirements</span></span>  
 <span data-ttu-id="453b2-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="453b2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="453b2-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="453b2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="453b2-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="453b2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="453b2-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="453b2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="453b2-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="453b2-116">See Also</span></span>  
 [<span data-ttu-id="453b2-117">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="453b2-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
