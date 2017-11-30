---
title: "ICorProfilerInfo2::DoStackSnapshot メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.DoStackSnapshot
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type: apiref
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6a210fc0c1984ee9bc77114ba30c3287ae43b169
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot メソッド
指定のスレッドのスタックでマネージ フレームを走査し、コールバックを通じてプロファイラーに情報を送信します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `thread`  
 [in]対象のスレッドの ID。  
  
 Null を渡す`thread`現在のスレッドのスナップショットを生成します。 場合、`ThreadID`の別のスレッドが渡される、共通言語ランタイム (CLR) そのスレッドを中断、スナップショットを行い、再開します。  
  
 `callback`  
 [in]実装へのポインター、 [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)各マネージ フレームおよびアンマネージ フレームのそれぞれの実行に関する情報を含む、プロファイラーを提供する CLR によって呼び出されるメソッド。  
  
 `StackSnapshotCallback`メソッドは、プロファイラー ライターによって実装されます。  
  
 `infoFlags`  
 [in]値、 [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)によって各フレームを渡されるデータの量を指定する列挙体`StackSnapshotCallback`です。  
  
 `clientData`  
 [in]渡されるまっすぐクライアントのデータへのポインター、`StackSnapshotCallback`コールバック関数。  
  
 `context`  
 [in]Win32 へのポインター`CONTEXT`構造は、これは、スタック ウォークのシードに使用します。 Win32`CONTEXT`構造は、CPU レジスタの値が含まれています、特定の時点での CPU の状態を表します。  
  
 シードにより、CLR をアンマネージ ヘルパー コード; 場合は、スタックの一番上に、スタック ウォークを開始する場所を特定します。それ以外の場合、シードは無視されます。 非同期ウォークのシードを指定する必要があります。 同期のウォークを実行してシードの必要はありません。  
  
 `context`パラメーターが COR_PRF_SNAPSHOT_CONTEXT フラグが渡された場合にのみ有効では、`infoFlags`パラメーター。  
  
 `contextSize`  
 [in]サイズ、`CONTEXT`によって参照されている構造体、`context`パラメーター。  
  
## <a name="remarks"></a>コメント  
 Null を渡す`thread`現在のスレッドのスナップショットを生成します。 時に対象のスレッドが中断されている場合にのみ、他のスレッドのスナップショットを取得できます。  
  
 プロファイラーは、スタック ウォークは、呼び出し`DoStackSnapshot`です。 CLR は、その呼び出しから戻る前に呼び出し、`StackSnapshotCallback`何回か 1 回ごとに管理されているフレーム (またはアンマネージ フレームの実行) スタックにします。 アンマネージ フレームが発生するとを自分でに説明する必要があります。  
  
 スタックを走査する順序は、フレームがスタックにプッシュされたどの逆: 最後 (最後にプッシュされた) 最初に、メイン (最初プッシュ) フレームをリーフです。  
  
 プロファイラーでマネージ スタックをプログラミングする方法の詳細については、次を参照してください。 [、.NET Framework 2.0 におけるプロファイラー スタック ウォーク: 基本と発展](http://go.microsoft.com/fwlink/?LinkId=73638)です。  
  
 スタック ウォークは、次のセクションで説明するよう同期または非同期を指定できます。  
  
## <a name="synchronous-stack-walk"></a>同期のスタック ウォーク  
 同期スタック ウォークには、現在のスレッドのスタックのウォーク コールバックへの応答が含まれます。 シードまたは中断は不要です。  
  
 同期を行うメソッドを呼び出すのプロファイラーのいずれかを呼び出して、CLR への応答[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (または[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md))、メソッドを呼び出す`DoStackSnapshot`のスタック ウォークを現在のスレッド。 これは、スタックがどのように通知でなどを表示する場合に役立ちます[icorprofilercallback::objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)です。 呼び出すだけで`DoStackSnapshot`内から、`ICorProfilerCallback`で null を渡して、メソッド、`context`と`thread`パラメーター。  
  
## <a name="asynchronous-stack-walk"></a>非同期のスタック ウォーク  
 非同期のスタック ウォークは、別のスレッドのスタックや、コールバックは現在のスレッドの命令ポインターをハイジャックしている応答ではなく、現在のスレッドのスタックのウォークを伴います。 非同期のウォークは、アンマネージ コード、プラットフォームの一部ではない場合は、スタックの一番上のシード呼び出し (PInvoke) 必要がありますまたは COM 呼び出しが CLR 自体でヘルパー コード。 たとえば、・ イン タイム (JIT) コンパイル中またはガベージ コレクションを実行するコードは、ヘルパー コードです。  
  
 直接対象のスレッドを中断、シードを取得し、自分で、最上位に表示されるまでにマネージ フレーム スタックを走査します。 対象のスレッドが中断された後は、対象のスレッドの現在のレジスタのコンテキストを取得します。 次に、レジスタのコンテキストが呼び出すことによってアンマネージ コードを指すかどうかを決定[icorprofilerinfo::getfunctionfromip](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) : 返された場合、 `FunctionID` 0 に等しい、フレームがアンマネージ コードです。 ここで、最初のマネージ フレームに到達し、そのフレームのレジスタのコンテキストに基づき、シード コンテキストを計算するまでは、スタックを走査します。  
  
 呼び出す`DoStackSnapshot`非同期スタック ウォークを開始する、シード コンテキストを使用します。 シードを指定しない場合`DoStackSnapshot`スタックの一番上でマネージ フレームをスキップする場合があり、その結果が提供するスタック ウォークが不完全です。 シードを指定する場合は、JIT コンパイルまたはネイティブ イメージ ジェネレーター (Ngen.exe) を指している必要があります-生成されたコードです。それ以外の場合、 `DoStackSnapshot` CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX、エラー コードを返します。  
  
 非同期のスタック ウォークはデッドロックが発生するまたはアクセス違反が次のガイドラインに従わない場合、簡単にできます。  
  
-   直接のスレッドを中断する場合は、マネージ コードを実行しないが、スレッドのみが別のスレッドを中断できますに注意してください。  
  
-   常にブロック、 [icorprofilercallback::threaddestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)そのスレッドのスタック ウォークが完了するまでのコールバック。  
  
-   プロファイラーは、ガベージ コレクションをトリガーできる CLR 関数を呼び出すときに、ロックを保持しないでください。 つまり、所有元のスレッドがガベージ コレクションをトリガーする呼び出しを行う場合は、ロックを保持しないでください。  
  
 デッドロックの危険性を呼び出す場合`DoStackSnapshot`別の対象のスレッドのスタックを走査できるように、プロファイラーが作成したスレッドからです。 最初に作成したスレッドが特定`ICorProfilerInfo*`メソッド (含む`DoStackSnapshot`)、CLR がスレッドごと、そのスレッドで CLR 固有の初期化を実行します。 プロファイラーが対象のスレッドがスタック ウォークをしようとしてを中断している場合、このスレッドごとの初期化を実行するために必要なロックを所有する対象のスレッドが発生した場合、デッドロックが発生します。 このデッドロックを避けるために最初の呼び出しを行う`DoStackSnapshot`に段階的に、プロファイラーが作成したスレッドから別のスレッドは対象まず対象のスレッドを中断しないようにします。 この初期の呼び出しにより、デッドロックなしスレッドごとの初期化を完了できるようにします。 場合`DoStackSnapshot`が成功し、レポートには、少なくとも 1 つのフレームでは、その後、ことが、対象のスレッドと呼び出しを中断するプロファイラーが作成したスレッドの安全な`DoStackSnapshot`その対象のスレッドのスタック ウォークをします。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
