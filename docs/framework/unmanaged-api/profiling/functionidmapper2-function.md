---
title: "FunctionIDMapper2 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionIDMapper2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionIDMapper2
helpviewer_keywords: FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5da0acdd7622ad06879b57d8d4b2a9faeba10ca9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2 関数
関数の特定の識別子が可能性がありますで使用される代替 ID に再割り当てされることをプロファイラーに通知、 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)、 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)、および[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)、または[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)、および[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)その関数のコールバック。 また `FunctionIDMapper2` により、プロファイラーはその関数のコールバックを受信するかどうかを示すことができます。  
  
## <a name="syntax"></a>構文  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `funcId`  
 [入力] 再割り当てされる関数識別子。  
  
 `clientData`  
 [入力] ランタイム間のあいまいさを解消するために使用されるデータへのポインター。  
  
 `pbHookFunction`  
 [出力] 出力プロファイラーが `FunctionEnter3`、`FunctionLeave3`、`FunctionTailcall3`、または  `FunctionEnter3WithInfo`、`FunctionLeave3WithInfo`、`FunctionTailcall3WithInfo` の各コールバックを受信する場合は `true` に設定される値へのポインター。それ以外の場合、この値は  `false` に設定されます。  
  
## <a name="return-value"></a>戻り値  
 プロファイラーは、実行エンジンが代替関数識別子として使用する値を返します。 `false` で `pbHookFunction` を返さない限り、戻り値を null にすることはできません。 これ以外の状況で戻り値を null にすると、プロセスの中止など、予測できない結果が発生します。  
  
## <a name="remarks"></a>コメント  
 このメソッドによって拡張、 [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)クライアント データを渡すために使用する追加パラメーターを持つ関数です。 クライアント データを使用すると、ランタイム間のあいまいさが解消されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Icorprofilerinfo::setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [Icorprofilerinfo 3::setfunctionidmapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [プロファイリング グローバル静的関数](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
