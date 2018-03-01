---
title: "OSINFO 構造体"
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
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd30fe7904fa6c0685dd9c39931cc545e4e30583
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="osinfo-structure"></a>OSINFO 構造体
アセンブリまたはモジュールのオペレーティング システムに関する詳細情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`dwOSPlatformId`|Microsoft Windows プラットフォーム関数で定義された識別子の値のいずれかの`GetVersionEx`します。 次の値がサポートされています。<br /><br /> -VER_PLATFORM_WIN32s、つまり 0x0000、Microsoft Windows 3.1 を指定します。<br />-VER_PLATFORM_WIN32_WINDOWS、または 0x0001、Windows 95、Windows 98、またはそれらの子とオペレーティング システムを指定します。<br />-VER_PLATFORM_WIN32_NT、または 0x0010、Windows NT またはそこから子とオペレーティング システムを指定します。|  
|`dwOSMajorVersion`|オペレーティング システムのメジャー バージョン、または任意のバージョンを示すために NULL 値。|  
|`dwOSMinorVersion`|オペレーティング システムのマイナー バージョン、または任意のバージョンを示すために NULL 値。|  
  
## <a name="remarks"></a>コメント  
 `OSINFO`基づく、`OSVERSIONINFOEX`構造体をで使用される関数への呼び出し、Microsoft Windows プラットフォーム`GetVersionEx`です。 この構造体の使用は、ASSEMBLYMETADATA 構造体によってをそのオペレーティング システムのサポートを示します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [メタデータ構造体](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
