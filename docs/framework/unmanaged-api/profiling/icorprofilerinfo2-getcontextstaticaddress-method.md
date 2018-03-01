---
title: "ICorProfilerInfo2::GetContextStaticAddress メソッド"
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
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e92435927203bb2a75ff92d883470832126da080
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a>ICorProfilerInfo2::GetContextStaticAddress メソッド
指定したコンテキストのスコープ内にある指定したコンテキストの静的フィールドのアドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `classId`  
 [in]要求されたコンテキストの静的フィールドを格納するクラスの ID。  
  
 `fieldToken`  
 [in]要求されたコンテキストの静的フィールドのメタデータ トークン。  
  
 `contextId`  
 [in]要求されたコンテキストの静的フィールドのスコープとなっているコンテキストの ID。  
  
 `ppAddress`  
 [out]指定したコンテキスト内にある静的フィールドのアドレスへのポインター。  
  
## <a name="remarks"></a>コメント  
 `GetContextStaticAddress`メソッドは、次のいずれかを返す可能性があります。  
  
-   指定された静的フィールドに指定されたコンテキスト内のアドレスが割り当てられていない場合の CORPROF_E_DATAINCOMPLETE HRESULT です。  
  
-   ガベージ コレクション ヒープ内で使用できるオブジェクトのアドレス。 これらのアドレスはガベージ コレクションの後にプロファイラーを想定しないでくださいが有効であるために、ガベージ コレクションの後に無効になる可能性があります。  
  
 クラスのクラスのコンス トラクターが完了するまで`GetContextStaticAddress`静的フィールドの一部は既に初期化可能性がありますが、すべての静的フィールドの CORPROF_E_DATAINCOMPLETE が返され、ガベージ コレクション オブジェクトをルートします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
