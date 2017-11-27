---
title: "ICorProfilerCallback::ModuleAttachedToAssembly メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ModuleAttachedToAssembly
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ModuleAttachedToAssembly
helpviewer_keywords:
- ICorProfilerCallback::ModuleAttachedToAssembly method [.NET Framework profiling]
- ModuleAttachedToAssembly method [.NET Framework profiling]
ms.assetid: b595798a-5d40-4cac-ab4f-911c61d2c5d2
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2c285a42bb48970756a54d5313d2839c76a9835c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackmoduleattachedtoassembly-method"></a>ICorProfilerCallback::ModuleAttachedToAssembly メソッド
モジュールが、親アセンブリにアタッチされていることをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ModuleAttachedToAssembly(  
    [in] ModuleID   moduleId,  
    [in] AssemblyID AssemblyId);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `moduleId`  
 [in]アタッチされるモジュールの ID。  
  
 `AssemblyId`  
 [in]モジュールが関連付けられている親アセンブリの ID。  
  
## <a name="remarks"></a>コメント  
 呼び出すことによってインポート アドレス テーブル (IAT) を通じて、モジュールを読み込むことができる`LoadLibrary`、またはメタデータの参照を使用します。 その結果、共通言語ランタイム (CLR) ローダーでは、モジュールが住んでいるアセンブリを判断するための複数のコード パスがあります。 したがって、可能であれば後に[icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)が呼び出されると、モジュールには、どのようなアセンブリはわからない内にあるし、親アセンブリ ID を取得することはできません。 `ModuleAttachedToAssembly`モジュールが、親アセンブリとその親アセンブリの ID を取得できるに関連付けられている場合、メソッドが呼び出されます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
