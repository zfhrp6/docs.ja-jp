---
title: ICorDebugModule::EnableJITDebugging メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71722293bfb80a7e57393916560f922d970ea2ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415643"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a><span data-ttu-id="f857e-102">ICorDebugModule::EnableJITDebugging メソッド</span><span class="sxs-lookup"><span data-stu-id="f857e-102">ICorDebugModule::EnableJITDebugging Method</span></span>
<span data-ttu-id="f857e-103">・ イン タイム (JIT) コンパイラがこのモジュール内でメソッドのデバッグ情報を保持するかどうかを制御します。</span><span class="sxs-lookup"><span data-stu-id="f857e-103">Controls whether the just-in-time (JIT) compiler preserves debugging information for methods within this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f857e-104">構文</span><span class="sxs-lookup"><span data-stu-id="f857e-104">Syntax</span></span>  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f857e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f857e-105">Parameters</span></span>  
 `bTrackJITInfo`  
 <span data-ttu-id="f857e-106">[in]この値を設定`true`Microsoft intermediate language (MSIL) のバージョンと、このモジュールの各メソッドの JIT コンパイルされたバージョン間のマッピング情報を保持するために JIT コンパイラを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f857e-106">[in] Set this value to `true` to enable the JIT compiler to preserve mapping information between the Microsoft intermediate language (MSIL) version and the JIT-compiled version of each method in this module.</span></span>  
  
 `bAllowJitOpts`  
 <span data-ttu-id="f857e-107">[in]この値を設定`true`デバッグの特定の特定の JIT 最適化とコードを生成する、JIT コンパイラを有効にします。</span><span class="sxs-lookup"><span data-stu-id="f857e-107">[in] Set this value to `true` to enable the JIT compiler to generate code with certain JIT-specific optimizations for debugging.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f857e-108">コメント</span><span class="sxs-lookup"><span data-stu-id="f857e-108">Remarks</span></span>  
 <span data-ttu-id="f857e-109">既定では、デバッガーがアクティブなときに読み込まれるすべてのモジュールの JIT デバッグが有効になっています。</span><span class="sxs-lookup"><span data-stu-id="f857e-109">JIT debugging is enabled by default for all modules that are loaded when the debugger is active.</span></span> <span data-ttu-id="f857e-110">プログラムによって有効化または、設定を無効にすると、グローバル設定を上書きします。</span><span class="sxs-lookup"><span data-stu-id="f857e-110">Programmatically enabling or disabling the settings overrides global settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f857e-111">要件</span><span class="sxs-lookup"><span data-stu-id="f857e-111">Requirements</span></span>  
 <span data-ttu-id="f857e-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f857e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f857e-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f857e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f857e-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f857e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f857e-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f857e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
