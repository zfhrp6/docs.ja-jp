---
title: "CoreClrDebugRuntimeInfo 構造体"
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
- CoreClrDebugRuntimeInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: effcc44b3f3b0926c1d711955fa77aa3e71a1592
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="6520d-102">CoreClrDebugRuntimeInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="6520d-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="6520d-103">リモート コンピューター上のプロセスに読み込まれる共通言語ランタイム (CLR) インスタンスを表します。</span><span class="sxs-lookup"><span data-stu-id="6520d-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6520d-104">構文</span><span class="sxs-lookup"><span data-stu-id="6520d-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="6520d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="6520d-105">Members</span></span>  
  
|<span data-ttu-id="6520d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="6520d-106">Member</span></span>|<span data-ttu-id="6520d-107">説明</span><span class="sxs-lookup"><span data-stu-id="6520d-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="6520d-108">対象のコンピューターで実行されているリモート デバッグ プロキシによって割り当てられたランタイム識別子。</span><span class="sxs-lookup"><span data-stu-id="6520d-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6520d-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="6520d-109">Requirements</span></span>  
 <span data-ttu-id="6520d-110">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="6520d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6520d-111">**ヘッダー:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="6520d-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="6520d-112">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="6520d-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="6520d-113">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="6520d-113">**.NET Framework Versions:** 3.5 SP1</span></span>
