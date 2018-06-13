---
title: LoggingLevelEnum 列挙型
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 331065d4aae82c66b9ebd82e99427501c3ba8a98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435956"
---
# <a name="logginglevelenum-enumeration"></a><span data-ttu-id="4db23-102">LoggingLevelEnum 列挙型</span><span class="sxs-lookup"><span data-stu-id="4db23-102">LoggingLevelEnum Enumeration</span></span>
<span data-ttu-id="4db23-103">マネージ スレッドがイベントを記録する際にイベント ログに書き込まれる説明メッセージの重大度レベルを示します。</span><span class="sxs-lookup"><span data-stu-id="4db23-103">Indicates the severity level of a descriptive message that is written to the event log when a managed thread logs an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4db23-104">構文</span><span class="sxs-lookup"><span data-stu-id="4db23-104">Syntax</span></span>  
  
```  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a><span data-ttu-id="4db23-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="4db23-105">Members</span></span>  
  
|<span data-ttu-id="4db23-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4db23-106">Member</span></span>|<span data-ttu-id="4db23-107">説明</span><span class="sxs-lookup"><span data-stu-id="4db23-107">Description</span></span>|  
|------------|-----------------|  
|`LTraceLevel0`|<span data-ttu-id="4db23-108">メッセージは、トレース レベル 0 です。</span><span class="sxs-lookup"><span data-stu-id="4db23-108">The message is a trace level 0.</span></span>|  
|`LTraceLevel1`|<span data-ttu-id="4db23-109">メッセージは、トレース レベル 1 です。</span><span class="sxs-lookup"><span data-stu-id="4db23-109">The message is a trace level 1.</span></span>|  
|`LTraceLevel2`|<span data-ttu-id="4db23-110">メッセージは、トレース レベル 2 です。</span><span class="sxs-lookup"><span data-stu-id="4db23-110">The message is a trace level 2.</span></span>|  
|`LTraceLevel3`|<span data-ttu-id="4db23-111">メッセージは、トレース レベル 3 です。</span><span class="sxs-lookup"><span data-stu-id="4db23-111">The message is a trace level 3.</span></span>|  
|`LTraceLevel4`|<span data-ttu-id="4db23-112">メッセージは、トレース レベル 4 です。</span><span class="sxs-lookup"><span data-stu-id="4db23-112">The message is a trace level 4.</span></span>|  
|`LStatusLevel0`|<span data-ttu-id="4db23-113">メッセージは、ステータス レベル 0 です。</span><span class="sxs-lookup"><span data-stu-id="4db23-113">The message is a status level 0.</span></span>|  
|`LStatusLevel1`|<span data-ttu-id="4db23-114">メッセージは、レベル 1 の状態です。</span><span class="sxs-lookup"><span data-stu-id="4db23-114">The message is a status level 1.</span></span>|  
|`LStatusLevel2`|<span data-ttu-id="4db23-115">メッセージは、ステータス レベル 2 です。</span><span class="sxs-lookup"><span data-stu-id="4db23-115">The message is a status level 2.</span></span>|  
|`LStatusLevel3`|<span data-ttu-id="4db23-116">メッセージは、ステータス レベル 3 です。</span><span class="sxs-lookup"><span data-stu-id="4db23-116">The message is a status level 3.</span></span>|  
|`LStatusLevel4`|<span data-ttu-id="4db23-117">メッセージは、ステータス レベル 4 です。</span><span class="sxs-lookup"><span data-stu-id="4db23-117">The message is a status level 4.</span></span>|  
|`LWarningLevel`|<span data-ttu-id="4db23-118">メッセージは、警告レベルです。</span><span class="sxs-lookup"><span data-stu-id="4db23-118">The message is a warning level.</span></span>|  
|`LErrorLevel`|<span data-ttu-id="4db23-119">メッセージは、エラー レベルです。</span><span class="sxs-lookup"><span data-stu-id="4db23-119">The message is an error level.</span></span>|  
|`LPanicLevel`|<span data-ttu-id="4db23-120">メッセージは、重大レベルです。</span><span class="sxs-lookup"><span data-stu-id="4db23-120">The message is a panic level.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4db23-121">コメント</span><span class="sxs-lookup"><span data-stu-id="4db23-121">Remarks</span></span>  
 <span data-ttu-id="4db23-122">共通言語ランタイム (CLR) を呼び出す、 [icordebugmanagedcallback::logmessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)マネージ スレッドがイベントを記録するデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="4db23-122">The common language runtime (CLR) calls the [ICorDebugManagedCallback::LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) method to notify the debugger that a managed thread has logged an event.</span></span> <span data-ttu-id="4db23-123">CLR の値を渡す、`LoggingLevelEnum`マネージ スレッドが、イベント ログに書き込んで、メッセージの重大度レベルを示す列挙体です。</span><span class="sxs-lookup"><span data-stu-id="4db23-123">The CLR passes a value of the `LoggingLevelEnum` enumeration to indicate the severity level of the message that the managed thread wrote to the event log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4db23-124">要件</span><span class="sxs-lookup"><span data-stu-id="4db23-124">Requirements</span></span>  
 <span data-ttu-id="4db23-125">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="4db23-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4db23-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4db23-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4db23-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4db23-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4db23-128">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4db23-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4db23-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="4db23-129">See Also</span></span>  
 <xref:System.Diagnostics.EventLog>  
 [<span data-ttu-id="4db23-130">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="4db23-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
