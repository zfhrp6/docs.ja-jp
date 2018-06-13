---
title: ICorDebugProcess6 インターフェイス
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 103a37d7549d7ec18617b74c777506b3ad225a18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422859"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="5c286-102">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c286-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="5c286-103">ネイティブ例外デバッグ イベントや仮想モジュール分割でエンコードされたマネージ デバッグ イベントをデコードなどの機能を有効にする ICorDebugProcess インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="5c286-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5c286-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="5c286-104">Methods</span></span>  
  
|<span data-ttu-id="5c286-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="5c286-105">Method</span></span>|<span data-ttu-id="5c286-106">説明</span><span class="sxs-lookup"><span data-stu-id="5c286-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5c286-107">DecodeEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="5c286-107">DecodeEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="5c286-108">特別に作成されたネイティブ例外デバッグ イベントのペイロードにカプセル化されたマネージ デバッグ イベントをデコードします。</span><span class="sxs-lookup"><span data-stu-id="5c286-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="5c286-109">EnableVirtualModuleSplitting メソッド</span><span class="sxs-lookup"><span data-stu-id="5c286-109">EnableVirtualModuleSplitting Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="5c286-110">仮想モジュール分割を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="5c286-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="5c286-111">GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="5c286-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|<span data-ttu-id="5c286-112">特定のコード アドレスで、マネージ コードに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="5c286-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="5c286-113">GetExportStepInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="5c286-113">GetExportStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="5c286-114">マネージ コードのステップ実行に役立つランタイム エクスポート関数の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5c286-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="5c286-115">MarkDebuggerAttached メソッド</span><span class="sxs-lookup"><span data-stu-id="5c286-115">MarkDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="5c286-116">.NET Framework クラス ライブラリの <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> メソッドが `true` を返すように、デバッグ対象の内部状態を変更します。</span><span class="sxs-lookup"><span data-stu-id="5c286-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="5c286-117">ProcessStateChanged メソッド</span><span class="sxs-lookup"><span data-stu-id="5c286-117">ProcessStateChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="5c286-118">通知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)プロセスを実行しています。</span><span class="sxs-lookup"><span data-stu-id="5c286-118">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c286-119">コメント</span><span class="sxs-lookup"><span data-stu-id="5c286-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c286-120">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="5c286-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="5c286-121">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="5c286-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c286-122">要件</span><span class="sxs-lookup"><span data-stu-id="5c286-122">Requirements</span></span>  
 <span data-ttu-id="5c286-123">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5c286-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c286-124">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5c286-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c286-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c286-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c286-126">**.NET framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c286-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c286-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="5c286-127">See Also</span></span>  
 [<span data-ttu-id="5c286-128">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5c286-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="5c286-129">デバッグ</span><span class="sxs-lookup"><span data-stu-id="5c286-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
