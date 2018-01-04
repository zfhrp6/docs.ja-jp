---
title: "ICorProfilerObjectEnum::Clone メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.Clone
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d8e478eb9165b4aa5bf019f02f4f128931d928b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenumclone-method"></a>ICorProfilerObjectEnum::Clone メソッド
これのコピーに対するインターフェイス ポインターを取得[ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)インターフェイスです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]さらに、このコピーを指すインターフェイス ポインターへのポインター`ICorProfilerObjectEnum`インターフェイスです。 コピーは、この 1 つから個別に独自の列挙状態を維持します。 ただし、そのコピーの最初のカーソル位置はこの列挙子の現在のカーソル位置と同じなります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICorProfilerObjectEnum インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
