---
title: ICorProfilerInfo::GetModuleMetaData メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2491b700e8fac512f0d782a42e30ae3114e93c3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455547"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData メソッド
指定したモジュールにマップされるメタデータ インターフェイスのインスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `moduleId`  
 [in]インターフェイスのインスタンスをマップするモジュールの ID。  
  
 `dwOpenFlags`  
 [in]値、 [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)マニフェスト ファイルを開くためのモードを指定する列挙です。 のみ、 `ofRead`、`ofWrite`と`ofNoTransform`のビットが無効です。  
  
 `riid`  
 [in]インスタンスが取得するメタデータ インターフェイスの ID (GUID) の参照。 参照してください[メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)インターフェイスの一覧についてはします。  
  
 `ppOut`  
 [out]メタデータ インターフェイスのインスタンスのアドレスへのポインター。  
  
## <a name="remarks"></a>コメント  
 読み取り/書き込みモードで開かれるメタデータを要求することがありますが、プログラムのメタデータ実行の速度が遅くなります、コンパイラから場合と同様に、メタデータを最適化することはできませんに変更が行われるためです。  
  
 メタデータを所有している (リソースのモジュール) などの一部のモジュールはありません。 ような場合、 `GetModuleMetaData` S_FALSE とに null 値の HRESULT 値を返す *`ppOut`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
