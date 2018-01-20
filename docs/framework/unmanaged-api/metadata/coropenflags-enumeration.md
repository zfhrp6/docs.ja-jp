---
title: "CorOpenFlags 列挙型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorOpenFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorOpenFlags
helpviewer_keywords: CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4447f648277576169c9004d1880283728639c8f3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="coropenflags-enumeration"></a>CorOpenFlags 列挙型
マニフェスト ファイルを開くときにメタデータの動作を制御するフラグ値を含めます。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`ofRead`|ファイルが読み取り専用で開かれることを示します。|  
|`ofWrite`|ファイルが書き込み用に開かれることを示します。<br /><br /> .winmd ファイルを開くときに `ofWrite` フラグを使用する場合は、`ofNoTransform` フラグも渡す必要があります。|  
|`ofReadWriteMask`|読み取りおよび書き込み用のマスク。|  
|`ofCopyMemory`|ファイルがメモリ内に読み込まれることを示します。 メタデータは自身のコピーを保持する必要があります。|  
|`ofCacheImage`|互換性のために残されています。 このフラグは無視されます。|  
|`ofManifestMetadata`|互換性のために残されています。 このフラグは無視されます。|  
|`ofReadOnly`|読み取り用にファイルが開かれることを示すへの呼び出し`QueryInterface`の[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)にすることはできません。|  
|`ofTakeOwnership`|呼び出しを使用してメモリが割り当てられたことを示す[CoTaskMemAlloc](http://msdn.microsoft.com/library/c4cb588d-9482-4f90-a92e-75b604540d5c)メタデータによって解放されるとします。|  
|`ofNoTypeLib`|互換性のために残されています。 このフラグは無視されます。|  
|`ofNoTransform`|.winmd ファイルの自動変換を無効にする必要があることを示します。 つまり、Windows Runtime タイプから .NET Framework タイプへの投射は無効になります。 詳細については、次を参照してください。[内部での .NET and Windows Runtime](http://msdn.microsoft.com/magazine/jj651569.aspx)です。|  
|`ofReserved1`|内部使用のために予約されています。|  
|`ofReserved2`|内部使用のために予約されています。|  
|`ofReserved`|内部使用のために予約されています。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorHdr.h  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [メタデータ列挙型](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
