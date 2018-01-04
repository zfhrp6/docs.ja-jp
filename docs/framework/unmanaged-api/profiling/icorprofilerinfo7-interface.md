---
title: "ICorProfilerInfo7 インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13282bec74df5e6159148aa4fbe92a84d035e044
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7 インターフェイス
[[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] 以降のバージョンでサポート]  
  
 サブクラス[ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)新しくを適用するためのメソッドでは、モジュールにメタデータが定義されているし、メモリ内のシンボルのストリームへのアクセスを提供するを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ApplyMetaData メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|新しく定義されたメタデータを適用、`IMetadataEmit::Define*`メソッドを指定されたモジュール。|  
|[GetInMemorySymbolsLength メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|メモリ内のシンボルのストリームの長さを返します。|  
|[ReadInMemorySymbols](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|メモリ内のシンボルのストリームからバイトを読み取ります。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
