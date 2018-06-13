---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9874c8e567a89fd3977be360666c86406f2cd395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455932"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] 以降のバージョンでサポート]  
  
 メモリ内のシンボルのストリームからバイトを読み取ります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `moduleId`  
 [in]メモリ内ストリームを含むモジュールの識別子。  
  
 `symbolsReadOffset`  
 [in]バイトの読み取りを開始位置をメモリ内ストリーム内のオフセット。  
  
 `pSymbolBytes`  
 [out]データのコピー先となるバッファーへのポインター。 バッファーが必要`countSymbolBytes`使用可能な領域。  
  
 `countSymbolBytes`  
 [in]コピーするバイト数。  
  
 `pCountSymbolBytesRead`  
 [out]メソッドが戻るときに、実際に読み取ったバイト数が含まれています。  
  
## <a name="return-value"></a>戻り値  
 `S_OK`、読み取られたバイト数、0 でない場合。  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`を使用して、モジュールが作成された場合<xref:System.Reflection.Emit>です。  
  
## <a name="remarks"></a>コメント  
 `ReadInMemorySymbols`メソッドの読み取りを試みます`countSymbolBytes`オフセットで始まるデータ`symbolsReadOffset`メモリ内のストリーム内です。 データがコピー`pSymbolBytes`が予期されて`countSymbolBytes`使用可能な領域。     `pCountSymbolsBytesRead` 実際の少ない可能性がありますが、読み取られたバイト数を含むより`countSymbolBytes`ストリームの末尾に達した場合。  
  
> [!NOTE]
>  現在の実装は、Reflection.Emit をサポートしていません。 メソッドを返しますのかどうか、モジュールは、Reflection.Emit を使用して作成された、`CORPROF_E_MODULE_IS_DYNAMIC`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerInfo7 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
