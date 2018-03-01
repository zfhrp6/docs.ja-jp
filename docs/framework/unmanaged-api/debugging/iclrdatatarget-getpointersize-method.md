---
title: "ICLRDataTarget::GetPointerSize メソッド"
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
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ca35246b82ed4adc982b6e7b157398d230dabe4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="2bd03-102">ICLRDataTarget::GetPointerSize メソッド</span><span class="sxs-lookup"><span data-stu-id="2bd03-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="2bd03-103">ターゲット プロセスが使用するポインター型のバイト単位のサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="2bd03-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="2bd03-104">このメソッドは、共通言語ランタイム データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2bd03-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bd03-105">構文</span><span class="sxs-lookup"><span data-stu-id="2bd03-105">Syntax</span></span>  
  
```  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2bd03-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2bd03-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="2bd03-107">[out]ターゲット プロセスのポインターのバイト単位のサイズを指定する整数値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="2bd03-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bd03-108">コメント</span><span class="sxs-lookup"><span data-stu-id="2bd03-108">Remarks</span></span>  
 <span data-ttu-id="2bd03-109">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="2bd03-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bd03-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="2bd03-110">Requirements</span></span>  
 <span data-ttu-id="2bd03-111">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2bd03-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bd03-112">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2bd03-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2bd03-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bd03-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bd03-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bd03-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd03-115">参照</span><span class="sxs-lookup"><span data-stu-id="2bd03-115">See Also</span></span>  
 [<span data-ttu-id="2bd03-116">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2bd03-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
