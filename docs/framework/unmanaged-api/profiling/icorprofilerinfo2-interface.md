---
title: ICorProfilerInfo2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2
helpviewer_keywords:
- ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8cec2a622a1a30881949ad5a9f2050077e195015
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461400"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 インターフェイス
コード プロファイラーが共通言語ランタイム (CLR) イベントの監視の制御と要求情報を通信に使用するメソッドを提供します。 `ICorProfilerInfo2`インターフェイスの拡張機能は、 [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)インターフェイスです。 つまり、.NET Framework バージョン 2.0 およびそれ以降のバージョンでサポートされている新しいメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DoStackSnapshot メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|マネージ呼び出しフレームをプロファイラーに報告する指定されたスレッドのスタックを走査します。|  
|[EnumModuleFrozenObjects メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|指定されたモジュール内の固定オブジェクト経由の反復処理する列挙子を取得します。|  
|[GetAppDomainStaticAddress メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|指定されたアプリケーション ドメインのスコープ内にある指定されたアプリケーション ドメインの静的フィールドのアドレスを取得します。|  
|[GetArrayObjectInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|配列オブジェクトに関する詳細情報を取得します。|  
|[GetBoxClassLayout メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|ボックス化は、指定された値の型のクラス レイアウトに関する情報を取得します。|  
|[GetClassFromTokenAndTypeArgs メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|取得、`ClassID`指定したメタデータ トークンを使用して、型の`ClassID`いずれかの値が引数を入力します。|  
|[GetClassIDInfo2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|指定したジェネリック クラス、クラス、メタデータ トークンの親モジュールを取得、`ClassID`その親クラスのおよび`ClassID`存在する場合、クラスの各型引数。|  
|[GetClassLayout メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|指定したクラスで定義されるフィールドのメモリ内レイアウトに関する情報を取得します。 つまり、このメソッドはクラスのフィールドのオフセットを取得します。|  
|[GetCodeInfo2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|指定した `FunctionID` に関連付けられているネイティブ コードの範囲を取得します。|  
|[GetContextStaticAddress メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|指定したコンテキストのスコープ内にある指定したコンテキストの静的フィールドのアドレスを取得します。|  
|[GetFunctionFromTokenAndTypeArgs メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|取得、 `FunctionID` 、クラスを含む、指定したメタデータ トークンを使用して関数のおよび`ClassID`いずれかの値が引数を入力します。|  
|[GetFunctionInfo2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|関数の親クラス、メタデータ トークン、および型引数が存在する場合はそれぞれの `ClassID` を取得します。|  
|[GetGenerationBounds メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|ガベージ コレクトされたヒープのジェネレーションを構成するメモリ領域 (ヒープのセグメント) を取得します。|  
|[GetNotifiedExceptionClauseInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|例外句のネイティブのアドレスとフレームの情報を取得します (`catch`/`finally`/`filter`) を実行する前に、またはが実行されているだけです。|  
|[GetObjectGeneration メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|指定したオブジェクトを含むヒープのセグメントを取得します。|  
|[GetRVAStaticAddress メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|指定された相対仮想アドレス (RVA) のアドレスを取得、静的フィールドです。|  
|[GetStaticFieldInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|指定したフィールドの静的なスコープを取得します。|  
|[GetStringLayout メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|文字列オブジェクトのレイアウトに関する情報を取得します。|  
|[GetThreadAppDomain メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|指定したスレッドが実行されているコード、アプリケーション ドメインの ID を取得します。|  
|[GetThreadStaticAddress メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|指定したスレッドのスコープ内にある指定したスレッド内静的フィールドのアドレスを取得します。|  
|[SetEnterLeaveFunctionHooks2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|「の入力」、「のまま」、およびマネージ関数の"tailcall"フックで呼び出されるプロファイラー実装関数を指定します。|  
  
## <a name="remarks"></a>コメント  
 プロファイラーのメソッドを呼び出す、 `ICorProfilerInfo2` CLR イベントの監視を制御し、情報を要求すると通信するインターフェイスです。  
  
 メソッド、`ICorProfilerInfo2`フリー スレッド モデルを使用して、CLR によってインターフェイスが実装されます。 各メソッドが、成功または失敗を示す HRESULT を返します。 返される可能性があるリターン コードの一覧については、CorError.h ファイルを参照してください。  
  
 CLR から渡される、`ICorProfilerInfo2`へのプロファイラーの実装を使用して初期化中に、各コード プロファイラーのインターフェイス[icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)です。 コード プロファイラーは、のメソッドを呼び出すことができますし、 `ICorProfilerInfo2` CLR の制御下で実行されているマネージ コードに関する情報を取得するインターフェイスです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
