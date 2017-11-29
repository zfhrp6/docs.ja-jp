---
title: "ICLRDataTarget::SetTLSValue メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.SetTLSValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75c9d25b496e300d66844e3fd88655ab38da4b0e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="41d5f-102">ICLRDataTarget::SetTLSValue メソッド</span><span class="sxs-lookup"><span data-stu-id="41d5f-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="41d5f-103">ターゲット プロセス内の指定されたスレッドのスレッド ローカル ストレージ (TLS) の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="41d5f-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="41d5f-104">このメソッドは、共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="41d5f-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41d5f-105">構文</span><span class="sxs-lookup"><span data-stu-id="41d5f-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41d5f-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="41d5f-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="41d5f-107">[in]ターゲット プロセス内のスレッドのオペレーティング システムの識別子です。</span><span class="sxs-lookup"><span data-stu-id="41d5f-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="41d5f-108">[in]位置のインデックス。</span><span class="sxs-lookup"><span data-stu-id="41d5f-108">[in] The index of the location.</span></span> <span data-ttu-id="41d5f-109">この値は、指定したスレッドのローカル ストアに有効なインデックスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="41d5f-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="41d5f-110">[in]A `CLRDATA_ADDRESS` TLS の指定された場所に配置する値を指定する値。</span><span class="sxs-lookup"><span data-stu-id="41d5f-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41d5f-111">コメント</span><span class="sxs-lookup"><span data-stu-id="41d5f-111">Remarks</span></span>  
 <span data-ttu-id="41d5f-112">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="41d5f-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41d5f-113">要件</span><span class="sxs-lookup"><span data-stu-id="41d5f-113">Requirements</span></span>  
 <span data-ttu-id="41d5f-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="41d5f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41d5f-115">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="41d5f-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="41d5f-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41d5f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41d5f-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41d5f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d5f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="41d5f-118">See Also</span></span>  
 [<span data-ttu-id="41d5f-119">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="41d5f-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
