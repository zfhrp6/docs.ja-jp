---
title: "デバッグのインターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
caps.latest.revision: "32"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: de2469d15eef40b9ef283d67aeca429d9d96a7ef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-interfaces"></a><span data-ttu-id="23864-102">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-102">Debugging Interfaces</span></span>
<span data-ttu-id="23864-103">ここでは、共通言語ランタイム (CLR: Common Language Runtime) で実行するプログラムのデバッグを処理するアンマネージ インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="23864-103">This section describes the unmanaged interfaces that handle the debugging of a program that is executing in the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23864-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="23864-104">In This Section</span></span>  
 [<span data-ttu-id="23864-105">ICLRDataEnumMemoryRegions インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-105">ICLRDataEnumMemoryRegions Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 <span data-ttu-id="23864-106">呼び出し元が指定したメモリ範囲を列挙するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-106">Provides a method to enumerate regions of memory that are specified by callers.</span></span>  
  
 [<span data-ttu-id="23864-107">ICLRDataEnumMemoryRegionsCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-107">ICLRDataEnumMemoryRegionsCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 <span data-ttu-id="23864-108">メモリの指定された領域を列挙した結果の `EnumMemoryRegions` をデバッガーにレポートするコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-108">Provides a callback method for `EnumMemoryRegions` to report to the debugger, the result of an attempt to enumerate a specified region of memory.</span></span>  
  
 [<span data-ttu-id="23864-109">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-109">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 <span data-ttu-id="23864-110">対象の CLR プロセスと対話するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-110">Provides methods for interaction with a target CLR process.</span></span>  
  
 [<span data-ttu-id="23864-111">ICLRDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-111">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 <span data-ttu-id="23864-112">データ アクセス サービス層で使用して対象プロセスの仮想メモリ領域を操作する、`ICLRDataTarget` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="23864-112">A subclass of `ICLRDataTarget` that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
 [<span data-ttu-id="23864-113">ICLRDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-113">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 <span data-ttu-id="23864-114">サブクラス[ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)例外情報へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-114">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
 [<span data-ttu-id="23864-115">ICLRDebugging インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-115">ICLRDebugging Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 <span data-ttu-id="23864-116">デバッグ用にモジュールの読み込みとアンロードを処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-116">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
 [<span data-ttu-id="23864-117">ICLRDebuggingLibraryProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-117">ICLRDebuggingLibraryProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 <span data-ttu-id="23864-118">含まれています、 [ProvideLibrary メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)メソッドで、コールバック インターフェイスの共通言語ランタイム バージョンに固有の上にロードし、要求時にデバッグ ライブラリをライブラリ プロバイダーを取得します。</span><span class="sxs-lookup"><span data-stu-id="23864-118">Includes the [ProvideLibrary Method](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
 [<span data-ttu-id="23864-119">ICLRMetadataLocator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-119">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 <span data-ttu-id="23864-120">データ アクセス サービス層で使用して、対象プロセス内のアセンブリのメタデータを見つけるためのインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-120">Interface used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
 [<span data-ttu-id="23864-121">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-121">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 <span data-ttu-id="23864-122">開発者が CLR 環境でアプリケーションをデバッグできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-122">Provides methods that allow developers to debug applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="23864-123">ICorDebugAppDomain Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-123">ICorDebugAppDomain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 <span data-ttu-id="23864-124">アプリケーション ドメインをデバッグするためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-124">Provides methods for debugging application domains.</span></span>  
  
 [<span data-ttu-id="23864-125">ICorDebugAppDomain2 Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-125">ICorDebugAppDomain2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 <span data-ttu-id="23864-126">配列、ポインター、関数ポインター、および ByRef 型を使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-126">Provides methods to work with arrays, pointers, function pointers, and ByRef types.</span></span> <span data-ttu-id="23864-127">これは、`ICorDebugAppDomain` インターフェイスの機能を拡張するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-127">This interface is an extension of the `ICorDebugAppDomain` interface.</span></span>  
  
 [<span data-ttu-id="23864-128">ICorDebugAppDomain3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-128">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 <span data-ttu-id="23864-129">アプリケーション ドメインで [!INCLUDE[wrt](../../../../includes/wrt-md.md)] 型を操作するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-129">Provides methods to work with the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain.</span></span> <span data-ttu-id="23864-130">このインターフェイスは、`ICorDebugAppDomain` インターフェイスと `ICorDebugAppDomain2` インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="23864-130">This interface is an extension of the `ICorDebugAppDomain` and `ICorDebugAppDomain2` interfaces.</span></span>  
  
 [<span data-ttu-id="23864-131">ICorDebugAppDomain4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-131">ICorDebugAppDomain4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 <span data-ttu-id="23864-132">論理的に拡張し、 [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) COM 呼び出し可能ラッパーからマネージ オブジェクトを取得するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-132">Logically extends the [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) interface to get a managed object from a COM callable wrapper.</span></span>  
  
 [<span data-ttu-id="23864-133">ICorDebugAppDomainEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-133">ICorDebugAppDomainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 <span data-ttu-id="23864-134">列挙体の次の位置から、指定した数の `ICorDebugAppDomain` の値を返すメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-134">Provides a method that returns a specified number of `ICorDebugAppDomain` values starting at the next location in the enumeration.</span></span>  
  
 [<span data-ttu-id="23864-135">ICorDebugArrayValue Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-135">ICorDebugArrayValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 <span data-ttu-id="23864-136">1 次元または多次元の配列を表す `ICorDebugHeapValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="23864-136">A subclass of `ICorDebugHeapValue` that represents a single-dimensional or multi-dimensional array.</span></span>  
  
 [<span data-ttu-id="23864-137">ICorDebugAssembly Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-137">ICorDebugAssembly Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 <span data-ttu-id="23864-138">アセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-138">Represents an assembly.</span></span>  
  
 [<span data-ttu-id="23864-139">ICorDebugAssembly2 Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-139">ICorDebugAssembly2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 <span data-ttu-id="23864-140">アセンブリを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-140">Represents an assembly.</span></span> <span data-ttu-id="23864-141">これは、`ICorDebugAssembly` インターフェイスの機能を拡張するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-141">This interface is an extension of the `ICorDebugAssembly` interface.</span></span>  
  
 [<span data-ttu-id="23864-142">ICorDebugAssembly3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-142">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 <span data-ttu-id="23864-143">論理的に拡張し、 [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)のコンテナー アセンブリとそのコンテナー内のサポートを提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-143">Logically extends the [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md) interface to provide support for container assemblies and their contained assemblies.</span></span> <span data-ttu-id="23864-144">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-144">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-145">ICorDebugAssemblyEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-145">ICorDebugAssemblyEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 <span data-ttu-id="23864-146">`ICorDebugEnum` メソッドを実装し、`ICorDebugAssembly` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="23864-146">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugAssembly` arrays.</span></span>  
  
 [<span data-ttu-id="23864-147">ICorDebugBlockingObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-147">ICorDebugBlockingObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 <span data-ttu-id="23864-148">一覧については、列挙子を提供[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)構造体。</span><span class="sxs-lookup"><span data-stu-id="23864-148">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>  
  
 [<span data-ttu-id="23864-149">ICorDebugBoxValue Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-149">ICorDebugBoxValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 <span data-ttu-id="23864-150">ボックス化された値クラスのオブジェクトを表す `ICorDebugHeapValue` のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="23864-150">A subclass of `ICorDebugHeapValue` that represents a boxed value class object.</span></span>  
  
 [<span data-ttu-id="23864-151">ICorDebugBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-151">ICorDebugBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 <span data-ttu-id="23864-152">関数のブレークポイント、または値のウォッチ ポイントを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-152">Represents a breakpoint in a function or a watch point on a value.</span></span>  
  
 [<span data-ttu-id="23864-153">ICorDebugBreakpointEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-153">ICorDebugBreakpointEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 <span data-ttu-id="23864-154">`ICorDebugEnum` メソッドを実装し、`ICorDebugBreakpoint` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="23864-154">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugBreakpoint` arrays.</span></span>  
  
 [<span data-ttu-id="23864-155">ICorDebugChain Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-155">ICorDebugChain Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 <span data-ttu-id="23864-156">物理呼び出し履歴または論理呼び出し履歴のセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-156">Represents a segment of a physical or logical call stack.</span></span>  
  
 [<span data-ttu-id="23864-157">ICorDebugChainEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-157">ICorDebugChainEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 <span data-ttu-id="23864-158">`ICorDebugEnum` メソッドを実装し、`ICorDebugChain` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="23864-158">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugChain` arrays.</span></span>  
  
 [<span data-ttu-id="23864-159">ICorDebugClass Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-159">ICorDebugClass Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 <span data-ttu-id="23864-160">基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。</span><span class="sxs-lookup"><span data-stu-id="23864-160">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="23864-161">型がジェネリックの場合、`ICorDebugClass` はインスタンス化されないジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="23864-161">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
 [<span data-ttu-id="23864-162">ICorDebugClass2 Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-162">ICorDebugClass2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 <span data-ttu-id="23864-163">ジェネリック、または <xref:System.Type> 型のメソッド パラメーターを持つクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-163">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="23864-164">このインターフェイスは、`ICorDebugClass` の機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="23864-164">This interface extends `ICorDebugClass`.</span></span>  
  
 [<span data-ttu-id="23864-165">ICorDebugCode Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-165">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 <span data-ttu-id="23864-166">Microsoft Intermediate Language (MSIL) コードまたはネイティブ コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-166">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
 [<span data-ttu-id="23864-167">ICorDebugCode2 Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-167">ICorDebugCode2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 <span data-ttu-id="23864-168">`ICorDebugCode` の機能を拡張するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-168">Provides methods that extend the capabilities of `ICorDebugCode`.</span></span>  
  
 [<span data-ttu-id="23864-169">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-169">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 <span data-ttu-id="23864-170">拡張メソッドを提供[ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)と[ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)マネージ戻り値に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-170">Provides a method that extends [ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md) and [ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md) to provide information about a managed return value.</span></span>  
  
 [<span data-ttu-id="23864-171">ICorDebugCode4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-171">ICorDebugCode4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 <span data-ttu-id="23864-172">ローカル変数と関数の引数を列挙するデバッガーを有効にするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-172">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="23864-173">ICorDebugCodeEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-173">ICorDebugCodeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 <span data-ttu-id="23864-174">`ICorDebugEnum` メソッドを実装し、`ICorDebugCode` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="23864-174">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugCode` arrays.</span></span>  
  
 [<span data-ttu-id="23864-175">ICorDebugComObjectValue のインターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-175">ICorDebugComObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 <span data-ttu-id="23864-176">キャッシュされたインターフェイス オブジェクトを取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-176">Provides methods to retrieve cached interface objects.</span></span>  
  
 [<span data-ttu-id="23864-177">ICorDebugContext Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-177">ICorDebugContext Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 <span data-ttu-id="23864-178">コンテキストのオブジェクトを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-178">Represents a context object.</span></span> <span data-ttu-id="23864-179">このインターフェイスはまだ実装されていません。</span><span class="sxs-lookup"><span data-stu-id="23864-179">This interface has not been implemented yet.</span></span>  
  
 [<span data-ttu-id="23864-180">ICorDebugController Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-180">ICorDebugController Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 <span data-ttu-id="23864-181">コードの実行コンテキストを制御できる <xref:System.Diagnostics.Process> または <xref:System.AppDomain> のスコープを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-181">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
 [<span data-ttu-id="23864-182">ICorDebugDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-182">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 <span data-ttu-id="23864-183">特定のターゲット プロセスにアクセスするためのコールバック インターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="23864-183">Provides a callback interface that provides access to a particular target process.</span></span>  
  
 [<span data-ttu-id="23864-184">ICorDebugDataTarget2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-184">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 <span data-ttu-id="23864-185">論理的に拡張し、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-185">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="23864-186">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-186">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-187">ICorDebugDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-187">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 <span data-ttu-id="23864-188">論理的に拡張し、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)読み込まれたモジュールに関する情報を提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-188">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span> <span data-ttu-id="23864-189">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-189">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-190">ICorDebugDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-190">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 <span data-ttu-id="23864-191">すべての `ICorDebug` デバッグ イベントを派生させる基本インターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="23864-191">Defines the base interface from which all `ICorDebug` debug events derive.</span></span> <span data-ttu-id="23864-192">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-192">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-193">ICorDebugEditAndContinueErrorInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-193">ICorDebugEditAndContinueErrorInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 <span data-ttu-id="23864-194">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="23864-194">Obsolete.</span></span> <span data-ttu-id="23864-195">このインターフェイスは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="23864-195">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="23864-196">ICorDebugEditAndContinueSnapshot Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-196">ICorDebugEditAndContinueSnapshot Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 <span data-ttu-id="23864-197">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="23864-197">Obsolete.</span></span> <span data-ttu-id="23864-198">このインターフェイスは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="23864-198">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="23864-199">ICorDebugEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-199">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 <span data-ttu-id="23864-200">デバッグ中の列挙子の抽象基底インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="23864-200">Serves as the abstract base interface for debugging enumerators.</span></span>  
  
 [<span data-ttu-id="23864-201">ICorDebugErrorInfoEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-201">ICorDebugErrorInfoEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 <span data-ttu-id="23864-202">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="23864-202">Obsolete.</span></span> <span data-ttu-id="23864-203">このインターフェイスは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="23864-203">Do not use this interface.</span></span>  
  
 [<span data-ttu-id="23864-204">ICorDebugEval Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-204">ICorDebugEval Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 <span data-ttu-id="23864-205">デバッガーが、デバッグ中のコードのコンテキスト内でコードを実行できるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-205">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
 [<span data-ttu-id="23864-206">ICorDebugEval2 Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-206">ICorDebugEval2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 <span data-ttu-id="23864-207">ジェネリック型をサポートできるように `ICorDebugEval` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="23864-207">Extends `ICorDebugEval` to provide support for generic types.</span></span>  
  
 [<span data-ttu-id="23864-208">ICorDebugExceptionDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-208">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 <span data-ttu-id="23864-209">拡張、 [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)例外イベントをサポートするインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-209">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span> <span data-ttu-id="23864-210">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-210">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-211">ICorDebugExceptionObjectCallStackEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-211">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 <span data-ttu-id="23864-212">例外オブジェクトに埋め込まれているコール スタックの情報の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-212">Provides an enumerator for call stack information that is embedded in an exception object.</span></span>  
  
 [<span data-ttu-id="23864-213">ICorDebugExceptionObjectValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-213">ICorDebugExceptionObjectValue Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 <span data-ttu-id="23864-214">拡張、 [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)マネージ例外オブジェクトからスタック トレース情報を提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-214">Extends the [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md) interface to provide stack trace information from a managed exception object.</span></span>  
  
 [<span data-ttu-id="23864-215">ICorDebugFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-215">ICorDebugFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 <span data-ttu-id="23864-216">現在のスタックのフレームを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-216">Represents a frame on the current stack.</span></span>  
  
 [<span data-ttu-id="23864-217">ICorDebugFrameEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-217">ICorDebugFrameEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 <span data-ttu-id="23864-218">`ICorDebugEnum` メソッドを実装し、`ICorDebugFrame` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="23864-218">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugFrame` arrays.</span></span>  
  
 [<span data-ttu-id="23864-219">ICorDebugFunction Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-219">ICorDebugFunction Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 <span data-ttu-id="23864-220">マネージ関数またはマネージ メソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-220">Represents a managed function or method.</span></span>  
  
 [<span data-ttu-id="23864-221">ICorDebugFunction2 Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-221">ICorDebugFunction2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 <span data-ttu-id="23864-222">`ICorDebugFunction` を論理的に拡張して、"マイ コードのみ" ステップ実行によるデバッグをサポートします。</span><span class="sxs-lookup"><span data-stu-id="23864-222">Logically extends `ICorDebugFunction` to provide support for Just My Code step-through debugging.</span></span>  
  
 [<span data-ttu-id="23864-223">ICorDebugFunction3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-223">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 <span data-ttu-id="23864-224">論理的に拡張し、 [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) ReJIT 要求からコードへのアクセスを提供するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-224">Logically extends the [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) interface to provide access to code from a ReJIT request.</span></span>  
  
 [<span data-ttu-id="23864-225">ICorDebugFunctionBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-225">ICorDebugFunctionBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 <span data-ttu-id="23864-226">関数内のブレークポイントをサポートするように `ICorDebugBreakpoint` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="23864-226">Extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
 [<span data-ttu-id="23864-227">ICorDebugGCReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-227">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 <span data-ttu-id="23864-228">ガベージ コレクトされるオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-228">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
 [<span data-ttu-id="23864-229">ICorDebugGenericValue Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-229">ICorDebugGenericValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 <span data-ttu-id="23864-230">すべての値に適用する `ICorDebugValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="23864-230">A subclass of `ICorDebugValue` that applies to all values.</span></span> <span data-ttu-id="23864-231">このインターフェイスは、値に対して Get メソッドと Set メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-231">This interface provides Get and Set methods for the value.</span></span>  
  
 [<span data-ttu-id="23864-232">ICorDebugGuidToTypeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-232">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 <span data-ttu-id="23864-233">GUID およびその対応する `ICorDebugType` オブジェクトをマップするオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-233">Provides an enumerator for an object that maps GUIDs and their corresponding `ICorDebugType` objects.</span></span>  
  
 [<span data-ttu-id="23864-234">ICorDebugHandleValue Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-234">ICorDebugHandleValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 <span data-ttu-id="23864-235">デバッガーが作成したガベージ コレクションのハンドルへの参照値を表す `ICorDebugReferenceValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="23864-235">A subclass of `ICorDebugReferenceValue` that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
 [<span data-ttu-id="23864-236">ICorDebugHeapEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-236">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 <span data-ttu-id="23864-237">マネージ ヒープのオブジェクトの列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-237">Provides an enumerator for objects on the managed heap.</span></span>  
  
 [<span data-ttu-id="23864-238">ICorDebugHeapSegmentEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-238">ICorDebugHeapSegmentEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 <span data-ttu-id="23864-239">マネージ ヒープのメモリ領域の列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-239">Provides an enumerator for the memory regions of the managed heap.</span></span>  
  
 [<span data-ttu-id="23864-240">ICorDebugHeapValue Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-240">ICorDebugHeapValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 <span data-ttu-id="23864-241">CLR ガベージ コレクターによって収集されたオブジェクトを表す `ICorDebugValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="23864-241">A subclass of `ICorDebugValue` that represents an object that has been collected by the CLR garbage collector.</span></span>  
  
 [<span data-ttu-id="23864-242">ICorDebugHeapValue2 Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-242">ICorDebugHeapValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 <span data-ttu-id="23864-243">ランタイム ハンドルのサポートを提供する `ICorDebugHeapValue` の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="23864-243">An extension of `ICorDebugHeapValue` that provides support for runtime handles.</span></span>  
  
 [<span data-ttu-id="23864-244">ICorDebugHeapValue3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-244">ICorDebugHeapValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 <span data-ttu-id="23864-245">オブジェクトのモニター ロック プロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="23864-245">Exposes the monitor lock properties of objects.</span></span>  
  
 [<span data-ttu-id="23864-246">ICorDebugILCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-246">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 <span data-ttu-id="23864-247">中間言語 (IL) コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-247">Represents a segment of intermediate language (IL) code.</span></span>  
  
 [<span data-ttu-id="23864-248">ICorDebugILCode2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-248">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 <span data-ttu-id="23864-249">論理的に拡張し、 [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)に元のメソッド IL オフセットを関数のローカル変数シグネチャに対するトークンを返すし、プロファイラーのインストルメント化された中間言語 (IL) にマップするメソッドを提供するインターフェイスオフセットします。</span><span class="sxs-lookup"><span data-stu-id="23864-249">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
 [<span data-ttu-id="23864-250">ICorDebugILFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-250">ICorDebugILFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 <span data-ttu-id="23864-251">MSIL コードのスタック フレームを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-251">Represents a stack frame of MSIL code.</span></span>  
  
 [<span data-ttu-id="23864-252">ICorDebugILFrame2 Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-252">ICorDebugILFrame2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 <span data-ttu-id="23864-253">`ICorDebugILFrame` の論理拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="23864-253">A logical extension of `ICorDebugILFrame`.</span></span>  
  
 [<span data-ttu-id="23864-254">ICorDebugILFrame3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-254">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 <span data-ttu-id="23864-255">関数の戻り値をカプセル化するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-255">Provides a method that encapsulates the return value of a function.</span></span>  
  
 [<span data-ttu-id="23864-256">ICorDebugILFrame4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-256">ICorDebugILFrame4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 <span data-ttu-id="23864-257">ローカル変数にアクセスできるようにするメソッドおよび中間言語 (IL) コードのスタック フレームのコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-257">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="23864-258">パラメーターは、プロファイラーの ReJIT インストルメンテーションに追加される変数およびコードへデバッガーがアクセスできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="23864-258">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
 [<span data-ttu-id="23864-259">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-259">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 <span data-ttu-id="23864-260">インスタンス フィールドのデバッグ シンボル情報を表します。</span><span class="sxs-lookup"><span data-stu-id="23864-260">Represents the debug symbol information for an instance field.</span></span> <span data-ttu-id="23864-261">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-261">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-262">ICorDebugInternalFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-262">ICorDebugInternalFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 <span data-ttu-id="23864-263">デバッガーのフレーム種類を識別します。</span><span class="sxs-lookup"><span data-stu-id="23864-263">Identifies frame types for the debugger.</span></span>  
  
 [<span data-ttu-id="23864-264">ICorDebugInternalFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-264">ICorDebugInternalFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 <span data-ttu-id="23864-265">スタックのアドレス位置に関連するなどの内部フレームに関する情報を提供[ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="23864-265">Provides information about internal frames, including stack address and position in relation to [ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md) objects.</span></span>  
  
 [<span data-ttu-id="23864-266">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-266">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 <span data-ttu-id="23864-267">読み込まれたモジュールに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-267">Provides information about a loaded module.</span></span> <span data-ttu-id="23864-268">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-268">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-269">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-269">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 <span data-ttu-id="23864-270">デバッガーのコールバックを処理するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-270">Provides methods to process debugger callbacks.</span></span>  
  
 [<span data-ttu-id="23864-271">ICorDebugManagedCallback2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-271">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 <span data-ttu-id="23864-272">デバッガーの例外処理およびマネージ デバッグ アシスタント (MDA: Managed Debugging Assistants) をサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-272">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="23864-273">`ICorDebugManagedCallback2` は、`ICorDebugManagedCallback` の論理拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="23864-273">`ICorDebugManagedCallback2` is a logical extension of `ICorDebugManagedCallback`.</span></span>  
  
 [<span data-ttu-id="23864-274">ICorDebugManagedCallback3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-274">ICorDebugManagedCallback3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 <span data-ttu-id="23864-275">有効なカスタムのデバッガー通知が発生したことを示すコールバック メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-275">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
 [<span data-ttu-id="23864-276">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-276">ICorDebugMDA Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 <span data-ttu-id="23864-277">マネージ デバッグ アシスタント (MDA) メッセージを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-277">Represents a managed debugging assistant (MDA) message.</span></span>  
  
 [<span data-ttu-id="23864-278">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-278">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 <span data-ttu-id="23864-279">メモリ内のバッファーを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-279">Represents an in-memory buffer.</span></span> <span data-ttu-id="23864-280">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-280">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-281">ICorDebugMergedAssemblyRecord インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-281">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 <span data-ttu-id="23864-282">マージされたアセンブリに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-282">Provides information about a merged assembly.</span></span> <span data-ttu-id="23864-283">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-283">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-284">ICorDebugMetaDataLocator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-284">ICorDebugMetaDataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 <span data-ttu-id="23864-285">デバッガーにメタデータ情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-285">Provides metadata information to the debugger.</span></span>  
  
 [<span data-ttu-id="23864-286">ICorDebugModule Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-286">ICorDebugModule Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 <span data-ttu-id="23864-287">実行可能ファイルまたはダイナミック リンク ライブラリ (DLL: Dynamic-Link Library) のいずれかの CLR モジュールを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-287">Represents a CLR module, which is either an executable or a dynamic-link library (DLL).</span></span>  
  
 [<span data-ttu-id="23864-288">ICorDebugModule2 Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-288">ICorDebugModule2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 <span data-ttu-id="23864-289">`ICorDebugModule` の論理的な拡張機能として動作します。</span><span class="sxs-lookup"><span data-stu-id="23864-289">Serves as a logical extension to `ICorDebugModule`.</span></span>  
  
 [<span data-ttu-id="23864-290">ICorDebugModule3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-290">ICorDebugModule3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 <span data-ttu-id="23864-291">動的モジュールのシンボル リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="23864-291">Creates a symbol reader for a dynamic module.</span></span>  
  
 [<span data-ttu-id="23864-292">ICorDebugModuleBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-292">ICorDebugModuleBreakpoint Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 <span data-ttu-id="23864-293">特定のモジュールにアクセスできるように `ICorDebugBreakpoint` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="23864-293">Extends `ICorDebugBreakpoint` to provide access to specific modules.</span></span>  
  
 [<span data-ttu-id="23864-294">ICorDebugModuleDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-294">ICorDebugModuleDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 <span data-ttu-id="23864-295">拡張、 [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)モジュール レベルのイベントをサポートするインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-295">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span> <span data-ttu-id="23864-296">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-296">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-297">ICorDebugModuleEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-297">ICorDebugModuleEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 <span data-ttu-id="23864-298">`ICorDebugEnum` メソッドを実装し、`ICorDebugModule` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="23864-298">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugModule` arrays.</span></span>  
  
 [<span data-ttu-id="23864-299">ICorDebugMutableDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-299">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 <span data-ttu-id="23864-300">拡張、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)変更可能なデータ ターゲットをサポートするインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-300">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
 [<span data-ttu-id="23864-301">ICorDebugNativeFrame Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-301">ICorDebugNativeFrame Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 <span data-ttu-id="23864-302">ネイティブ フレームで使用される `ICorDebugFrame` の特化された実装。</span><span class="sxs-lookup"><span data-stu-id="23864-302">A specialized implementation of `ICorDebugFrame` used for native frames.</span></span>  
  
 [<span data-ttu-id="23864-303">ICorDebugNativeFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-303">ICorDebugNativeFrame2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 <span data-ttu-id="23864-304">子と親のフレームの関係をテストするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-304">Provides methods that test for child and parent frame relationships.</span></span>  
  
 [<span data-ttu-id="23864-305">ICorDebugObjectEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-305">ICorDebugObjectEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 <span data-ttu-id="23864-306">`ICorDebugEnum` メソッドを実装し、オブジェクトの配列を相対仮想アドレス (RVA: Relative Virtual Address) で列挙します。</span><span class="sxs-lookup"><span data-stu-id="23864-306">Implements `ICorDebugEnum` methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
 [<span data-ttu-id="23864-307">ICorDebugObjectValue Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-307">ICorDebugObjectValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 <span data-ttu-id="23864-308">オブジェクトが含まれた値を表す `ICorDebugValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="23864-308">A subclass of `ICorDebugValue` that represents a value that contains an object.</span></span>  
  
 [<span data-ttu-id="23864-309">ICorDebugObjectValue2 Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-309">ICorDebugObjectValue2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 <span data-ttu-id="23864-310">継承およびオーバーライドをサポートするように `ICorDebugObjectValue` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="23864-310">Extends `ICorDebugObjectValue` to support inheritance and overrides.</span></span>  
  
 [<span data-ttu-id="23864-311">ICorDebugProcess Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-311">ICorDebugProcess Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 <span data-ttu-id="23864-312">マネージ コードを実行しているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-312">Represents a process that is executing managed code.</span></span>  
  
 [<span data-ttu-id="23864-313">ICorDebugProcess2 Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-313">ICorDebugProcess2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 <span data-ttu-id="23864-314">`ICorDebugProcess` の論理拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="23864-314">A logical extension of `ICorDebugProcess`.</span></span>  
  
 [<span data-ttu-id="23864-315">ICorDebugProcess3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-315">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 <span data-ttu-id="23864-316">カスタムのデバッガー通知を制御します。</span><span class="sxs-lookup"><span data-stu-id="23864-316">Controls custom debugger notifications.</span></span>  
  
 [<span data-ttu-id="23864-317">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-317">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 <span data-ttu-id="23864-318">拡張、 [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)マネージ オブジェクトのガベージ コレクションに関する情報を提供して、デバッガーがアプリケーションからイメージを読み込むかどうかを決定する、マネージ ヒープへのアクセスをサポートするためにインターフェイスのローカルネイティブ イメージ キャッシュします。</span><span class="sxs-lookup"><span data-stu-id="23864-318">Extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application's local native image cache.</span></span>  
  
 [<span data-ttu-id="23864-319">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-319">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 <span data-ttu-id="23864-320">論理的に拡張し、 [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)ネイティブ例外デバッグ イベントや仮想モジュール分割でエンコードされたマネージ デバッグ イベントをデコードなどの機能を有効にするインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-320">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span> <span data-ttu-id="23864-321">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-321">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-322">ICorDebugProcess7 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-322">ICorDebugProcess7 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 <span data-ttu-id="23864-323">ターゲット プロセスでメモリ内のメタデータ更新を処理するようにデバッガーを構成するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-323">Provides a method that configures the debugger to handle in-memory metadata updates in the target process.</span></span>  
  
 [<span data-ttu-id="23864-324">ICorDebugProcess8 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-324">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 <span data-ttu-id="23864-325">論理的に拡張し、 [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)有効または無効に特定の種類のインターフェイス[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外コールバック。</span><span class="sxs-lookup"><span data-stu-id="23864-325">Logically extends the [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md) interface to enable or disable certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
 [<span data-ttu-id="23864-326">ICorDebugProcessEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-326">ICorDebugProcessEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 <span data-ttu-id="23864-327">`ICorDebugEnum` メソッドを実装し、`ICorDebugProcess` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="23864-327">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugProcess` arrays.</span></span>  
  
 [<span data-ttu-id="23864-328">ICorDebugReferenceValue Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-328">ICorDebugReferenceValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 <span data-ttu-id="23864-329">参照型をサポートする `ICorDebugValue` のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="23864-329">A subclass of `ICorDebugValue` that supports reference types.</span></span>  
  
 [<span data-ttu-id="23864-330">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-330">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 <span data-ttu-id="23864-331">現在コードを実行しているマシン上で使用できるレジスタ セットを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-331">Represents the set of registers available on the machine that is currently executing code.</span></span>  
  
 [<span data-ttu-id="23864-332">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-332">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 <span data-ttu-id="23864-333">64 を超えるレジスタを持つハードウェア プラットフォーム用に `ICorDebugRegisterSet` の機能を拡張します。</span><span class="sxs-lookup"><span data-stu-id="23864-333">Extends the capabilities of `ICorDebugRegisterSet` for hardware platforms that have more than 64 registers.</span></span>  
  
 [<span data-ttu-id="23864-334">ICorDebugRemote インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-334">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 <span data-ttu-id="23864-335">リモート ターゲット プロセスに対してマネージ デバッガーを起動または接続する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-335">Provides the ability to launch or attach a managed debugger to a remote target process.</span></span>  
  
 [<span data-ttu-id="23864-336">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-336">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 <span data-ttu-id="23864-337">開発者が CLR 環境で Silverlight ベース アプリケーションをデバッグできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-337">Provides methods that enable you to debug Silverlight-based applications in the CLR environment.</span></span>  
  
 [<span data-ttu-id="23864-338">ICorDebugRuntimeUnwindableFrame インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-338">ICorDebugRuntimeUnwindableFrame Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 <span data-ttu-id="23864-339">共通言語ランタイム (CLR: Common Language Runtime) でフレームをアンワインドする必要のあるアンマネージ メソッドに対してサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-339">Provides support for unmanaged methods that require the common language runtime (CLR) to unwind a frame.</span></span>  
  
 [<span data-ttu-id="23864-340">ICorDebugStackWalk インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-340">ICorDebugStackWalk Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 <span data-ttu-id="23864-341">スレッドのスタック上のマネージ メソッド (フレーム) を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-341">Provides methods for getting the managed methods, or frames, on a thread’s stack.</span></span>  
  
 [<span data-ttu-id="23864-342">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-342">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 <span data-ttu-id="23864-343">静的フィールドのデバッグ シンボル情報を表します。</span><span class="sxs-lookup"><span data-stu-id="23864-343">Represents the debug symbol information for a static field.</span></span> <span data-ttu-id="23864-344">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-344">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-345">ICorDebugStepper Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-345">ICorDebugStepper Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 <span data-ttu-id="23864-346">デバッガーが実行するコード実行内のステップを表します。コマンドの発行から完了までの間は識別子として機能します。これを使用するとステップをキャンセルできます。</span><span class="sxs-lookup"><span data-stu-id="23864-346">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
 [<span data-ttu-id="23864-347">ICorDebugStepper2 Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-347">ICorDebugStepper2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 <span data-ttu-id="23864-348">マイ コードのみ (JMC: Just My Code) デバッグのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-348">Provides support for Just My Code (JMC) debugging.</span></span>  
  
 [<span data-ttu-id="23864-349">ICorDebugStepperEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-349">ICorDebugStepperEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 <span data-ttu-id="23864-350">`ICorDebugEnum` メソッドを実装し、`ICorDebugStepper` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="23864-350">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugStepper` arrays.</span></span>  
  
 [<span data-ttu-id="23864-351">ICorDebugStringValue Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-351">ICorDebugStringValue Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 <span data-ttu-id="23864-352">文字列値に適用する `ICorDebugHeapValue` のサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="23864-352">A subclass of `ICorDebugHeapValue` that applies to string values.</span></span>  
  
 [<span data-ttu-id="23864-353">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-353">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 <span data-ttu-id="23864-354">デバッグ シンボル情報を取得するために使用できるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-354">Provides methods that can be used to retrieve debug symbol information.</span></span> <span data-ttu-id="23864-355">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-355">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-356">ICorDebugSymbolProvider2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-356">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 <span data-ttu-id="23864-357">論理的に拡張し、 [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)追加のデバッグ シンボル情報を取得するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-357">Logically extends the [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) interface to retrieve additional debug symbol information.</span></span> <span data-ttu-id="23864-358">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-358">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-359">ICorDebugThread Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-359">ICorDebugThread Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 <span data-ttu-id="23864-360">プロセス内のスレッドを表します。</span><span class="sxs-lookup"><span data-stu-id="23864-360">Represents a thread in a process.</span></span> <span data-ttu-id="23864-361">`ICorDebugThread` インスタンスの有効期間は、それが表しているスレッドの有効期間と同じです。</span><span class="sxs-lookup"><span data-stu-id="23864-361">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
 [<span data-ttu-id="23864-362">ICorDebugThread2 Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-362">ICorDebugThread2 Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 <span data-ttu-id="23864-363">`ICorDebugThread` の論理的な拡張機能として動作します。</span><span class="sxs-lookup"><span data-stu-id="23864-363">Serves as a logical extension to `ICorDebugThread`.</span></span>  
  
 [<span data-ttu-id="23864-364">ICorDebugThread3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-364">ICorDebugThread3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 <span data-ttu-id="23864-365">エントリ ポイントを提供、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)と対応するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-365">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
 [<span data-ttu-id="23864-366">ICorDebugThread4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-366">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 <span data-ttu-id="23864-367">スレッドのブロック情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-367">Provides thread blocking information.</span></span>  
  
 [<span data-ttu-id="23864-368">ICorDebugThreadEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-368">ICorDebugThreadEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 <span data-ttu-id="23864-369">`ICorDebugEnum` メソッドを実装し、`ICorDebugThread` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="23864-369">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugThread` arrays.</span></span>  
  
 [<span data-ttu-id="23864-370">ICorDebugType Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-370">ICorDebugType Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 <span data-ttu-id="23864-371">基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。</span><span class="sxs-lookup"><span data-stu-id="23864-371">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="23864-372">型がジェネリックの場合、`ICorDebugType` はインスタンス化されたジェネリック型を表します。</span><span class="sxs-lookup"><span data-stu-id="23864-372">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
 [<span data-ttu-id="23864-373">ICorDebugType2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-373">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 <span data-ttu-id="23864-374">拡張、 [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)基本データ型または複合 (ユーザー定義) の型の型の識別子を取得するインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="23864-374">Extends the [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
 [<span data-ttu-id="23864-375">ICorDebugTypeEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="23864-375">ICorDebugTypeEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 <span data-ttu-id="23864-376">`ICorDebugEnum` メソッドを実装し、`ICorDebugType` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="23864-376">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugType` arrays.</span></span>  
  
 [<span data-ttu-id="23864-377">ICorDebugUnmanagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-377">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 <span data-ttu-id="23864-378">CLR に直接関連していないネイティブ イベントについて通知します。</span><span class="sxs-lookup"><span data-stu-id="23864-378">Provides notification of native events that are not directly related to the CLR.</span></span>  
  
 <span data-ttu-id="23864-379">"ICorDebugValue"</span><span class="sxs-lookup"><span data-stu-id="23864-379">"ICorDebugValue"</span></span>  
 <span data-ttu-id="23864-380">デバッグ中のプロセス内の読み取り値または書き込み値を表します。</span><span class="sxs-lookup"><span data-stu-id="23864-380">Represents a read or write value in the process being debugged.</span></span>  
  
 <span data-ttu-id="23864-381">"ICorDebugValue2"</span><span class="sxs-lookup"><span data-stu-id="23864-381">"ICorDebugValue2"</span></span>  
 <span data-ttu-id="23864-382">`ICorDebugValue` をサポートできるように `ICorDebugType` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="23864-382">Extends `ICorDebugValue` to provide support for `ICorDebugType`.</span></span>  
  
 [<span data-ttu-id="23864-383">ICorDebugValue3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-383">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 <span data-ttu-id="23864-384">2 GB よりも大きな配列をサポートする"ICorDebugValue"および"ICorDebugValue2"インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="23864-384">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
 <span data-ttu-id="23864-385">"ICorDebugValueBreakpoint"</span><span class="sxs-lookup"><span data-stu-id="23864-385">"ICorDebugValueBreakpoint"</span></span>  
 <span data-ttu-id="23864-386">特定の値にアクセスできるように `ICorDebugBreakpoint` を拡張します。</span><span class="sxs-lookup"><span data-stu-id="23864-386">Extends `ICorDebugBreakpoint` to provide access to specific values.</span></span>  
  
 <span data-ttu-id="23864-387">"ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="23864-387">"ICorDebugValueEnum"</span></span>  
 <span data-ttu-id="23864-388">`ICorDebugEnum` メソッドを実装し、`ICorDebugValue` 配列を列挙します。</span><span class="sxs-lookup"><span data-stu-id="23864-388">Implements `ICorDebugEnum` methods, and enumerates `ICorDebugValue` arrays.</span></span>  
  
 [<span data-ttu-id="23864-389">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-389">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 <span data-ttu-id="23864-390">ローカル変数または関数の引数を表します。</span><span class="sxs-lookup"><span data-stu-id="23864-390">Represents a local variable or argument of a function.</span></span>  
  
 [<span data-ttu-id="23864-391">ICorDebugVariableHomeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-391">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 <span data-ttu-id="23864-392">ローカル変数と関数の引数、列挙子を提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-392">Provides an enumerator to the local variables and arguments in a function.</span></span>  
  
 [<span data-ttu-id="23864-393">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-393">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 <span data-ttu-id="23864-394">変数のデバッグ シンボル情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="23864-394">Retrieves the debug symbol information for a variable.</span></span> <span data-ttu-id="23864-395">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-395">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-396">ICorDebugVirtualUnwinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-396">ICorDebugVirtualUnwinder Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 <span data-ttu-id="23864-397">スタック アンワインドを支援するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-397">Provides methods to help in stack unwinding.</span></span> <span data-ttu-id="23864-398">**.NET ネイティブのみで使用できます。**</span><span class="sxs-lookup"><span data-stu-id="23864-398">**Available on .NET Native only.**</span></span>  
  
 [<span data-ttu-id="23864-399">ICorPublish インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-399">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 <span data-ttu-id="23864-400">発行プロセスの汎用インターフェイスとして機能します。</span><span class="sxs-lookup"><span data-stu-id="23864-400">Serves as the general interface for the publishing processes.</span></span>  
  
 [<span data-ttu-id="23864-401">ICorPublishAppDomain インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-401">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 <span data-ttu-id="23864-402">アプリケーション ドメインの情報を表し、提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-402">Represents and provides information about an application domain.</span></span>  
  
 [<span data-ttu-id="23864-403">ICorPublishAppDomainEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-403">ICorPublishAppDomainEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 <span data-ttu-id="23864-404">現在プロセス内に存在する `ICorPublishAppDomain` オブジェクトのコレクションを走査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-404">Provides methods that traverse a collection of `ICorPublishAppDomain` objects that currently exist within a process.</span></span>  
  
 [<span data-ttu-id="23864-405">ICorPublishEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-405">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 <span data-ttu-id="23864-406">発行する列挙子の抽象ベースとして機能します。</span><span class="sxs-lookup"><span data-stu-id="23864-406">Serves as the abstract base for publishing enumerators.</span></span>  
  
 [<span data-ttu-id="23864-407">ICorPublishProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-407">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 <span data-ttu-id="23864-408">プロセスの情報にアクセスするメソッドを適用します。</span><span class="sxs-lookup"><span data-stu-id="23864-408">Provides methods that access information about a process.</span></span>  
  
 [<span data-ttu-id="23864-409">ICorPublishProcessEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23864-409">ICorPublishProcessEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 <span data-ttu-id="23864-410">`ICorPublishProcess` オブジェクトのコレクションを走査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="23864-410">Provides methods that traverse a collection of `ICorPublishProcess` objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="23864-411">関連項目</span><span class="sxs-lookup"><span data-stu-id="23864-411">Related Sections</span></span>  
 [<span data-ttu-id="23864-412">デバッグ コクラス</span><span class="sxs-lookup"><span data-stu-id="23864-412">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="23864-413">デバッグ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="23864-413">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [<span data-ttu-id="23864-414">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="23864-414">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="23864-415">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="23864-415">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
