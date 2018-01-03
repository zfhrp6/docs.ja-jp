---
title: "ICLRDataTarget インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget
helpviewer_keywords: ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73966ffe89f0e84d5a516f20962472d900332faa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget インターフェイス
共通言語ランタイム (CLR) のターゲット項目と対話するためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetCurrentThreadID メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|現在のスレッドのオペレーティング システムの識別子を取得します。|  
|[GetImageBase メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|指定したイメージのメモリのベース アドレスを取得します。|  
|[GetMachineType メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|ターゲット プロセスを使用している命令セットの種類の識別子を取得します。|  
|[GetPointerSize メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|(バイト単位)、現在のターゲットへのポインターのサイズを取得します。|  
|[GetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|指定した識別子のスレッドのコンテキストへのポインターを取得します。|  
|[GetTLSValue メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|指定したスレッドの指定したインデックスにあるスレッド ローカル ストレージ (TLS) の値を取得します。|  
|[ReadVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|指定されたバッファーに指定された仮想メモリ アドレスからデータを読み取ります。|  
|[Request メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|実装によって定義されているように、操作を要求する共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。|  
|[SetThreadContext メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|ターゲット プロセスで指定されたスレッドの現在のコンテキストを設定します。|  
|[SetTLSValue メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|ターゲット プロセス内の指定されたスレッドのスレッド ローカル ストレージ (TLS) の値を設定します。|  
|[WriteVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|指定された仮想メモリ アドレスに指定されたバッファーからデータを書き込みます。|  
  
## <a name="remarks"></a>コメント  
 API クライアント (つまりデバッガー) は、特定のターゲット項目に応じてこのインターフェイスを実装する必要があります。 たとえば、ライブ プロセスの実装は、メモリ ダンプの実装とは異なります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** ClrData.idl、ClrData.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICLRDataTarget2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
