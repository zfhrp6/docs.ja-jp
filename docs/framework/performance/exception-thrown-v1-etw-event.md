---
title: Exception Thrown_V1 ETW イベント
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dafa5846f779276ab81e8e30e7c7a50b9fbff853
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="5e77f-102">Exception Thrown_V1 ETW イベント</span><span class="sxs-lookup"><span data-stu-id="5e77f-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="5e77f-103">このイベントは、スローされる例外に関する情報をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="5e77f-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="5e77f-104">イベントが発生するキーワードとイベントのレベルを次の表に示します </span><span class="sxs-lookup"><span data-stu-id="5e77f-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="5e77f-105">(詳細については、「 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md)」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="5e77f-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="5e77f-106">イベントを発生させるキーワード</span><span class="sxs-lookup"><span data-stu-id="5e77f-106">Keyword for raising the event</span></span>|<span data-ttu-id="5e77f-107">レベル</span><span class="sxs-lookup"><span data-stu-id="5e77f-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="5e77f-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="5e77f-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="5e77f-109">警告 (2)</span><span class="sxs-lookup"><span data-stu-id="5e77f-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="5e77f-110">次の表にイベント情報を示します。</span><span class="sxs-lookup"><span data-stu-id="5e77f-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="5e77f-111">event</span><span class="sxs-lookup"><span data-stu-id="5e77f-111">Event</span></span>|<span data-ttu-id="5e77f-112">イベント ID</span><span class="sxs-lookup"><span data-stu-id="5e77f-112">Event ID</span></span>|<span data-ttu-id="5e77f-113">いつ発生するか</span><span class="sxs-lookup"><span data-stu-id="5e77f-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="5e77f-114">80</span><span class="sxs-lookup"><span data-stu-id="5e77f-114">80</span></span>|<span data-ttu-id="5e77f-115">マネージ例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="5e77f-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="5e77f-116">次の表にイベント データを示します。</span><span class="sxs-lookup"><span data-stu-id="5e77f-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="5e77f-117">フィールド名</span><span class="sxs-lookup"><span data-stu-id="5e77f-117">Field name</span></span>|<span data-ttu-id="5e77f-118">データ型</span><span class="sxs-lookup"><span data-stu-id="5e77f-118">Data type</span></span>|<span data-ttu-id="5e77f-119">説明</span><span class="sxs-lookup"><span data-stu-id="5e77f-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="5e77f-120">例外の種類</span><span class="sxs-lookup"><span data-stu-id="5e77f-120">Exception Type</span></span>|<span data-ttu-id="5e77f-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5e77f-121">win:UnicodeString</span></span>|<span data-ttu-id="5e77f-122">例外の種類 (`System.NullReferenceException` など)。</span><span class="sxs-lookup"><span data-stu-id="5e77f-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="5e77f-123">例外メッセージ</span><span class="sxs-lookup"><span data-stu-id="5e77f-123">Exception Message</span></span>|<span data-ttu-id="5e77f-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5e77f-124">win:UnicodeString</span></span>|<span data-ttu-id="5e77f-125">実際の例外メッセージ。</span><span class="sxs-lookup"><span data-stu-id="5e77f-125">Actual exception message.</span></span>|  
|<span data-ttu-id="5e77f-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="5e77f-126">EIPCodeThrow</span></span>|<span data-ttu-id="5e77f-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="5e77f-127">win:Pointer</span></span>|<span data-ttu-id="5e77f-128">例外が発生した命令ポインター。</span><span class="sxs-lookup"><span data-stu-id="5e77f-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="5e77f-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="5e77f-129">ExceptionHR</span></span>|<span data-ttu-id="5e77f-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5e77f-130">win:UInt32</span></span>|<span data-ttu-id="5e77f-131">例外 [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679)。</span><span class="sxs-lookup"><span data-stu-id="5e77f-131">Exception [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="5e77f-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="5e77f-132">ExceptionFlags</span></span>|<span data-ttu-id="5e77f-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5e77f-133">win:UInt16</span></span>|<span data-ttu-id="5e77f-134">0x01: HasInnerException (Visual Basic のドキュメントで「[CLR ETW イベント](../../../docs/framework/performance/clr-etw-events.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="5e77f-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="5e77f-135">0x02: IsNestedException。</span><span class="sxs-lookup"><span data-stu-id="5e77f-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="5e77f-136">0x04: IsRethrownException。</span><span class="sxs-lookup"><span data-stu-id="5e77f-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="5e77f-137">0x08: IsCorruptedStateException (プロセスの状態が破損していることを示す。MSDN で「[破損状態例外を処理する](http://go.microsoft.com/fwlink/?LinkId=179681)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="5e77f-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](http://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="5e77f-138">0x10: IsCLSCompliant (<xref:System.Exception> から派生した例外は CLS 準拠で、それ以外は CLS 非準拠)。</span><span class="sxs-lookup"><span data-stu-id="5e77f-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="5e77f-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5e77f-139">ClrInstanceID</span></span>|<span data-ttu-id="5e77f-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5e77f-140">win:UInt16</span></span>|<span data-ttu-id="5e77f-141">CLR または CoreCLR のインスタンスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="5e77f-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e77f-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e77f-142">See Also</span></span>  
 [<span data-ttu-id="5e77f-143">CLR ETW イベント</span><span class="sxs-lookup"><span data-stu-id="5e77f-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
