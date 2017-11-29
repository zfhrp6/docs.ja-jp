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
ms.openlocfilehash: f8c9ac4ecc0cffda4038129b1244b81501e9a1f7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="e9fce-102">ICLRDataTarget3::GetExceptionRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="e9fce-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="e9fce-103">ターゲット プロセスに関連付けられた例外レコードを取得するために、共通言語ランタイム (CLR: Common Language Runtime) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e9fce-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="e9fce-104">たとえば、ダンプ ターゲットについてなります経由で渡される例外レコードと同じ、`ExceptionParam`への引数、 [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) Windows デバッグ ヘルプ ライブラリ (DbgHelp) の関数。</span><span class="sxs-lookup"><span data-stu-id="e9fce-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9fce-105">構文</span><span class="sxs-lookup"><span data-stu-id="e9fce-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9fce-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e9fce-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="e9fce-107">[入力] 入力バッファー サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="e9fce-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="e9fce-108">これと同じである必要があります`sizeof(` [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`です。</span><span class="sxs-lookup"><span data-stu-id="e9fce-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="e9fce-109">[出力] 実際にバッファーに書き込まれるバイト数を受け取る `ULONG32` 型へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e9fce-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e9fce-110">[出力] 例外レコードのコピーを受信するメモリ バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e9fce-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="e9fce-111">例外レコードとして返されます、 [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)型です。</span><span class="sxs-lookup"><span data-stu-id="e9fce-111">The exception record is returned as a [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9fce-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="e9fce-112">Return Value</span></span>  
 <span data-ttu-id="e9fce-113">戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。</span><span class="sxs-lookup"><span data-stu-id="e9fce-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="e9fce-114">次が `HRESULT` コードに含まれることはありますが、限定されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e9fce-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="e9fce-115">リターン コード</span><span class="sxs-lookup"><span data-stu-id="e9fce-115">Return code</span></span>|<span data-ttu-id="e9fce-116">説明</span><span class="sxs-lookup"><span data-stu-id="e9fce-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="e9fce-117">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="e9fce-117">Method succeeded.</span></span> <span data-ttu-id="e9fce-118">例外レコードは出力バッファーにコピーされました。</span><span class="sxs-lookup"><span data-stu-id="e9fce-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="e9fce-119">例外レコードはターゲットに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="e9fce-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="e9fce-120">入力バッファーのサイズは `sizeof(MINIDUMP_EXCEPTION)` と等しくありません。</span><span class="sxs-lookup"><span data-stu-id="e9fce-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9fce-121">コメント</span><span class="sxs-lookup"><span data-stu-id="e9fce-121">Remarks</span></span>  
 <span data-ttu-id="e9fce-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) dbghelp.h および imagehlp.h Windows SDK で定義されている構造です。</span><span class="sxs-lookup"><span data-stu-id="e9fce-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="e9fce-123">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="e9fce-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9fce-124">要件</span><span class="sxs-lookup"><span data-stu-id="e9fce-124">Requirements</span></span>  
 <span data-ttu-id="e9fce-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e9fce-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9fce-126">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e9fce-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e9fce-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9fce-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9fce-128">**.NET framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9fce-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9fce-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9fce-129">See Also</span></span>  
 [<span data-ttu-id="e9fce-130">ICLRDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e9fce-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="e9fce-131">GetExceptionContextRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="e9fce-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [<span data-ttu-id="e9fce-132">GetExceptionThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="e9fce-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
