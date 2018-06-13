---
title: ICorDebugAssembly2::IsFullyTrusted メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 895c8bc7b550fd063a9215c60f10f183e24bac83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402953"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="74f0a-102">ICorDebugAssembly2::IsFullyTrusted メソッド</span><span class="sxs-lookup"><span data-stu-id="74f0a-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>
<span data-ttu-id="74f0a-103">かどうか、アセンブリで許可されている完全な信頼ランタイムのセキュリティ システムを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="74f0a-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74f0a-104">構文</span><span class="sxs-lookup"><span data-stu-id="74f0a-104">Syntax</span></span>  
  
```  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74f0a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="74f0a-105">Parameters</span></span>  
 `pbFullyTrusted`  
 <span data-ttu-id="74f0a-106">[out]`true`場合は、アセンブリで許可されている完全な信頼ランタイムのセキュリティ システムです。 それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="74f0a-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74f0a-107">コメント</span><span class="sxs-lookup"><span data-stu-id="74f0a-107">Remarks</span></span>  
 <span data-ttu-id="74f0a-108">このメソッドは、HRESULT の CORDBG_E_NOTREADY アセンブリのセキュリティ ポリシーまだ解決されていません、つまり、コードが見つからない、アセンブリ内の場合はまだ実行されているを返します。</span><span class="sxs-lookup"><span data-stu-id="74f0a-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74f0a-109">要件</span><span class="sxs-lookup"><span data-stu-id="74f0a-109">Requirements</span></span>  
 <span data-ttu-id="74f0a-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="74f0a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74f0a-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74f0a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74f0a-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74f0a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74f0a-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74f0a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
