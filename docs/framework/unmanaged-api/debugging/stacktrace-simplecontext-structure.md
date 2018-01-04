---
title: "StackTrace_SimpleContext 構造体"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackTrace_SimpleContext
api_location: diasymreader.dll
api_type: COM
f1_keywords: SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 756c1d4129aebedea46443613d286a51562a3896
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="a8d7c-102">StackTrace_SimpleContext 構造体</span><span class="sxs-lookup"><span data-stu-id="a8d7c-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="a8d7c-103">完全な `CONTEXT` 構造の代わりに使用できる単純なコンテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8d7c-104">構文</span><span class="sxs-lookup"><span data-stu-id="a8d7c-104">Syntax</span></span>  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="a8d7c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a8d7c-105">Members</span></span>  
  
|<span data-ttu-id="a8d7c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a8d7c-106">Member</span></span>|<span data-ttu-id="a8d7c-107">説明</span><span class="sxs-lookup"><span data-stu-id="a8d7c-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="a8d7c-108">スタック ポインター、または x86 で enter スタック ポインター (ESP) プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="a8d7c-109">フレームのオフセット、または x86 で EBP レジスタ プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="a8d7c-110">命令ポインター、または x86 で enter 命令ポインター (EIP) プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8d7c-111">コメント</span><span class="sxs-lookup"><span data-stu-id="a8d7c-111">Remarks</span></span>  
 <span data-ttu-id="a8d7c-112">スタック トレース関数は、通常、アドレス、フレームのオフセット、およびスタック アドレスのみを返す必要があるため、必要に応じて、使用して、`SimpleContext`ではなく、大きな構造`CONTEXT`構造体。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8d7c-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="a8d7c-113">Requirements</span></span>  
 <span data-ttu-id="a8d7c-114">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="a8d7c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8d7c-115">**ヘッダー:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="a8d7c-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="a8d7c-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8d7c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d7c-117">参照</span><span class="sxs-lookup"><span data-stu-id="a8d7c-117">See Also</span></span>  
 [<span data-ttu-id="a8d7c-118">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="a8d7c-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="a8d7c-119">デバッグ</span><span class="sxs-lookup"><span data-stu-id="a8d7c-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
