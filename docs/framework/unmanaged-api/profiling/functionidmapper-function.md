---
title: FunctionIDMapper 関数
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 151b790afaf6a251ba5d8d8932f44a503cde853a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458599"
---
# <a name="functionidmapper-function"></a>FunctionIDMapper 関数
関数の特定の識別子が可能性がありますで使用される代替 ID に再割り当てされることをプロファイラーに通知、 [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)、および[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)その関数のコールバック。 また `FunctionIDMapper` により、プロファイラーはその関数のコールバックを受信するかどうかを示すことができます。  
  
## <a name="syntax"></a>構文  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `funcId`  
 [入力] 再割り当てされる関数識別子。  
  
 `pbHookFunction`  
 [out]プロファイラーに設定される値へのポインター`true`を受信する必要がある場合`FunctionEnter2`、 `FunctionLeave2`、および`FunctionTailcall2`コールバックです。 それ以外の場合この値が設定`false`です。  
  
## <a name="return-value"></a>戻り値  
 プロファイラーは、実行エンジンが代替関数識別子として使用する値を返します。 `false` で `pbHookFunction` を返さない限り、戻り値を null にすることはできません。 それ以外の場合、戻り値を null、プロセスの中止など、予期しない結果が生成されます。  
  
## <a name="remarks"></a>コメント  
 `FunctionIDMapper`関数がコールバック。 プロファイラーのより有用なは、他の何らかの識別子に関数の ID を再マップするには、プロファイラーによって実装されます。 `FunctionIDMapper`任意指定の関数に使用される代替 ID を返します。 実行エンジンは、し、適用することで、プロファイラーの要求だけでなく、従来の関数の ID では、この別の ID でプロファイラーに渡すことによって、`clientData`のパラメーター、 `FunctionEnter2`、 `FunctionLeave2`、および`FunctionTailcall2`フックを識別するには対象のフック関数が呼び出される関数。  
  
 使用することができます、 [icorprofilerinfo::setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)メソッドの実装を指定する、`FunctionIDMapper`関数。 呼び出すことができます、`ICorProfilerInfo::SetFunctionIDMapper`とメソッドを 1 回のみに実行することをお勧め、 [icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)コールバック。  
  
 既定と見なされますこと、プロファイラーを COR_PRF_MONITOR_ENTERLEAVE フラグ設定を使用して[icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)を使用してフックを設定して[icorprofilerinfo::setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)または[icorprofilerinfo 2::setenterleavefunctionhooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)、受信する必要があります、 `FunctionEnter2`、 `FunctionLeave2`、および`FunctionTailcall2`関数は、すべてのコールバック。 ただし、プロファイラーの実装が`FunctionIDMapper`選択的に受信しないためにこれらのコールバック特定の設定によって機能`pbHookFunction`に`false`です。  
  
 プロファイラーは、プロファイリング対象のアプリケーションの複数のスレッドが、同じメソッド/関数を同時に呼び出す場合に対応する必要があります。 このような場合、プロファイラーが表示される複数`FunctionIDMapper`のコールバックを同じ`FunctionID`です。 プロファイラーがする必要がありますが同じ複数回呼び出された場合、このコールバックから同じの値を返す特定`FunctionID`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [SetFunctionIDMapper メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [FunctionIDMapper2 関数](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 [FunctionEnter2 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [FunctionTailcall2 関数](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
