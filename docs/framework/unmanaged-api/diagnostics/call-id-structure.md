---
title: CALL_ID 構造体
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f8d6b16f3eeb32e41f3568e0b237f18c945a8cb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423898"
---
# <a name="callid-structure"></a><span data-ttu-id="f2d18-102">CALL_ID 構造体</span><span class="sxs-lookup"><span data-stu-id="f2d18-102">CALL_ID Structure</span></span>
<span data-ttu-id="f2d18-103">呼び出される関数はデバッガーに情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="f2d18-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="f2d18-104">参照してください、 [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)詳細についてはインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="f2d18-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2d18-105">構文</span><span class="sxs-lookup"><span data-stu-id="f2d18-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f2d18-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f2d18-106">Members</span></span>  
  
|<span data-ttu-id="f2d18-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="f2d18-107">Member</span></span>|<span data-ttu-id="f2d18-108">説明</span><span class="sxs-lookup"><span data-stu-id="f2d18-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="f2d18-109">呼び出しを行っているコンピューターを識別します。</span><span class="sxs-lookup"><span data-stu-id="f2d18-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="f2d18-110">コンピューターのプロセッサを識別します。</span><span class="sxs-lookup"><span data-stu-id="f2d18-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="f2d18-111">呼び出しを実行しているスレッドを識別します。</span><span class="sxs-lookup"><span data-stu-id="f2d18-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="f2d18-112">呼び出しスタックのアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="f2d18-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="f2d18-113">呼び出しのアドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="f2d18-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="f2d18-114">呼び出しを実行するコンピューターを識別します。</span><span class="sxs-lookup"><span data-stu-id="f2d18-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f2d18-115">要件</span><span class="sxs-lookup"><span data-stu-id="f2d18-115">Requirements</span></span>  
 <span data-ttu-id="f2d18-116">**ヘッダー:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="f2d18-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2d18-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f2d18-117">See Also</span></span>  
 [<span data-ttu-id="f2d18-118">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f2d18-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="f2d18-119">シンボル ストア診断構造体</span><span class="sxs-lookup"><span data-stu-id="f2d18-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
