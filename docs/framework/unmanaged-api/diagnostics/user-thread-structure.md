---
title: "USER_THREAD 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: USER_THREAD
api_location: diasymreader.dll
api_type: COM
f1_keywords: USER_THREAD
helpviewer_keywords: USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 50533ce25812ad49d538c5a6a6c814d7a9704053
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="userthread-structure"></a><span data-ttu-id="a65c3-102">USER_THREAD 構造体</span><span class="sxs-lookup"><span data-stu-id="a65c3-102">USER_THREAD Structure</span></span>
<span data-ttu-id="a65c3-103">デバッガー スレッドに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="a65c3-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="a65c3-104">詳細については、次を参照してください。、 [inotifysource 2::setnotifyfilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)メソッドです。</span><span class="sxs-lookup"><span data-stu-id="a65c3-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a65c3-105">構文</span><span class="sxs-lookup"><span data-stu-id="a65c3-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="a65c3-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a65c3-106">Members</span></span>  
  
|<span data-ttu-id="a65c3-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="a65c3-107">Member</span></span>|<span data-ttu-id="a65c3-108">説明</span><span class="sxs-lookup"><span data-stu-id="a65c3-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="a65c3-109">スレッドのバッファーのアドレス。</span><span class="sxs-lookup"><span data-stu-id="a65c3-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="a65c3-110">(バイト単位) のスレッドのバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="a65c3-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="a65c3-111">スレッド id です。</span><span class="sxs-lookup"><span data-stu-id="a65c3-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a65c3-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="a65c3-112">Requirements</span></span>  
 <span data-ttu-id="a65c3-113">**ヘッダー:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="a65c3-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a65c3-114">参照</span><span class="sxs-lookup"><span data-stu-id="a65c3-114">See Also</span></span>  
 [<span data-ttu-id="a65c3-115">SetNotifyFilter メソッド</span><span class="sxs-lookup"><span data-stu-id="a65c3-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)  
 [<span data-ttu-id="a65c3-116">シンボル ストア診断構造体</span><span class="sxs-lookup"><span data-stu-id="a65c3-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
