---
title: "ICorProfilerInfo::SetILFunctionBody メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d97827555ecefb775323fdf9dbd6577f941f1e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a>ICorProfilerInfo::SetILFunctionBody メソッド
指定したモジュール内の指定した関数の本体を置換します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `moduleId`  
 [in]関数が存在するモジュールの ID。  
  
 `methodid`  
 [in]本文を置換する関数のトークンです。  
  
 `pbNewILMethodHeader`  
 [in]関数の新しいヘッダー。  
  
## <a name="remarks"></a>コメント  
 `SetILFunctionBody`関数の新しい本文をポイントし、必要に応じて、内部データ構造を調整できるように、メソッドは、メタデータ内の関数の相対仮想アドレスを置き換えます。  
  
 `SetILFunctionBody` ・ イン タイム (JIT) コンパイラでコンパイルされていることはありません関数だけにメソッドを呼び出すことができます。  
  
 使用して、 [icorprofilerinfo::getilfunctionbodyallocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)新しいメソッドがバッファーに互換性があることを確認する領域を割り当てるためのメソッドです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
