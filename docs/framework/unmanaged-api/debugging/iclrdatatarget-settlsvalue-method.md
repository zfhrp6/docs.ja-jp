---
title: ICLRDataTarget::SetTLSValue メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18733c2d643a75f9bb11159ba4acdbc8ab064c55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404113"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="c0619-102">ICLRDataTarget::SetTLSValue メソッド</span><span class="sxs-lookup"><span data-stu-id="c0619-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="c0619-103">ターゲット プロセス内の指定されたスレッドのスレッド ローカル ストレージ (TLS) の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="c0619-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="c0619-104">このメソッドは、共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c0619-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0619-105">構文</span><span class="sxs-lookup"><span data-stu-id="c0619-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0619-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c0619-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c0619-107">[in]ターゲット プロセス内のスレッドのオペレーティング システムの識別子です。</span><span class="sxs-lookup"><span data-stu-id="c0619-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="c0619-108">[in]位置のインデックス。</span><span class="sxs-lookup"><span data-stu-id="c0619-108">[in] The index of the location.</span></span> <span data-ttu-id="c0619-109">この値は、指定したスレッドのローカル ストアに有効なインデックスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0619-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="c0619-110">[in]A `CLRDATA_ADDRESS` TLS の指定された場所に配置する値を指定する値。</span><span class="sxs-lookup"><span data-stu-id="c0619-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0619-111">コメント</span><span class="sxs-lookup"><span data-stu-id="c0619-111">Remarks</span></span>  
 <span data-ttu-id="c0619-112">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="c0619-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0619-113">要件</span><span class="sxs-lookup"><span data-stu-id="c0619-113">Requirements</span></span>  
 <span data-ttu-id="c0619-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="c0619-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0619-115">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c0619-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c0619-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0619-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0619-117">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0619-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0619-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0619-118">See Also</span></span>  
 [<span data-ttu-id="c0619-119">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c0619-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
