---
title: "ICLRDataTarget3::GetExceptionRecord メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetExceptionRecord
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e78131eda9d10646a881dbbd4e3f7a4aaf8f607
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="0f80d-102">ICLRDataTarget3::GetExceptionRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="0f80d-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="0f80d-103">ターゲット プロセスに関連付けられた例外レコードを取得するために、共通言語ランタイム (CLR: Common Language Runtime) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0f80d-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="0f80d-104">たとえば、ダンプ ターゲットについてなります経由で渡される例外レコードと同じ、`ExceptionParam`への引数、 [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) Windows デバッグ ヘルプ ライブラリ (DbgHelp) の関数。</span><span class="sxs-lookup"><span data-stu-id="0f80d-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f80d-105">構文</span><span class="sxs-lookup"><span data-stu-id="0f80d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f80d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0f80d-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="0f80d-107">[入力] 入力バッファー サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="0f80d-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="0f80d-108">これと同じである必要があります`sizeof(` [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`です。</span><span class="sxs-lookup"><span data-stu-id="0f80d-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="0f80d-109">[出力] 実際にバッファーに書き込まれるバイト数を受け取る `ULONG32` 型へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0f80d-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="0f80d-110">[出力] 例外レコードのコピーを受信するメモリ バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0f80d-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="0f80d-111">例外レコードとして返されます、 [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)型です。</span><span class="sxs-lookup"><span data-stu-id="0f80d-111">The exception record is returned as a [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f80d-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="0f80d-112">Return Value</span></span>  
 <span data-ttu-id="0f80d-113">戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。</span><span class="sxs-lookup"><span data-stu-id="0f80d-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="0f80d-114">次が `HRESULT` コードに含まれることはありますが、限定されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="0f80d-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="0f80d-115">リターン コード</span><span class="sxs-lookup"><span data-stu-id="0f80d-115">Return code</span></span>|<span data-ttu-id="0f80d-116">説明</span><span class="sxs-lookup"><span data-stu-id="0f80d-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="0f80d-117">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="0f80d-117">Method succeeded.</span></span> <span data-ttu-id="0f80d-118">例外レコードは出力バッファーにコピーされました。</span><span class="sxs-lookup"><span data-stu-id="0f80d-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="0f80d-119">例外レコードはターゲットに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="0f80d-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="0f80d-120">入力バッファーのサイズは `sizeof(MINIDUMP_EXCEPTION)` と等しくありません。</span><span class="sxs-lookup"><span data-stu-id="0f80d-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f80d-121">コメント</span><span class="sxs-lookup"><span data-stu-id="0f80d-121">Remarks</span></span>  
 <span data-ttu-id="0f80d-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) dbghelp.h および imagehlp.h Windows SDK で定義されている構造です。</span><span class="sxs-lookup"><span data-stu-id="0f80d-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="0f80d-123">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="0f80d-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f80d-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="0f80d-124">Requirements</span></span>  
 <span data-ttu-id="0f80d-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="0f80d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f80d-126">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="0f80d-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0f80d-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f80d-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f80d-128">**.NET framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f80d-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f80d-129">参照</span><span class="sxs-lookup"><span data-stu-id="0f80d-129">See Also</span></span>  
 [<span data-ttu-id="0f80d-130">ICLRDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f80d-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="0f80d-131">GetExceptionContextRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="0f80d-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [<span data-ttu-id="0f80d-132">GetExceptionThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="0f80d-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
