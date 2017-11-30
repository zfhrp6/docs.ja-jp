---
title: "ICorDebugProcess6::DecodeEvent メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1453bc0c-6e0d-4d5a-b176-22607f8a3e6c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c0186fb91a4c47f1988af58577cee1b7a64987a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6decodeevent-method"></a><span data-ttu-id="aabcc-102">ICorDebugProcess6::DecodeEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="aabcc-102">ICorDebugProcess6::DecodeEvent Method</span></span>
<span data-ttu-id="aabcc-103">特別に作成されたネイティブ例外デバッグ イベントのペイロードにカプセル化されたマネージ デバッグ イベントをデコードします。</span><span class="sxs-lookup"><span data-stu-id="aabcc-103">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aabcc-104">構文</span><span class="sxs-lookup"><span data-stu-id="aabcc-104">Syntax</span></span>  
  
```  
HRESULT DecodeEvent(  
        [in, length_is(countBytes), size_is(countBytes)]  const BYTE pRecord[],  
        [in] DWORD countBytes,  
        [in] CorDebugRecordFormat format,  
        [in] DWORD dwFlags,   
        [in] DWORD dwThreadId,   
        [out] ICorDebugDebugEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aabcc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aabcc-105">Parameters</span></span>  
 `pRecord`  
 <span data-ttu-id="aabcc-106">[入力] マネージ デバッグ イベントに関する情報が含まれているネイティブ例外デバッグ イベントからバイト配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aabcc-106">[in] A pointer to a byte array from a native exception debug event that includes information about a managed debug event.</span></span>  
  
 `countBytes`  
 <span data-ttu-id="aabcc-107">[入力] `pRecord` バイト配列にある要素数。</span><span class="sxs-lookup"><span data-stu-id="aabcc-107">[in] The number of elements in the `pRecord` byte array.</span></span>  
  
 `format`  
 <span data-ttu-id="aabcc-108">[in]A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)アンマネージ デバッグ イベントの形式を指定する列挙体メンバーです。</span><span class="sxs-lookup"><span data-stu-id="aabcc-108">[in] A [CorDebugRecordFormat](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md) enumeration member that specifies the format of the unmanaged debug event.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="aabcc-109">[入力] ターゲット アーキテクチャに依存し、デバッグ イベントに関する追加情報を指定するビット フィールド。</span><span class="sxs-lookup"><span data-stu-id="aabcc-109">[in] A bit field that depends on the target architecture and that specifies additional information about the debug event.</span></span> <span data-ttu-id="aabcc-110">Windows システム用のメンバーであることができます、 [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)列挙します。</span><span class="sxs-lookup"><span data-stu-id="aabcc-110">For Windows systems, it can be a member of the [CorDebugDecodeEventFlagsWindows](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md) enumeration.</span></span>  
  
 `dwThreadId`  
 <span data-ttu-id="aabcc-111">[入力] 例外がスローされたスレッドのオペレーティング システムの識別子。</span><span class="sxs-lookup"><span data-stu-id="aabcc-111">[in] The operating system identifier of the thread on which the exception was thrown.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="aabcc-112">[out]アドレスへのポインター、 [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)をデコードされたマネージ デバッグ イベントを表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="aabcc-112">[out] A pointer to the address of an [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) object that represents a decoded managed debug event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aabcc-113">コメント</span><span class="sxs-lookup"><span data-stu-id="aabcc-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aabcc-114">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="aabcc-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aabcc-115">要件</span><span class="sxs-lookup"><span data-stu-id="aabcc-115">Requirements</span></span>  
 <span data-ttu-id="aabcc-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="aabcc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aabcc-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aabcc-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aabcc-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aabcc-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aabcc-119">**.NET framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aabcc-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aabcc-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="aabcc-120">See Also</span></span>  
 [<span data-ttu-id="aabcc-121">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="aabcc-121">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [<span data-ttu-id="aabcc-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="aabcc-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)