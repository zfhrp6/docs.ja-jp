---
title: "ClrCreateManagedInstance 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: ClrCreateManagedInstance
helpviewer_keywords: ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d27a881f84121f0d096eae7c693dec5b674caec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="clrcreatemanagedinstance-function"></a><span data-ttu-id="3c488-102">ClrCreateManagedInstance 関数</span><span class="sxs-lookup"><span data-stu-id="3c488-102">ClrCreateManagedInstance Function</span></span>
<span data-ttu-id="3c488-103">指定したマネージ型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c488-103">Creates an instance of the specified managed type.</span></span>  
  
 <span data-ttu-id="3c488-104">この関数は、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] では推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="3c488-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="3c488-105">COM のアクティブ化を使用して、マネージ型のインスタンスを作成するか、ホストを使用して (を参照してください[CLR をホストしている .NET Framework 4 および 4.5 で追加されたインターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md))。</span><span class="sxs-lookup"><span data-stu-id="3c488-105">Use COM activation to create an instance of the managed type, or use hosting (see [CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c488-106">構文</span><span class="sxs-lookup"><span data-stu-id="3c488-106">Syntax</span></span>  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c488-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3c488-107">Parameters</span></span>  
 `pTypeName`  
 <span data-ttu-id="3c488-108">[in]要求されているインスタンスの型の名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3c488-108">[in] A pointer to the name of the instance type being requested.</span></span>  
  
 `riid`  
 <span data-ttu-id="3c488-109">[in]`IID`要求されているインスタンスの型のです。</span><span class="sxs-lookup"><span data-stu-id="3c488-109">[in] The `IID` of the instance type being requested.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="3c488-110">[out]呼び出し元によって要求されたマネージ型のインスタンスへのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3c488-110">[out] A pointer to a pointer to an instance of the managed type that was requested by the caller.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c488-111">コメント</span><span class="sxs-lookup"><span data-stu-id="3c488-111">Remarks</span></span>  
 <span data-ttu-id="3c488-112">共通言語ランタイムは、プロセスに既に読み込まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c488-112">The common language runtime should already be loaded into a process.</span></span> <span data-ttu-id="3c488-113">たとえば、読み込むことができますに呼び出しを使用して、 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)関数の前に、`ClrCreateManagedInstance`関数が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3c488-113">For example, it can be loaded by using a call to the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) function before the `ClrCreateManagedInstance` function is called.</span></span> <span data-ttu-id="3c488-114">ランタイムが読み込まれていない場合`ClrCreateManagedInstance`最初に、ランタイムの v1.0.3705 の読み込みを試みます。</span><span class="sxs-lookup"><span data-stu-id="3c488-114">If the runtime is not loaded, `ClrCreateManagedInstance` first tries to load v1.0.3705 of the runtime.</span></span> <span data-ttu-id="3c488-115">失敗した場合、ランタイムの最新バージョンをロードしようとします。</span><span class="sxs-lookup"><span data-stu-id="3c488-115">If that fails, it attempts to load the latest version of the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c488-116">要件</span><span class="sxs-lookup"><span data-stu-id="3c488-116">Requirements</span></span>  
 <span data-ttu-id="3c488-117">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="3c488-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c488-118">**ヘッダー:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3c488-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3c488-119">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3c488-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c488-120">**.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c488-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c488-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c488-121">See Also</span></span>  
 [<span data-ttu-id="3c488-122">推奨されなくなった CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="3c488-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [<span data-ttu-id="3c488-123">ホスティング</span><span class="sxs-lookup"><span data-stu-id="3c488-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
