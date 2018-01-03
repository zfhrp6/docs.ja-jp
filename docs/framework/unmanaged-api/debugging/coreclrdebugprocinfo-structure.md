---
title: "CoreClrDebugProcInfo 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoreClrDebugProcInfo
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: CoreClrDebugProcInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreClrDebugProcInfo structure
- Silverlight, remote debugging
ms.assetid: 4ddc37da-5c94-4beb-b61c-b54071c0e749
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d341b875f9f64b9aa1fcdcf21668dafea0beac12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="coreclrdebugprocinfo-structure"></a><span data-ttu-id="687b9-102">CoreClrDebugProcInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="687b9-102">CoreClrDebugProcInfo Structure</span></span>
<span data-ttu-id="687b9-103">リモート コンピューターで実行されているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="687b9-103">Represents a process that is running on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="687b9-104">構文</span><span class="sxs-lookup"><span data-stu-id="687b9-104">Syntax</span></span>  
  
```  
struct  CoreClrDebugProcInfo {  
    DWORD m_dwPID;  
    DWORD m_dwInternalID;  
    WCHAR m_wszName[256];  
};  
```  
  
## <a name="members"></a><span data-ttu-id="687b9-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="687b9-105">Members</span></span>  
  
|<span data-ttu-id="687b9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="687b9-106">Member</span></span>|<span data-ttu-id="687b9-107">説明</span><span class="sxs-lookup"><span data-stu-id="687b9-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwPID`|<span data-ttu-id="687b9-108">OS によって割り当てられたプロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="687b9-108">OS-assigned process identifier.</span></span>|  
|`m_dwInternalID`|<span data-ttu-id="687b9-109">対象のコンピューターで実行されているリモート デバッグ プロキシによって割り当てられたプロセス識別子。</span><span class="sxs-lookup"><span data-stu-id="687b9-109">Process identifier that is assigned by the remote debugging proxy running on the target machine.</span></span> <span data-ttu-id="687b9-110">この識別子は OS 識別子よりも少ない頻度で再利用されます。</span><span class="sxs-lookup"><span data-stu-id="687b9-110">This identifier recycles less often than the OS identifier.</span></span>|  
|`m_wszName`|<span data-ttu-id="687b9-111">プロセスのコマンド ライン。</span><span class="sxs-lookup"><span data-stu-id="687b9-111">Command-line of the process.</span></span> <span data-ttu-id="687b9-112">このメンバーは切り詰められる場合があります。</span><span class="sxs-lookup"><span data-stu-id="687b9-112">This member may be truncated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="687b9-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="687b9-113">Requirements</span></span>  
 <span data-ttu-id="687b9-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="687b9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="687b9-115">**ヘッダー:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="687b9-115">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="687b9-116">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="687b9-116">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="687b9-117">**.NET framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="687b9-117">**.NET Framework Versions:** 3.5 SP1</span></span>
