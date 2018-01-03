---
title: "CreateCoreClrDebugTarget 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateCorClrDebugTarget
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: CreateCoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- Silverlight, remote debugging
- CreateCoreClrDebugTarget function
ms.assetid: 1cf4ca8e-d9bb-4633-9adf-5e24315bf87a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5b05cc6c84f2f891691613a485d35d008ef79e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="createcoreclrdebugtarget-function"></a><span data-ttu-id="abba6-102">CreateCoreClrDebugTarget 関数</span><span class="sxs-lookup"><span data-stu-id="abba6-102">CreateCoreClrDebugTarget Function</span></span>
<span data-ttu-id="abba6-103">リモート コンピューターで実行しているデバッガー プロキシへの接続を作成、 [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)クエリ実行中のプロセスとリモート コンピューターに読み込まれたランタイムを使用できるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="abba6-103">Creates a connection to a debugger proxy that is running on a remote machine, and returns an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that can be used to query running processes and loaded runtimes on the remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abba6-104">構文</span><span class="sxs-lookup"><span data-stu-id="abba6-104">Syntax</span></span>  
  
```  
HRESULT CreateCoreClrDebugTarget (  
       [in]  DWORD    dwAddress,   
       [out] ICoreClrDebugTarget**     ppTarget  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abba6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="abba6-105">Parameters</span></span>  
 `dwAddress`  
 <span data-ttu-id="abba6-106">[in] リモート対象コンピューターの IPv4 アドレス。</span><span class="sxs-lookup"><span data-stu-id="abba6-106">[in] IPv4 address of a remote target machine.</span></span>  
  
 `ppTarget`  
 <span data-ttu-id="abba6-107">[out]ポインターへのポインター、 [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)作成されるオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="abba6-107">[out] Pointer to a pointer to an [ICoreClrDebugTarget](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md) object that will be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abba6-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="abba6-108">Return Value</span></span>  
 <span data-ttu-id="abba6-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="abba6-109">S_OK</span></span>  
 <span data-ttu-id="abba6-110">プロセス内の CLR 数が正常に判別され、対応するハンドルとパスの配列が正しく入力されました。</span><span class="sxs-lookup"><span data-stu-id="abba6-110">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="abba6-111">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="abba6-111">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="abba6-112">`ppTarget`  用に十分なメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="abba6-112">Unable to allocate enough memory for `ppTarget`.</span></span>  
  
 <span data-ttu-id="abba6-113">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="abba6-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="abba6-114">その他のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="abba6-114">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abba6-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="abba6-115">Requirements</span></span>  
 <span data-ttu-id="abba6-116">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="abba6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abba6-117">**ヘッダー:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="abba6-117">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="abba6-118">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="abba6-118">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="abba6-119">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="abba6-119">**.NET Framework Versions:** 3.5 SP1</span></span>
