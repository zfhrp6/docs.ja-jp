---
title: "CorMethodImpl 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodImpl
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodImpl
helpviewer_keywords: CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e82eb50e4850ffbb4d5fc67d9603a3128cf8bcf6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="cormethodimpl-enumeration"></a>CorMethodImpl 列挙型
メソッド実装の機能を記述する値が格納されます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`miCodeTypeMask`|コードの種類を説明するフラグ。|  
|`miIL`|メソッドの実装が Microsoft intermediate language (MSIL) であることを指定します。|  
|`miNative`|メソッド実装がネイティブであることを指定します。|  
|`miOPTIL`|メソッドの実装を optil で指定します。|  
|`miRuntime`|メソッドの実装が、共通言語ランタイムによって提供されたことを指定します。|  
|`miManagedMask`|コードがマネージかアンマネージかどうかを示すフラグです。|  
|`miUnmanaged`|メソッドの実装が管理されていることを指定します。|  
|`miManaged`|メソッドの実装が管理されていることを指定します。|  
|`miForwardRef`|メソッドが定義されていることを指定します。 このフラグは、マージ シナリオで、主に使用します。|  
|`miPreserveSig`|HRESULT の変換メソッドのシグネチャを変形することはできませんを指定します。|  
|`miInternalCall`|共通言語ランタイムでは、内部使用に予約されています。|  
|`miSynchronized`|メソッドがその内部から、シングル スレッドを指定します。|  
|`miNoInlining`|メソッドがインライン化できないことを指定します。|  
|`miAggressiveInlining`|メソッド必要があるないインライン展開可能な場合を指定します。|  
|`miNoOptimization`|メソッドを最適化されていないことを指定します。|  
|`miMaxMethodImplVal`|最大有効値、`CorMethodImpl`です。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
