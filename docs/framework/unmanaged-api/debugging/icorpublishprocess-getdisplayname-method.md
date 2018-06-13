---
title: ICorPublishProcess::GetDisplayName メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetDisplayName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 815f2e2f695837c973210a21ab3631ef307c23d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423638"
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="f44b2-102">ICorPublishProcess::GetDisplayName メソッド</span><span class="sxs-lookup"><span data-stu-id="f44b2-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="f44b2-103">これによって参照されるプロセスの実行可能ファイルの完全なパスを取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="f44b2-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f44b2-104">構文</span><span class="sxs-lookup"><span data-stu-id="f44b2-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f44b2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f44b2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f44b2-106">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="f44b2-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f44b2-107">[out]返されるワイド文字の数、`szName`配列。</span><span class="sxs-lookup"><span data-stu-id="f44b2-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="f44b2-108">[out]実行可能ファイルの完全パスを含む、名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="f44b2-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="f44b2-109">名前は、null で終わる。</span><span class="sxs-lookup"><span data-stu-id="f44b2-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f44b2-110">要件</span><span class="sxs-lookup"><span data-stu-id="f44b2-110">Requirements</span></span>  
 <span data-ttu-id="f44b2-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f44b2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f44b2-112">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f44b2-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f44b2-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f44b2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f44b2-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f44b2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f44b2-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f44b2-115">See Also</span></span>  
 [<span data-ttu-id="f44b2-116">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f44b2-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
