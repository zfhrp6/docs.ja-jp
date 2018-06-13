---
title: StackSnapshotCallback 関数
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78fdcb69e73bc7238972d1a6ffb37b5ba91c7953
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459086"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback 関数
によって開始されるスタック ウォーク中のスタックの各マネージ フレームとアンマネージのフレームの各実行に関する情報を使用してプロファイラーを提供、 [icorprofilerinfo 2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `funcId`  
 [in]この値が 0 の場合は、このコールバックはアンマネージ フレーム; の実行それ以外の場合、マネージ関数の識別子、このコールバックがあるマネージ フレーム。  
  
 `ip`  
 [in]フレーム内のネイティブ コードの命令ポインターの値。  
  
 `frameInfo`  
 [in]A`COR_PRF_FRAME_INFO`スタック フレームに関する情報を参照する値。 この値は、このコールバック中にのみ使用するため有効です。  
  
 `contextSize`  
 [in]サイズ、`CONTEXT`によって参照されている構造体、`context`パラメーター。  
  
 `context`  
 [in]Win32 へのポインター`CONTEXT`このフレームの CPU の状態を表す構造です。  
  
 `context`パラメーターは、COR_PRF_SNAPSHOT_CONTEXT フラグが渡された場合にのみ有効`ICorProfilerInfo2::DoStackSnapshot`です。  
  
 `clientData`  
 [in]ストレートから渡されるクライアント データへのポインター`ICorProfilerInfo2::DoStackSnapshot`です。  
  
## <a name="remarks"></a>コメント  
 `StackSnapshotCallback`関数は、プロファイラー ライターによって実装されます。 行われた作業の複雑さを制限する必要があります`StackSnapshotCallback`です。 使用する場合など、`ICorProfilerInfo2::DoStackSnapshot`非同期で対象のスレッドがするロックを保持しています。 場合内のコード`StackSnapshotCallback`、同じロックが必要です、デッドロックが発生したりする可能性があります。  
  
 `ICorProfilerInfo2::DoStackSnapshot`メソッドの呼び出し、`StackSnapshotCallback`マネージ フレームごとに 1 回または 1 回はアンマネージ フレームの実行ごとの関数。 場合`StackSnapshotCallback`が呼び出された、プロファイラーのアンマネージ フレームの実行、レジスタのコンテキストを使用して可能性があります (により参照されている、`context`パラメーター) をアンマネージ スタック ウォークを実行します。 この場合は、Win32`CONTEXT`構造体が最後にプッシュされたフレーム アンマネージ フレームの実行中の CPU の状態を表します。 ただし、Win32`CONTEXT`構造体には、すべてのレジスタの値が含まれています、フレーム ポインター レジスタ、スタック ポインター レジスタ、命令ポインター レジスタ、および (つまり、保持された) 非揮発性の値にのみ依存する必要があります整数レジスタします。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [DoStackSnapshot メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
