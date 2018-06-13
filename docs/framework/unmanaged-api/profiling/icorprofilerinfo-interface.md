---
title: ICorProfilerInfo インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo
helpviewer_keywords:
- ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: eb4e4ce0-06e7-4469-bbc4-edc2eb5da4b1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da5a041e8a18420b4cf9962e4315683be8857711
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462271"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo インターフェイス
共通言語ランタイム (CLR) のイベントの監視を制御し、情報を要求に通信するためにコード プロファイラーで使用するためのメソッドを提供します。  
  
> [!NOTE]
>  各メソッドに、`ICorProfilerInfo`インターフェイスは、成功または失敗を示す HRESULT を返します。 リターン コードの一覧については、CorError.h を参照してください。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[BeginInprocDebugging メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|初期化は、プロセス内のデバッグのサポート。 このメソッドは、.NET Framework version 2.0 廃止されています。|  
|[EndInprocDebugging メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|プロセスのデバッグ セッションを終了します。 このメソッドは、.NET Framework version 2.0 廃止されています。|  
|[ForceGC メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|ランタイム内で発生する可能性を強制的にガベージ コレクション。|  
|[GetAppDomainInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|指定されたアプリケーション ドメインについての情報を取得します。|  
|[GetAssemblyInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|指定したアセンブリに関する情報を取得します。|  
|[GetClassFromObject メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|取得、`ClassID`の<br /><br /> 指定されたオブジェクトの`ObjectID`します。|  
|[GetClassFromToken メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|指定したメタデータ トークン、クラスの ID を取得します。 このメソッドは、.NET Framework version 2.0 廃止されています。 使用して、 [icorprofilerinfo 2::getclassfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)メソッド代わりにします。|  
|[GetClassIDInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|指定したクラスの親モジュールとメタデータ トークンを取得します。|  
|[GetCodeInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|指定した関数 ID に関連付けられているネイティブ コードの範囲を取得します。 このメソッドは、互換性のために残されています。 使用して、 [icorprofilerinfo 2::getcodeinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)メソッド代わりにします。|  
|[GetCurrentThreadID メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|マネージ スレッドである場合は、現在のスレッドの ID を取得します。|  
|[GetEventMask メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|プロファイラーが CLR からのイベント通知を受け取る、現在のイベント カテゴリを取得します。|  
|[GetFunctionFromIP メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|マネージ コードの命令ポインターのマップ、`FunctionID`です。|  
|[GetFunctionFromToken メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|関数の ID を取得します。 このメソッドは、.NET Framework version 2.0 廃止されています。 使用して、 [icorprofilerinfo 2::getfunctionfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)メソッド代わりにします。|  
|[GetFunctionInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|指定した関数の親クラスとメタデータ トークンを取得します。|  
|[GetHandleFromThread メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|Win32 スレッド ハンドルをスレッドの ID を割り当てます。|  
|[GetILFunctionBody メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|開始位置のヘッダーとして、Microsoft intermediate language (MSIL) コードでメソッドの本体へのポインターを取得します。|  
|[GetILFunctionBodyAllocator メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|MSIL コード内のメソッドの本体を交換するために使用されるメモリを割り当てる方法を提供するインターフェイスを取得します。|  
|[GetILToNativeMapping メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|MSIL オフセットから指定された関数に含まれるコードのネイティブ オフセットへのマップを取得します。|  
|[GetInprocInspectionInterface メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|ICorDebugProcess インターフェイスの照会されるオブジェクトを取得します。 このメソッドは、.NET Framework version 2.0 廃止されています。|  
|[GetInprocInspectionIThisThread メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|ICorDebugThread インターフェイスの照会されるオブジェクトを取得します。 このメソッドは、.NET Framework version 2.0 廃止されています。|  
|[GetModuleInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|モジュール ID を指定して、モジュールのファイル名とモジュールの親アセンブリの ID を取得します。|  
|[GetModuleMetaData メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|指定したモジュールにマップされるメタデータ インターフェイスのインスタンスを取得します。|  
|[GetObjectSize メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|指定したオブジェクトのサイズを取得します。|  
|[GetThreadContext メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|指定したスレッドに関連付けられているコンテキスト id を取得します。|  
|[GetThreadInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|指定したスレッドの現在の Win32 スレッド id を取得します。|  
|[GetTokenAndMetadataFromFunction メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|メタデータ トークン、トークンに対して指定した関数の使用できるメタデータ インターフェイスのインスタンスを取得します。|  
|[IsArrayClass メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|指定したクラスが、配列クラスであるかどうかを判断します。|  
|[SetEnterLeaveFunctionHooks メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|「の入力」、「のまま」、およびマネージ関数の"tailcall"フックで呼び出されるプロファイラー実装関数を指定します。|  
|[SetEventMask メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|プロファイラーが CLR から通知を受け取るイベントの種類を指定する値を設定します。|  
|[SetFunctionIDMapper メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|`FunctionID` 値を代替値に対応付けるために呼び出すプロファイラー実装関数を指定します。代替値は、プロファイラーの関数の開始フックと終了フックに渡されます。|  
|[SetFunctionReJIT メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|実装されていません。 使用しないでください。|  
|[SetILFunctionBody メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|指定したモジュール内の指定した関数の本体を置換します。|  
|[SetILInstrumentedCodeMap メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|新しい関数のプロファイラーで変更された MSIL のオフセットに指定された関数の元の MSIL のオフセットがどのようにマップするかを指定します。|  
  
## <a name="remarks"></a>コメント  
 プロファイラーのメソッドを呼び出す、 `ICorProfilerInfo` CLR イベントの監視を制御し、情報を要求すると通信するインターフェイスです。  
  
 メソッド、`ICorProfilerInfo`フリー スレッド モデルを使用して、CLR によってインターフェイスが実装されます。 各メソッドが、成功または失敗を示す HRESULT を返します。 リターン コードの一覧については、CorError.h を参照してください。  
  
 プロファイラーの実装を使用して、CLR から渡される[icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)、`ICorProfilerInfo`を初期化中に各コード プロファイラーのインターフェイスです。 コード プロファイラーは、のメソッドを呼び出すことができますし、 `ICorProfilerInfo` CLR の制御下で実行されているマネージ コードに関する情報を取得するインターフェイスです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
