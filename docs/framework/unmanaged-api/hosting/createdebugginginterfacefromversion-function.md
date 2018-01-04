---
title: "CreateDebuggingInterfaceFromVersion 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CreateDebuggingInterfaceFromVersion
helpviewer_keywords: CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b3f269f5b1758481995d6064e7137e62bff4a868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="938a0-102">CreateDebuggingInterfaceFromVersion 関数</span><span class="sxs-lookup"><span data-stu-id="938a0-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="938a0-103">作成、 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)オブジェクトが指定されたバージョン情報に基づいています。</span><span class="sxs-lookup"><span data-stu-id="938a0-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="938a0-104">この関数は廃止されていますが、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="938a0-104">This function is obsolete in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="938a0-105">代わりに、共通言語ランタイム (CLR) 2.0 用のインターフェイスを取得する次のように使用します。、 [iclrruntimeinfo::getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)メソッド クラス識別子 CLSID_CLRDebuggingLegacy と IID_ICorDebug インターフェイス識別子を指定します。</span><span class="sxs-lookup"><span data-stu-id="938a0-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="938a0-106">CLR 4 をインターフェイスを取得するか、後で、呼び出しを[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)関数し、クラス識別子 CLSID_CLRDebugging と IID_ICLRDebugging インターフェイス識別子を指定します。</span><span class="sxs-lookup"><span data-stu-id="938a0-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="938a0-107">構文</span><span class="sxs-lookup"><span data-stu-id="938a0-107">Syntax</span></span>  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="938a0-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="938a0-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="938a0-109">[in]バージョン`ICorDebug`はデバッガーで想定します。</span><span class="sxs-lookup"><span data-stu-id="938a0-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="938a0-110">参照してください、 [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)有効な値を列挙します。</span><span class="sxs-lookup"><span data-stu-id="938a0-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="938a0-111">[in]デバッグするには、アプリケーションまたはプロセスに関連付けられている、共通言語ランタイム バージョンです。</span><span class="sxs-lookup"><span data-stu-id="938a0-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="938a0-112">参照してください、 [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)または[GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)については、この値を取得するメソッド。</span><span class="sxs-lookup"><span data-stu-id="938a0-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="938a0-113">[out]ポインターを受け取る場所、`ICorDebug`オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="938a0-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="938a0-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="938a0-114">Return Value</span></span>  
 <span data-ttu-id="938a0-115">このメソッドは、次の値だけでなく WinError.h ファイルで定義されている標準の COM エラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="938a0-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="938a0-116">リターン コード</span><span class="sxs-lookup"><span data-stu-id="938a0-116">Return code</span></span>|<span data-ttu-id="938a0-117">説明</span><span class="sxs-lookup"><span data-stu-id="938a0-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="938a0-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="938a0-118">S_OK</span></span>|<span data-ttu-id="938a0-119">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="938a0-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="938a0-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="938a0-120">E_INVALIDARG</span></span>|<span data-ttu-id="938a0-121">`szDebuggeeVersion`または`ppCordb`が null の場合、またはバージョン文字列が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="938a0-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="938a0-122">コメント</span><span class="sxs-lookup"><span data-stu-id="938a0-122">Remarks</span></span>  
 <span data-ttu-id="938a0-123">`szDebuggeeVersion`パラメーターが MSCorDbi.dll の対応するバージョンにマップします。</span><span class="sxs-lookup"><span data-stu-id="938a0-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="938a0-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="938a0-124">Requirements</span></span>  
 <span data-ttu-id="938a0-125">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="938a0-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="938a0-126">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="938a0-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="938a0-127">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="938a0-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="938a0-128">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="938a0-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938a0-129">参照</span><span class="sxs-lookup"><span data-stu-id="938a0-129">See Also</span></span>  
 [<span data-ttu-id="938a0-130">サポートされなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="938a0-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
