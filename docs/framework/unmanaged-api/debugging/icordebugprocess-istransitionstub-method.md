---
title: "ICorDebugProcess::IsTransitionStub メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9fe38cf5f53c2514b845238c1d52fa12df526fdd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="504d6-102">ICorDebugProcess::IsTransitionStub メソッド</span><span class="sxs-lookup"><span data-stu-id="504d6-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="504d6-103">マネージ コードへの遷移を発生させるスタブ内にアドレスがあるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="504d6-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="504d6-104">構文</span><span class="sxs-lookup"><span data-stu-id="504d6-104">Syntax</span></span>  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="504d6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="504d6-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="504d6-106">[in]A`CORDB_ADDRESS`対象のアドレスを指定する値。</span><span class="sxs-lookup"><span data-stu-id="504d6-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="504d6-107">[out]ブール値へのポインター`true`場合は、指定したアドレスがマネージ コードへの遷移を発生させるスタブ内のそれ以外の場合 \*`pbTransitionStub`は`false`します。</span><span class="sxs-lookup"><span data-stu-id="504d6-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="504d6-108">コメント</span><span class="sxs-lookup"><span data-stu-id="504d6-108">Remarks</span></span>  
 <span data-ttu-id="504d6-109">`IsTransitionStub`をマネージ ステッパをステップ実行の制御を返すタイミングを決定するアンマネージのステップ実行のコードでメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="504d6-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="504d6-110">こともできます identity 遷移スタブ ポータブル実行可能 (PE) ファイルに情報を参照しています。</span><span class="sxs-lookup"><span data-stu-id="504d6-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="504d6-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="504d6-111">Requirements</span></span>  
 <span data-ttu-id="504d6-112">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="504d6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="504d6-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="504d6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="504d6-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="504d6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="504d6-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="504d6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
