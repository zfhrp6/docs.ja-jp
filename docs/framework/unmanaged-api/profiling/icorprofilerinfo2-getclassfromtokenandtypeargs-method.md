---
title: "ICorProfilerInfo2::GetClassFromTokenAndTypeArgs メソッド"
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
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a459f8e9ec6d63dc42d6a0a8f752c129d278524
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs メソッド
取得、`ClassID`指定したメタデータ トークンを使用して、型の`ClassID`いずれかの値が引数を入力します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `moduleID`  
 [in]型が含まれているモジュールの ID。  
  
 `typeDef`  
 [in]`mdTypeDef`型を参照するメタデータ トークン。  
  
 `cTypeArgs`  
 [in]指定した型の型パラメーターの数。 この値は、非ジェネリック型の 0 にする必要があります。  
  
 `typeArgs`  
 [in]配列`ClassID`値、それぞれが、型の引数。 値`typeArgs`場合は NULL にすることができます`cTypeArgs`は 0 に設定します。  
  
 `pClassID`  
 [out]ポインター、`ClassID`指定した型のです。  
  
## <a name="remarks"></a>コメント  
 呼び出す、`GetClassFromTokenAndTypeArgs`メソッドを`mdTypeRef`の代わりに、`mdTypeDef`メタデータ トークンが予期しない結果を持つことができます。 呼び出し元を解決する必要があります、`mdTypeRef`を、`mdTypeDef`渡すときです。  
  
 型が既に読み込まれていない場合は、呼び出す`GetClassFromTokenAndTypeArgs`読み込みで、さまざまなコンテキストでこの操作をトリガーします。 たとえば、モジュールまたはその他の型の読み込み中にこのメソッドを呼び出す可能性があります無限ループが発生するように、ランタイムが循環的に読み込みを試みます。  
  
 一般の使用`GetClassFromTokenAndTypeArgs`をお勧めします。 プロファイラーは、特定の種類のイベントに関心があるを場合格納する必要があります、`ModuleID`と`mdTypeDef`その種類、および使用の[icorprofilerinfo 2::getclassidinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)を確認するかどうか、指定された`ClassID`はの名前に、必要な型。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
