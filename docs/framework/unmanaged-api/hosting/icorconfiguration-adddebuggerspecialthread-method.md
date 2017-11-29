---
title: "ICorConfiguration::AddDebuggerSpecialThread メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.AddDebuggerSpecialThread
api_location: mscoree.dll
api_type: COM
f1_keywords: AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2501461267ff7369cd9c48f4cef6cda42063a48b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="3c088-102">ICorConfiguration::AddDebuggerSpecialThread メソッド</span><span class="sxs-lookup"><span data-stu-id="3c088-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>
<span data-ttu-id="3c088-103">デバッグ サービスを特定のスレッドがデバッガーがマネージまたはアンマネージ デバッグ シナリオの中に停止したアプリケーションの実行を続行できることを示します。</span><span class="sxs-lookup"><span data-stu-id="3c088-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c088-104">構文</span><span class="sxs-lookup"><span data-stu-id="3c088-104">Syntax</span></span>  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c088-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3c088-105">Parameters</span></span>  
 `dwSpecialThreadId`  
 <span data-ttu-id="3c088-106">[in]実行の継続を許可するか、スレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="3c088-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c088-107">コメント</span><span class="sxs-lookup"><span data-stu-id="3c088-107">Remarks</span></span>  
 <span data-ttu-id="3c088-108">指定したスレッドはことはできませんをマネージ コードを実行または任意の方法でランタイムを入力します。</span><span class="sxs-lookup"><span data-stu-id="3c088-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="3c088-109">このようなスレッドの例は、レガシ スクリプト デバッガーをサポートするために、プロセスのスレッドになります。</span><span class="sxs-lookup"><span data-stu-id="3c088-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c088-110">要件</span><span class="sxs-lookup"><span data-stu-id="3c088-110">Requirements</span></span>  
 <span data-ttu-id="3c088-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3c088-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c088-112">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3c088-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c088-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています。</span><span class="sxs-lookup"><span data-stu-id="3c088-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c088-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c088-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c088-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c088-115">See Also</span></span>  
 [<span data-ttu-id="3c088-116">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3c088-116">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
