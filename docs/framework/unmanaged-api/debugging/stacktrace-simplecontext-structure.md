---
title: StackTrace_SimpleContext 構造体
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acf2ba752ace49ae288857dc22819a8e7e429a34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="47a62-102">StackTrace_SimpleContext 構造体</span><span class="sxs-lookup"><span data-stu-id="47a62-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="47a62-103">完全な `CONTEXT` 構造の代わりに使用できる単純なコンテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="47a62-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47a62-104">構文</span><span class="sxs-lookup"><span data-stu-id="47a62-104">Syntax</span></span>  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="47a62-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="47a62-105">Members</span></span>  
  
|<span data-ttu-id="47a62-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="47a62-106">Member</span></span>|<span data-ttu-id="47a62-107">説明</span><span class="sxs-lookup"><span data-stu-id="47a62-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="47a62-108">スタック ポインター、または x86 で enter スタック ポインター (ESP) プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="47a62-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="47a62-109">フレームのオフセット、または x86 で EBP レジスタ プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="47a62-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="47a62-110">命令ポインター、または x86 で enter 命令ポインター (EIP) プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="47a62-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47a62-111">コメント</span><span class="sxs-lookup"><span data-stu-id="47a62-111">Remarks</span></span>  
 <span data-ttu-id="47a62-112">スタック トレース関数は、通常、アドレス、フレームのオフセット、およびスタック アドレスのみを返す必要があるため、必要に応じて、使用して、`SimpleContext`ではなく、大きな構造`CONTEXT`構造体。</span><span class="sxs-lookup"><span data-stu-id="47a62-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47a62-113">要件</span><span class="sxs-lookup"><span data-stu-id="47a62-113">Requirements</span></span>  
 <span data-ttu-id="47a62-114">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="47a62-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47a62-115">**ヘッダー:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="47a62-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="47a62-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47a62-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a62-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="47a62-117">See Also</span></span>  
 [<span data-ttu-id="47a62-118">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="47a62-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="47a62-119">デバッグ</span><span class="sxs-lookup"><span data-stu-id="47a62-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
