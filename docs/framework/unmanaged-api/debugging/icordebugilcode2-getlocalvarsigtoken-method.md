---
title: ICorDebugILCode2::GetLocalVarSigToken メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetLocalVarSigToken
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e02f44e4f581170a842a1c103ed069cb90cde79c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412299"
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="68e81-102">ICorDebugILCode2::GetLocalVarSigToken メソッド</span><span class="sxs-lookup"><span data-stu-id="68e81-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="68e81-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="68e81-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="68e81-104">このインスタンスで示される関数について、ローカル変数のシグネチャのメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="68e81-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68e81-105">構文</span><span class="sxs-lookup"><span data-stu-id="68e81-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68e81-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="68e81-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="68e81-107">[out] この機能のローカル変数シグネチャの `mdSignature` トークンへのポインター、またはシグネチャがない場合 (つまり、機能にローカル変数がない場合) は `mdSignatureNil`。</span><span class="sxs-lookup"><span data-stu-id="68e81-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68e81-108">コメント</span><span class="sxs-lookup"><span data-stu-id="68e81-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68e81-109">要件</span><span class="sxs-lookup"><span data-stu-id="68e81-109">Requirements</span></span>  
 <span data-ttu-id="68e81-110">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="68e81-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68e81-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68e81-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68e81-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68e81-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68e81-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68e81-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e81-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="68e81-114">See Also</span></span>  
 [<span data-ttu-id="68e81-115">ICorDebugILCode2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="68e81-115">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [<span data-ttu-id="68e81-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="68e81-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
