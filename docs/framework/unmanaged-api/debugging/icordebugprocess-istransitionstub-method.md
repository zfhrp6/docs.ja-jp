---
title: ICorDebugProcess::IsTransitionStub メソッド
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e06dc35998a2874ed1d2f76725078874817e94d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420096"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="4a01b-102">ICorDebugProcess::IsTransitionStub メソッド</span><span class="sxs-lookup"><span data-stu-id="4a01b-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="4a01b-103">マネージ コードへの遷移を発生させるスタブ内にアドレスがあるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4a01b-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a01b-104">構文</span><span class="sxs-lookup"><span data-stu-id="4a01b-104">Syntax</span></span>  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a01b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4a01b-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="4a01b-106">[in]A`CORDB_ADDRESS`対象のアドレスを指定する値。</span><span class="sxs-lookup"><span data-stu-id="4a01b-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="4a01b-107">[out]ブール値へのポインター`true`場合は、指定したアドレスがマネージ コードへの遷移を発生させるスタブ内のそれ以外の場合 \*`pbTransitionStub`は`false`します。</span><span class="sxs-lookup"><span data-stu-id="4a01b-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a01b-108">コメント</span><span class="sxs-lookup"><span data-stu-id="4a01b-108">Remarks</span></span>  
 <span data-ttu-id="4a01b-109">`IsTransitionStub`をマネージ ステッパをステップ実行の制御を返すタイミングを決定するアンマネージのステップ実行のコードでメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4a01b-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="4a01b-110">こともできます identity 遷移スタブ ポータブル実行可能 (PE) ファイルに情報を参照しています。</span><span class="sxs-lookup"><span data-stu-id="4a01b-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a01b-111">要件</span><span class="sxs-lookup"><span data-stu-id="4a01b-111">Requirements</span></span>  
 <span data-ttu-id="4a01b-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4a01b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a01b-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a01b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a01b-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a01b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a01b-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a01b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
