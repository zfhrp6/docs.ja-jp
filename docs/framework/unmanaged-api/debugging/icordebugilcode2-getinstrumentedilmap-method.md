---
title: ICorDebugILCode2::GetInstrumentedILMap メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode2.GetInstrumentedILMap
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 7a4e3085-8f95-40ef-a4be-7d6146f47ce2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a712ed9e3534ca6bb2962989f1ab3750a25d539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417903"
---
# <a name="icordebugilcode2getinstrumentedilmap-method"></a>ICorDebugILCode2::GetInstrumentedILMap メソッド
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 このインスタンスについて、プロファイラー インストルメント中間言語 (IL: intermediate language) オフセットから、元のメソッドの IL オフセットまでのマップを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetInstrumentedILMap(  
   [in] ULONG32 cMap,  
   [out] ULONG32 *pcMap,  
   [out, size_is(cMap), length_is(*pcMap)] COR_IL_MAP map[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 cMap  
 [入力] `map` 配列の記憶容量。 詳細については、次の「解説」を参照してください。  
  
 pcMap  
 [out]マップ配列へ書き込まれた COR_IL_MAP 値の数。  
  
 map  
 [out]元のメソッドの IL へのマッピングにプロファイラー インストルメント IL からの情報を提供する COR_IL_MAP 値の配列。  
  
## <a name="remarks"></a>コメント  
 呼び出して、プロファイラーがマッピングを設定する場合、 [icorprofilerinfo::setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)メソッド、デバッガーはスタックのオフセット IL を計算するときに、マッピングを内部的に使用して、マッピングの取得には、このメソッドを呼び出すことができますトレースと変数の有効期間。  
  
 場合`cMap`は 0 と`pcMap`以外**null**、 `pcMap` COR_IL_MAP が可能な値の数に設定されています。 `cMap` が 0 以外の場合は、`map` アレイの記憶容量を表します。 メソッドが戻るときに`map`の最大値が含まれています`cMap`項目、および`pcMap`に実際に書き込まれた COR_IL_MAP 値の数に設定されている、`map`配列。  
  
 IL がインストルメント化されていない、またはプロファイラーによってマッピングが指定されなかった場合、このメソッドは `S_OK` を返し、`pcMap` を 0 に設定します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Icorprofilerinfo::setilinstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)  
 [ICorDebugILCode2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
