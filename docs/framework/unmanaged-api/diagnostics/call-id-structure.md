---
title: "CALL_ID 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CALL_ID
api_location: diasymreader.dll
api_type: COM
f1_keywords: CALL_ID
helpviewer_keywords: CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c44db9021a7dbf5b497db3536eddcea020e71bf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="callid-structure"></a><span data-ttu-id="e4a04-102">CALL_ID 構造体</span><span class="sxs-lookup"><span data-stu-id="e4a04-102">CALL_ID Structure</span></span>
<span data-ttu-id="e4a04-103">呼び出される関数はデバッガーに情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="e4a04-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="e4a04-104">参照してください、 [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)詳細についてはインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="e4a04-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4a04-105">構文</span><span class="sxs-lookup"><span data-stu-id="e4a04-105">Syntax</span></span>  
  
```  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a><span data-ttu-id="e4a04-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e4a04-106">Members</span></span>  
  
|<span data-ttu-id="e4a04-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="e4a04-107">Member</span></span>|<span data-ttu-id="e4a04-108">説明</span><span class="sxs-lookup"><span data-stu-id="e4a04-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="e4a04-109">呼び出しを行っているコンピューターを識別します。</span><span class="sxs-lookup"><span data-stu-id="e4a04-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="e4a04-110">コンピューターのプロセッサを識別します。</span><span class="sxs-lookup"><span data-stu-id="e4a04-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="e4a04-111">呼び出しを実行しているスレッドを識別します。</span><span class="sxs-lookup"><span data-stu-id="e4a04-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="e4a04-112">呼び出しスタックのアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4a04-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="e4a04-113">呼び出しのアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="e4a04-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="e4a04-114">呼び出しを実行するコンピューターを識別します。</span><span class="sxs-lookup"><span data-stu-id="e4a04-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4a04-115">要件</span><span class="sxs-lookup"><span data-stu-id="e4a04-115">Requirements</span></span>  
 <span data-ttu-id="e4a04-116">**ヘッダー:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="e4a04-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a04-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4a04-117">See Also</span></span>  
 [<span data-ttu-id="e4a04-118">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e4a04-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="e4a04-119">シンボル ストア診断構造体</span><span class="sxs-lookup"><span data-stu-id="e4a04-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
