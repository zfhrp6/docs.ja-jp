---
title: "ICorDebugCode3::GetReturnValueLiveOffset メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugCode3.GetReturnValueLiveOffset
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4516f2244b72bd4f254c5090b09d6d90579f1ae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="83eca-102">ICorDebugCode3::GetReturnValueLiveOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="83eca-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>
<span data-ttu-id="83eca-103">指定した IL オフセットについて、デバッガーが関数からの戻り値を取得できるように、ブレークポイントを配置する必要があるネイティブなオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="83eca-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83eca-104">構文</span><span class="sxs-lookup"><span data-stu-id="83eca-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="83eca-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83eca-105">Parameters</span></span>  
 `ILoffset`  
 <span data-ttu-id="83eca-106">オフセット IL。</span><span class="sxs-lookup"><span data-stu-id="83eca-106">The IL offset.</span></span> <span data-ttu-id="83eca-107">関数呼び出しサイトであることが必要です。そうでない場合、関数呼び出しは失敗します。</span><span class="sxs-lookup"><span data-stu-id="83eca-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="83eca-108">`pOffsets` を格納できるバイト数。</span><span class="sxs-lookup"><span data-stu-id="83eca-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="83eca-109">実際に返されたオフセットの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="83eca-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="83eca-110">通常、この値は 1 ですが、単一の IL 命令が複数の `CALL` アセンブリ命令にマップする場合があります。</span><span class="sxs-lookup"><span data-stu-id="83eca-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="83eca-111">ネイティブ オフセットの配列。</span><span class="sxs-lookup"><span data-stu-id="83eca-111">An array of native offsets.</span></span> <span data-ttu-id="83eca-112">通常、`pOffsets` には単一のオフセットが含まれますが、単一の IL 命令が複数の `CALL` アセンブリ命令に対する複数のマップに対応する場合があります。</span><span class="sxs-lookup"><span data-stu-id="83eca-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83eca-113">コメント</span><span class="sxs-lookup"><span data-stu-id="83eca-113">Remarks</span></span>  
 <span data-ttu-id="83eca-114">このメソッドはと共に使用、 [icordebugilframe 3::getreturnvalueforiloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)参照型を返すメソッドの戻り値を取得します。</span><span class="sxs-lookup"><span data-stu-id="83eca-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="83eca-115">関数呼び出しサイトに対する IL オフセットをこのメソッドに渡すと、1 つ以上のネイティブ オフセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="83eca-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="83eca-116">これによってデバッガーは、関数内のこうしたネイティブ オフセット上でブレークポイントを設定できます。</span><span class="sxs-lookup"><span data-stu-id="83eca-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="83eca-117">このメソッドに渡された同じ IL オフセットを渡すことができますし、デバッガーに達すると、ブレークポイントのいずれか、 [icordebugilframe 3::getreturnvalueforiloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)戻り値を取得します。</span><span class="sxs-lookup"><span data-stu-id="83eca-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="83eca-118">この場合、デバッガーは設定したブレークポイントすべてをクリアする必要があります。</span><span class="sxs-lookup"><span data-stu-id="83eca-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="83eca-119">`ICorDebugCode3::GetReturnValueLiveOffset`と[icordebugilframe 3::getreturnvalueforiloffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)メソッドを使用する参照型だけの戻り値の情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="83eca-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="83eca-120">値型 (つまり、<xref:System.ValueType> から派生するすべての型) からの戻り値情報の取得はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="83eca-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="83eca-121">この関数は、次の表に示す `HRESULT` 値を返します。</span><span class="sxs-lookup"><span data-stu-id="83eca-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="83eca-122">`HRESULT` の値</span><span class="sxs-lookup"><span data-stu-id="83eca-122">`HRESULT` value</span></span>|<span data-ttu-id="83eca-123">説明</span><span class="sxs-lookup"><span data-stu-id="83eca-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="83eca-124">成功。</span><span class="sxs-lookup"><span data-stu-id="83eca-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="83eca-125">指定した IL オフセット サイトが呼び出し命令ではないか、関数が `void` を返しています。</span><span class="sxs-lookup"><span data-stu-id="83eca-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="83eca-126">指定した IL オフセットは適切な呼び出しですが、取得する戻り値の型がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="83eca-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="83eca-127">`ICorDebugCode3::GetReturnValueLiveOffset` メソッドは、x86 ベースおよび AMD64 システムでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="83eca-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83eca-128">要件</span><span class="sxs-lookup"><span data-stu-id="83eca-128">Requirements</span></span>  
 <span data-ttu-id="83eca-129">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="83eca-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83eca-130">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83eca-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="83eca-131">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83eca-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83eca-132">**.NET framework のバージョン:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83eca-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83eca-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="83eca-133">See Also</span></span>  
 [<span data-ttu-id="83eca-134">GetReturnValueForILOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="83eca-134">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)  
 [<span data-ttu-id="83eca-135">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83eca-135">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
