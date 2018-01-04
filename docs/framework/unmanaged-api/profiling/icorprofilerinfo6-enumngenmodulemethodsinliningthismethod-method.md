---
title: "ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e11dd1c24001c764c82ed3f11336873ee57b2e9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a><span data-ttu-id="eb3a7-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="eb3a7-102">ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method</span></span>
<span data-ttu-id="eb3a7-103">[.NET Framework 4.6 およびそれ以降のバージョンでサポート]</span><span class="sxs-lookup"><span data-stu-id="eb3a7-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="eb3a7-104">特定の NGen モジュールとインライン特定のメソッドで定義されているすべてのメソッドを列挙子を返します。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-104">Returns an enumerator to all the methods that          are defined in  a given NGen module and          inline a given method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb3a7-105">構文</span><span class="sxs-lookup"><span data-stu-id="eb3a7-105">Syntax</span></span>  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb3a7-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="eb3a7-106">Parameters</span></span>  
 `inlinersModuleId`  
 <span data-ttu-id="eb3a7-107">[in]NGen モジュールの識別子。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-107">[in] The identifier of an NGen module.</span></span>  
  
 `inlineeModuleId`  
 <span data-ttu-id="eb3a7-108">[in]定義するモジュールの識別子`inlineeMethodId`です。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-108">[in] The identifier of a module that defines `inlineeMethodId`.</span></span> <span data-ttu-id="eb3a7-109">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-109">See the Remarks section for more information.</span></span>  
  
 `inlineeMethodId`  
 <span data-ttu-id="eb3a7-110">[in]インライン関数では、メソッドの識別子。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-110">[in] The identifier of an inlined method.</span></span> <span data-ttu-id="eb3a7-111">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-111">See the Remarks section for more information.</span></span>  
  
 `incompleteData`  
 <span data-ttu-id="eb3a7-112">[out]フラグを示すかどうか`ppEnum`特定のメソッドにはインライン展開のすべてのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-112">[out] A flag that indicates whether `ppEnum` contains all methods inlining a given method.</span></span>  <span data-ttu-id="eb3a7-113">詳細については、次の「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-113">See the Remarks section for more information.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="eb3a7-114">[out]列挙子のアドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="eb3a7-114">[out] A pointer to the address of an enumerator</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb3a7-115">コメント</span><span class="sxs-lookup"><span data-stu-id="eb3a7-115">Remarks</span></span>  
 <span data-ttu-id="eb3a7-116">`inlineeModuleId`および`inlineeMethodId`インライン展開できない可能性があります、メソッドの完全な識別子を形成します。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-116">`inlineeModuleId` and `inlineeMethodId` together form the full identifier for the method that might be inlined.</span></span> <span data-ttu-id="eb3a7-117">たとえば、モジュール`A`メソッドを定義`Simple.Add`:</span><span class="sxs-lookup"><span data-stu-id="eb3a7-117">For example, assume module `A` defines a method `Simple.Add`:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 <span data-ttu-id="eb3a7-118">モジュール Bdefines `Fancy.AddTwice`:</span><span class="sxs-lookup"><span data-stu-id="eb3a7-118">and module Bdefines `Fancy.AddTwice`:</span></span>  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 <span data-ttu-id="eb3a7-119">によりもあると想定`Fancy.AddTwice`インライン呼び出しを`SimpleAdd`です。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-119">Lets also assume that `Fancy.AddTwice` inlines the call to `SimpleAdd`.</span></span> <span data-ttu-id="eb3a7-120">プロファイラーは、この列挙子を使用してモジュール B でどのインラインで定義されたすべてのメソッドを検索する可能性があります`Simple.Add`、結果の列挙は、`AddTwice`です。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-120">A profiler could use this enumerator to find all methods defined in module B which inline `Simple.Add`, and the result would enumerate `AddTwice`.</span></span>  <span data-ttu-id="eb3a7-121">`inlineeModuleId`モジュールの識別子は、 `A`、および`inlineeeMethodId`の識別子は、`Simple.Add(int a, int b)`です。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-121">`inlineeModuleId` is the identifier of module `A`,   and `inlineeeMethodId` is the identifier of `Simple.Add(int a, int b)`.</span></span>  
  
 <span data-ttu-id="eb3a7-122">場合`incompleteData`が関数の後に true を返します、列挙子は、インライン展開のすべてのメソッドの指定されたメソッドを含んでいませんしません。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-122">If `incompleteData` is true after the function returns, the enumerator does not contain all methods inlining a given method.</span></span> <span data-ttu-id="eb3a7-123">これは、1 つの場合に発生することができますかより直接的または間接的な依存関係のインライン モジュールをまだ読み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-123">This can happen when one or more direct or indirect dependencies of inliners module haven't been loaded yet.</span></span> <span data-ttu-id="eb3a7-124">プロファイラーは、データの正確性を必要とする場合、複数のモジュールが読み込まれるときに、可能であれば 各モジュールの読み込み後に再試行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-124">If a profiler needs accurate data, it should retry later when more modules are loaded, preferably on each module load.</span></span>  
  
 <span data-ttu-id="eb3a7-125">`EnumNgenModuleMethodsInliningThisMethod`で制限を回避するメソッドを使用できます ReJIT のインライン展開されます。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-125">The `EnumNgenModuleMethodsInliningThisMethod` method can be used to work around limitations on inlining for ReJIT.</span></span> <span data-ttu-id="eb3a7-126">ReJIT により、プロファイラー メソッドの実装を変更し、その場での新しいコードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-126">ReJIT lets a profiler change the implementation of a method and then create new code for it on the fly.</span></span> <span data-ttu-id="eb3a7-127">たとえば、変更お`Simple.Add`次のようにします。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-127">For example, we could change `Simple.Add` as follows:</span></span>  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 <span data-ttu-id="eb3a7-128">ただしため`Fancy.AddTwice`がインライン関数では既に`Simple.Add`、これは引き続き以前と同様の動作は同じにします。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-128">However because `Fancy.AddTwice` has already inlined `Simple.Add`, it continues to have the same behavior as before.</span></span> <span data-ttu-id="eb3a7-129">その制限を回避するには、呼び出し元がすべてのモジュールにそのインラインのすべてのメソッドを検索する`Simple.Add`を使用して`ICorProfilerInfo5::RequestRejit`これらのメソッドごとにします。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-129">To work around that limitation, the caller has to search for all methods in all modules that inline `Simple.Add` and use `ICorProfilerInfo5::RequestRejit` on each of those methods.</span></span> <span data-ttu-id="eb3a7-130">新しい動作は、メソッドは、再コンパイル、`Simple.Add`従来の動作の代わりにします。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-130">When the methods are re-compiled, they will have the new behavior of `Simple.Add` instead of the old behavior.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb3a7-131">必要条件</span><span class="sxs-lookup"><span data-stu-id="eb3a7-131">Requirements</span></span>  
 <span data-ttu-id="eb3a7-132">**プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="eb3a7-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb3a7-133">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb3a7-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb3a7-134">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb3a7-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb3a7-135">**.NET framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb3a7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb3a7-136">参照</span><span class="sxs-lookup"><span data-stu-id="eb3a7-136">See Also</span></span>  
 [<span data-ttu-id="eb3a7-137">ICorProfilerInfo6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="eb3a7-137">ICorProfilerInfo6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
