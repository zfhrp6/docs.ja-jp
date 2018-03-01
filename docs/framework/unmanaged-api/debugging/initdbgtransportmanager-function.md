---
title: "InitDbgTransportManager 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 37b849ed482f76692a63c70cbb0a3b9e1bacc8ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="9b21c-102">InitDbgTransportManager 関数</span><span class="sxs-lookup"><span data-stu-id="9b21c-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="9b21c-103">プロセスおよびランタイムの列挙のためにリモート ターゲットに接続するよう、トランスポート マネージャーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="9b21c-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b21c-104">構文</span><span class="sxs-lookup"><span data-stu-id="9b21c-104">Syntax</span></span>  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9b21c-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="9b21c-105">Return Value</span></span>  
 <span data-ttu-id="9b21c-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b21c-106">S_OK</span></span>  
 <span data-ttu-id="9b21c-107">成功。</span><span class="sxs-lookup"><span data-stu-id="9b21c-107">Success.</span></span>  
  
 <span data-ttu-id="9b21c-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9b21c-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="9b21c-109">関数はトランスポート マネージャーにメモリを割り当てられませんでした。</span><span class="sxs-lookup"><span data-stu-id="9b21c-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="9b21c-110">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="9b21c-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="9b21c-111">その他のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="9b21c-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b21c-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="9b21c-112">Requirements</span></span>  
 <span data-ttu-id="9b21c-113">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="9b21c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b21c-114">**ヘッダー:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="9b21c-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="9b21c-115">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="9b21c-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="9b21c-116">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="9b21c-116">**.NET Framework Versions:** 3.5 SP1</span></span>
