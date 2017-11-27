---
title: "ICLRDataTarget::GetThreadContext メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 480b65b279dbc0359b078f3f1d543f63a0bfd0f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="723bf-102">ICLRDataTarget::GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="723bf-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="723bf-103">ターゲット プロセスで特定のスレッドの現在の実行コンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="723bf-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="723bf-104">このメソッドは、共通言語ランタイム データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="723bf-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="723bf-105">構文</span><span class="sxs-lookup"><span data-stu-id="723bf-105">Syntax</span></span>  
  
```  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="723bf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="723bf-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="723bf-107">[in]ターゲット プロセス内のスレッドのオペレーティング システムの識別子です。</span><span class="sxs-lookup"><span data-stu-id="723bf-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="723bf-108">[in]返されるコンテキストのどの部分を指定するフラグ。</span><span class="sxs-lookup"><span data-stu-id="723bf-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="723bf-109">実装では、コンテキストには、少なくともそれらの部分を返します。</span><span class="sxs-lookup"><span data-stu-id="723bf-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="723bf-110">[in]コンテキストのサイズ。</span><span class="sxs-lookup"><span data-stu-id="723bf-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="723bf-111">[out]コンテキストを格納するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="723bf-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="723bf-112">内のデータ、`context`バッファーは、Win32 の形式である必要があります`CONTEXT`構造体。</span><span class="sxs-lookup"><span data-stu-id="723bf-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="723bf-113">コンテキストはプロセッサ固有のレジスタのデータを指定するので、Win32 の定義`CONTEXT`構造は、プロセッサのアーキテクチャによって異なります。</span><span class="sxs-lookup"><span data-stu-id="723bf-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="723bf-114">Win32 の定義については、WinNT.h ヘッダー ファイルを参照してください`CONTEXT`構造体。</span><span class="sxs-lookup"><span data-stu-id="723bf-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="723bf-115">コメント</span><span class="sxs-lookup"><span data-stu-id="723bf-115">Remarks</span></span>  
 <span data-ttu-id="723bf-116">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="723bf-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="723bf-117">要件</span><span class="sxs-lookup"><span data-stu-id="723bf-117">Requirements</span></span>  
 <span data-ttu-id="723bf-118">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="723bf-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="723bf-119">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="723bf-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="723bf-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="723bf-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="723bf-121">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="723bf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="723bf-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="723bf-122">See Also</span></span>  
 [<span data-ttu-id="723bf-123">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="723bf-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
