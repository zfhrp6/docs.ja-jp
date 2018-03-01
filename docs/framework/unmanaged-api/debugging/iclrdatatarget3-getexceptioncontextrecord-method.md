---
title: "ICLRDataTarget3::GetExceptionContextRecord メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 517e2a692c3b67a85bc24437dd5fbaedd5fc7254
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="136e5-102">ICLRDataTarget3::GetExceptionContextRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="136e5-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="136e5-103">ターゲット プロセスに関連付けられたコンテキスト レコードを取得するために、共通言語ランタイム (CLR: Common Language Runtime) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="136e5-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="136e5-104">たとえば、ダンプ ターゲットについてなります経由で渡されるコンテキスト レコードと同じ、`ExceptionParam`への引数、 [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) Windows デバッグ ヘルプ ライブラリ (DbgHelp) の関数。</span><span class="sxs-lookup"><span data-stu-id="136e5-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="136e5-105">構文</span><span class="sxs-lookup"><span data-stu-id="136e5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="136e5-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="136e5-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="136e5-107">[入力] 入力バッファー サイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="136e5-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="136e5-108">これはコンテキスト レコードを格納するのに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="136e5-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="136e5-109">[出力] 実際にバッファーに書き込まれるバイト数を受け取る `ULONG32` 型へのポインター。</span><span class="sxs-lookup"><span data-stu-id="136e5-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="136e5-110">[出力] コンテキスト レコードのコピーを受け取るメモリ バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="136e5-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="136e5-111">例外レコードとして返されます、[コンテキスト](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx)型です。</span><span class="sxs-lookup"><span data-stu-id="136e5-111">The exception record is returned as a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="136e5-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="136e5-112">Return Value</span></span>  
 <span data-ttu-id="136e5-113">戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。</span><span class="sxs-lookup"><span data-stu-id="136e5-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="136e5-114">次が `HRESULT` コードに含まれることはありますが、限定されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="136e5-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="136e5-115">リターン コード</span><span class="sxs-lookup"><span data-stu-id="136e5-115">Return code</span></span>|<span data-ttu-id="136e5-116">説明</span><span class="sxs-lookup"><span data-stu-id="136e5-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="136e5-117">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="136e5-117">Method succeeded.</span></span> <span data-ttu-id="136e5-118">コンテキスト レコードは出力バッファーにコピーされました。</span><span class="sxs-lookup"><span data-stu-id="136e5-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="136e5-119">コンテキスト レコードはターゲットに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="136e5-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="136e5-120">入力バッファーのサイズが足りないため、コンテキスト レコードを格納できません。</span><span class="sxs-lookup"><span data-stu-id="136e5-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="136e5-121">コメント</span><span class="sxs-lookup"><span data-stu-id="136e5-121">Remarks</span></span>  
 <span data-ttu-id="136e5-122">[コンテキスト](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx)Windows SDK によって提供されたヘッダーで定義されているプラットフォームに固有の構造です。</span><span class="sxs-lookup"><span data-stu-id="136e5-122">[CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="136e5-123">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="136e5-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="136e5-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="136e5-124">Requirements</span></span>  
 <span data-ttu-id="136e5-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="136e5-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="136e5-126">**ヘッダー:** ClrData.idl、ClrData.h</span><span class="sxs-lookup"><span data-stu-id="136e5-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="136e5-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="136e5-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="136e5-128">**.NET framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="136e5-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="136e5-129">参照</span><span class="sxs-lookup"><span data-stu-id="136e5-129">See Also</span></span>  
 [<span data-ttu-id="136e5-130">ICLRDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="136e5-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="136e5-131">GetExceptionRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="136e5-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [<span data-ttu-id="136e5-132">GetExceptionThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="136e5-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)
