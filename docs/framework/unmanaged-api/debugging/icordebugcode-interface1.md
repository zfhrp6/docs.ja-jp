---
title: ICorDebugCode Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode
helpviewer_keywords: ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7813381c345db3d14318dddd93df1b491b46549e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode-interface1"></a><span data-ttu-id="8bcc7-102">ICorDebugCode Interface1</span><span class="sxs-lookup"><span data-stu-id="8bcc7-102">ICorDebugCode Interface1</span></span>
<span data-ttu-id="8bcc7-103">Microsoft Intermediate Language (MSIL) コードまたはネイティブ コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8bcc7-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="8bcc7-104">Methods</span></span>  
  
|<span data-ttu-id="8bcc7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8bcc7-105">Method</span></span>|<span data-ttu-id="8bcc7-106">説明</span><span class="sxs-lookup"><span data-stu-id="8bcc7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8bcc7-107">CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="8bcc7-107">CreateBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="8bcc7-108">指定したオフセット位置にブレークポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="8bcc7-109">GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="8bcc7-109">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getaddress-method.md)|<span data-ttu-id="8bcc7-110">この `ICorDebugCode` が表すコード セグメントの RVA (Relative Virtual Address) を取得します。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="8bcc7-111">GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="8bcc7-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)|<span data-ttu-id="8bcc7-112">指定した関数のすべてのコードを取得し、逆アセンブリ用に書式設定します。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="8bcc7-113">このメソッドは廃止されました。使用して[icordebugcode 2::getcodechunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)代わりにします。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="8bcc7-114">GetEnCRemapSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="8bcc7-114">GetEnCRemapSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="8bcc7-115">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-115">Not implemented.</span></span>|  
|[<span data-ttu-id="8bcc7-116">GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="8bcc7-116">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getfunction-method.md)|<span data-ttu-id="8bcc7-117">これに関連付けられている"ICorDebugFunction"を取得`ICorDebugCode`です。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="8bcc7-118">GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="8bcc7-118">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="8bcc7-119">MSIL のオフセットからネイティブ オフセットへのマッピングを表す"COR_DEBUG_IL_TO_NATIVE_MAP"インスタンスの配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="8bcc7-120">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="8bcc7-120">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getsize-method.md)|<span data-ttu-id="8bcc7-121">この `ICorDebugCode` で表されるバイナリ コードのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="8bcc7-122">GetVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="8bcc7-122">GetVersionNumber Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md)|<span data-ttu-id="8bcc7-123">この `ICorDebugCode` が表すコードのバージョンを識別する、1 から始まる数字を取得します。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="8bcc7-124">IsIL メソッド</span><span class="sxs-lookup"><span data-stu-id="8bcc7-124">IsIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-isil-method.md)|<span data-ttu-id="8bcc7-125">この `ICorDebugCode` が MSIL でコンパイルされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bcc7-126">コメント</span><span class="sxs-lookup"><span data-stu-id="8bcc7-126">Remarks</span></span>  
 <span data-ttu-id="8bcc7-127">`ICorDebugCode` は、MSIL またはネイティブ コードを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="8bcc7-128">MSIL コードを表す"ICorDebugFunction"オブジェクトは、0 または 1 個のいずれかを持つことができます`ICorDebugCode`それに関連付けられているオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="8bcc7-129">ネイティブ コードを表す"ICorDebugFunction"オブジェクトは、任意の数を持つことができます`ICorDebugCode`それに関連付けられているオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8bcc7-130">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bcc7-131">要件</span><span class="sxs-lookup"><span data-stu-id="8bcc7-131">Requirements</span></span>  
 <span data-ttu-id="8bcc7-132">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="8bcc7-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bcc7-133">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8bcc7-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8bcc7-134">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bcc7-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bcc7-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bcc7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bcc7-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="8bcc7-136">See Also</span></span>  
    
 [<span data-ttu-id="8bcc7-137">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bcc7-137">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="8bcc7-138">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8bcc7-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
