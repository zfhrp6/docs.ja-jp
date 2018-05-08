---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6cce181037ee4f4db3a828f98cc3e07dfb45aff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="corprofeunsupportedcallsequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT は、.NET Framework version 2.0 で導入されました。 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] 2 つのシナリオでこの HRESULT を返します。  
  
-   ハイジャック プロファイラーは、スレッドを強制的にリセットされたときのコンテキスト任意の時点でように登録、スレッドは不整合な状態には、構造にアクセスしようとしてください。  
  
-   プロファイラーのコールバック メソッドからガベージ コレクションをトリガーする情報のメソッドを呼び出すしようとすると、ガベージ コレクションが禁止されているがします。  
  
 これら 2 つのシナリオは、次のセクションで説明します。  
  
## <a name="hijacking-profilers"></a>プロファイラーをハイジャックしています。  
 (このシナリオは、プロファイラーをハイジャックしている場合は非ハイジャック プロファイラーがこの HRESULT を確認できますが、主の問題です)。  
  
 このシナリオでハイジャック プロファイラー強制的にリセット レジスタ コンテキストのスレッドの任意の時点で、スレッドがプロファイラー コードを入力または共通言語ランタイム (CLR) を再入力できるようにするを通じて、 [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)メソッドです。  
  
 プロファイル API が、CLR でのデータ構造体へのポイントを提供する Id の多くはします。 多く`ICorProfilerInfo`呼び出しは単なるこれらのデータ構造から情報を読み取るし、それらを渡します。 ただし、CLR であってを実行し、そのためにはロックを使用する場合があります、それらの構造体の内容が変更可能性があります。 CLR が既に保持している (または取得しようとしています) 時にロックと、プロファイラーは、スレッドをハイジャックです。 スレッドは CLR を再入力して、多くのロックがかかるか変更されている処理を行っていた構造体を検査しようとしています。、これらの構造が不整合な状態にあります。 デッドロックとアクセス違反は、簡単にこのような状況で発生します。  
  
 一般に、非ハイジャック プロファイラーが内のコードを実行するとき、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)メソッドと呼び出しを`ICorProfilerInfo`メソッドの有効なパラメーターを使用する必要がありますいないデッドロック、アクセス違反が発生します。 プロファイラー コード内で実行される、 [icorprofilercallback::classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)メソッドを呼び出すことによってクラスについての情報の要求、 [icorprofilerinfo 2::getclassidinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)メソッド。 コードは、情報が使用可能であることを示す CORPROF_E_DATAINCOMPLETE HRESULT を受け取る可能性があります。ただし、デッドロックまたはされませんアクセス違反が発生します。 このクラスへの呼び出しの`ICorProfilerInfo`から構成されているため、同期と呼びます、`ICorProfilerCallback`メソッドです。  
  
 ただし、マネージ スレッドを実行するコード内ではない、`ICorProfilerCallback`メソッドの非同期呼び出しを行うと見なされます。 .NET framework バージョン 1 では、非同期呼び出しで行われる処理を決定するが困難でした。 呼び出しでは、デッドロック、クラッシュし、または無効な回答でした。 .NET Framework version 2.0 には、この問題を回避するためにいくつかの簡単なチェックが導入されました。 呼び出す、安全でない場合は、.NET Framework 2.0 の`ICorProfilerInfo`関数の非同期的には、CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT が表示されて失敗します。  
  
 一般に、非同期呼び出しは安全ではありません。 ただし、次のメソッドは、安全であるおよび、具体的には非同期呼び出しをサポートします。  
  
-   [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
-   [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
-   [GetCurrentThreadID](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
-   [GetThreadContext](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
-   [GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
-   [GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
-   [GetFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
-   [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
-   [GetCodeInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
-   [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
-   [GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
-   [GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
-   [GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
-   [IsArrayClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
-   [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
-   [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 詳細については、エントリを参照してください。 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE あります](http://go.microsoft.com/fwlink/?LinkId=169156)CLR プロファイル API のブログにします。  
  
## <a name="triggering-garbage-collections"></a>ガベージ コレクションをトリガーします。  
 このシナリオでは、コールバック メソッドの内部を実行しているプロファイラー (たとえば、1 つの`ICorProfilerCallback`メソッド) のガベージ コレクションが禁止されています。 プロファイラーは、情報提供メソッドを呼び出すしようとした場合 (などのメソッド、`ICorProfilerInfo`インターフェイス)、ガベージ コレクションをトリガーする可能性があります、情報提供メソッド CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT で失敗します。  
  
 次の表は、ガベージ コレクションが禁止されているコールバック メソッドとは、ガベージ コレクションをトリガー情報提供のメソッドを表示します。 プロファイラーは一覧表示されたコールバック メソッドのいずれかの内側を実行し、表示されている情報メソッドのいずれかを呼び出して、その情報のメソッドは CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT で失敗します。  
  
|ガベージ コレクションが禁止されているコールバック メソッド|ガベージ コレクションをトリガーする情報提供メソッド|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [ICorProfilerCallback3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
