---
title: "ICorPublishProcess::GetDisplayName メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.GetDisplayName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::GetDisplayName
helpviewer_keywords:
- ICorPublishProcess::GetDisplayName method [.NET Framework debugging]
- GetDisplayName method, ICorPublishProcess interface [.NET Framework debugging]
ms.assetid: 7c0af9e9-a73f-41aa-a685-b21c439e059d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2bbaa05d767302bcd75303ec902a82e7992e1db3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessgetdisplayname-method"></a><span data-ttu-id="f5244-102">ICorPublishProcess::GetDisplayName メソッド</span><span class="sxs-lookup"><span data-stu-id="f5244-102">ICorPublishProcess::GetDisplayName Method</span></span>
<span data-ttu-id="f5244-103">これによって参照されるプロセスの実行可能ファイルの完全なパスを取得[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="f5244-103">Gets the full path of the executable for the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5244-104">構文</span><span class="sxs-lookup"><span data-stu-id="f5244-104">Syntax</span></span>  
  
```  
HRESULT GetDisplayName (  
    [in]  ULONG32                    cchName,   
    [out] ULONG32                    *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR                        *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5244-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f5244-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f5244-106">[in] `szName` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="f5244-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f5244-107">[out]返されるワイド文字の数、`szName`配列。</span><span class="sxs-lookup"><span data-stu-id="f5244-107">[out] The number of wide characters returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="f5244-108">[out]実行可能ファイルの完全パスを含む、名前を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="f5244-108">[out] An array to store the name, including the full path, of the executable.</span></span> <span data-ttu-id="f5244-109">名前は、null で終わる。</span><span class="sxs-lookup"><span data-stu-id="f5244-109">The name is null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5244-110">要件</span><span class="sxs-lookup"><span data-stu-id="f5244-110">Requirements</span></span>  
 <span data-ttu-id="f5244-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f5244-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5244-112">**ヘッダー:** CorPub.idl、CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f5244-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f5244-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5244-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5244-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5244-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5244-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5244-115">See Also</span></span>  
 [<span data-ttu-id="f5244-116">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5244-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
