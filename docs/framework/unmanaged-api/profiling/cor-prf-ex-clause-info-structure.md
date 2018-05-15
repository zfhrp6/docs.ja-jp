---
title: COR_PRF_EX_CLAUSE_INFO 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3cf8b8735fc10b741d13b041eedc3e96607bef4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="corprfexclauseinfo-structure"></a><span data-ttu-id="1fa70-102">COR_PRF_EX_CLAUSE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="1fa70-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="1fa70-103">特定の例外句インスタンスおよび関連するフレームに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="1fa70-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fa70-104">構文</span><span class="sxs-lookup"><span data-stu-id="1fa70-104">Syntax</span></span>  
  
```  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="1fa70-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="1fa70-105">Members</span></span>  
  
|<span data-ttu-id="1fa70-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="1fa70-106">Member</span></span>|<span data-ttu-id="1fa70-107">説明</span><span class="sxs-lookup"><span data-stu-id="1fa70-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="1fa70-108">値、 [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md)または出た例外句だけ入力したコードの種類を指定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="1fa70-108">A value of the [COR_PRF_CLAUSE_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="1fa70-109">句のハンドラーのネイティブ エントリ ポイント-X86 EIP レジスタの内容などです。</span><span class="sxs-lookup"><span data-stu-id="1fa70-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="1fa70-110">句のハンドラーの論理的なフレームへのポインター-X86 EBP レジスタの内容などです。</span><span class="sxs-lookup"><span data-stu-id="1fa70-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="1fa70-111">シャドウ スタックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1fa70-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="1fa70-112">この値は、BSP レジスタの内容は、IA64 にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="1fa70-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fa70-113">コメント</span><span class="sxs-lookup"><span data-stu-id="1fa70-113">Remarks</span></span>  
 <span data-ttu-id="1fa70-114">例外の通知が受信されると、 [icorprofilerinfo 2::getnotifiedexceptionclauseinfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)例外句のネイティブのアドレスとフレームの情報を取得するために使用できます (`catch` / `finally`/フィルター) を実行する前に、またはが実行されているだけです。</span><span class="sxs-lookup"><span data-stu-id="1fa70-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="1fa70-115">例外句の実行には、共通言語ランタイム (CLR) からこれらのコールバックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="1fa70-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
-   [<span data-ttu-id="1fa70-116">Icorprofilercallback::exceptioncatcherenter</span><span class="sxs-lookup"><span data-stu-id="1fa70-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)  
  
-   [<span data-ttu-id="1fa70-117">Icorprofilercallback::exceptionunwindfinallyenter</span><span class="sxs-lookup"><span data-stu-id="1fa70-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
-   [<span data-ttu-id="1fa70-118">Icorprofilercallback::exceptionsearchfilterenter</span><span class="sxs-lookup"><span data-stu-id="1fa70-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
-   [<span data-ttu-id="1fa70-119">Icorprofilercallback::exceptioncatcherleave</span><span class="sxs-lookup"><span data-stu-id="1fa70-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)  
  
-   [<span data-ttu-id="1fa70-120">Icorprofilercallback::exceptionunwindfinallyleave</span><span class="sxs-lookup"><span data-stu-id="1fa70-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
-   [<span data-ttu-id="1fa70-121">Icorprofilercallback::exceptionsearchfilterleave</span><span class="sxs-lookup"><span data-stu-id="1fa70-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="1fa70-122">要件</span><span class="sxs-lookup"><span data-stu-id="1fa70-122">Requirements</span></span>  
 <span data-ttu-id="1fa70-123">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1fa70-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fa70-124">**ヘッダー:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="1fa70-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1fa70-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fa70-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fa70-126">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fa70-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fa70-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="1fa70-127">See Also</span></span>  
 [<span data-ttu-id="1fa70-128">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="1fa70-128">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
