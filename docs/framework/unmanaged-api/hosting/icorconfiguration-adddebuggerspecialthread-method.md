---
title: ICorConfiguration::AddDebuggerSpecialThread メソッド
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59b940c0dbe9462dda513e933b7360ff55a9b447
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437350"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="767bc-102">ICorConfiguration::AddDebuggerSpecialThread メソッド</span><span class="sxs-lookup"><span data-stu-id="767bc-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="767bc-103">デバッグ サービスを特定のスレッドがデバッガーがマネージまたはアンマネージ デバッグ シナリオの中に停止したアプリケーションの実行を続行できることを示します。</span><span class="sxs-lookup"><span data-stu-id="767bc-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="767bc-104">構文</span><span class="sxs-lookup"><span data-stu-id="767bc-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="767bc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="767bc-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="767bc-106">[in]実行の継続を許可するか、スレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="767bc-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="767bc-107">コメント</span><span class="sxs-lookup"><span data-stu-id="767bc-107">Remarks</span></span>  
 <span data-ttu-id="767bc-108">指定したスレッドはことはできませんをマネージ コードを実行または任意の方法でランタイムを入力します。</span><span class="sxs-lookup"><span data-stu-id="767bc-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="767bc-109">このようなスレッドの例は、レガシ スクリプト デバッガーをサポートするために、プロセスのスレッドになります。</span><span class="sxs-lookup"><span data-stu-id="767bc-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="767bc-110">要件</span><span class="sxs-lookup"><span data-stu-id="767bc-110">Requirements</span></span>  
 <span data-ttu-id="767bc-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="767bc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="767bc-112">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="767bc-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="767bc-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="767bc-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="767bc-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="767bc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="767bc-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="767bc-115">See Also</span></span>  
 [<span data-ttu-id="767bc-116">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="767bc-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
