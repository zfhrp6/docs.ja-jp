---
title: "プロファイリングのインターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
caps.latest.revision: "31"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f8c2a5ce5e1231c55f598e48d14bec896a4b5f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-interfaces"></a>プロファイリングのインターフェイス
ここでは、共通言語ランタイム (CLR) で実行中のプログラムに対してプロファイルを可能にするアンマネージ インターフェイスについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ICLRProfiling インターフェイス](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 提供、 [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)メソッドは、プロファイラーが実行中のプロセスにアタッチすることができます。  
  
 [ICorProfilerAssemblyReferenceProvider インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 プロファイラーのプロファイラーを追加するアセンブリ参照の CLR に通知を有効に、 [icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)コールバック。  
  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 プロファイラーがサブスクライブしたイベントが発生したときにコード プロファイラーに通知するために、CLR が使用するメソッドを提供します。  
  
 [ICorProfilerCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 .NET Framework 2.0 以降でサポートされるコールバックによって、`ICorProfilerCallback` インターフェイスを拡張します。  
  
 [ICorProfilerCallback3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 CLR がプロファイラーにアタッチとデタッチの状態情報を伝えるために使用するコールバック メソッドを提供します。  
  
 [ICorProfilerCallback4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 プロファイラーと情報をやりとりするために CLR が使用するコールバック メソッドを提供します。  
  
 [ICorProfilerCallback5 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 ガベージ コレクションのルートによって参照されるオブジェクトの遷移的なクロージャを識別するメソッドを提供します。  
  
 [ICorProfilerCallback6 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 CLR が プロファイラーに対して、アセンブリがロード中であることを通知するために使用するコールバック メソッドを提供します。  
  
 [ICorProfilerCallback7 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 共通言語ランタイムを使用してメモリ内のモジュールに関連付けられているシンボルのストリームが更新されることをプロファイラーに通知するコールバック メソッドを提供します。  
  
 [ICorProfilerFunctionControl インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 コード プロファイラーが CLR と通信できるようにするためのメソッドを提供します。これは特定のメソッドを再コンパイルするときに、JIT コンパイラーがどのようにしてコードを生成するかを制御するためのものです。  
  
 [ICorProfilerFunctionEnum インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 CLR で関数のコレクションを順番に反復処理するためのメソッドを提供します。  
  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 コード プロファイラーが、イベントの監視および情報の要求を制御するために CLR との通信で使用するメソッドを提供します。  
  
 [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 .NET Framework 2.0 以降でサポートされるメソッドによって、`ICorProfilerInfo` インターフェイスを拡張します。  
  
 [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 `ICorProfilerInfo2` 以降でサポートされるメソッドによって、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] インターフェイスを拡張します。  
  
 [ICorProfilerInfo4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 コード プロファイラーが、イベントの監視および情報の要求を制御するために CLR との通信で使用するメソッドを提供します。  
  
 [ICorProfilerInfo5 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 コード プロファイラーが、イベントの監視を制御するために CLR との通信で使用するメソッドを提供します。  
  
 [ICorProfilerInfo6 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 列挙子を指定した NGen モジュールに属するし、は、特定のメソッドの本体でインライン展開をすべてのメソッドを提供します。  
  
 [ICorProfilerInfo7 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 新しくを適用するためのメソッドでは、モジュールにメタデータが定義されているし、メモリ内のシンボルのストリームへのアクセスを提供するを提供します。  
  
 [ICorProfilerModuleEnum インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 アプリケーションまたはプロファイラーによってロードされたモジュールのコレクションを順番に反復処理するためのメソッドを提供します。  
  
 [ICorProfilerObjectEnum インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 によって生成される固定されたオブジェクトのコレクションを順番に反復処理するメソッドを提供[Ngen.exe (ネイティブ イメージ ジェネレーター)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)です。  
  
 [ICorProfilerThreadEnum インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 CLR でスレッドのコレクションを順番に反復処理するためのメソッドを提供します。  
  
 [IMethodMalloc インターフェイス](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 提供、[アロケーション](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)メソッドの新しい Microsoft intermediate language (MSIL) 関数本体にメモリを割り当てられません。  
  
## <a name="related-sections"></a>関連項目  
 [プロファイルの概要](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [構造体のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
