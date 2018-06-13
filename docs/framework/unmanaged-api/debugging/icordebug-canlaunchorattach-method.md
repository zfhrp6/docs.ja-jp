---
title: ICorDebug::CanLaunchOrAttach メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f86cc83936dd8150ca6b3f28c9b6a624278e2b36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406292"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="10299-102">ICorDebug::CanLaunchOrAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="10299-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="10299-103">現在コンピューターとランタイムの構成のコンテキスト内で、新しいプロセスの起動または指定した既存のプロセスへのアタッチを実行するかどうかを示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="10299-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10299-104">構文</span><span class="sxs-lookup"><span data-stu-id="10299-104">Syntax</span></span>  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10299-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="10299-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="10299-106">[in]既存のプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="10299-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="10299-107">[in]渡す`true`Win32 デバッグを有効にするを起動しようとしています。 または、Win32 デバッグを有効になっている、それ以外を使用して接続を渡す場合`false`です。</span><span class="sxs-lookup"><span data-stu-id="10299-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10299-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="10299-108">Return Value</span></span>  
 <span data-ttu-id="10299-109">デバッグ サービスを決定する、新しいプロセスの起動または特定のプロセスにアタッチする場合は S_OK は、現在のコンピューターとランタイムの構成に関する情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="10299-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="10299-110">HRESULT 値をとります。</span><span class="sxs-lookup"><span data-stu-id="10299-110">Possible HRESULT values are:</span></span>  
  
-   <span data-ttu-id="10299-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="10299-111">S_OK</span></span>  
  
-   <span data-ttu-id="10299-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="10299-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
-   <span data-ttu-id="10299-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="10299-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
-   <span data-ttu-id="10299-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="10299-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10299-115">コメント</span><span class="sxs-lookup"><span data-stu-id="10299-115">Remarks</span></span>  
 <span data-ttu-id="10299-116">このメソッドは、純粋な情報です。</span><span class="sxs-lookup"><span data-stu-id="10299-116">This method is purely informational.</span></span> <span data-ttu-id="10299-117">インターフェイスはありません停止するを起動するかによって返される値に関係なく、プロセスへのアタッチ`CanLaunchOrAttach`です。</span><span class="sxs-lookup"><span data-stu-id="10299-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="10299-118">Win32 デバッグを有効に起動または attach Win32 デバッグを有効になっていると、パスにする場合`true`の`win32DebuggingEnabled`します。</span><span class="sxs-lookup"><span data-stu-id="10299-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="10299-119">によって返される HRESULT`CanLaunchOrAttach`は、このオプションを使用する場合に異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="10299-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10299-120">要件</span><span class="sxs-lookup"><span data-stu-id="10299-120">Requirements</span></span>  
 <span data-ttu-id="10299-121">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="10299-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10299-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10299-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10299-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10299-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10299-124">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10299-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10299-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="10299-125">See Also</span></span>  
 [<span data-ttu-id="10299-126">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10299-126">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
