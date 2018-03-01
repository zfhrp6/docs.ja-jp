---
title: "ICorDebugProcess2::GetDesiredNGENCompilerFlags メソッド"
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
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7306174f6c60d814474d7f142da49a2a4013f19b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="694f5-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="694f5-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="694f5-103">現在のコンパイラ、共通言語ランタイム (CLR) がプリコンパイル済み正しい選択に使用するフラグの設定を取得 (つまり、ネイティブ) イメージが、このプロセスに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="694f5-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="694f5-104">構文</span><span class="sxs-lookup"><span data-stu-id="694f5-104">Syntax</span></span>  
  
```  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="694f5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="694f5-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="694f5-106">[out]ビットごとの組み合わせへのポインター、 [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)ロードする適切なプリコンパイル済みイメージの選択に使用する列挙値。</span><span class="sxs-lookup"><span data-stu-id="694f5-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="694f5-107">コメント</span><span class="sxs-lookup"><span data-stu-id="694f5-107">Remarks</span></span>  
 <span data-ttu-id="694f5-108">使用して、 [icordebugprocess 2::setdesiredngencompilerflags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md)を読み込む正しいコンパイル済みのイメージを選択して、CLR が使用するフラグを設定します。</span><span class="sxs-lookup"><span data-stu-id="694f5-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="694f5-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="694f5-109">Requirements</span></span>  
 <span data-ttu-id="694f5-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="694f5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="694f5-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="694f5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="694f5-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="694f5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="694f5-113">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="694f5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
