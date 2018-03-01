---
title: "ICorProfilerInfo3::GetRuntimeInformation メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5eadd9970d29cc65d8411692407dcae5471e51c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation メソッド
プロファイリングされている共通言語ランタイム (CLR) のバージョン情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pClrInstanceId`  
 [out]プロセスで実行中の CLR インスタンスの代表者の ID です。 これと同じ、 `ClrInstanceID` Windows (ETW) のスタートアップ イベントのイベントのトレースをレポートすることです。  
  
 `pRuntimeType`  
 [out]ランタイムの型。 このパラメーターを返します`COR_PRF_DESKTOP_CLR`、CLR のデスクトップ バージョンのまたは`COR_PRF_CORE_CLR`Silverlight で使用されている CLR のコア バージョン。  
  
 `pMajorVersion`  
 [out]CLR のメジャー バージョン番号。  
  
 `pMinorVersion`  
 [out]CLR のマイナー バージョン番号。  
  
 `pBuildVersion`  
 [out]CLR のビルド バージョン番号。  
  
 `pQFEVersion`  
 [out]ソフトウェア更新プログラムに関連付けられている CLR のバージョン番号。  
  
 `cchVersionString`  
 [in]バッファーの文字の長さを`szVersionString`を指します。  
  
 `pcchVersionString`  
 [out]文字の長さの`szVersionString`します。  
  
 `szVersionString`  
 [out]CLR バージョン文字列です。  
  
## <a name="remarks"></a>コメント  
 任意のパラメーターに null を渡すことがあります。 ただし、 `pcchVersionString` null にすることはできませんしない限り、`szVersionString`も null です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
