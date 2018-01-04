---
title: "ICorProfilerInfo6 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfilerInfo6
api_location: mscorwks.dll
api_type: COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 805f1e451b2c13c356d904c42dff87304aa2093c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo6-interface"></a>ICorProfilerInfo6 インターフェイス
[.NET Framework 4.6 およびそれ以降のバージョンでサポート]  
  
 サブクラス[ICorProfilerInfo5](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)特定 NGen モジュールおよびインラインの特定のメソッドに定義されているすべてのメソッドの列挙子を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|指定した NGen モジュールに属するし、は特定のメソッドの本体でインライン展開をすべてのメソッドの列挙子を返します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
