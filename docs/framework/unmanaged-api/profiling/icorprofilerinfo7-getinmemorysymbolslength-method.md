---
title: ICorProfilerInfo7::GetInMemorySymbolsLength メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e662270fc8db3fb85e058e8d4f3346f58f79bb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457962"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7::GetInMemorySymbolsLength メソッド
[.NET Framework 4.6.1 以降のバージョンでのみでサポート]  
  
 メモリ内のシンボルのストリームの長さを返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `moduleId`  
 [in]メモリ内ストリームを含むモジュールの識別子。  
  
 pCountSymbolBytes  
 [out]ポインター、`DWORD`値をメソッドが戻るときに、バイト単位のストリームの長さが含まれています。  
  
## <a name="return-value"></a>戻り値  
 このメソッドを返します`S_OK`かどうか、メモリ ストリームの長さを決定する場合でも、ゼロ (0) であります。  
  
 このメソッドを返します`CORPROF_E_MODULE_IS_DYNAMIC`を使用して、メソッドが作成された場合<xref:System.Reflection.Emit?displayProperty=nameWithType>です。  
  
## <a name="remarks"></a>コメント  
 モジュールは、メモリ内のシンボルには場合、に、ストリームの長さが格納されます。`pCountSymbolBytes`です。 モジュールは、メモリ内のシンボルを持っていない場合`*pCountSymbolBytes = 0`です。  
  
> [!NOTE]
>  現在の実装は、Reflection.Emit をサポートしていません。 メソッドを返しますのかどうか、モジュールは、Reflection.Emit を使用して作成された、`CORPROF_E_MODULE_IS_DYNAMIC`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerInfo7 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
