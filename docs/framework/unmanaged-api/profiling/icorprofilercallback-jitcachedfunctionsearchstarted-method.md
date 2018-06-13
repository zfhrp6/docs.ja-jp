---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d97b40412b6999000a601b72904a03edf2acd08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454038"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted メソッド
ネイティブ イメージ ジェネレーター (NGen.exe) を使用して以前にコンパイルされた関数の検索が開始されたことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]検索が実行される関数の ID。  
  
 `pbUseCachedFunction`  
 [out]`true`実行エンジンは、(使用可能な場合) に、キャッシュされたバージョンの関数を使用する場合は、それ以外の`false`します。 値が場合`false`の実行エンジンは JIT コンパイルではないバージョンを使用する代わりに、関数、JIT コンパイルします。  
  
## <a name="remarks"></a>コメント  
 .NET framework version 2.0 では、`JITCachedFunctionSearchStarted`と[icorprofilercallback::jitcachedfunctionsearchfinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)正規の NGen イメージのすべての関数のコールバックは行われません。 プロファイル用に最適化された NGen イメージだけは、すべての関数のコールバックをイメージに生成されます。 ただし、追加のオーバーヘッドにより、プロファイラー NGen イメージのプロファイラー最適化する必要があります要求した場合、関数のコンパイル済みジャストでタイム (JIT) を強制的にこれらのコールバックを使用する場合にのみにします。 それ以外の場合、プロファイラーは、関数の情報を収集するため、限定的な戦略を使用する必要があります。  
  
 プロファイラーは、プロファイリング対象のアプリケーションの複数のスレッドが、同じメソッドを同時に呼び出す場合をサポートする必要があります。 たとえば、スレッド A が`JITCachedFunctionSearchStarted`し応答する状態を設定して、プロファイラー *pbUseCachedFunction*JIT コンパイルを強制する場合は FALSE にします。 A はそのを呼び出すスレッド[icorprofilercallback::jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)と[icorprofilercallback::jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)です。  
  
 スレッド B の呼び出しのようになりました`JITCachedFunctionSearchStarted`同じ関数。 プロファイラーがスレッド B が A のスレッドの呼び出しにプロファイラーが前に、コールバックを送信するために、2 番目のコールバックを受け取る場合でも、プロファイラーは、関数の JIT コンパイルする意向を言うと、`JITCachedFunctionSearchStarted`です。 スレッドが呼び出しを行う順序は、スレッドのスケジュール方法によって異なります。  
  
 によって参照される値を設定する必要があります、プロファイラーは、重複するコールバックを受信すると`pbUseCachedFunction`重複するすべてのコールバックの同じ値にします。 つまり、`JITCachedFunctionSearchStarted`同じで複数回呼び出された`functionId`値、プロファイラー対応する必要が同じたびにします。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
