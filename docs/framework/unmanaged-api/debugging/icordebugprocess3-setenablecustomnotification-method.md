---
title: ICorDebugProcess3::SetEnableCustomNotification メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a84061cff7cc5dbdeba1e0e66396e04a8f345cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423157"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="bb778-102">ICorDebugProcess3::SetEnableCustomNotification メソッド</span><span class="sxs-lookup"><span data-stu-id="bb778-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="bb778-103">有効にし、指定した型のカスタムのデバッガー通知を無効にします。</span><span class="sxs-lookup"><span data-stu-id="bb778-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb778-104">構文</span><span class="sxs-lookup"><span data-stu-id="bb778-104">Syntax</span></span>  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb778-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bb778-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="bb778-106">[in]カスタムのデバッガー通知を指定する型。</span><span class="sxs-lookup"><span data-stu-id="bb778-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="bb778-107">[in]`true` ; カスタムのデバッガー通知を有効にするには`false`通知を無効にします。</span><span class="sxs-lookup"><span data-stu-id="bb778-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="bb778-108">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="bb778-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb778-109">コメント</span><span class="sxs-lookup"><span data-stu-id="bb778-109">Remarks</span></span>  
 <span data-ttu-id="bb778-110">ときに`fEnable`に設定されている`true`への呼び出し、<xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType>メソッド トリガー、 [icordebugmanagedcallback 3::customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)コールバック。</span><span class="sxs-lookup"><span data-stu-id="bb778-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="bb778-111">既定では通知が無効になっていますしたがって、デバッガーは、通知の種類が認識しを処理する必要があるを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb778-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="bb778-112">[ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)クラスのスコープのアプリケーション ドメインで、デバッガーを呼び出す必要があります`SetEnableCustomNotification`プロセス全体で通知を受信する必要がある場合、プロセスでのアプリケーション ドメインごとにします。</span><span class="sxs-lookup"><span data-stu-id="bb778-112">Because the [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="bb778-113">以降で、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]では、サポートされている通知は、スレッド間の依存関係の通知のみです。</span><span class="sxs-lookup"><span data-stu-id="bb778-113">Starting with the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb778-114">要件</span><span class="sxs-lookup"><span data-stu-id="bb778-114">Requirements</span></span>  
 <span data-ttu-id="bb778-115">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="bb778-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb778-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb778-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb778-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb778-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb778-118">**.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb778-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb778-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb778-119">See Also</span></span>  
 [<span data-ttu-id="bb778-120">ICorDebugProcess3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb778-120">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 [<span data-ttu-id="bb778-121">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb778-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="bb778-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="bb778-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
